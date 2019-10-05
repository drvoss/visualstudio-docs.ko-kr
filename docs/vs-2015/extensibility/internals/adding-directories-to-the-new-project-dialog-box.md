---
title: 새 프로젝트 대화 상자에 디렉터리 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203868"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에 디렉터리 추가
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

새 프로젝트 형식을 만들면도 등록할 수 있습니다에 새 디렉터리를 **새 프로젝트** 대화 상자를 템플릿으로 사용 하기 위해 표시 합니다. 다음 코드 예제에서는 노드 라고도 하며 새 디렉터리를 등록 하는 방법에 설명 합니다. 예제에서는 VSPackage CLSID_Package에서 노출 하는 템플릿 등록 됩니다. 결과적으로 좌 변의 합니다 **새 프로젝트** 대화 상자 이름 Folder_Label_ResID 리소스를 기준으로 추가 노드를 제공 합니다. 이 리소스는 VSPackage 위성 DLL에서에서 로드 됩니다.  
  
 합니다 **폴더** 값 Folder_Label_ResID 노드에 표시 되는 폴더의 GUID를 나타냅니다. GUID를 나타내는 예에서는 **기타 프로젝트** 폴더에는 **프로젝트 형식** 창의 **새 프로젝트** 대화 상자. 경우는 **기타 프로젝트** 값이 없음, 레이블이 최상위에 배치 됩니다.  
  
 TemplatesDir 값 프로젝트 템플릿이 포함 된 디렉터리의 전체 경로 지정 합니다. 이러한 파일은.vsz 파일 또는 일반적인 템플릿 파일을 복제할 수 있습니다.  
  
 TemplatesLocalizedSubDir를 지정 하는 경우 지역화 된 템플릿에 들어 있는 TemplatesDir의 하위 디렉터리의 이름을 지정 하는 문자열의 리소스 ID 여야 합니다. 때문에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 문자열 리소스를 로드 위성 DLL에서에서 하나에 있는 경우 각 위성 DLL 포함 될 수 있습니다 다른 하위 디렉터리 이름입니다. SortPriority 값 정렬 우선 순위를 지정합니다.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)   
 [항목에 추가 된 새 항목 추가 대화 상자](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [새 항목 추가 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
