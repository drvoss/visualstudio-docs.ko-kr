---
title: '방법: 설치 관리자에 대 한 레지스트리 정보를 생성 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
- VSPackages, registration manifests
ms.assetid: b1b41012-a777-4ccf-81a6-3b41f0e96583
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be17b2f78048bd0e9c2052066796857dbeba2048
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435258"
---
# <a name="how-to-generate-registry-information-for-an-installer"></a>방법: 설치 관리자에 대한 레지스트리 정보 생성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

관리 되는 VSPackage에 대 한 등록 매니페스트를 생성 하는 RegPkg.exe 유틸리티를 사용할 수 있습니다. 매니페스트는 Windows Installer 설치 패키지를 통합할 수 있습니다. RegPkg도 파일을 생성할 수에 따라 설치 원본 파일에 포함 될 수 있는 합니다 [Windows Installer XML 도구 집합](http://go.microsoft.com/fwlink/?LinkId=62238)합니다.  
  
> [!IMPORTANT]
> 적절 한 Windows Installer 속성을 포맷 되므로 사용 하 여 출력을 편집 해야 RegPkg를 사용할 때마다, RegPkg 개발 시스템에 관련 된 경로 이름을 생성 합니다. 예를 들어 InprocServer32 값 이어야 합니다 **[SystemFolder]mscoree.dll** 경로 사용 해야 **[#filekey]** 하 고 **[$componentkey]** 합니다. 이 방식으로 출력을 조정 Windows 또는 다른 디렉터리, 지역화 된 디렉터리 이름 및 사용자가 선택할 수 있는 경로 다른 드라이브에 설치 되어 있는 컴퓨터를 지원 합니다. 자세한 내용은 [서식 있음](http://go.microsoft.com/fwlink/?LinkId=71120) Windows Installer SDK의 합니다. 개발 시스템 경로 대 한 RegPkg 규칙에 따라 경우-예를 들어 파일 형식의 File_ Id*filename*-적은 변경 해야 합니다.  
  
### <a name="to-create-a-registration-manifest"></a>등록 매니페스트를 만들려면  
  
- RegPkg 사용 하 여 실행 합니다 **/regfile** 전환 합니다. 다른 스위치, 출력 파일의 이름 및 VSPackage의 경로 제공 합니다.  
  
     예를 들어, 명령 프롬프트에서 입력 다음과 유사 하 게 합니다.  
  
    ```  
    [Visual Studio SDK installation path]\VisualStudioIntegration\Tools\Bin\RegPkg /regfile:MyRegFile.reg MyPackage.dll  
    ```  
  
### <a name="to-view-a-registration-manifest"></a>등록 매니페스트를 보려면  
  
- 임의의 텍스트 편집기에서 등록 매니페스트를 엽니다.  
  
     다음 예제는 RegPkg IronPython 언어 서비스에 대해 만든 등록 매니페스트:  
  
    ```  
    REGEDIT4  
  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python]  
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"  
    "DisplayName"="131"  
    "IndexPath"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\SnippetsIndex.xml"  
    "LangStringId"="python"  
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "ShowRoots"=dword:00000000  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs]  
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths]  
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]  
    @="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"  
    "InprocServer32"="C:\\WINNT\\system32\\mscoree.dll"  
    "Class"="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage"  
    "Assembly"="IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py]  
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python]  
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"  
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "LangResID"=dword:00000064  
    "ShowMatchingBrace"=dword:00000001  
    "CodeSense"=dword:00000001  
    "MatchBraces"=dword:00000001  
    "EnableCommenting"=dword:00000001  
    "ShowCompletion"=dword:00000001  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]  
    "ID"=dword:00000001  
    "MinEdition"="standard"  
    "ProductVersion"="1.0"  
    "ProductName"="Visual Studio Integration of IronPython Language Service"  
    "CompanyName"="Microsoft Corporation"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}]  
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "Name"="IPythonLibraryManager"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}]  
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "Name"="Python"  
  
    ```  
  
### <a name="to-create-a-windows-installer-xml-toolset-include-file"></a>Windows Installer XML 도구 집합을 만들려면 파일을 포함 합니다.  
  
- RegPkg 사용 하 여 실행 합니다 **/wixfile** 전환 합니다. 다른 스위치, 출력 파일의 이름 및 VSPackage의 경로 제공 합니다.  
  
     예를 들어, 명령 프롬프트에서 입력 다음과 유사 하 게 합니다.  
  
    ```  
    [Visual Studio SDK installation path]\VisualStudioIntegration\Tools\Bin\RegPkg /codebase /wixfile:IronPython.LanguageService.wxi ..\bin\Release\IronPython.LanguageService.dll  
    ```  
  
### <a name="to-view-a-windows-installer-xml-toolset-include-file"></a>Windows Installer XML 도구 집합을 보려면 파일을 포함 합니다.  
  
- 열기 Windows Installer XML 도구 집합 파일을 포함 텍스트 편집기에서.  
  
     다음 예제는 IronPython 언어 서비스에 대 한 RegPkg 만든 포함 파일:  
  
    ```  
    <Include>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\IntellisenseProviders\IronPythonCodeProvider">  
        <Registry Name="GUID" Value="{9c1807ea-d222-4775-afa8-c092c580e451}" Type="string" />  
        <Registry Name="AddItemLanguageName" Value="Iron Python" Type="string" />  
        <Registry Name="DefaultExtension" Value=".py" Type="string" />  
        <Registry Name="ShortLanguageName" Value="IronPython;Python" Type="string" />  
        <Registry Name="TemplateFolderName" Value="IronPython" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">  
        <Registry Name="DisplayName" Value="131" Type="string" />  
        <Registry Name="IndexPath" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\SnippetsIndex.xml" Type="string" />  
        <Registry Name="LangStringId" Value="python" Type="string" />  
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />  
        <Registry Name="ShowRoots" Value="0" Type="integer" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs">  
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths">  
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string" />  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">  
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />  
        <Registry Name="LangResID" Value="100" Type="integer" />  
        <Registry Name="ShowCompletion" Value="1" Type="integer" />  
        <Registry Name="ShowMatchingBrace" Value="1" Type="integer" />  
        <Registry Name="CodeSense" Value="1" Type="integer" />  
        <Registry Name="MatchBraces" Value="1" Type="integer" />  
        <Registry Name="EnableCommenting" Value="1" Type="integer" />  
        <Registry Name="DefaultToInsertSpaces" Value="1" Type="integer" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2394.27719, Culture=neutral, PublicKeyToken=null" Type="string">  
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />  
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage" Type="string" />  
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />  
        <Registry Name="ID" Value="1" Type="integer" />  
        <Registry Name="MinEdition" Value="standard" Type="string" />  
        <Registry Name="ProductVersion" Value="1.0" Type="string" />  
        <Registry Name="ProductName" Value="Visual Studio Integration of IronPython Language Service" Type="string" />  
        <Registry Name="CompanyName" Value="Microsoft Corporation" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\CLSID\{9c1807ea-d222-4775-afa8-c092c580e451}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string">  
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />  
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string" />  
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />  
        <Registry Name="ThreadingModel" Value="Both" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">  
        <Registry Name="Name" Value="IPythonLibraryManager" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">  
        <Registry Name="Name" Value="Python" Type="string" />  
      </Registry>  
    </Include>  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [Vspackage 등록](registering-vspackages.md)   
 [VSPackage](../../extensibility/internals/vspackages.md)
