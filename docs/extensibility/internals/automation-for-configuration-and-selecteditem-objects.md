---
title: 구성 및 SelectedItem 개체 자동화 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c9dc8012433f9ec73f15b9249f6b7ac08bdad7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347967"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>구성 및 SelectedItem 개체 자동화

빌드 및 Visual Studio에서 선택한 항목 프로세스를 자동화할 수 있습니다.

## <a name="automation-for-builds"></a>빌드에 대 한 자동화

빌드 또는 구성에 구현 하는 경우 제공 되는 자동화 모델이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>합니다. 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md)를 참조하세요.

VSPackage를 만들고 구성 옵션을 제어 하려는 경우 자동화 모델을 사용 해야 합니다.

## <a name="automation-for-selecteditem"></a>SelectedItem에 대 한 자동화

에 대 한 구현을 제공 해야 합니다 `SelectedItem` Visual Studio 표준 구현을 포함 하기 때문에 개체입니다. 그러나 구현할 수 있습니다는 `SelectedItem` 것이 바람직 할 개체입니다. 포함 하는 개체를 구현 해야 합니다는 `SelectedItem` 인터페이스 및에 대 한 호출에 대 한 응답을 반환 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드 `VSITEMID` 로 [__VSHPROPID 합니다. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)합니다.

## <a name="see-also"></a>참고자료

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [자동화 모델에 참여](../../extensibility/internals/contributing-to-the-automation-model.md)
- [빌드 구성 이해](../../ide/understanding-build-configurations.md)