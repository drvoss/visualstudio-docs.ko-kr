---
title: 컨텍스트 매개 변수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 679bf567d2f44564d31d70b62c8663e665e1ea65
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697282"
---
# <a name="context-parameters"></a>컨텍스트 매개 변수
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE) 마법사를 추가할 수 있습니다 합니다 **새 프로젝트**를 **새 항목 추가**, 또는 **하위 프로젝트 추가** 대화 상자. 추가 마법사에서 사용할 수는 **파일** 메뉴에서 프로젝트를 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**합니다. IDE는 마법사의 구현에 컨텍스트 매개 변수를 전달합니다. IDE는 마법사를 호출 하는 경우 프로젝트의 상태를 정의 하는 컨텍스트 매개 변수입니다.  
  
 IDE 설정 하 여 마법사를 시작 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> IDE의 호출에서 플래그를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 프로젝트에 대 한 메서드. 설정 된 경우 프로젝트를 수행 해야 하는 `IVsExtensibility::RunWizardFile` 등록된 마법사 이름 또는 GUID 및 IDE에서 전달 하는 다른 컨텍스트 매개 변수를 사용 하 여 실행할 메서드를 합니다.  
  
## <a name="context-parameters-for-new-project"></a>새 프로젝트에 대 한 컨텍스트 매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`WizardType`|등록 된 마법사 형식 (<xref:EnvDTE.Constants.vsWizardNewProject>) 또는 마법사의 형식을 나타내는 GUID입니다. 에 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 구현 마법사에 대 한 GUID가 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|고유 문자열로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 이름입니다.|  
|`LocalDirectory`|프로젝트 파일을 작업 하는 로컬 위치입니다.|  
|`InstallationDirectory`|디렉터리 경로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 설치 됩니다.|  
|`FExclusive`|프로젝트 열기 솔루션을 닫아야를 나타내는 부울 플래그입니다.|  
|`SolutionName`|디렉터리 부분 없이.sln 확장명 솔루션 파일의 이름입니다. .Suo 파일 이름을 사용 하 여도 만들어집니다 `SolutionName`합니다. 마법사를 사용 하 여이 인수는 빈 문자열이 없는 경우 <xref:EnvDTE._Solution.Create%2A> 사용 하 여 프로젝트를 추가 하기 전에 <xref:EnvDTE._Solution.AddFromTemplate%2A>입니다. 이 이름은 빈 문자열을 사용 하 여 <xref:EnvDTE._Solution.AddFromTemplate%2A> 호출 하지 않고 <xref:EnvDTE._Solution.Create%2A>합니다.|  
|`Silent`|마법사를 자동으로 실행할지 여부를 나타내는 부울 값 처럼 **완료** 클릭 (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>에 대 한 컨텍스트 매개 변수는 새 항목 추가  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`WizardType`|등록 된 마법사 형식 (<xref:EnvDTE.Constants.vsWizardAddItem>) 또는 마법사의 형식을 나타내는 GUID입니다. 에 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 구현 마법사에 대 한 GUID가 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|고유 문자열로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 이름입니다.|  
|`ProjectItems`|작업 중인 프로젝트 파일을 포함 하는 로컬 위치입니다.|  
|`ItemName`|추가 되는 항목의 이름입니다. 이 이름은 기본 파일 이름 또는 사용자가에서 파일 이름을 합니다 **항목 추가** 대화 상자. 이름을은.vsdir 파일에 설정 된 플래그를 기반으로 합니다. 이름을 null 값이 될 수 있습니다.|  
|`InstallationDirectory`|디렉터리 경로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 설치 됩니다.|  
|`Silent`|마법사를 자동으로 실행할지 여부를 나타내는 부울 값 처럼 **완료** 클릭 (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>추가 하위 프로젝트에 대 한 컨텍스트 매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`WizardType`|등록 된 마법사 형식 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) 또는 마법사의 형식을 나타내는 GUID입니다. 에 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 구현 마법사에 대 한 GUID가 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|고유 문자열로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 이름입니다.|  
|`ProjectItems`|에 대 한 포인터를 `ProjectItems` 마법사 작동 하는 컬렉션입니다. 이 포인터는 프로젝트 계층 선택에 따라 마법사에 전달 됩니다. 사용자가 일반적으로 항목을 저장할 폴더를 선택 하 고 프로젝트의 다음 호출 **항목 추가** 대화 상자.|  
|`LocalDirectory`|프로젝트 파일을 작업 하는 로컬 위치입니다.|  
|`ItemName`|추가 되는 항목의 이름입니다. 이 이름은 기본 파일 이름 또는 사용자가에서 파일 이름을 합니다 **항목 추가** 대화 상자. 이름을은.vsdir 파일에 설정 된 플래그를 기반으로 합니다. 이름을 null 값이 될 수 있습니다.|  
|`InstallationDirectory`|디렉터리 경로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 설치 됩니다.|  
|`Silent`|마법사를 자동으로 실행할지 여부를 나타내는 부울 값 처럼 **완료** 클릭 (`TRUE`).|  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)   
 [마법사](../../extensibility/internals/wizards.md)   
 [마법사 (합니다. Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [마법사를 시작 하는 것에 대 한 컨텍스트 매개 변수](https://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)
