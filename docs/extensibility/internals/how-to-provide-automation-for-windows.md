---
title: '방법: Windows에 대 한 자동화 제공 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 547ace3b093aa8c5f21b0bcbdbafda5a1452dd23
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351052"
---
# <a name="how-to-provide-automation-for-windows"></a>방법: Windows에 대 한 자동화 제공

문서 창과 도구에 대 한 자동화를 제공할 수 있습니다. 창에서 자동화 개체를 사용할 수 있도록 하 고 환경에 아직 때마다 자동화 끄 제공 작업 목록으로 바로 사용할 수 있는 자동화 개체를 제공 합니다.

## <a name="automation-for-tool-windows"></a>도구 창에 대 한 자동화

환경 도구 창에는 표준 반환 하 여 자동화를 제공 <xref:EnvDTE.Window> 다음 절차에 설명 된 대로 개체:

1. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 메서드를 사용 하 여 환경을 통해 [__VSFPROPID 합니다. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) 으로 `VSFPROPID` 가져오려면 매개 변수는 `Window` 개체입니다.

2. 호출자를 통해 도구 창에 대 한 VSPackage 관련 자동화 개체를 요청 하는 경우 <xref:EnvDTE.Window.Object%2A>, 환경 `QueryInterface` 에 대 한 `IExtensibleObject`를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, 또는 `IDispatch` 인터페이스입니다. 둘 다 `IExtensibleObject` 하 고 `IVsExtensibleObject` 제공을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 메서드.

3. 환경을 다음으로 호출 합니다 `GetAutomationObject` 전달 메서드 `NULL`, VSPackage 관련 개체를 다시 전달 하 여 응답 합니다.

4. 호출 하는 경우 `QueryInterface` 에 대 한 `IExtensibleObject` 하 고 `IVsExtensibleObject` 실패 하는 환경 호출 `QueryInterface` 에 대 한 `IDispatch`합니다.

## <a name="automation-for-document-windows"></a>문서 창에 대 한 자동화

표준 <xref:EnvDTE.Document> 또한 개체는 환경에서 사용할 수 있는 편집기의 자체 구현이 있을 수 있지만 합니다 <xref:EnvDTE.Document> 구현 하 여 개체 `IExtensibleObject` 인터페이스 및 대응 `GetAutomationObject`합니다.

편집기를 통해 검색할 VSPackage 관련 자동화 개체를 제공할 수 또한 합니다 <xref:EnvDTE.Document.Object%2A> 메서드를 구현 하 여는 `IVsExtensibleObject` 또는 `IExtensibleObject` 인터페이스입니다. 합니다 [VSSDK 샘플](https://aka.ms/vs2015sdksamples) RTF 문서 관련 자동화 개체를 제공 합니다.

## <a name="see-also"></a>참고자료

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>