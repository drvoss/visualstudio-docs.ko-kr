---
title: 프로젝트 및 항목 템플릿 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185832"
---
# <a name="registering-project-and-item-templates"></a>프로젝트 템플릿 및 항목 템플릿 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 형식에는 해당 프로젝트 및 프로젝트 항목 템플릿을 위치한 디렉터리를 등록 해야 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에 표시할 작업을 결정 하 여 프로젝트 형식과 연결 된 등록 정보를 사용 하는 **새 프로젝트 추가** 하 고 **새 항목 추가** 대화 상자.  
  
 템플릿에 대 한 자세한 내용은 참조 하세요. [추가 프로젝트 및 프로젝트 항목 템플릿](../../extensibility/internals/adding-project-and-project-item-templates.md)합니다.  
  
## <a name="registry-entries-for-projects"></a>프로젝트에 대 한 레지스트리 항목  
 다음 예제에서는 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio 레지스트리 항목 표시\\<*버전*>. 함께 제공 되는 테이블 예제에서 사용 되는 요소에 설명 합니다.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|이름|형식|설명|  
|----------|----------|-----------------|  
|@|REG_SZ|이러한 종류의 프로젝트의 기본 이름입니다.|  
|DisplayName|REG_SZ|패키지에서 등록 하는 위성 DLL에서에서 검색할 이름의 리소스 ID입니다.|  
|패키지|REG_SZ|패키지에서 등록 된 패키지의 클래스 ID입니다.|  
|ProjectTemplatesDir|REG_SZ|프로젝트 템플릿 파일의 기본 경로입니다. 프로젝트 템플릿 파일에서 표시 되는 **새 프로젝트** 템플릿.|  
  
### <a name="registering-item-templates"></a>등록 항목 템플릿  
 항목 템플릿을 저장할 디렉터리를 등록 해야 합니다.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|이름|형식|Description|  
|----------|----------|-----------------|  
|@|REG_SZ|항목 추가 템플릿에 대 한 리소스 ID입니다.|  
|TemplatesDir|REG_SZ|에 대 한 대화 상자에서 표시 된 프로젝트 항목의 경로 **새 항목 추가** 마법사.|  
|TemplatesLocalizedSubDir|REG_SZ|리소스 ID는 TemplatesDir의 하위 디렉터리의 이름을 지정 하는 문자열의 지역화 된 템플릿에 보유 합니다. 때문에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 로드의 문자열 리소스를 위성 Dll에 있는 경우, 각 위성 DLL에는 지역화 된 다른 하위 디렉터리 이름을 포함할 수 있습니다.|  
|SortPriority|REG_DWORD|서식 파일에 표시 되는 순서를 제어 하는 SortPriority를 설정 합니다 **새 항목 추가** 대화 상자. 더 큰 SortPriority 값 템플릿 목록에서 앞에 표시 됩니다.|  
  
### <a name="registering-file-filters"></a>파일 필터를 등록합니다.  
 필요에 따라 필터를 등록할 수 있습니다는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 파일 이름에 대 한 프롬프트를 사용 합니다. 예를 들어 합니다 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 필터링 합니다 **파일 열기** 대화 상자는:  
  
 **Visual C# 파일 (\*.cs\*.resx,\*.settings,\*.xsd 인데\*.wsdl);\*합니다. cs\*.resx,\*.settings,\*.xsd 인데\*.wsdl)**  
  
 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio 아래에 자체 하위 키에 등록 된 각 필터를 지원 하기 위해 여러 필터의 등록\\<*버전*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*하위 키*>. 하위 키 이름은 임의입니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 하위 키의 이름을 무시 하 고 해당 값만 사용 합니다.  
  
 다음 표에 나와 있는 플래그를 설정 하 여 사용 되는 필터 컨텍스트를 제어할 수 있습니다. 필터 설정 플래그에 없는 경우이 나열 됩니다에서 공통 필터를 **기존 항목 추가** 대화 상자 및 **파일 열기** 대화 상자, 하지만 사용 되지 것입니다에 **파일에서 찾기**  대화 상자.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|이름|형식|Description|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|공통 필터 중 하나에서 필터를 사용 하면 합니다 **파일에서 찾기** 대화 상자. 공통 필터는 필터 일반적으로 표시 되지 전에 필터 목록에 나열 됩니다.|  
|CommonOpenFilesFilter|REG_DWORD|공통 필터 중 하나에서 필터를 사용 하면 합니다 **열려 있는 파일** 대화 상자. 공통 필터는 필터 일반적으로 표시 되지 전에 필터 목록에 나열 됩니다.|  
|FindInFilesFilter|REG_DWORD|공통 필터 후 필터를 나열 합니다 **파일에서 찾기** 대화 상자.|  
|NotOpenFileFilter|REG_DWORD|필터에서 사용 되지 않음을 나타냅니다 합니다 **열려 있는 파일** 대화 상자.|  
|NotAddExistingItemFilter|REG_DWORD|필터에서 사용 되지 않음을 나타냅니다 합니다 **기존 항목 추가** 대화 상자.|  
|SortPriority|REG_DWORD|필터 표시 되는 순서를 제어 하는 SortPriority를 설정 합니다. 더 큰 SortPriority 값 필터 목록에서 앞에 표시 됩니다.|  
  
## <a name="directory-structure"></a>디렉터리 구조  
 Vspackage에 넣을 수 템플릿 파일 및 폴더 아무 곳 이나 로컬 또는 원격 디스크 위치는 통합된 개발 환경 (IDE)를 통해 등록 된으로 합니다. 그러나 조직 편의성을 위해 제품의 설치 경로 다음 디렉터리 구조를 권장 합니다.  
  
 \Templates  
  
 \Projects (프로젝트 템플릿을 포함)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (프로젝트 항목을 포함 합니다.)  
  
 \Class  
  
 \Form  
  
 \Web Page  
  
 \HelperFiles (다중 파일 프로젝트 항목에 사용 되는 파일 포함)  
  
 \WizardFiles  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [마법사](../../extensibility/internals/wizards.md)   
 [응용 프로그램 지역화](../../ide/localizing-applications.md)   
 [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
