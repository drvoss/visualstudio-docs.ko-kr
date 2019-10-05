---
title: '새 프로젝트 생성: 내부적으로 2 부 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6643c52ff8e5801c562524e99c4e3f03c00f74b9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687495"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>새 프로젝트 생성: 내부 살펴보기, 2부
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[새 프로젝트 생성: 내부적으로 1 부](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 살펴보았습니다 하는 방법을 **새 프로젝트** 대화 상자가 채워집니다. 선택한를 가정해 보겠습니다를 **Visual C# Windows 응용 프로그램**작성, 합니다 **이름** 및 **위치** 텍스트 상자 및 확인을 클릭된 합니다.  
  
## <a name="generating-the-solution-files"></a>솔루션 파일 생성  
 지시 하는 응용 프로그램 템플릿을 선택 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 압축을 풀고 해당.vstemplate 파일을 열에이 파일의 XML 명령을 해석 하기 위한 템플릿을 시작 합니다. 이러한 명령은 새로운 또는 기존의 솔루션에서 프로젝트 및 프로젝트 항목을 만듭니다.  
  
 템플릿의는.vstemplate 파일을 포함 하는 동일한.zip 폴더에서 항목 템플릿을 호출 하는 소스 파일을 압축을 풉니다. 서식 파일을 적절 하 게 사용자 지정 새 프로젝트에 이러한 파일을 복사 합니다. 프로젝트 및 항목 템플릿의 개요를 참조 하세요. [NIB: Visual Studio 템플릿](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)합니다.  
  
### <a name="template-parameter-replacement"></a>템플릿 매개 변수 대체  
 항목 템플릿을 새 프로젝트에 복사 하는 서식 파일, 모든 템플릿 매개 변수 파일을 사용자 지정 하는 문자열을 사용 하 여 대체 합니다. 템플릿 매개 변수는 특수 한 토큰은 앞뒤에 달러 기호를 예를 들어입니다 $date$입니다.  
  
 일반적인 프로젝트 항목 템플릿을 살펴보겠습니다. 추출 하 고 Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 폴더에서 Program.cs를 검사 합니다.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 템플릿을 대체 하는 간단한 라는 새 Windows 응용 프로그램 프로젝트를 만드는 경우는 `$safeprojectname$` 매개 변수를 프로젝트의 이름입니다.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 템플릿 매개 변수의 전체 목록은 [템플릿 매개 변수](../../ide/template-parameters.md)를 참조하세요.  
  
## <a name="a-look-inside-a-vstemplate-file"></a>살펴보기를 합니다. VSTemplate 파일  
 이 형식은 기본.vstemplate 파일을  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 살펴보았습니다 합니다 \<TemplateData > 섹션을 [새 프로젝트 생성: 내부적으로 1 부](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)합니다. 이 섹션의 태그의 모양을 제어 되는 **새 프로젝트** 대화 상자.  
  
 태그는 \<TemplateContent > 새 프로젝트 및 프로젝트 항목의 생성 제어 섹션입니다. 다음은 \<TemplateContent > \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 폴더 cswindowsapplication.vstemplate 파일에서 섹션입니다.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 합니다 \<프로젝트 > 프로젝트의 생성을 제어 하는 태그 및 \<ProjectItem > 태그 프로젝트 항목의 생성을 제어 합니다. ReplaceParameters 매개 변수가 true 인 경우 서식 파일 프로젝트 파일 또는 항목에 모든 템플릿 매개 변수 사용자 지정 합니다. 이 경우 모든 프로젝트 항목 사용자 지정 된를 Settings.settings 제외 하 고 합니다.  
  
 TargetFileName 매개 변수 이름 및 결과 프로젝트 파일 또는 항목의 상대 경로 지정합니다. 이 프로젝트에 대 한 폴더 구조를 만들 수 있습니다. 이 인수를 지정 하지 않으면, 프로젝트 항목의 이름은 프로젝트 항목 템플릿 해야 합니다.  
  
 결과 Windows 응용 프로그램 폴더 구조는 다음과 같습니다.  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 첫 번째이자 유일한 \<프로젝트 > 템플릿 읽기가 태그:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 이렇게 하면 템플릿 항목 windowsapplication.csproj를 지정 하 고 복사 함으로써 Simple.csproj 프로젝트 파일을 만들려면 새 프로젝트 템플릿.  
  
### <a name="designers-and-references"></a>디자이너 및 참조  
 Properties 폴더 있는지, 그리고 파일이 예상 되는 솔루션 탐색기에서 볼 수 있습니다. 하지만 참조 프로젝트에 대 한 자세한 내용 및 디자이너 파일 Resources.resx에 Resources.Designer.cs 등 Form1.Designer.cs Form1.cs 종속성?  생성 되 면 Simple.csproj 파일에서 설정이 됩니다.  
  
 다음은 \<ItemGroup > 프로젝트 참조를 만드는 Simple.csproj에서:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 이 솔루션 탐색기에 표시 되는 6 개의 프로젝트 참조를 확인할 수 있습니다. 다음은 다른 섹션 \<ItemGroup >. 여러 줄 코드의 명확성을 위해 삭제 되었습니다. 이 절에서는 Settings.Designer.cs를 Settings.settings에 따라 달라 집니다.  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>참고 항목  
 [새 프로젝트 생성: 내부 살펴보기, 1부](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)
