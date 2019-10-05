---
title: 기본 프로젝트 시스템 만들기, 2 부 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d44e99b584ec347abd407753f965170658969b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685421"
---
# <a name="creating-a-basic-project-system-part-2"></a>기본 프로젝트 시스템 만들기, 2부
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 시리즈의 첫 번째 연습의 [기본 프로젝트 시스템, 1 부 만들기](../extensibility/creating-a-basic-project-system-part-1.md), 기본 프로젝트 시스템을 만드는 방법을 보여 줍니다. 이 연습에서는 Visual Studio 템플릿, 속성 페이지 및 기타 기능을 추가 하 여 기본 프로젝트 시스템에 작성 합니다. 이 시작 하기 전에 첫 번째 연습을 완료 해야 합니다.  
  
 이 연습에서는 프로젝트 파일 이름 확장명.myproj 있는 프로젝트 형식을 만드는 방법을 설명 합니다. 이 연습을 완료 하려면 기존 Visual C# 프로젝트 시스템에서이 연습을 활용 하기 때문에 고유 언어를 만들 필요가 없습니다.  
  
 이 연습에서는 이러한 작업을 수행 하는 방법에 설명 합니다.  
  
- Visual Studio 템플릿을 만듭니다.  
  
- Visual Studio 템플릿을 배포 합니다.  
  
- 프로젝트 형식 자식 노드를 만드는 합니다 **새 프로젝트** 대화 상자.  
  
- Visual Studio 템플릿에서 매개 변수 대체를 사용 하도록 설정 합니다.  
  
- 프로젝트 속성 페이지를 만듭니다.  
  
> [!NOTE]
> 이 연습 단계에서는 C# 프로젝트를 기반으로 합니다. 그러나 파일 이름 확장명 및 코드와 같은 세부 정보를 제외 하 고 Visual Basic 프로젝트에 대 한 동일한 단계를 사용할 수 있습니다.  
  
## <a name="creating-a-visual-studio-template"></a>Visual Studio 템플릿 만들기  
 [기본 프로젝트 시스템, 1 부 만들기](../extensibility/creating-a-basic-project-system-part-1.md) 기본 프로젝트 템플릿을 만들고 프로젝트 시스템에 추가 하는 방법을 보여 줍니다. 또한이 템플릿은 Visual Studio를 사용 하 여 등록 하는 방법을 보여 줍니다는 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> \Templates\Projects\SimpleProject\ 폴더의 전체 경로를 시스템 레지스트리에 쓰는 특성입니다.  
  
 기본 프로젝트 템플릿이 아닌 Visual Studio 템플릿 (.vstemplate 파일)를 통해 제어할 수 있습니다에 템플릿이 표시 되는 방식을 합니다 **새 프로젝트** 대화 상자 및 템플릿 매개 변수를 대체 하는 방법입니다.  .Vstemplate 파일은 프로젝트 시스템 템플릿을 사용 하 여 프로젝트를 만들면 포함 되도록 소스 파일은 하는 방법을 설명 하는 XML 파일입니다. 프로젝트 시스템 자체를.zip 파일에 소스 파일과.vstemplate 파일을 수집 하 여 빌드 및 Visual Studio에 알려진 위치에.zip 파일을 복사 하 여 배포 합니다. 이 프로세스는이 연습의 뒷부분에서 자세히 설명 합니다.  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 수행 하 여 만든 SimpleProject 솔루션을 엽니다 [기본 프로젝트 시스템, 1 부 만들기](../extensibility/creating-a-basic-project-system-part-1.md)합니다.  
  
2. SimpleProjectPackage.cs 파일인 ProvideProjectFactory 특성을 찾습니다. Null 사용 하 여 두 번째 매개 변수 (프로젝트 이름) 및 네 번째 매개 변수 (프로젝트 템플릿 폴더 경로)으로 바꿔야 "합니다. \\\NullPath ", 다음과 같습니다.  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. \Templates\Projects\SimpleProject\ 폴더로 SimpleProject.vstemplate 이라는 XML 파일을 추가 합니다.  
  
4. SimpleProject.vstemplate의 내용을 다음 코드로 바꿉니다.  
  
   ```xml  
   <VSTemplate Version="2.0.0" Type="Project"  
       xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
     <TemplateData>  
       <Name>SimpleProject Application</Name>  
       <Description>  
           A project for creating a SimpleProject application  
        </Description>  
        <Icon>SimpleProject.ico</Icon>  
        <ProjectType>SimpleProject</ProjectType>  
     </TemplateData>  
     <TemplateContent>  
       <Project File="SimpleProject.myproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
             Program.cs  
         </ProjectItem>  
         <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
            AssemblyInfo.cs  
         </ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
5. 에 **속성** 창에서 모든 5 집합과 \Templates\Projects\SimpleProject\ 폴더의 파일을 **빌드 작업** 를 **ZipProject**합니다.  
  
   ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
   합니다 \<TemplateData > 섹션 위치 및 모양의 SimpleProject 프로젝트 형식 결정 합니다 **새 프로젝트** 같이 대화 상자에서:  
  
- \<이름 > 요소 SimpleProject 응용 프로그램 프로젝트 템플릿 이름을 지정 합니다.  
  
- \<설명 > 요소에 표시 되는 설명이 포함 된 **새 프로젝트** 프로젝트 템플릿을 선택 하면 대화 상자.  
  
- \<아이콘 > 요소 SimpleProject 프로젝트 형식과 함께 표시 되는 아이콘을 지정 합니다.  
  
- 합니다 \<ProjectType > 요소에 프로젝트 이름 합니다 **새 프로젝트** 대화 상자. 이 이름은 ProvideProjectFactory 특성의 프로젝트 이름 매개 변수를 대체 합니다.  
  
  > [!NOTE]
  > \<ProjectType > 요소와 일치 해야 합니다 `LanguageVsTemplate` 인수는 `ProvideProjectFactory` SimpleProjectPackage.cs 파일의 특성에에서.  
  
  \<TemplateContent > 섹션에 새 프로젝트가 만들어질 때 생성 되는 이러한 파일에 설명 합니다.  
  
- SimpleProject.myproj  
  
- Program.cs  
  
- AssemblyInfo.cs  
  
  모든 파일을 세 개의 `ReplaceParameters` 매개 변수 대체를 사용 하도록 설정을 true로 설정 합니다.  Program.cs 파일에 `OpenInEditor` 프로젝트가 만들어질 때 코드 편집기에서 열려는 파일을 true로 설정 합니다.  
  
  Visual Studio 템플릿 스키마의 요소에 대 한 자세한 내용은 참조는 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)합니다.  
  
> [!NOTE]
> 프로젝트를 Visual Studio 템플릿이 둘 이상 있으면 모든 템플릿은 별도 폴더에서입니다. 해당 폴더의 모든 파일도 있어야 합니다 **빌드 작업** 로 설정 **ZipProject**합니다.  
  
## <a name="adding-a-minimal-vsct-file"></a>최소.vsct 파일 추가  
 Visual Studio 새롭거나 수정 된 Visual Studio 템플릿을 인식 설치 모드에서 실행 되어야 합니다. 설치 모드 있어야.vsct 파일을 필요 합니다. 따라서 최소.vsct 파일을 프로젝트에 추가 해야 합니다.  
  
1. SimpleProject 프로젝트 SimpleProject.vsct 이라는 XML 파일을 추가 합니다.  
  
2. SimpleProject.vsct 파일의 내용을 다음 코드로 바꿉니다.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3. 설정 된 **빌드 작업** 이 파일의 **VSCTCompile**합니다. 이렇게 하려면.csproj 파일에만 없습니다 합니다 **속성** 창입니다. 있는지 확인 합니다 **빌드 작업** 로 설정 되어이 파일의 **None** 이 시점에서.  
  
    1. SimpleProject 노드를 마우스 오른쪽 단추로 누른 **SimpleProject.csproj 편집**합니다.  
  
    2. .Csproj 파일에서 SimpleProject.vsct 항목을 찾습니다.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3. 빌드 동작을 변경 **VSCTCompile**합니다.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4. 프로젝트 파일 및 편집기를 닫습니다.  
  
    5. SimpleProject 노드를 저장 한 다음에 **솔루션 탐색기** 클릭 **프로젝트 다시 로드**합니다.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Visual Studio 템플릿 빌드 단계를 검사합니다.  
 .Vstemplate 파일 변경 되거나.vstemplate 파일을 포함 하는 프로젝트를 다시 작성 하는 경우 VSPackage 프로젝트 빌드 시스템은 설치 모드에서 Visual Studio를 실행 되는 일반적으로 합니다. 보통 이상 MSBuild의 자세한 정도 설정 하 여 따라 할 수 있습니다.  
  
1. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
2. 확장 된 **프로젝트 및 솔루션** 노드를 선택한 후 **빌드 및 실행**합니다.  
  
3. 설정할 **MSBuild 프로젝트 빌드 출력의 자세한 정도** 하 **보통**합니다. **확인**을 클릭합니다.  
  
4. SimpleProject 프로젝트를 다시 작성 합니다.  
  
   .Zip 프로젝트 파일을 만드는 빌드 단계에는 다음 예제와 유사 합니다.  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>Visual Studio 템플릿 배포  
 Visual Studio 템플릿 경로 정보가 포함 되지 않습니다. 따라서 템플릿.zip 파일은 Visual Studio에 알려진 위치에 배포 되어야 합니다. ProjectTemplates 폴더의 위치는 대개  **\<% LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**합니다.  
  
 프로젝트 팩터리를 배포 하려면 설치 프로그램에 관리자 권한이 있어야 합니다. Visual Studio 설치 노드에서 템플릿 배포: **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**합니다.  
  
## <a name="testing-a-visual-studio-template"></a>Visual Studio 템플릿 테스트  
 Visual Studio 템플릿을 사용 하 여 프로젝트 계층 구조를 만드는 지 여부를 확인 하려면 프로젝트 팩터리를 테스트 합니다.  
  
1. Visual Studio SDK 실험적 인스턴스 다시 설정 합니다.  
  
    [!INCLUDE[win7](../includes/win7-md.md)]: 시작 메뉴에서 찾을 합니다 **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** 폴더를 선택한 후 **Microsoft Visual Studio 실험적 인스턴스 재설정**합니다.  
  
    Windows의 이후 버전: 시작 화면에서 입력 **Microsoft Visual Studio를 다시 설정 \<버전 > 실험적 인스턴스**합니다.  
  
2. 명령 프롬프트 창이 나타납니다. 단어가 표시 되 면 `Press any key to continue`, enter 키를 클릭 합니다. 창을 닫은 후에 Visual Studio를 엽니다.  
  
3. SimpleProject 프로젝트 다시 빌드 및 디버깅을 시작 합니다. 실험적 인스턴스가 표시 됩니다.  
  
4. 실험적 인스턴스에서 SimpleProject 프로젝트를 만듭니다. 에 **새 프로젝트** 대화 상자에서 **SimpleProject**합니다.  
  
5. SimpleProject의 새 인스턴스를 표시 됩니다.  
  
   ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
   ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>프로젝트 형식 자식 노드 만들기  
 프로젝트 형식 노드는 자식 노드를 추가할 수는 **새 프로젝트** 대화 상자.  예를 들어 SimpleProject 프로젝트 형식에 대 한 콘솔 응용 프로그램, 창 응용 프로그램, 웹 응용 프로그램 등에 대 한 자식 노드가 있을 수 있습니다.  
  
 프로젝트 파일을 변경 하 고 추가 하 여 자식 노드가 만들어집니다 \<OutputSubPath > 자식은 \<ZipProject > 요소입니다. 모든 자식 노드 템플릿을 빌드 또는 배포 중 복사 되 면 프로젝트 템플릿 폴더의 하위 폴더입니다.  
  
 이 섹션에서는 SimpleProject 프로젝트 형식에 대 한 콘솔 자식 노드를 만드는 방법을 보여 줍니다.  
  
1. \Templates\Projects\ConsoleApp \Templates\Projects\SimpleProject\ 폴더의 이름을\\입니다.  
  
2. 에 **속성** 창 \Templates\Projects\ConsoleApp\ 폴더에서 모든 5 개의 파일을 선택 하 고 있는지 확인 합니다 **빌드 작업** 로 설정 되어 **ZipProject**합니다.  
  
3. SimpleProject.vstemplate 파일에 다음 줄의 끝에 추가 된 \<TemplateData > 닫는 태그 바로 앞의 섹션입니다.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     이렇게 하면 콘솔 응용 프로그램 템플릿을 콘솔 자식 노드와 SimpleProject 부모 노드의 자식 노드 위의 한 수준에서 표시 합니다.  
  
4. SimpleProject.vstemplate 파일을 저장 합니다.  
  
5. .Csproj 파일에서 추가 \<OutputSubPath > 각 ZipProject 요소입니다. 앞으로 프로젝트를 업로드 하 고 프로젝트 파일을 편집 합니다.  
  
6. 찾을 \<ZipProject > 요소입니다. 각 \<ZipProject > 요소에 추가 \<OutputSubPath > 요소 콘솔 값을 지정 합니다. ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7. 이 추가 \<PropertyGroup > 프로젝트 파일에:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8. 프로젝트 파일을 저장 하 고 프로젝트를 다시 로드 합니다.  
  
## <a name="testing-the-project-type-child-node"></a>프로젝트 형식 자식 노드를 테스트합니다.  
 확인 하려면 수정 된 프로젝트 파일을 테스트 하는지 여부를 **콘솔** 에 자식 노드가 표시 됩니다는 **새 프로젝트** 대화 상자.  
  
1. 실행 합니다 **Microsoft Visual Studio 실험적 인스턴스 재설정** 도구입니다.  
  
2. SimpleProject 프로젝트 다시 빌드 및 디버깅을 시작 합니다. 실험적 인스턴스에서가 나타납니다.  
  
3. 에 **새 프로젝트** 대화 상자에서 클릭 합니다 **SimpleProject** 노드. 합니다 **콘솔 응용 프로그램** 템플릿이 표시 해야 합니다 **템플릿** 창.  
  
4. 확장 된 **SimpleProject** 노드. 합니다 **콘솔** 자식 노드가 표시 됩니다. 합니다 **SimpleProject 응용 프로그램** 서식 파일에 계속 표시 합니다 **템플릿** 창입니다.  
  
5. . 클릭 **취소** 디버깅을 중지 하 고  
  
   ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
   ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>프로젝트 템플릿 매개 변수를 대체합니다.  
 [기본 프로젝트 시스템, 1 부](../extensibility/creating-a-basic-project-system-part-1.md) 덮어쓰는 방법을 보여 주었습니다는 `ProjectNode.AddFileFromTemplate` 템플릿 매개 변수를 대체 하는 기본 유형의 작업을 수행 하는 메서드. 이 섹션에서는 보다 복잡 한 Visual Studio 템플릿 매개 변수를 사용 하는 방법을 설명 합니다.  
  
 Visual Studio 템플릿을 사용 하 여 프로젝트를 만들면 합니다 **새 프로젝트** 프로젝트를 사용자 지정 대화 상자에서 템플릿을 사용 하 여 매개 변수는 대체 문자열입니다. 템플릿 매개 변수는 시작 하 고 예를 들어 $time$ 달러 기호로 끝나는 특수 토큰입니다. 다음 두 매개 변수는 사용자 지정 템플릿을 기반으로 하는 프로젝트에서 사용 하도록 설정 하는 데 특히 유용:  
  
- [1 ~ 10] $GUID$ 새 Guid로 대체 됩니다. 예를 들어 $guid1$ 최대 10 개의 고유 Guid를 지정할 수 있습니다.  
  
- $safeprojectname $는 사용자가 제공한 이름 합니다 **새 프로젝트** 대화 상자에서 모든 안전 하지 않은 문자 및 공백을 제거 하도록 수정 합니다.  
  
  템플릿 매개 변수의 전체 목록은 [템플릿 매개 변수](../ide/template-parameters.md)를 참조하세요.  사용자 고유의 사용자 지정 템플릿 매개 변수를 만들려는 경우 참조 [NIB: 방법: 템플릿 사용자 지정 매개 변수를 전달할](https://msdn.microsoft.com/5bc2ad11-84c7-4683-a276-e5e00d85d8fb)합니다.  
  
#### <a name="to-substitute-project-template-parameters"></a>프로젝트 템플릿 매개 변수를 대체 합니다.  
  
1. SimpleProjectNode.cs 파일에서 제거 된 `AddFileFromTemplate` 메서드.  
  
2. \Templates\Projects\ConsoleApp\SimpleProject.myproj 파일에서 찾습니다는 \<RootNamespace > 속성 $safeprojectname $ 해당 값을 변경 합니다.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3. \Templates\Projects\SimpleProject\Program.cs 파일에서 파일의 내용을 다음 코드로 바꿉니다.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4. SimpleProject 프로젝트 다시 빌드 및 디버깅을 시작 합니다. 실험적 인스턴스에서 표시 됩니다.  
  
5. 새 SimpleProject 콘솔 응용 프로그램을 만듭니다. (에 **프로젝트 형식** 창 **SimpleProject**합니다. 아래 **Visual Studio 설치 된 템플릿**를 선택 **콘솔 응용 프로그램**.)  
  
6. 새로 만든 프로젝트에서 Program.cs를 엽니다. 다음과 같이 표시 됩니다 (파일의 GUID 값이 달라 집니다.):  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>프로젝트 속성 페이지 만들기  
 사용자 보기를 업데이트 하 고 템플릿을 기반으로 하는 프로젝트의 속성을 변경할 수 있도록 프로젝트 형식에 대 한 속성 페이지를 만들 수 있습니다. 이 섹션에서는 구성에 관계 없이 속성 페이지를 만드는 방법을 보여 줍니다. 이 기본 속성 페이지 속성 표를 사용 하 여 속성 페이지 클래스에서 노출 하는 공용 속성을 표시 합니다.  
  
 속성 페이지에서 파생 된 `SettingsPage` 기본 클래스입니다. 제공한 속성 그리드는 `SettingsPage` 클래스의 가장 기본적인 데이터 형식을 인식 하 고 표시 하는 방법을 알고 있습니다.  또한는 `SettingsPage` 클래스에는 프로젝트 파일에 속성 값을 유지 하는 방법을 알고 있습니다.  
  
 이 섹션에서 만든 속성 페이지를 사용 하 여 변경 하 고 이러한 프로젝트 속성을 저장할 수 있습니다.  
  
- AssemblyName  
  
- OutputType  
  
- RootNamespace.  
  
1. 추가 SimpleProjectPackage.cs 파일인 `ProvideObject` 특성을 `SimpleProjectPackage` 클래스:  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    이렇게 하면 속성 페이지 클래스를 사용 하 고 등록 `GeneralPropertyPage` com  
  
2. SimpleProjectNode.cs 파일에서 이러한 두 가지 재정의 메서드를 추가 합니다 `SimpleProjectNode` 클래스:  
  
   ```  
   protected override Guid[] GetConfigurationIndependentPropertyPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
       return result;  
   }  
   protected override Guid[] GetPriorityProjectDesignerPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
   }  
   ```  
  
    두이 방법 모두 속성 페이지 Guid의 배열을 반환합니다.  GeneralPropertyPage GUID는 배열의 유일한 요소 이므로 **속성 페이지** 대화 상자에 한 페이지만 표시 됩니다.  
  
3. GeneralPropertyPage.cs SimpleProject 프로젝트 라는 클래스 파일을 추가 합니다.  
  
4. 다음 코드를 사용 하 여이 파일의 내용을 바꿉니다.  
  
   ```  
   using System;  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Project;  
   using System.ComponentModel;  
  
   namespace SimpleProject  
   {  
       [ComVisible(true)]  
       [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
       public class GeneralPropertyPage : SettingsPage  
       {  
           private string assemblyName;  
           private OutputType outputType;  
           private string defaultNamespace;  
  
           public GeneralPropertyPage()  
           {  
               this.Name = "General";  
           }  
  
           [Category("AssemblyName")]  
           [DisplayName("AssemblyName")]  
           [Description("The output file holding assembly metadata.")]  
           public string AssemblyName  
           {  
               get { return this.assemblyName; }  
           }  
           [Category("Application")]  
           [DisplayName("OutputType")]  
           [Description("The type of application to build.")]  
           public OutputType OutputType  
           {  
               get { return this.outputType; }  
               set { this.outputType = value; this.IsDirty = true; }  
           }  
           [Category("Application")]  
           [DisplayName("DefaultNamespace")]  
           [Description("Specifies the default namespace for added items.")]  
           public string DefaultNamespace  
           {  
               get { return this.defaultNamespace; }  
               set { this.defaultNamespace = value; this.IsDirty = true; }  
           }  
  
           protected override void BindProperties()  
           {  
               this.assemblyName = this.ProjectMgr.GetProjectProperty(  
   "AssemblyName", true);  
               this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
   "RootNamespace", false);  
  
               string outputType = this.ProjectMgr.GetProjectProperty(  
   "OutputType", false);  
               this.outputType =   
   (OutputType)Enum.Parse(typeof(OutputType), outputType);  
           }  
  
           protected override int ApplyChanges()  
           {  
               this.ProjectMgr.SetProjectProperty(  
   "AssemblyName", this.assemblyName);  
               this.ProjectMgr.SetProjectProperty(  
   "OutputType", this.outputType.ToString());  
               this.ProjectMgr.SetProjectProperty(  
   "RootNamespace", this.defaultNamespace);  
               this.IsDirty = false;  
  
               return VSConstants.S_OK;  
           }  
       }  
   }  
   ```  
  
    `GeneralPropertyPage` 클래스 AssemblyName, OutputType, 및 RootNamespace 세 가지 공용 속성을 노출 합니다. AssemblyName set 메서드 없음 있으므로 읽기 전용 속성으로 표시 됩니다. OutputType 열거형된 상수, 이므로 드롭다운 목록으로 표시 됩니다.  
  
    합니다 `SettingsPage` 기본 클래스를 제공 `ProjectMgr` 속성을 유지 합니다. 합니다 `BindProperties` 메서드는 `ProjectMgr` 지속형된 속성 값을 검색 하 고 해당 속성을 설정 합니다.  합니다 `ApplyChanges` 메서드 `ProjectMgr` 속성의 값을 얻으려면 및 프로젝트 파일에 유지 합니다. 속성이 설정 메서드 집합 `IsDirty` 속성을 유지 해야 함을 나타내려면 true입니다.  지 속성에는 프로젝트 또는 솔루션을 저장할 때 발생 합니다.  
  
5. SimpleProject 솔루션 다시 빌드 및 디버깅을 시작 합니다. 실험적 인스턴스에서 표시 됩니다.  
  
6. 실험적 인스턴스에서 새 SimpleProject 응용 프로그램을 만듭니다.  
  
7. Visual Studio 프로젝트를 만들려면 Visual Studio 템플릿을 사용 하 여 프로젝트 팩터리를 호출 합니다. 새 Program.cs 파일이 코드 편집기에서 열립니다.  
  
8. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**를 클릭 하 고 **속성**합니다. **속성 페이지** 대화 상자가 표시됩니다.  
  
   ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>프로젝트 속성 페이지를 테스트합니다.  
 이제 수정 하 고 속성 값을 변경할 수 있는지 여부를 테스트할 수 있습니다.  
  
1. 에 **MyConsoleApplication 속성 페이지** 대화 상자에서 변경 합니다 **DefaultNamespace** 에 **MyApplication**합니다.  
  
2. 선택 된 **OutputType** 속성을 선택한 후 **클래스 라이브러리**합니다.  
  
3. 클릭 **Apply**를 클릭 하 고 **확인**합니다.  
  
4. 다시 합니다 **속성 페이지** 대화 상자 및 변경 내용이 지속 되었는지 확인 합니다.  
  
5. Visual Studio의 실험적 인스턴스를 닫습니다.  
  
6. 실험적 인스턴스를 다시 엽니다.  
  
7. 다시 합니다 **속성 페이지** 대화 상자 및 변경 내용이 지속 되었는지 확인 합니다.  
  
8. Visual Studio의 실험적 인스턴스를 닫습니다.  
  
   ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")
