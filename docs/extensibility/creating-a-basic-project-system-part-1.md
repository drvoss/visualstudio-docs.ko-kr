---
title: 기본 프로젝트 시스템 만들기, 1 부 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19c73e47e8c07ebcf7c1124e6e59d80f76101458
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341650"
---
# <a name="create-a-basic-project-system-part-1"></a>1 부 기본 프로젝트 시스템을 만들려면
Visual Studio에서 프로젝트는 개발자가 소스 코드 파일 및 기타 자산을 구성 하는 데 사용할 컨테이너를 사용 합니다. 프로젝트에서 솔루션의 자식으로 표시 합니다 **솔루션 탐색기**합니다. 프로젝트를 사용 하 여 구성, 빌드, 디버그 및 소스 코드를 배포 및 웹 서비스, 데이터베이스 및 기타 리소스에 대 한 참조를 만들 수 있습니다.

 예를 들어 프로젝트 파일에 정의 된 프로젝트를 *.csproj* Visual C# 프로젝트 파일입니다. 사용자 고유의 프로젝트 파일 이름 확장명을 가진 고유한 프로젝트 형식을 만들 수 있습니다. 프로젝트 형식에 대 한 자세한 내용은 참조 하세요. [프로젝트 형식](../extensibility/internals/project-types.md)합니다.

> [!NOTE]
> 사용자 지정 프로젝트 형식을 사용 하 여 Visual Studio를 확장 하는 경우 좋습니다 활용 하 여 [Visual Studio 프로젝트 시스템](https://github.com/Microsoft/VSProjectSystem) (VSP) 다양 한 프로젝트 시스템을 처음부터 구축 하는 장점이 있는:
>
> - 쉽게 온 보 딩 합니다.  기본 프로젝트 시스템 에서도 수천 줄의 코드만 필요합니다.  VSP를 활용 하 여 비용을 줄일 수 온 보 딩 몇 번의 클릭을 요구 사항에 맞게 사용자 지정할 준비가 되었습니다. 전에 합니다.
> - 더 쉽게 유지 관리 합니다.  VSP를 활용 하 여 고유한 시나리오를 유지 관리 하기만 하면 됩니다.  프로젝트 시스템 인프라의 모든 진다는 점을 처리 합니다.
>
>   대상 버전의 Visual Studio 2013 이전의 Visual Studio를 해야 하는 경우 VSP Visual Studio 확장을 활용 하는 수 없습니다.  이 연습에서는,이 경우 시작 하는 것이 좋습니다.

 이 연습에서는 프로젝트 파일 이름 확장명을 가진 프로젝트 형식을 만드는 방법을 보여 줍니다. *.myproj*합니다. 이 연습에서는 기존 Visual C# 프로젝트 시스템에서 활용합니다.

> [!NOTE]
> 더 많은 예제 확장 프로젝트를 참조 하세요 [VSSDK 샘플](https://aka.ms/vs2015sdksamples)합니다.

 이 연습에서는 이러한 작업을 수행 하는 방법에 설명 합니다.

- 기본 프로젝트 형식을 만듭니다.

- 기본 프로젝트 템플릿을 만듭니다.

- Visual Studio 프로젝트 템플릿을 등록 합니다.

- 프로젝트 인스턴스를 열어 만듭니다는 **새 프로젝트** 대화 상자 및 다음 템플릿을 사용 하 여 합니다.

- 프로젝트 시스템에 대 한 프로젝트 팩터리를 만듭니다.

- 프로젝트 시스템에 대 한 프로젝트 노드를 만듭니다.

- 프로젝트 시스템에 대 한 사용자 지정 아이콘을 추가 합니다.

- 기본 템플릿 매개 변수 대체를 구현 합니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

 또한 소스 코드를 다운로드 해야 합니다 [프로젝트에 대 한 관리 되는 패키지 프레임 워크](https://github.com/tunnelvisionlabs/MPFProj10)합니다. 만들려고 한다고 솔루션에 액세스할 수 있는 위치로 파일을 추출 합니다.

## <a name="create-a-basic-project-type"></a>기본 프로젝트 형식 만들기
 라는 C# VSIX 프로젝트를 만듭니다 **SimpleProject**합니다. (**파일** > **새** > **프로젝트** 차례로 **Visual C#**  >   **확장성** > **VSIX 프로젝트**). Visual Studio 패키지 프로젝트 항목 템플릿을 추가 (에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**이동한 다음 **확장성** > **Visual Studio 패키지**). 파일 이름을 *SimpleProjectPackage*합니다.

## <a name="creating-a-basic-project-template"></a>기본 프로젝트 템플릿 만들기
 이제 새 구현 하기 위해이 기본 VSPackage를 수정할 수 있습니다 *.myproj* 형식 프로젝션 합니다. 기반이 되는 프로젝트를 만들려면 합니다 *.myproj* 프로젝트 형식의 경우, Visual Studio에는 파일, 리소스 및 새 프로젝트에 추가할 참조를 알아야 합니다. 이 정보를 제공 하려면 프로젝트 템플릿 폴더에 있는 프로젝트 파일을 저장 합니다. 사용자가 사용 하는 경우는 *.myproj* 프로젝트를 만들려면 프로젝트에서 새 프로젝트에 파일 복사 됩니다.

### <a name="to-create-a-basic-project-template"></a>기본 프로젝트 템플릿을 만들려면

1. 다른 하나는 프로젝트에 세 개의 폴더를 추가 합니다. *Templates\Projects\SimpleProject*. (에서 **솔루션 탐색기**, 마우스 오른쪽 단추로 클릭 합니다 **SimpleProject** 프로젝트 노드를 가리키도록 **추가**를 클릭 하 고 **새 폴더**. 폴더의 이름을 *템플릿*합니다. 에 *템플릿을* 폴더를 라는 폴더를 추가 *프로젝트*합니다. 에 *프로젝트* 폴더를 라는 폴더를 추가 *SimpleProject*.)

2. 에 *Templates\Projects\SimpleProject* 폴더를 라는 아이콘으로 사용할 비트맵 이미지 파일 추가 *SimpleProject.ico*합니다. 클릭 하면 **추가**, 아이콘 편집기가 열립니다.

3. 눈에 띄는 아이콘을 확인 합니다. 이 아이콘에 표시 됩니다는 **새 프로젝트** 연습 뒷부분에서 대화 상자.

    ![간단한 프로젝트 아이콘](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. 아이콘을 저장 하 고 아이콘 편집기를 닫습니다.

5. 에 *Templates\Projects\SimpleProject* 폴더에 추가 **클래스** 라는 항목 *Program.cs*합니다.

6. 기존 코드를 다음 줄으로 바꿉니다.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > 이 최종 형식으로는 *Program.cs* 코드, 매개 변수는 이후 단계에서 처리 될 대체 합니다. 표시 될 수 있습니다 컴파일 오류를 하지만 한 파일의 **빌드 작업** 됩니다 **콘텐츠**를 구축 하 고 프로젝트를 정상적으로 실행 해야 합니다.

7. 파일을 저장합니다.

8. 복사를 *AssemblyInfo.cs* 에서 파일을 *속성* 폴더를 *Projects\SimpleProject* 폴더입니다.

9. 에 *Projects\SimpleProject* 라는 XML 파일을 추가 하는 폴더 *SimpleProject.myproj*합니다.

   > [!NOTE]
   > 이 형식의 모든 프로젝트의 파일 이름 확장명은 *.myproj*합니다. 변경 하려는 경우 변경 해야 everywhere 연습에서 설명 합니다.

10. 기존 콘텐츠를 다음 줄을 바꿉니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. 파일을 저장합니다.

12. 에 **속성** 창에서 설정 합니다 **빌드 작업** 의 *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* , 및 *SimpleProject.myproj* 하 **콘텐츠**를 설정 하 고 해당 **VSIX에 포함** 속성을 **True**.

    이 프로젝트 템플릿은 기본 Visual C# 프로젝트를 디버그 구성 및 릴리스 구성을를 설명 합니다. 프로젝트에 두 개의 소스 파일 *AssemblyInfo.cs* 하 고 *Program.cs*, 및 여러 어셈블리 참조입니다. 프로젝트를 템플릿에서 만들면 ProjectGuid 값은 새 GUID로 자동 교체 됩니다.

    **솔루션 탐색기**, 확장 된 **템플릿** 폴더가 다음과 같이 표시 되어야 합니다.

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>기본 프로젝트 팩터리 만들기
 Visual Studio 프로젝트 템플릿 폴더의 위치를 알려야 합니다. 이렇게 하려면 VSPackage를 빌드할 때 템플릿 위치가 시스템 레지스트리에 쓸 수 있도록 프로젝트 팩터리 구현 하는 VSPackage 클래스에 특성을 추가 합니다. 프로젝트 팩터리 GUID로 식별 되는 기본 프로젝트 팩터리를 만들어 시작 합니다. 사용 된 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 특성은 프로젝트 팩터리를 연결할를 `SimpleProjectPackage` 클래스.

### <a name="to-create-a-basic-project-factory"></a>기본 프로젝트 팩터리를 만들려면

1. 프로젝트 팩터리 Guid 만들기 (에 **도구** 메뉴에서 클릭 **GUID 만들기**), 하거나 다음 예제에서를 사용 합니다. Guid를 추가 합니다 `SimpleProjectPackage` 이미 정의 된 포함 하는 섹션 가까운 지역의 강의 `PackageGuidString`합니다. Guid를 GUID 형식 및 문자열 형식 이어야 합니다. 결과 코드에는 다음 예제와 유사 해야 합니다.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. 클래스 맨 위에 추가 *SimpleProject* 폴더가 *SimpleProjectFactory.cs*합니다.

3. 다음 추가 문을 사용 하 여:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. GUID 특성을 추가 합니다 `SimpleProjectFactory` 클래스입니다. 특성의 값은 새 프로젝트 팩터리 GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   이제 프로젝트 템플릿을 등록할 수 있습니다.

### <a name="to-register-the-project-template"></a>프로젝트 템플릿을 등록 하려면

1. *SimpleProjectPackage.cs*에 추가 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 특성을 `SimpleProjectPackage` 클래스를 다음과 같이 합니다.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. 솔루션을 다시 작성 하 고 오류 없이 빌드되는지 확인 합니다.

    다시 작성 프로젝트 템플릿을 등록합니다.

   매개 변수 `defaultProjectExtension` 하 고 `possibleProjectExtensions` 프로젝트 파일 이름 확장명으로 설정 됩니다 ( *.myproj*). `projectTemplatesDirectory` 매개 변수 설정의 상대 경로 *템플릿* 폴더입니다. 빌드 중에이 경로 전체 빌드를 변환 하 고 프로젝트 시스템을 등록 하려면 레지스트리를 추가할 수 됩니다.

## <a name="test-the-template-registration"></a>템플릿 등록 테스트
 템플릿 등록 하면 Visual Studio 프로젝트 템플릿 폴더의 위치가 Visual Studio 템플릿 이름 및 아이콘에 표시 될 수 있도록 합니다 **새 프로젝트** 대화 상자.

### <a name="to-test-the-template-registration"></a>템플릿 등록을 테스트 하려면

1. 키를 눌러 **F5** Visual Studio의 실험적 인스턴스에서 디버깅을 시작 합니다.

2. 실험적 인스턴스를 새로 만든 프로젝트 형식의 새 프로젝트를 만듭니다. 에 **새 프로젝트** 표시 대화 상자에서 **SimpleProject** 아래에 있는 **설치 되어 있는 템플릿**합니다.

   이제 프로젝트 팩터리를 등록 해야 합니다. 그러나 프로젝트를 만들 아직 없습니다. 프로젝트 패키지와 프로젝트 팩터리를 만들고 프로젝트를 초기화 하려면 함께 작동 합니다.

## <a name="add-the-managed-package-framework-code"></a>관리 패키지 프레임 워크 코드를 추가 합니다.
 프로젝트 패키지와 프로젝트 팩터리 간의 연결을 구현 합니다.

- 관리 패키지 프레임 워크에 대 한 소스 코드 파일을 가져옵니다.

    1. SimpleProject 프로젝트 언로드 (에서 **솔루션 탐색기**, 프로젝트 노드를 선택 하 고 상황에 맞는 메뉴를 클릭 **프로젝트 언로드**.) 및 XML 편집기에서 프로젝트 파일을 엽니다.

    2. 프로젝트 파일에 다음 요소를 추가 (바로 위에 \<가져오기 > 요소). 설정 `ProjectBasePath` 의 위치를 *ProjectBase.files* 방금 다운로드 한 관리 되는 패키지 프레임 워크 코드는 파일입니다. 경로 이름에 백슬래시를 추가 해야 합니다. 이렇게 하지 않으면 프로젝트 관리 패키지 프레임 워크 소스 코드를 찾을에 실패할 수 있습니다.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > 경로 끝에 백슬래시를 잊지 마십시오.

    3. 프로젝트를 다시 로드 합니다.

    4. 다음 어셈블리에 대한 참조를 추가합니다.

        - `Microsoft.VisualStudio.Designer.Interfaces` (에  *\<VSSDK 설치 > \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>프로젝트 팩터리를 초기화 하려면

1. 에 *SimpleProjectPackage.cs* 파일에서 다음을 추가 합니다 `using` 문입니다.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. 파생 된 `SimpleProjectPackage` 클래스에서 `Microsoft.VisualStudio.Package.ProjectPackage`합니다.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. 프로젝트 팩터리를 등록 합니다. 다음 줄을 추가 합니다 `SimpleProjectPackage.Initialize` 메서드를 직후 `base.Initialize`합니다.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. 추상 속성을 구현 `ProductUserContext`:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. *SimpleProjectFactory.cs*, 다음을 추가 합니다 `using` 기존 뒤의 문으로 `using` 문입니다.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. 파생 된 `SimpleProjectFactory` 클래스에서 `ProjectFactory`합니다.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. 다음 더미 메서드를 추가 합니다 `SimpleProjectFactory` 클래스입니다. 이후 섹션에서이 메서드를 구현 합니다.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. 다음 필드 및 생성자를 추가 합니다 `SimpleProjectFactory` 클래스입니다. 이 `SimpleProjectPackage` 설정 서비스 공급자 사이트에서 사용할 수 있도록 참조를 개인 필드에 캐시 됩니다.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. 솔루션을 다시 작성 하 고 오류 없이 빌드되는지 확인 합니다.

## <a name="test-the-project-factory-implementation"></a>프로젝트 팩터리 구현 테스트
 프로젝트 팩터리 구현에 대 한 생성자가 호출 여부를 테스트 합니다.

### <a name="to-test-the-project-factory-implementation"></a>프로젝트 팩터리 구현을 테스트 하려면

1. 에 *SimpleProjectFactory.cs* 파일에서 다음 줄에 중단점을 설정 합니다는 `SimpleProjectFactory` 생성자입니다.

    ```csharp
    this.package = package;
    ```

2. 키를 눌러 **F5** Visual Studio의 실험적 인스턴스를 시작 합니다.

3. 실험적 인스턴스에서 새 프로젝트 만들기를 시작 합니다. **새 프로젝트** 대화 상자를 선택 합니다 **SimpleProject** 프로젝트 형식 및 클릭 **확인**합니다. 중단점에서 실행이 중지됩니다.

4. 중단점의 선택을 취소 하 고 디버깅을 중지 합니다. 만들었으므로 하지 프로젝트 노드 아직, 프로젝트 생성 코드는 여전히 예외를 throw 합니다.

## <a name="extend-the-projectnode-class"></a>ProjectNode 클래스 확장
 이제 구현할 수 있습니다는 `SimpleProjectNode` 에서 파생 되는 클래스는 `ProjectNode` 클래스입니다. `ProjectNode` 프로젝트 만들기의 다음 작업을 처리 하는 기본 클래스:

- 프로젝트 템플릿 파일을 복사 *SimpleProject.myproj*, 새 프로젝트 폴더에 있습니다. 복사본에 입력 된 이름에 따라 이름이 합니다 **새 프로젝트** 대화 상자. `ProjectGuid` 속성 값이 새 GUID로 대체 됩니다.

- 프로젝트 템플릿 파일의 MSBuild 요소를 통과 *SimpleProject.myproj*를 검색 및 `Compile` 요소입니다. 각 `Compile` 대상 파일을 새 프로젝트 폴더에 파일을 복사 합니다.

  파생 된 `SimpleProjectNode` 클래스는 이러한 작업을 처리 합니다.

- 프로젝트 및 파일 노드에 대 한 아이콘을 사용 하도록 설정 **솔루션 탐색기** 만들거나 선택 합니다.

- 추가 프로젝트 템플릿 매개 변수를 대체를를 지정할 수 있습니다.

### <a name="to-extend-the-projectnode-class"></a>ProjectNode 클래스를 확장 하려면

1. 라는 클래스를 추가 `SimpleProjectNode.cs`합니다.

2. 기존 코드를 다음 코드로 바꿉니다.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   이 `SimpleProjectNode` 클래스 구현을 다음 재정의 된 메서드를 포함 합니다.

- `ProjectGuid`를 프로젝트 팩터리 GUID를 반환 합니다.

- `ProjectType`에서 프로젝트 형식의 지역화 된 이름을 반환 합니다.

- `AddFileFromTemplate`에서 선택한 파일 템플릿 폴더에서 대상 프로젝트에 복사 합니다. 이 메서드는 이후 섹션에서 추가로 구현 됩니다.

  `SimpleProjectNode` 생성자 마찬가지로 합니다 `SimpleProjectFactory` 생성자에 캐시를 `SimpleProjectPackage` 나중에 사용할 개인 필드에 대 한 참조.

  연결할를 `SimpleProjectFactory` 클래스를 `SimpleProjectNode` 클래스를 인스턴스화해야 새 `SimpleProjectNode` 에서 `SimpleProjectFactory.CreateProject` 메서드 하 고 나중에 사용할 개인 필드에 캐시 합니다.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>프로젝트 팩터리 클래스 및 노드 클래스를 연결 하려면

1. 에 *SimpleProjectFactory.cs* 파일을 다음 추가 `using` 문:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. 대체는 `SimpleProjectFactory.CreateProject` 메서드를 다음 코드를 사용 합니다.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. 솔루션을 다시 작성 하 고 오류 없이 빌드되는지 확인 합니다.

## <a name="test-the-projectnode-class"></a>ProjectNode 클래스 테스트
 프로젝트 계층 구조를 만들면 여부를 확인 하려면 프로젝트 팩터리를 테스트 합니다.

### <a name="to-test-the-projectnode-class"></a>ProjectNode 클래스를 테스트 하려면

1. **F5** 키를 눌러 디버깅을 시작합니다. 새 SimpleProject 실험적 인스턴스를 만듭니다.

2. Visual Studio 프로젝트를 만들려면 프로젝트 팩터리를 호출 해야 합니다.

3. Visual Studio의 실험적 인스턴스를 닫습니다.

## <a name="add-a-custom-project-node-icon"></a>추가 사용자 지정 프로젝트 노드 아이콘
 이전 섹션에서 프로젝트 노드 아이콘은 기본 아이콘입니다. 사용자 지정 아이콘을 변경할 수 있습니다.

### <a name="to-add-a-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘을 추가 하려면

1. 에 **리소스** 폴더를 라는 비트맵 파일을 추가 *SimpleProjectNode.bmp*합니다.

2. 에 **속성** windows 16x16 픽셀 비트맵을 줄입니다. 눈에 띄는 비트맵을 확인 합니다.

    ![간단한 프로젝트 명령](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. 에 **속성** 창에서 변경 합니다 **빌드 작업** 비트맵의 **포함 리소스**합니다.

4. *SimpleProjectNode.cs*, 다음 추가 `using` 문:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. 정적 필드 및 생성자를 추가 합니다 `SimpleProjectNode` 클래스입니다.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. 시작 부분에 다음 속성을 추가 합니다 `SimpleProjectNode` 클래스입니다.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. 인스턴스 생성자를 다음 코드로 바꿉니다.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   정적 생성 하는 동안 `SimpleProjectNode` 어셈블리 매니페스트 리소스에서 프로젝트 노드 비트맵을 검색 하 고 나중에 사용할 개인 필드에 캐시 합니다. 구문을 확인 합니다 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 이미지 경로입니다. 어셈블리에 포함 된 매니페스트 리소스의 이름을 보려면는 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 메서드. 이 메서드가 적용 되는 경우는 `SimpleProject` 어셈블리 결과 다음과 같아야 합니다.

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  인스턴스 생성 도중 합니다 `ProjectNode` 기본 클래스 로드 *Resources.imagelis.bmp*에서에서 16 x 16 비트맵을 사용 하는 일반적으로 포함 됩니다 *Resources\imagelis.bmp*. 이 비트맵 목록에 제공 됩니다 `SimpleProjectNode` 으로 `ImageHandler.ImageList`입니다. `SimpleProjectNode` 프로젝트 노드 비트맵 목록에 추가합니다. 이미지 목록에서 프로젝트 노드 비트맵의 오프셋은 나중에 사용할 공용 값으로 캐시 됩니다 `ImageIndex` 속성입니다. Visual Studio에서 프로젝트 노드 아이콘으로 표시 하는 비트맵을 확인 하려면이 속성을 사용 합니다.

## <a name="test-the-custom-project-node-icon"></a>테스트 사용자 지정 프로젝트 노드 아이콘
 사용자 지정 프로젝트 노드 아이콘이 있는 프로젝트 계층 구조를 만들면 여부를 확인 하려면 프로젝트 팩터리를 테스트 합니다.

### <a name="to-test-the-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘을 테스트 하려면

1. 디버깅을 시작 하 고 실험적 인스턴스에서 새 SimpleProject 만듭니다.

2. 새로 만든 프로젝트를 알 수 있듯이 *SimpleProjectNode.bmp* 프로젝트 노드가 아이콘으로 사용 됩니다.

     ![간단한 프로젝트 노드를 새 프로젝트](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. 오픈 *Program.cs* 코드 편집기에서. 다음 코드와 비슷한 소스 코드를 표시 되어야 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     템플릿 매개 변수 $nameSpace$ 및 $ $className$ 수행할 새 값이 없는지 확인 합니다. 다음 섹션에서 템플릿 매개 변수 대체를 구현 하는 방법을 배웁니다.

## <a name="substitute-template-parameters"></a>템플릿 매개 변수를 대체 합니다.
 이전 단원에서 등록할 프로젝트 템플릿을 Visual Studio를 사용 하 여 사용 하 여는 `ProvideProjectFactory` 특성입니다. 재정의 하 고 확장 하 여 기본 템플릿 매개 변수 대체를 사용 하면 이러한 방식으로 템플릿 폴더의 경로 등록 합니다 `ProjectNode.AddFileFromTemplate` 클래스입니다. 자세한 내용은 참조 하세요. [새 프로젝트 생성: 내부적으로 2 부](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)합니다.

 대체 코드를 추가 합니다 `AddFileFromTemplate` 클래스입니다.

### <a name="to-substitute-template-parameters"></a>템플릿 매개 변수를 대체 합니다.

1. 에 *SimpleProjectNode.cs* 파일에서 다음을 추가 합니다 `using` 문입니다.

   ```csharp
   using System.IO;
   ```

2. 대체는 `AddFileFromTemplate` 메서드를 다음 코드를 사용 합니다.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. 직후 메서드에서 중단점을 설정 합니다 `className` 대입문 합니다.

   대입문을 사용 하 여 새 클래스 이름 및 네임 스페이스에 대 한 적절 한 값을 결정합니다. 두 `ProjectNode.FileTemplateProcessor.AddReplace` 메서드 호출에 이러한 새 값을 사용 하 여 해당 템플릿 매개 변수 값으로 바꿉니다.

## <a name="test-the-template-parameter-substitution"></a>템플릿 매개 변수 대체를 테스트 합니다.
 이제 템플릿 매개 변수 대체를 테스트할 수 있습니다.

### <a name="to-test-the-template-parameter-substitution"></a>템플릿 매개 변수 대체를 테스트 하려면

1. 디버깅을 시작 하 고 실험적 인스턴스에서 새 SimpleProject 만듭니다.

2. 실행이 중단점에서 중지 되는 `AddFileFromTemplate` 메서드.

3. 에 대 한 값을 확인 합니다 `nameSpace` 고 `className` 매개 변수입니다.

   - `nameSpace` 값이 지정 되는 \<RootNamespace > 요소에는 *\Templates\Projects\SimpleProject\SimpleProject.myproj* 프로젝트 템플릿 파일입니다. 이 경우 값은 `MyRootNamespace`입니다.

   - `className` 클래스 이름의 원본 파일, 파일 이름 확장명이 없는 값이 지정 됩니다. 이 경우 첫 번째 대상 폴더에 복사할 파일이 *AssemblyInfo.cs*따라서 className의 값은 `AssemblyInfo`합니다.

4. 중단점 및 키를 눌러 제거 **F5** 실행을 계속 합니다.

    Visual Studio 프로젝트 만들기를 완료 해야 합니다.

5. 오픈 *Program.cs* 코드 편집기에서. 다음 코드와 비슷한 소스 코드를 표시 되어야 합니다.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    네임 스페이스는 이제 되었다는 `MyRootNamespace` 클래스 이름을 이제 이며 `Program`합니다.

6. 프로젝트 디버깅을 시작 합니다. 새 프로젝트는 컴파일, 실행 및 "VSX Hello!"를 표시 합니다. 콘솔 창에 표시합니다.

    ![간단한 프로젝트 명령](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   축하합니다. 관리 되는 기본 프로젝트 시스템을 구현 했습니다.