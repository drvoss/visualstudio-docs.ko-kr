---
title: 프로젝트 형식 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b950ea6dde73ecb7f20ef45e945106e8711aefb0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353358"
---
# <a name="registering-a-project-type"></a>프로젝트 형식 등록
레지스트리 항목을 사용 하도록 설정 하는 새 프로젝트 형식을 만들면 만들어야 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 인식 및 프로젝트 형식을 사용 하 여 작동 합니다. 일반적으로 레지스트리 스크립트 (.rgs) 파일을 사용 하 여 이러한 레지스트리 항목을 만듭니다.

 아래 예제에서 레지스트리에서 문을 기본 경로 제공 하 고 데이터 해당 하는 경우 뒤에 각 문에 대 한 레지스트리 스크립트에서 항목을 포함 하는 테이블입니다. 테이블은 스크립트 항목 및 문에 대 한 추가 정보를 제공합니다.

> [!NOTE]
> 다음 레지스트리 정보를 형식의 예제 및 프로젝트 형식 등록을 작성 하 게 됩니다 레지스트리 스크립트에 있는 항목의 목적을 할 것입니다. 실제 항목 및 해당 용도 프로젝트 형식의 특정 요구 사항에 따라 달라질 수 있습니다. 프로젝트를 개발 하는 형식에 매우 유사 하나를 찾을 수는 샘플을 검토 하 고 해당 샘플에 대 한 레지스트리 스크립트를 검토 해야 합니다.

 다음 예제는 HKEY_CLASSES_ROOT에서입니다.

## <a name="example"></a>예제

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|프로젝트의 이름 및 설명 형식 확장.figp 있는 파일입니다.|
|`Content Type`|REG_SZ|`Text/plain`|프로젝트 파일에 대 한 콘텐츠 형식입니다.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|이 유형의 프로젝트에 사용 되는 기본 아이콘입니다. 프로젝트 형식 DLL의 기본 위치는 레지스트리의 % 모듈 % 문이 완료 됩니다.|
|`@`|REG_SZ|`&Open in Visual Studio`|기본 응용 프로그램을이 프로젝트 형식을 열 수입니다.|
|`@`|REG_SZ|`devenv.exe "%1"`|이 유형의 프로젝트를 열 때 실행 되는 기본 명령입니다.|

 다음 예제에서는 HKEY_LOCAL_MACHINE에서 되며 레지스트리 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] 아래에 있습니다.

## <a name="example"></a>예제

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@` (기본값)|REG_SZ|`FigPrj Project VSPackage`|VSPackage (프로젝트 형식)를 등록 하는 지역화할 수 있는 이름이입니다.|
|`InprocServer32`|REG_SZ|`%MODULE%`|프로젝트 형식 DLL의 경로입니다. 이 DLL을 로드 하 고를 VSPackage CLSID를 전달 하는 IDE `DllGetClassObject` 가져오려는 <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> 생성 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 개체입니다.|
|`CompanyName`|REG_SZ|`Microsoft`|프로젝트 형식을 개발한 회사의 이름입니다.|
|`ProductName`|REG_SZ|`Figure Project Sample`|프로젝트 형식에 대 한 이름입니다.|
|`ProductVersion`|REG_SZ|`9.0`|프로젝트 형식의 버전 번호를 해제 합니다.|
|`MinEdition`|REG_SZ|`professional`|등록 되는 VSPackage의 버전입니다.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|VSPackage 프로젝트에 대 한 키를 로드 하는 패키지입니다. 키에는 환경을 시작 된 후에 프로젝트가 로드 될 때 유효성이 검사 됩니다.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|위성 DLL 프로젝트 형식에 대 한 지역화 된 리소스를 포함 하는 파일 이름입니다.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|위성 DLL의 경로입니다.|
|`FigProjectsEvents`|REG_SZ|값 방침을 참조 하세요.|이 automation 이벤트에 대해 반환 되는 텍스트 문자열을 결정 합니다.|
|`FigProjectItemsEvents`|REG_SZ|값 방침을 참조 하세요.|이 automation 이벤트에 대해 반환 되는 텍스트 문자열을 결정 합니다.|

 다음 예제에서는 모든 레지스트리 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 아래에 있습니다.

## <a name="example"></a>예제

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|이 유형의 프로젝트의 기본 이름입니다.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|패키지에서 등록 하는 위성 DLL에서에서 검색할 이름의 리소스 ID입니다.|
|`Package`|REG_SZ|`%CLSID_Package%`|패키지에서 등록 하는 VSPackage의 클래스 ID입니다.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|프로젝트 템플릿 파일의 기본 경로입니다. 이들은 새 프로젝트 템플릿에 의해 표시 되는 파일입니다.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|프로젝트 항목 템플릿 파일의 기본 경로입니다. 이들은 새 항목 추가 템플릿에 의해 표시 되는 파일입니다.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|구현 하는 IDE를 사용 하도록 설정 합니다 **열려** 대화 상자.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|이 프로젝트 형식 (프로젝트 팩터리)에서 열려 있는 프로젝트를 처리할지 여부를 확인 하려면 IDE에서 사용 합니다. 둘 이상의 항목에 대 한 형식은 세미콜론으로 구분 된 목록입니다. 예를 들어 "vdproj; vdp"입니다.|
|`DefaultProjectExtension`|REG_SZ|`.figp`|다른 이름으로 저장 작업에 대 한 기본 파일 이름 확장명으로 IDE에서 사용 합니다.|
|`Filter Settings`|REG_DWORD|다양 한 문 및 다음 표에 설명 참조 합니다.|UI 대화 상자에서 파일을 표시 하는 것에 대 한 다양 한 필터를 설정 하려면 이러한 설정이 사용 됩니다.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|항목 추가 템플릿에 대 한 리소스 ID입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|에 대 한 대화 상자에서 표시 된 프로젝트 항목의 경로 **새 항목 추가** 템플릿.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|에 표시 된 파일의 트리 노드가 정렬 순서를 결정 합니다 **새 항목 추가** 대화 상자.|

 다음 표에서 앞의 코드 세그먼트에서 사용할 수 있는 필터 옵션을 보여 줍니다.

|필터 옵션|설명|
|-------------------|-----------------|
|`CommonFindFilesFilter`|필터의 공통 필터 중 하나 임을 나타냅니다 합니다 **파일에서 찾기** 대화 상자. 공통 필터는 일반적으로 표시 되지 않은 필터 전에 필터 목록에 나열 됩니다.|
|`CommonOpenFilesFilter`|필터의 공통 필터 중 하나 임을 나타냅니다 합니다 **열려 있는 파일** 대화 상자. 공통 필터는 일반적으로 표시 되지 않은 필터 전에 필터 목록에 나열 됩니다.|
|`FindInFilesFilter`|나타냅니다 필터의 필터 중 하나는 **파일에서 찾기** 대화 상자 및 공통 필터 나열 됩니다.|
|`NotOpenFileFilter`|필터에서 사용 되지 것입니다 나타냅니다 합니다 **열려 있는 파일** 대화 상자.|
|`NotAddExistingItemFilter`|추가 필터를 사용 되지 것입니다 나타냅니다 **기존 항목** 대화 상자.|

 기본적으로 이러한 많은 플래그 집합이 또는 필터가 없는 경우 필터는 합니다 **기존 항목 추가** 대화 상자와 **열려 있는 파일** 공통 필터는 나열 된 대화 상자. 필터에서 사용 되지 않습니다 합니다 **파일에서 찾기** 대화 상자.

 다음 예제에서는 모든 레지스트리 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 아래에 있습니다.

## <a name="example"></a>예제

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|새 프로젝트 템플릿에 대 한 리소스 ID입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|기본 등록된 프로젝트 형식의 프로젝트에 대 한 경로입니다.|
|`SortPriority`|REG_DWORD|`41 (x29)`|새 프로젝트 마법사 대화 상자에 표시 되는 프로젝트의 순서를 정렬 하는 집합입니다.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0이이 유형의 프로젝트를 새 프로젝트 대화 상자에만 표시 됨을 나타냅니다.|

 다음 예제에서는 모든 레지스트리 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 아래에 있습니다.

## <a name="example"></a>예제

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|없음|기타 파일 프로젝트 항목에 대해 다음 항목을 되는지 여부를 나타내는 기본 값입니다.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|새 항목 추가 템플릿 파일에 대 한 리소스 ID 값입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|에 표시 되는 항목의 기본 경로 **새 항목 추가** 대화 상자.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|트리 노드의 표시에 대 한 정렬 순서를 설정 합니다 **새 항목 추가** 대화 상자.|

 다음 예제는 레지스트리의 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] 아래에 있습니다.

## <a name="example"></a>예제

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 메뉴 항목이 메뉴 정보를 검색할 사용 되는 리소스를 IDE를 가리킵니다. 메뉴 데이터베이스로이 데이터 병합 되었기 동일한 키 레지스트리 MenusMerged 섹션에 추가 됩니다. VSPackage 해야 MenusMerged 섹션에서 아무 것도 직접 수정 합니다. 데이터 필드는 다음 표에 세 개의 쉼표로 구분 된-필드 있습니다. 첫 번째 필드를 메뉴 리소스 파일의 전체 경로 식별합니다.

- 첫 번째 필드를 생략 하면 메뉴 리소스 위성 VSPackage GUID로 식별 되는 DLL에서에서 로드 됩니다.

  두 번째 필드 형식의 CTMENU 메뉴 리소스 ID를 식별합니다.

- 리소스 ID를 지정 하 고 첫 번째 매개 변수에서 파일 경로 지정 하는 경우 메뉴 리소스의 전체 파일 경로에서 로드 됩니다.

- 리소스 ID를 제공한 파일 경로가 아닙니다. 그러나 메뉴 리소스 위성 DLL에서에서 로드 됩니다.

- 전체 파일 경로 제공 하 고 리소스 ID를 생략 하는 경우의 CTO 파일로 로드할 파일을 사용할 수 있습니다.

  마지막 필드 CTMENU 리소스에 대 한 버전 번호를 식별합니다. 버전 번호를 변경 하 여 메뉴를 다시 병합할 수 있습니다.

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|메뉴 정보를 검색할 리소스입니다.|

 다음 예제에서는 모든 레지스트리 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] 아래에 있습니다.

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|그림 프로젝트-새 프로젝트 템플릿에 대 한 리소스 ID 값입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|새 프로젝트 디렉터리의 기본 경로입니다. 이 디렉터리의 항목에 표시 됩니다는 **새 프로젝트 마법사** 대화 상자.|
|`SortPriority`|REG_DWORD|`41 (x29)`|트리 노드의 프로젝트 표시 될 순서를 설정 합니다 **새 프로젝트** 대화 상자.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0이 유형의 프로젝트에만 표시 됨을 나타냅니다 합니다 **새 프로젝트** 대화 상자.|

 다음 예제는 레지스트리의 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] 아래에 있습니다.

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|등록 된 VSPackage의 클래스 ID입니다.|
|`UseInterface`|REG_DWORD|`1`|1 UI이이 프로젝트와 상호 작용 하는 것을 나타냅니다. 0 UI 인터페이스가 없는 임을 나타냅니다.|

 새 프로젝트 형식을 자주 제어 하는 The.vsz 파일 RELATIVE_PATH 항목을 포함 합니다. 다음 설정 키 프로젝트 형식의 \ProductDir 항목에서 지정 된 경로 상대적인이 경로가입니다.

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 예를 들어, 엔터프라이즈 프레임 워크 프로젝트 템플릿은 다음 레지스트리 항목을 추가합니다.

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 즉, 한 PROJECT_TYPE를 포함 하는 경우 = 이전에 지정한 ProductDir 디렉터리에 사용자.vsz 파일 환경 찾습니다.vsz 파일에서 EF 항목입니다.

## <a name="see-also"></a>참고 항목
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)
- [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)