---
title: 일반적으로 프로젝트를 확장 하는 데 사용 되는 개체에 대 한 Catid | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a9a5643a217fb9be3147417ffd0405ab9b0cc9f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324255"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>일반적으로 프로젝트를 확장 하는 데 사용 되는 개체에 대 한 Catid
다음 표에서 확장 하는 데 사용 되는 Catid `Project` 및 `ProjectItem` 자동화 개체에 대 한 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], 및 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트. 에 정의 된 이러한 Catid *VSLangProj.olb*합니다.

## <a name="listing-of-catids"></a>Catid 목록

|이름|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic Catid
 다음 표에서 Catid를 확장 하는 데 사용 되는 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 개체를 검색 합니다. 모든 정의 된 *VSLangProj.olb*합니다.

|이름|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>Visual C# Catid
 다음 Catid를 사용 하 여을 확장할 수 있습니다 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 개체를 검색 합니다. 모든 정의 된 *VSLangProj.olb*합니다.

|이름|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>C++Catid
 다음 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트 시스템 Catid에서 형식 라이브러리에서 노출 되지 않는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 및 이러한 프로젝트 개체를 확장 하려고 할 때마다 코드에 포함 되어야 합니다. 형식 라이브러리의 이후 릴리스에서 이러한 Catid가 포함될지 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

|이름|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 다음 코드 예제에서는 코드에서 이러한 Catid를 프로그래밍 하는 방법을 보여 줍니다.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 다음 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트 시스템 Catid 또한에 있는 형식 라이브러리에서 노출 되지 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 및 이러한 프로젝트 개체를 확장 하려고 할 때마다 코드에 포함 되어야 합니다. 에서만 사용할 수 있는 이러한 Catid [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003의 이후 릴리스에서 제공 되지 것입니다 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

|이름|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 다음 코드 예제에서는 코드에서 이러한 Catid를 프로그래밍 하는 방법을 보여 줍니다.

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 에 대 한 Guid를 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 형식 표에 표시 됩니다.

| 프로젝트 형식 | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>참고자료
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [프로젝트 및 항목 템플릿을 등록합니다](../../extensibility/internals/registering-project-and-item-templates.md)