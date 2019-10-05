---
title: Managed Extensibility Framework 편집기에서 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65731a905c157737ca4c01416f9d76fdecba30d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351039"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>편집기에서 managed Extensibility Framework
편집기는 프레임 워크 MEF (Managed Extensibility) 구성 요소를 사용 하 여 빌드됩니다. 사용자 고유의 MEF 구성 요소 편집기를 확장을 빌드하고 코드 편집기 구성 요소도 사용할 수 있습니다.

## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework 개요
 MEF에 추가 하 고 응용 프로그램 또는 구성 요소는 MEF 프로그래밍 모델의 기능을 수정할 수 있는.NET 라이브러리입니다. Visual Studio 편집기 제공 및 MEF 구성 요소 파트를 사용할 수 있습니다.

 .NET Framework 버전 4에에서 포함 된 MEF *System.ComponentModel.Composition.dll* 어셈블리입니다.

 MEF에 대 한 자세한 내용은 참조 하세요. [Framework MEF (Managed Extensibility)](/dotnet/framework/mef/index)합니다.

### <a name="component-parts-and-composition-containers"></a>구성 요소 및 컴퍼지션 컨테이너
 구성 요소 부분은 다음 중 하나 (또는 둘 다)를 수행할 수 있는 클래스의 멤버 이거나 클래스:

- 다른 구성 요소를 사용 합니다.

- 다른 구성 요소에서 사용할 수

  예를 들어 쇼핑 응용 프로그램을 웨어하우스 인벤토리 구성 요소에 의해 제공 되는 제품 가용성 데이터에 의존 하는 주문 항목 구성 요소가 있는 것이 좋습니다. MEF 관점에서 인벤토리 파트 수 *내보낼* 제품 가용성 데이터 및 주문 항목 파트 수 있습니다 *가져오기* 데이터입니다. 주문 항목 부분과 인벤토리 부분; 서로에 대해 알아야 할 없는 합니다 *컴퍼지션 컨테이너* (호스트 응용 프로그램에서 제공) 내보내기 집합을 유지 하 고 내보내기를 해결을 담당 하 고 가져옵니다.

  컴퍼지션 컨테이너 <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, 호스트에서 일반적으로 소유 합니다. 컴퍼지션 컨테이너를 유지 관리를 *카탈로그* 내보낸된 구성 요소입니다.

### <a name="export-and-import-component-parts"></a>구성 요소 부분을 가져오고 내보내려면
 공용 클래스 또는 클래스 (속성 또는 메서드)의 공용 멤버 함수로 구현으로 모든 기능을 내보낼 수 있습니다. 에 구성 요소 파트에서 파생 시킬 필요가 없습니다 <xref:System.ComponentModel.Composition.Primitives.ComposablePart>합니다. 대신 추가 해야 합니다는 <xref:System.ComponentModel.Composition.ExportAttribute> 클래스 또는 클래스 멤버를 내보내려는 특성입니다. 이 특성은 지정 된 *계약* 파트는 다른 구성 요소에서 기능을 가져올 수 있습니다.

### <a name="the-export-contract"></a>내보내기 계약
 <xref:System.ComponentModel.Composition.ExportAttribute> (클래스, 인터페이스 또는 구조체)는 내보낼 엔터티를 정의 합니다. 일반적으로 export 특성 내보내기의 형식을 지정 하는 매개 변수를 사용 합니다.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 기본적으로 <xref:System.ComponentModel.Composition.ExportAttribute> 특성 내보내기 클래스의 형식이 있는 계약을 정의 합니다.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 예제에서는 기본 `[Export]` 특성은 `[Export(typeof(TestAdornmentLayerDefinition))]`합니다.

 다음 예제에서와 같이 속성 또는 메서드를 내보낼 수도 있습니다.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>MEF 내보내기를 가져오기
 계약 (일반적으로 형식)는 내보낸를 하 고 추가 알아야 MEF 내보내기를 사용 하려는 경우는 <xref:System.ComponentModel.Composition.ImportAttribute> 해당 값이 있는 특성입니다. 기본적으로 가져오기 특성은 하나의 매개 변수를 수정 하는 클래스의 형식인를 사용 합니다. 코드 가져오기의 다음 줄을 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> 형식입니다.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>MEF 구성 요소 파트에서 편집기 기능 가져오기
 기존 코드를 MEF 구성 요소 일부 이면 편집기 구성 요소 파트를 사용 하려면 MEF 메타 데이터를 사용할 수 있습니다.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>MEF 구성 요소 파트에서 편집기 기능을 사용 하려면

1. 에 대 한 참조를 추가 *System.Composition.ComponentModel.dll*, 편집기 어셈블리를 전역 어셈블리 캐시 (GAC)에 합니다.

2. 추가 관련 문을 사용 하 여 합니다.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. 추가 된 `[Import]` 에 서비스 인터페이스에 특성을 다음과 같이 합니다.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. 서비스를 가져온 경우에 해당 구성 요소 중 하나를 사용할 수 있습니다.

5. 경우에 배치 하 여 어셈블리를 컴파일한는 *... \Common7\IDE\Components\* Visual Studio 설치의 폴더입니다.

## <a name="see-also"></a>참고자료
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)