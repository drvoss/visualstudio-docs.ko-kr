---
title: '방법: Windows에 대 한 자동화 기능 제공 Microsoft Docs'
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
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848850"
---
# <a name="how-to-provide-automation-for-windows"></a>방법: windows에 대 한 자동화 제공

문서 및 도구 창에 대 한 자동화를 제공할 수 있습니다. 자동화를 제공 하는 것은 창에서 자동화 개체를 사용할 수 있도록 하 고 환경에서 작업 목록과 같이 미리 만들어진 자동화 개체를 아직 제공 하지 않을 때마다 사용 하는 것이 좋습니다.

## <a name="automation-for-tool-windows"></a>도구 창에 대 한 자동화

환경에서는 다음 절차에 설명 된 대로 표준 <xref:EnvDTE.Window> 개체를 반환 하 여 도구 창에 대 한 자동화를 제공 합니다.

1. __VSFPROPID를 사용 하 여 환경을 통해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 메서드를 호출 합니다 [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>)`Window` 개체를 가져오기 위한 `VSFPROPID` 매개 변수로 VSFPROPID_ExtWindowObject.

2. 호출자가 <xref:EnvDTE.Window.Object%2A>를 통해 도구 창에 대 한 VSPackage automation 개체를 요청 하면 환경에서 `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>또는 `IDispatch` 인터페이스에 대 한 `QueryInterface`를 호출 합니다. `IExtensibleObject` 및 `IVsExtensibleObject` 모두 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 메서드를 제공 합니다.

3. 그러면 환경에서 `NULL`를 전달 하는 `GetAutomationObject` 메서드를 호출 하 고 VSPackage 개체를 다시 전달 하 여 응답 합니다.

4. `IExtensibleObject` 및 `IVsExtensibleObject`에 대 한 `QueryInterface`를 호출할 경우 환경에서는 `IDispatch`에 대 한 `QueryInterface`를 호출 합니다.

## <a name="automation-for-document-windows"></a>문서 창에 대 한 자동화

표준 <xref:EnvDTE.Document> 개체는 환경 에서도 사용할 수 있습니다. 하지만 편집기는 `IExtensibleObject` 인터페이스를 구현 하 고 `GetAutomationObject`에 응답 하 여 <xref:EnvDTE.Document> 개체의 고유한 구현을 가질 수 있습니다.

또한 편집기는 `IVsExtensibleObject` 또는 `IExtensibleObject` 인터페이스를 구현 하 여 <xref:EnvDTE.Document.Object%2A> 메서드를 통해 검색 되는 VSPackage 특정 자동화 개체를 제공할 수 있습니다. 고가 중 [진한 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 은 RTF 문서 관련 자동화 개체를 제공 합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
