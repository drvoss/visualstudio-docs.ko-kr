---
title: 기여 하는 새 항목 추가 대화 상자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 443f52edda5f3bedb2e3f8c8dbbe748254fd7be7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335566"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 참여
프로젝트 하위 형식에 대 한 항목의 전체 새 디렉터리를 제공할 수 있습니다 합니다 **새 항목 추가** 등록 하 여 대화 상자 **항목 추가** 에서 템플릿 합니다 **프로젝트** 레지스트리 하위 키입니다.

## <a name="register-add-new-item-templates"></a>새 항목 추가 템플릿 등록
 이 섹션에서는 아래에 있는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** 레지스트리에서 합니다. 다음 레지스트리 항목 가정를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 가상 프로젝트 하위 형식으로 집계 합니다. 에 대 한 항목을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트는 다음과 같습니다.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]
@="#2143"
"DefaultProjectExtension"="vbproj"
"PossibleProjectExtensions"="vbproj;vbp"
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]
@="#100"
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"
```

 합니다 **AddItemTemplates\TemplateDirs** 항목에서 사용할 수 있는 디렉터리의 경로를 사용 하 여 레지스트리 항목을 포함 하는 하위 키를 **새 항목 추가** 대화 상자에 배치 됩니다.

 환경에 모든 항목을 자동으로 로드 합니다 **AddItemTemplates** 아래에서 데이터를 **프로젝트** 레지스트리 하위 키입니다. 이 데이터는 특정 프로젝트 하위 형식에 대 한 데이터 뿐만 아니라 기본 프로젝트 구현에 대 한 데이터에 포함할 수 있습니다. 각 프로젝트 하위 형식 프로젝트 형식으로 식별 되 **GUID**합니다. 대체 집합이 프로젝트 하위 형식을 지정할 수 있습니다 **항목 추가** 서식 파일에 사용할 특정 버전이 지정 된 프로젝트 인스턴스를 지원 하 여 합니다 `VSHPROPID_ AddItemTemplatesGuid` 열거형 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 프로젝트 하위 형식의 GUID 값을 반환 하는 구현입니다. 경우는 `VSHPROPID_AddItemTemplatesGuid` 속성을 지정 하지 않으면 기본 프로젝트 GUID가 사용 됩니다.

 항목을 필터링 할 수 있습니다 합니다 **새 항목 추가** 구현 하 여 대화 상자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> 프로젝트 하위 형식 aggregator 개체의 인터페이스입니다. 집계 하 여 데이터베이스 프로젝트를 구현 하는 프로젝트 하위 형식 예를 들어를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트를 필터링 할 수는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에서 특정 항목을 **새 항목 추가** 대화 상자에 필터링을 구현 하 여 설정에서 추가할 수 있습니다 데이터베이스를 지원 하 여 프로젝트 관련 항목 `VSHPROPID_ AddItemTemplatesGuid` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>합니다. 필터링 및 항목을 추가 대 한 자세한 내용은 합니다 **새 항목 추가** 대화 상자, 참조 [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)합니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [일반적으로 프로젝트를 확장 하는 데 사용 되는 개체에 대 한 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)