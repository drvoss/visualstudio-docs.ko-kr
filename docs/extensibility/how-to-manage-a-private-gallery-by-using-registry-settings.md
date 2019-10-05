---
title: '방법: 레지스트리 설정을 사용 하 여 개인 갤러리 관리 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b4f33f7ecf974fe527f814b9febdc861101f1ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318491"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>방법: 레지스트리 설정을 사용 하 여 개인 갤러리 관리
관리자 또는 격리 셸 확장의 개발자 인 경우에 컨트롤, 템플릿 및 도구는 Visual Studio 갤러리, 샘플 갤러리 또는 전용 갤러리에 대 한 액세스를 제어할 수 있습니다. 갤러리를 사용 가능 여부 확인을 만들려면을 *.pkgdef* 수정 된 레지스트리 키와 값을 설명 하는 파일입니다.

## <a name="manage-private-galleries"></a>개인 갤러리 관리
 만들 수 있습니다는 *.pkgdef* 파일을 여러 컴퓨터에서 갤러리에 대 한 액세스를 제어 합니다. 이 파일에는 다음 형식을 이어야 합니다.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 `Repositories` 키가 참조 갤러리를 사용 하거나 사용 하지 않도록 설정 합니다. Visual Studio 갤러리 및 샘플 갤러리는 다음 리포지토리에 Guid를 사용합니다.

- Visual Studio 갤러리: 0F45E408-7995-4375-9485-86B8DB553DC9

- 샘플 갤러리: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled` 값은 선택 사항입니다. 기본적으로 갤러리 사용 됩니다.

  합니다 `Priority` 갤러리에 나열 되는 순서를 결정 하는 값을 **옵션** 대화 상자. Visual Studio 갤러리에 우선 순위 10 있고 샘플 갤러리 20 우선 순위입니다. 전용 갤러리 우선 순위가 100부터 시작합니다. 표시 되는 순서는 지역화 된 값에 의해 결정 됩니다 여러 갤러리 동일한 우선 순위 값이 있으면 `DisplayName` 특성입니다.

  `Protocol` Atom 기반 또는 SharePoint를 기반으로 갤러리에 값이 필요 합니다.

  중 하나 `DisplayName`, 또는 둘 다 `DisplayNameResourceID` 고 `DisplayNamePackageGuid`를 지정 해야 합니다. 모든 지정 된 경우 해당 `DisplayNameResourceID` 및 `DisplayNamePackageGuid` 쌍을 사용 합니다.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>.Pkgdef 파일을 사용 하 여 Visual Studio 갤러리를 사용 하지 않도록 설정
 갤러리에서 사용 하지 않도록 설정 된 *.pkgdef* 파일입니다. 다음 항목은 Visual Studio 갤러리를 비활성화합니다.

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 다음 항목 샘플 갤러리를 비활성화합니다.

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>참고자료
- [전용 갤러리](../extensibility/private-galleries.md)