---
title: 새 프로젝트 대화 상자에 디렉터리 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e81d09c2a4e97ca5f3da112e593b04b219e6314
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327997"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에 디렉터리 추가
새 프로젝트 형식을 만들면도 등록할 수 있습니다에 새 디렉터리를 **새 프로젝트** 대화 상자를 템플릿으로 사용 하기 위해 표시 합니다. 다음 코드 예제에서는 노드 라고도 하며 새 디렉터리를 등록 하는 방법에 설명 합니다. 예제에서는 VSPackage에 의해 노출 되는 템플릿 *CLSID_Package*, 등록 됩니다. 결과적으로 좌 변의 합니다 **새 프로젝트** 대화 상자에 따른 이름으로 추가 노드를 제공 합니다 *Folder_Label_ResID* 리소스. 이 리소스는 VSPackage 위성 DLL에서에서 로드 됩니다.

 합니다 **폴더** 값 중인 폴더의 GUID를 나타내는 합니다 *Folder_Label_ResID* 노드가 표시 됩니다. GUID를 나타내는 예에서는 **기타 프로젝트** 폴더에는 **프로젝트 형식** 창의 **새 프로젝트** 대화 상자. 경우는 **기타 프로젝트** 값이 없음, 레이블이 최상위에 배치 됩니다.

 `TemplatesDir` 값 프로젝트 템플릿이 포함 된 디렉터리의 전체 경로 지정 합니다. 이러한 파일 일 수 있습니다 *.vsz* 파일 또는 일반적인 템플릿 파일을 복제할 수 있습니다.

 지정 하는 경우 `TemplatesLocalizedSubDir`의 하위 디렉터리의 이름을 지정 하는 문자열의 리소스 ID 여야 합니다 `TemplatesDir` 지역화 된 템플릿에 들어 있는입니다. 때문에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 문자열 리소스를 로드 위성 DLL에서에서 하나에 있는 경우 각 위성 DLL 포함 될 수 있습니다 다른 하위 디렉터리 이름입니다. `SortPriority` 값 정렬 우선 순위를 지정 합니다.

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

## <a name="see-also"></a>참고자료
- [프로젝트 및 항목 템플릿을 등록합니다](../../extensibility/internals/registering-project-and-item-templates.md)
- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [새 항목 추가 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)