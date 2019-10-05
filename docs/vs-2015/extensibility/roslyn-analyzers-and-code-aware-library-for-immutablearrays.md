---
title: Roslyn 분석기 및 코드 인식 라이브러리 ImmutableArrays에 대 한 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 44cb171594a6d595652b3c013505927bd82f947e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685244"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>ImmutableArrays에 대한 Roslyn 분석기 및 코드 인식 라이브러리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 [.NET 컴파일러 플랫폼](https://github.com/dotnet/roslyn) ("Roslyn")를 사용 하면 코드 인식 라이브러리를 작성할 수 있습니다. 코드 인식 라이브러리는 가장 좋은 방법은 또는 오류를 방지 하려면 기능을 사용할 수 있습니다 및 라이브러리를 사용할 수 있습니다 (Roslyn 분석기) 도구를 제공 합니다. 이 항목에서는 사용할 때 일반적인 오류를 catch 하는 실제 Roslyn 분석기를 빌드하는 방법을 보여 줍니다.는 [NIB: 변경할 수 없는 컬렉션](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet 패키지. 예제에는 분석기가 발견 한 코드 문제에 대 한 코드 수정 제공 하는 방법을 보여 줍니다. 사용자 코드 수정 사항은 Visual Studio 전구 UI에서에서 참조 하 고 코드에 대 한 수정 프로그램이 자동으로 적용할 수 있습니다.

## <a name="getting-started"></a>시작
이 예제를 빌드하려면 다음이 필요 합니다.

- Visual Studio 2015 (하지는 Express Edition) 또는 이후 버전입니다. 무료 따르면 [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md). 확인할 수도 있습니다, Visual Studio를 설치 하는 경우 동시에 SDK를 설치 하려면 일반 도구에 있는 Visual Studio 확장성 도구입니다. Visual Studio를 이미 설치한 경우 설치할 수도 있습니다이 SDK 주 메뉴로 이동 하 여 **파일 &#124; 새로 만들기 &#124;프로젝트...** 왼쪽된 탐색 창에서 C#를 선택 하 고 다음 확장을 선택 합니다. 선택 하는 경우는 "**Visual Studio 확장성 도구를 설치할**" 이동 경로 탐색 프로젝트 템플릿을 묻는 다운로드 하 여 SDK를 설치 합니다.

- [.NET 컴파일러 플랫폼 ("Roslyn") SDK](https://aka.ms/roslynsdktemplates)합니다. 주 메뉴로 이동 하 여이 SDK를 설치할 수도 있습니다 **파일 &#124; 새로 만들기 &#124; 프로젝트...** , 선택 **C#** 왼쪽된 탐색 창에서을 차례로 선택 **확장성**합니다. 선택 하는 경우 "**.NET Compiler Platform SDK 다운로드**" 이동 경로 탐색 프로젝트 템플릿을 묻는 다운로드 하 여 SDK를 설치 합니다. 이 SDK에 포함 된 [Roslyn 구문 시각화 도우미](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)합니다. 코드 모델 유형을 파악이 매우 유용한 도구를 사용 하면 확인 해야 할 사용자 분석기에서입니다. 분석기 인프라 코드만 필요한 경우를 실행 하 고 관련 코드 분석에 집중할 수 있도록 특정 코드 모델 형식에 대 한 코드를 호출 합니다.

## <a name="whats-the-problem"></a>문제가 뭔가요?
ImmutableArray를 라이브러리에 제공 imagine (예를 들어 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>)를 지원 합니다. C# 개발자는 많은.NET 배열 경험이 있습니다. 그러나 ImmutableArrays 및 최적화 기술 구현에 사용의 특성상 C# 개발자 intuitions 발생할 라이브러리 사용자는 손상 된 코드를 작성 하려면 아래 설명 된 대로. 또한 사용자가.NET을 사용 하 여 Visual Studio에 사용 되는 품질 환경에 없는 실행된 시간까지 해당 오류가 표시 되지 않습니다.

사용자가 다음과 같은 코드 작성 방법을 잘 알고 있습니다.

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

후속 줄의 코드만으로 채워 넣을 빈 배열 만들기 및 컬렉션 이니셜라이저 구문을 사용 하는 C# 개발자에 게 매우 친숙 합니다. 그러나 코드는 ImmutableArray 런타임에 충돌 동일한 작성:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

첫 번째 오류 구조체를 사용 하 여 내부 데이터 저장소를 래핑하는 ImmutableArray 구현 되었기 때문입니다. 구조체는 매개 변수가 없는 생성자가 있어야 있도록 `default(T)` 식은 모든 구조체를 반환할 수 있습니다 0 또는 null 멤버입니다. 코드에 액세스 하는 경우 `b1.Length`, 내부 저장소 배열 ImmutableArray 구조체에 있기 때문에 런타임 null 역참조 오류는 합니다. 빈 ImmutableArray를 만들려면 올바른 방법은 `ImmutableArray<int>.Empty`합니다.

 컬렉션 이니셜라이저를 사용 하 여 오류 ImmutableArray.Add 메서드를 호출할 때마다 새 인스턴스를 반환 하기 때문에 발생 합니다. ImmutableArrays 변경 되지 않으면 새 요소를 추가 하면, 때문에 돌아갈 있습니다를 새 ImmutableArray 개체 (이전에 기존 ImmutableArray를 사용 하 여 성능상의 이유로 저장소를 공유할 수 있습니다). 때문에 `b2` 호출 하기 전에 첫 번째 ImmutableArray를 가리키는 `Add()` 다섯 번 `b2` ImmutableArray를 기본값입니다. 오류를 역참조 호출 길이에 null 충돌 합니다. 사용 하는 수동으로 추가 호출 하지 않고는 ImmutableArray를 초기화 하는 올바른 방법은 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`합니다.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>관련 구문 노드 형식에 분석기를 트리거할 수 찾기
분석기 빌드를 시작 하려면 먼저 파악 SyntaxNode 유형을 검색할 해야 합니다.   시작 메뉴에서 구문 시각화 도우미 **보기 &#124; 다른 Windows &#124; Roslyn 구문 시각화 도우미**합니다.

편집기의 캐럿 선언 하는 줄에 배치 `b1`합니다. 구문 시각화 도우미에서 표시 하는 것이 보면는 `LocalDeclarationStatement` 구문 트리의 노드입니다. 이 노드의 `VariableDeclaration`,이 `VariableDeclarator`,이 `EqualsValueClause`, 마지막는 `ObjectCreationExpression`합니다. 구문 시각화 도우미 트리의 노드를 클릭 하면 해당 노드에 의해 표시 되는 코드를 표시 하려면 편집기 창의 구문을 강조 표시 됩니다. C# 문법에서 사용 된 이름과 일치 하는 SyntaxNode 하위 형식의 이름입니다.

## <a name="creating-the-analyzer-project"></a>분석기 프로젝트 만들기
주 메뉴에서 선택 **파일 &#124; 새로 만들기 &#124; 프로젝트...** . 에 **새 프로젝트** 대화 아래에 있는 **C#** 프로젝트 왼쪽된 탐색 모음에서 확장성을 선택 하 고 오른쪽 창에서 선택 합니다 **분석기를 사용 하 여 코드 수정** 프로젝트 템플릿입니다. 이름을 입력 하 고 대화 상자를 확인 합니다.

템플릿을은 DiagnosticAnalyzer.cs 파일을 엽니다. 해당 편집기 버퍼 탭을 선택 합니다. 이 파일에는 분석기 클래스 (구성 프로젝트 이름에서 제공한)에서 파생 되는 `DiagnosticAnalyzer` (Roslyn API 형식). 새 클래스에는 `DiagnosticAnalyzerAttribute` 에 분석기를 선언도 C# 언어와 관련이 있으므로 컴파일러 검색에 분석기를 로드 합니다.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# 코드를 대상으로 하는 Visual Basic을 사용 하 여 분석기를 구현할 수 있습니다 및 그 반대의 경우도 마찬가지입니다. 것이 더 중요 한 언어 중 하나 또는 둘 다에 분석기를 대상으로 하는지 여부를 선택할 DiagnosticAnalyzerAttribute. 언어의 자세한 모델링 해야 하는 보다 복잡 한 분석기는 단일 언어를 대상만 수 있습니다. 에 분석기를 예를 들어만 확인 하면 형식 이름 또는 공용 멤버 이름, Roslyn Visual Basic 및 C#에서 제공 하는 일반적인 언어 모델을 사용할 수 있습니다. 예를 들어, FxCop 경고 클래스를 구현 함을 <xref:System.Runtime.Serialization.ISerializable>, 클래스 없는 <xref:System.SerializableAttribute> 특성 언어 독립적 이며 Visual Basic 및 C# 코드에 대해 작동 합니다.

## <a name="initalizing-the-analyzer"></a>초기화 분석기
약간 아래로 스크롤하여는 `DiagnosticAnalyzer` 보려는 클래스를 `Initialize` 메서드. 컴파일러는 분석기를 활성화 하는 경우이 메서드를 호출 합니다. 메서드는는 `AnalysisContext` 컨텍스트 정보를 가져오기 하 고 분석 하려는 코드의 종류에 대 한 이벤트에 대 한 콜백을 등록 하 여 분석기를 사용할 수 있는 개체입니다.

```csharp
public override void Initialize(AnalysisContext context) {}
```

이 컨텍스트에서 메서드 및 형식"." 새 줄을 엽니다 에 Intellisense 완성 목록을 참조 하세요. 여러 완성 목록에서 볼 수 `Register…` 다양 한 종류의 이벤트를 처리 하는 방법입니다. 예를 들어, 첫 번째 `RegisterCodeBlockAction`에 일반적으로 중괄호 사이 코드 블록에 대 한 코드를 다시 호출 합니다. 블록에 대 한 등록도 다시 호출 코드에는 필드, 특성에 지정 된 값 또는 선택적 매개 변수 값의 이니셜라이저에 대 한 합니다.

또 다른 예로, `RegisterCompilationStartAction`, 여러 위치를 통해 상태를 수집 해야 하는 경우에 유용 컴파일 시작 시 코드 다시 호출 합니다. 데이터 구조를 예를 들어 수집을 사용 하는 모든 기호를 만들고 일부 구문 또는 기호에 대 한 프로그램 분석기가 다시 호출 될 때마다 데이터 구조의 각 위치에 대 한 정보를 저장할 수 있습니다. 컴파일 종료로 인해 다시 호출 하는 경우 저장, 예를 들어, 각 코드를 사용 하 여 기호를 보고 하는 모든 위치를 분석할 수 있습니다 `using` 문입니다.

사용 하는 **구문 시각화 도우미**, 컴파일러는 ObjectCreationExpression 처리할 때 호출 될 것임을 알아보았습니다. 이 코드를 사용 하 여 콜백을 설정 합니다.

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

구문 노드 및 개체 생성 구문 노드만 대 한 필터를 등록 합니다. 규칙에 따라 분석기 작성자는 상태 비저장 분석기를 유지 하는 데 도움이 되는 작업을 등록 하는 경우 람다를 사용 합니다. Visual Studio 기능을 사용할 수 있습니다 **관례에서 생성** 만들려는 `AnalyzeObjectCreation` 메서드. 이 올바른 형식을 생성 컨텍스트 매개 변수를 너무 합니다.

## <a name="setting-properties-for-users-of-your-analyzer"></a>프로그램 분석기의 사용자에 대 한 속성을 설정합니다.
에 분석기 상자가 표시 되도록 Visual Studio UI에 적절 하 게, 검색할 및에 분석기를 식별 하는 코드의 다음 줄을 수정 합니다.

```csharp
internal const string Category = "Naming";
```

변경 `"Naming"` 에 `"API Guidance"`입니다.

다음 찾기 및 사용 하 여 프로젝트에서 Resources.resx 파일을 엽니다는 **솔루션 탐색기**합니다. 프로그램 분석기, 제목 등에 대 한 설명에 넣을 수 있습니다. 이러한 모든 값을 변경할 수 있습니다 `“Don’t use ImmutableArray<T> constructor”` 지금은 합니다. 인수 문자열에 서식 지정 문자열을 입력할 수 있습니다 ({0}, {1}등), 호출 하는 경우 이후 `Diagnostic.Create()`, 매개 변수 배열을 전달할 인수를 제공할 수 있습니다.

## <a name="analyzing-an-object-creation-expression"></a>개체 생성 식을 분석
`AnalyzeObjectCreation` 메서드는 다른 유형의 코드 분석기 프레임 워크에서 제공 되는 컨텍스트를 사용 합니다. Initialize 메서드의 `AnalysisContext` 작업에 분석기를 설정 하는 콜백을 등록할 수 있습니다. 합니다 `SyntaxNodeAnalysisContext`, 예에 `CancellationToken` 주위 전달할 수 있습니다. 사용자가 편집기에서 입력을 시작 하는 경우 Roslyn 작업을 저장 하 고 성능 향상에 분석기를 실행 취소 합니다. 또 다른 예로,이 컨텍스트 개체 생성 구문 노드를 반환 하는 노드 속성이 있습니다.

구문 노드 작업을 필터링 하는 형식임을 가정할 수 있습니다 하 고 노드를 가져옵니다.

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>처음에 분석기를 사용 하 여 Visual Studio를 시작합니다.
빌드에 분석기를 실행 하 여 Visual Studio를 시작 (키를 눌러 **F5**). 시작 프로젝트 때문에 합니다 **솔루션 탐색기** , 코드 및 VSIX를 코드 빌드를 실행 하는 VSIX 프로젝트 이며 해당 VSIX 설치를 사용 하 여 Visual Studio를 시작 합니다. 이러한 방식으로 Visual Studio를 시작 하 여 Visual Studio의 주 사용은 영향을 받지 테스트 인스턴스 분석기를 빌드하는 동안 고유한 레지스트리 하이브를 사용 하 여 시작 합니다. 이러한 방식으로 시작 하면 처음으로 Visual Studio를 처음 시작할 때 Visual Studio 설치 후 비슷합니다 여러 초기화를 수행 합니다.

 콘솔 프로젝트를 만들고 콘솔 응용 프로그램 Main 메서드로 배열 코드를 입력:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

사용 하 여 코드의 줄 `ImmutableArray` 물결선을 변경할 수 없는 NuGet 패키지를 가져오고 추가 해야 하기 때문에 있는 `using` 문을 코드에 있습니다. 오른쪽 포인터 단추에서 프로젝트 노드를 **솔루션 탐색기** 선택한 **NuGet 패키지 관리...** . NuGet 관리자에서 검색 상자에 "변경할 수 없는"를 입력 하 고 "System.Collections.Immutable" 항목 선택 ("Microsoft.Bcl.Immutable"을 선택 하지 않으면)의 왼쪽 창과 오른쪽 창에서 설치 단추를 누르십시오. 프로젝트 참조에 대 한 참조를 추가 패키지를 설치 합니다.

아래에 빨간색 물결선을 계속 표시 `ImmutableArray`을 누릅니다 식별자에 캐럿을 배치 하므로 **CTRL +.** (마침표)에 제안 된 수정 프로그램 메뉴를 표시 하 고 적절 한 추가할 `using` 문입니다.

**모두 저장 하 고 닫습니다** 깨끗 한 상태로 계속 하 게 지금은 Visual Studio의 두 번째 인스턴스.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>편집 하며 계속 하기는 분석기를 사용 하 여 완료 합니다.
Visual Studio의 첫 번째 인스턴스의 경우에서 맨 앞에 중단점을 설정 하 `AnalyzeObjectCreation` 메서드를 눌러 **F9** 첫 번째 줄에 캐럿을 사용 하 여 합니다.

에 분석기를 사용 하 여 다시 시작 **F5**, Visual Studio의 두 번째 인스턴스에서 마지막으로 만든 콘솔 응용 프로그램 다시 여세요.

Roslyn 컴파일러 개체 생성 식을 확인 하 고에 분석기를 호출 하기 때문에 중단점에서 Visual Studio의 첫 번째 인스턴스를 반환 합니다.

**개체 만들기 노드를 가져옵니다.** 설정 하는 줄 건너뛰기 합니다 `objectCreation` 키를 눌러 변수 **F10**, 및를 **직접 실행 창** 식을 계산할 `“objectCreation.ToString()”`합니다. 변수를 가리키는 구문 노드는 코드를 표시 `"new ImmutableArray<int>()"`, 방금 원하는 내용을 대 한 합니다.

**ImmutableArray를 가져올\<T > 형식 개체입니다.** 생성 될 형식이 ImmutableArray 인지 확인 해야 합니다. 먼저이 형식을 나타내는 개체를 가져옵니다. 의미 체계 모델을 사용 하 여 올바른 형식이 정확 하 게 해야 하 고 tostring () 문자열을 비교 하지 형식을 확인할 수 있습니다. 함수의 끝에 있는 코드의 다음 줄을 입력 합니다.

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

제네릭 매개 변수의 수와 backquotes (')를 사용 하 여 메타 데이터의 제네릭 형식을 지정합니다. "... 나타나지 않는 이유 ImmutableArray\<T > "메타 데이터 이름에서입니다.

의미 체계 모델 기호, 데이터 흐름, 변수 수명에 대해 질문할 수 있는 많은 유용한 작업 있습니다. Roslyn 의미 체계 모델에서 다양 한 이유로 엔지니어링 (성능, 잘못 된 코드 등을 모델링 합니다.) 구문 노드를 구분 합니다. 컴파일 모델을 정확 하 게 비교에 대 한 참조에 포함 된 정보를 조회 해야 합니다.

편집기 창의 왼쪽에 노란색 실행 포인터를 끌어 수 있습니다. 설정 하는 줄까지 끌 합니다 `objectCreation` 변수 및 코드를 사용 하 여 새 줄 건너뛰기 **F10**합니다. 변수 위로 마우스 포인터를 가져가면 경우 `immutableArrayOfType`, 의미 체계 모델의 정확한 형식을 있음을 표시 합니다.

**개체 생성 식의 형식을 가져옵니다.** "Type"이 문서에서는 몇 가지 방법으로 사용 되지만 즉, 새 검색어 경우 Foo의 모델 해야 하는 식입니다. ImmutableArray 인지 확인 된 개체 생성 식의 형식을 가져오기 위해 필요한\<T > 형식입니다. 개체 생성 식에 형식 기호 (ImmutableArray)에 대 한 기호 정보를 얻으려면 의미 체계 모델을 다시 사용 합니다. 함수의 끝에 있는 코드의 다음 줄을 입력 합니다.

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

편집기 버퍼에 불완전 하거나 잘못 된 코드를 처리 하 여 분석기 해야 하기 때문에 (예를 들어, 누락 된 `using` 문)를 확인 해야 `symbolInfo` 되 `null`. 분석을 완료 하려면 기호 정보 개체에서 명명된 된 형식 (INamedTypeSymbol)를 가져올 필요 합니다.

**형식을 비교 합니다.** 무엇 인지 (개방형 제네릭 형식)에서 생성 되는 것에 대 한 기호 정보를 쿼리 및 해당 결과를 비교 하는 개방형 제네릭 형식 t를 모색 중인 것 이므로 코드에서 형식이 제네릭 형식인 구체적인 `immutableArrayOfTType`합니다. 메서드의 끝에 다음을 입력 합니다.

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**진단을 보고 합니다.** 진단 보고 하는 것은 매우 쉽습니다. 사용할 규칙 전에 Initialize 메서드에 정의 되어 있는 프로젝트 템플릿에서 만들어집니다. 코드에서이 이런 오류가 이기 때문에 대체 하는 규칙을 초기화 하는 줄을 변경할 수 있습니다 `DiagnosticSeverity.Warning` (녹색 표시 선은) 사용 하 여 `DiagnosticSeverity.Error` (빨간색 구부러진 곡선은). 규칙의 나머지 연습을 시작할 때 편집한 리소스를 초기화 합니다. 오류 표시선 개체 생성 expresssion 형식 사양의 위치에 대 한 위치를 보고 해야 합니다. 이 코드를 입력 합니다 `if` 블록:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

함수는 (아마도 서식이 다르게 지정)이 같습니다.

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

보고 수 있습니다 분석기 작업 (Visual Studio의 첫 번째 인스턴스를 반환 하지) 있도록 중단점을 제거 합니다. 누릅니다 메서드를 처음으로 실행 포인터를 끌어 **F5** 실행을 계속 합니다. Visual Studio의 두 번째 인스턴스를 다시 전환 하면 컴파일러는 코드를 다시 검사 하기 시작한에 분석기를 호출 합니다. 아래에 구불구불한 선이 표시 `ImmutableType<int>`합니다.

## <a name="adding-a-code-fix-for-the-code-issue"></a>"코드 수정" 코드 문제에 대 한 추가
를 시작 하기 전에 Visual Studio의 두 번째 인스턴스를 닫고 첫 번째 인스턴스의 (여기서 개발 하는 분석기) Visual Studio에서 디버깅을 중지 합니다.

**새 클래스를 추가 합니다.** 솔루션 탐색기에서 프로젝트 노드 바로 가기 메뉴 (오른쪽 포인터 단추)를 사용 하 하며 새 항목을 추가 하려면 선택 키를 누릅니다. 라는 클래스를 추가 `BuildCodeFixProvider`합니다. 이 클래스에서 파생 되어야 `CodeFixProvider`를 사용 해야 하 고 **CTRL +.** (마침표)를 올바른 추가 하는 코드 수정 사항을 호출 `using` 문입니다. 이 클래스는 또한로 주석을 달아야 해야 `ExportCodeFixProvider` 특성을 추가 해야 합니다는 `using` 해결 하는 문을 `LanguageNames` 열거형입니다. 클래스 파일에 다음 코드를 사용 하 여 해야 합니다.

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Out 스텁 멤버를 파생 합니다.** 이제는 식별자에 편집기 캐럿을 배치 `CodeFixProvider` 키를 누릅니다 **CTRL +.** (마침표)이 추상 기본 클래스에 대 한 구현을 스텁 하 합니다. 이 속성 및 메서드를 생성합니다.

**속성을 구현 합니다.** 입력 합니다 `FixableDiagnosticIds` 속성의 `get` 다음 코드를 사용 하 여 본문:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn 진단 결합 하 고는 문자열일 뿐 이러한 식별자를 비교 하 여 수정 합니다. 프로젝트 템플릿, 진단 ID를 생성 및 자유롭게 변경할 수 있습니다. 속성의 코드는 방금 분석기 클래스에서 ID를 반환합니다.

**RegisterCodeFixAsync 메서드 컨텍스트를 사용 합니다.** 컨텍스트는 여러 진단 코드 수정 적용 하거나 코드 줄에 둘 이상의 문제 수 있으므로 중요 합니다. "컨텍스트입니다."를 입력 하는 경우 메서드의 본문에 Intellisense 완성 목록이 표시 됩니다 몇 가지 유용한 멤버. CancellationToken 멤버 항목 수정 취소 하려는 경우를 확인할 수 있습니다. 많은 유용한 멤버가 있고 프로젝트 및 솔루션 모델 개체에 사용할 수 있습니다 문서 멤버 임 시작 된 범위 구성원이 며 종료 코드 위치의 진단 보고 하는 시점을 지정 합니다.

**비동기일 수 메서드를 확인 합니다.** 가장 먼저 해야 할 수정 되도록 생성 된 메서드 선언 되는 `async` 메서드. 추상 클래스의 구현을 스텁 코드 수정 사항을 포함 하지 않습니다 합니다 `async` 메서드가 반환 하는 경우에 키워드는 `Task`합니다.

**구문 트리의 루트를 가져옵니다.** 변경 내용으로 새 구문 트리를 생성 하는 데 필요한 코드를 수정 하려면 코드 수정 사항을 만듭니다. 해야 합니다 `Document` 호출 컨텍스트에서 `GetSyntaxRootAsync`합니다. 즉 비동기 메서드를 알 수 없는 작업이 가능한 경우 디스크에서 파일을 가져오는, 등, 구문 분석에 대 한 Roslyn 코드 모델을 작성, 구문 트리를 가져오기 때문입니다. Visual Studio UI는 사용 하 여이 시간 동안 응답 해야 `async` 사용 하도록 설정 합니다. 다음 메서드에서 코드 줄을 바꿉니다.

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**문제가 있는 노드를 찾습니다.** 컨텍스트의 범위 에서만 변경 해야 하는 코드 아닐 찾아야 노드에 전달 합니다. 보고 된 진단만 (여기서 오류 표시선 속했던) 형식 식별자에 대 한 범위를 제공 하지만 전체 개체 생성 식에 교체 해야 포함 하는 `new` keywoard 시작과 끝에 괄호입니다. 메서드에 다음 코드를 추가 합니다. (사용 하 여 **CTRL +.** 추가 하는 `using` 방침 `ObjectCreationExpressionSyntax`):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **전구 UI에 대 한 코드 수정 사항을 등록 합니다.** 코드 수정 사항을 등록 하면 Visual Studio 전구 UI에 Roslyn 자동으로 연결 합니다. 최종 사용자가 사용할 수 있습니다 나타납니다 **CTRL +.** 프로그램 분석기 물결선 잘못 된 경우 (마침표) `ImmutableArray<T>` 생성자 사용 합니다. 코드 픽스 공급자만 실행 되므로 문제가 발생 하는 경우, 원하는 개체 생성 식이 있다고 가정할 수 있습니다. 컨텍스트 매개 변수에서 새 코드 수정 사항을의 끝에 다음 코드를 추가 하 여 등록할 수 있습니다 `RegisterCodeFixAsync` 메서드:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

식별자에서 편집기의 캐럿을 배치 해야 `CodeAction`를 사용 하 여 **CTRL +.** (마침표) 적절 한 추가할 `using` 이 형식에 대 한 문입니다.

그런 다음에 편집기 캐럿을 배치 합니다 `ChangeToImmutableArrayEmpty` 식별자 및 사용 하 여 **CTRL +.** 이 메서드 스텁 생성를 다시.

추가한 마지막 코드 조각은이 전달 하 여 코드 수정 사항을 등록을 `CodeAction` 및 발견 된 문제의 종류에 대 한 진단 ID입니다. 이 예제에서는 하나씩만 있기이 코드를 제공 하는 진단 ID를 수정 하므로 방금 진단 Id 배열의 첫 번째 요소를 전달할 수 있습니다. 만들 때의 `CodeAction`, 전구 UI에 대 한 코드 수정 사항 설명으로 사용 해야 하는 텍스트에 전달 합니다. CancellationToken을 사용 하 고 새 문서를 반환 하는 함수에 전달할 수도 있습니다. 새 문서에 호출 하는 패치가 적용 된 코드를 포함 하는 새 구문 트리 `ImmutableArray.Empty`합니다. 이 코드 조각은 objectCreation 노드와 컨텍스트의 문서를 통해 닫을 수 있도록 하는 람다를 사용 합니다.

**새 구문 트리를 생성 합니다.** 에 `ChangeToImmutableArrayEmpty` 앞에서 생성 된 스텁 코드 줄을 입력 하는 메서드: `ImmutableArray<int>.Empty;`합니다. 구문 시각화 도우미 도구 창을 다시 보면이 구문은 SimpleMemberAccessExpression 노드를 볼 수 있습니다. 만들고 새 문서에 돌아가거나 필요한이 메서드는 것이입니다.

첫 번째 변경 `ChangeToImmutableArrayEmpty` 추가 하는 것 `async` 하기 전에 `Task<Document>` 코드 생성기 메서드를 비동기 해야 가정할 수 없습니다 때문입니다.

메서드가 다음과 비슷하게 표시 되도록 다음 코드를 사용 하 여 본문을 입력 합니다.

```csharp

private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

편집기의 캐럿을 배치 해야 합니다 `SyntaxGenerator` 식별자 및 사용 하 여 **CTRL +.** (마침표) 적절 한 추가할 `using` 이 형식에 대 한 문입니다.

이 코드를 사용 하 여 `SyntaxGenerator`, 형식인 매우 유용한 새 코드를 생성 합니다. 코드 문제에는 문서에 대 한 생성기를 시작 후 `ChangeToImmutableArrayEmpty` 호출 `MemberAccessExpression`, 액세스 하려는 멤버를 가진 형식을 전달 하 고 멤버의 이름을 문자열로 전달 합니다.

다음으로, 메서드는 문서의 루트를 인출 하 고이 일반적인 경우 임의의 작업 과정을 하기 때문에 코드를이 호출 될 때까지 기다립니다 취소 토큰을 전달 합니다. Roslyn 코드 모델이.NET 문자열을 사용 하는 같은 변경할 수 없습니다 문자열을 업데이트 하면 새 문자열 개체를 반환 가져옵니다. 호출 하는 경우 `ReplaceNode`를 새 루트 노드를 다시 가져옵니다. (하지 않기 때문에 변경할 수 있는) 대부분의 구문 트리를 공유 하지만 `objectCreation` 노드 바뀝니다는 `memberAccess` 구문 트리 루트 까지의 모든 부모 노드 뿐만 아니라 노드.

## <a name="trying-your-code-fix"></a>코드 수정 사항을 시도
이제 눌러도 **F5** Visual Studio의 두 번째 인스턴스에서 분석기를 실행 합니다. 이전에 사용한 콘솔 프로젝트를 엽니다. 새 개체 생성 식에 대 한 위치에 나타날 전구를 표시 하는 이제 `ImmutableArray<int>`합니다. 키를 누르면 **CTRL +.** (기간), 수정, 코드를 다음 표시 되 고 전구 UI에서에서 미리 보기를 자동으로 생성 된 코드 차이 표시 됩니다. Roslyn을이 만듭니다.

Pro 팁: Visual Studio의 두 번째 인스턴스를 시작 하 고 코드 수정 사항을 사용 하 여 밝은 전구 표시 되지 않는 경우 Visual Studio 구성 요소 캐시를 지우려면 해야 할 수 있습니다. Visual Studio의 Visual Studio 최신 구성 요소를 선택 해야 하므로 구성 요소 다시 검사를 강제로 캐시 지우기. 먼저 Visual Studio의 두 번째 인스턴스를 종료 합니다. 그런 다음 Windows 탐색기에서 사용자 디렉터리로 이동 (c:\users\\< userid\>) AppData\Local\Microsoft\VisualStudio\14.0Roslyn 찾고\\합니다. 이 디렉터리에서 ComponentModelCache 하위 디렉터리를 삭제 합니다. "14" 변경 내용을 Visual Studio를 사용 하 여 버전입니다.

## <a name="talk-video-and-finish-code-project"></a>강연 비디오 및 코드 프로젝트 완료 날짜
이 예제에서는 개발 하 고 설명에 표시에 대 한 자세한 [이 강연](http://channel9.msdn.com/events/Build/2015/3-725)합니다. 설명 작업 분석기를 보여 줍니다. 및 빌드하는 것을 안내 합니다.

완성된 된 모든 코드를 볼 수 있습니다 [여기](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)합니다. DoNotUseImmutableArrayCollectionInitializer 및 DoNotUseImmutableArrayCtor 각 하위 폴더를 C# 파일에서 문제 및 Visual Studio 전구 UI에에서 표시 된 코드 수정 프로그램을 구현 하는 C# 파일을 찾는 경우 참고, 완성 된 코드에는 약간의 추상화는 ImmutableArray를 페치 하지 않으려면\<T > 형식 개체를 반복 합니다. 중첩 된 등록된 작업을 사용 하 여 사용할 수 있는 컨텍스트에서 형식 개체를 저장 하 때마다 하위 작업 (개체 생성을 분석 하 고 컬렉션 초기화 분석)를 실행 합니다.

## <a name="see-also"></a>참고 항목
[\\\Build 2015 talk](http://channel9.msdn.com/events/Build/2015/3-725)
[GitHub의 코드 완료](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[GitHub에서 몇 가지 예제 분석기의 세 가지 그룹화](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
 [OSS GitHub 사이트에서 다른 docs](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
[GitHub의 Roslyn 분석기를 사용 하 여 구현 하는 FxCop 규칙](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
