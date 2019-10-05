---
title: 기호 검색 도구를 지 원하는 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5e79969c3b4be22a3c9bb01f06297f54b0734ee
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746002"
---
# <a name="supporting-symbol-browsing-tools"></a>기호 검색 도구 지원
**개체 브라우저**, **클래스 뷰**를 **호출 브라우저** 하 고 **기호 찾기 결과** 도구는 Visual Studio의 기능을 검색 하는 기호를 제공 합니다. 이러한 도구는 기호의 계층적 트리 보기를 표시 하 고 트리에서 기호 사이의 관계를 보여 줍니다. 네임 스페이스, 개체, 클래스, 클래스 멤버 및 다양 한 구성 요소에 포함 된 다른 언어 요소에 기호를 나타낼 수 있습니다. 구성 요소는 Visual Studio 프로젝트,.NET Framework 구성 요소를 외부 및 형식 (.tlb) 라이브러리를 포함 합니다. 자세한 내용은 [코드 구조 보기](../../ide/viewing-the-structure-of-code.md)를 참조하세요.

## <a name="symbol-browsing-libraries"></a>기호 검색 라이브러리
 언어 구현자로 구성 요소에서 기호를 추적 하 고 인터페이스의 집합을 통해 Visual Studio 개체 관리자에 게는 기호 목록을 제공 하는 라이브러리를 만들어 Visual Studio 기호 검색 기능을 확장할 수 있습니다. 라이브러리에서 설명 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> 인터페이스입니다. Visual Studio 개체 관리자 요청에 응답할 새 데이터에 대 한 기호 검색 도구에서 라이브러리에서 데이터 가져오기 및 구성 합니다. 이후에 채웁니다 또는 요청된 된 데이터를 사용 하 여 도구를 업데이트 합니다. Visual Studio 개체 관리자에 대 한 참조를 가져오는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>를 전달 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID 서비스는 `GetService` 메서드.

 각 라이브러리는 모든 라이브러리의 정보를 수집 하는 Visual Studio 개체 관리자를 사용 하 여 등록 해야 합니다. 라이브러리를 등록 하려면 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 메서드. 요청을 시작 하는 도구에 따라 Visual Studio 개체 관리자는 적절 한 라이브러리를 찾아서 데이터를 요청 합니다. 라이브러리 간에 데이터 이동 하며 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에서 설명 하는 기호 목록 개체 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 인터페이스입니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자는 주기적으로 기호 검색 도구 라이브러리에 포함 된 최신 데이터를 반영 하도록 새로 고침 하는 일을 담당 합니다.

 아래 다이어그램 샘플 라이브러리와 Visual Studio 개체 관리자 간의 요청/데이터 교환 프로세스의 핵심 요소를 포함합니다. 다이어그램에서 인터페이스를 사용 하면 관리 코드 응용 프로그램의 일부인 합니다.

 ![데이터 흐름 라이브러리와 개체 관리자 간의](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 기호 목록에는 Visual Studio 개체 관리자를 제공 하려면 먼저 등록 해야 라이브러리는 Visual Studio 개체 관리자를 사용 하 여 호출 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 메서드. 라이브러리를 등록 한 후 Visual Studio 개체 관리자 라이브러리의 기능에 대 한 특정 정보를 요청 합니다. 예를 들어 라이브러리 플래그를 요청 하 고 호출 하 여 범주를 지원 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> 메서드. 어느 시점에서 도구 중 하나이 라이브러리에서 데이터를 요청 하는 경우 개체 관리자를 최상위 기호 목록을 호출 하 여 요청 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> 메서드. 응답으로 라이브러리 기호 목록을 제조 및 Visual Studio 개체 관리자를 통해 노출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 인터페이스입니다. 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자를 호출 하 여 목록에 있는 항목 수를 결정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> 메서드. 모든 다음 요청 목록에 지정 된 항목과 관련 및 각 요청에 항목 인덱스 번호를 제공 합니다. Visual Studio 개체 관리자를 호출 하 여 항목의 다른 속성, 유형 및 접근성을에 정보를 수집 진행 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> 메서드.

 호출 하 여 항목의 이름을 결정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> 메서드 호출 하 여 아이콘 정보를 요청 하 고는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> 메서드. 아이콘 항목 이름의 왼쪽에 표시 되 고 항목, 접근성, 및 기타 속성의 형식을 보여 줍니다.

 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manager 호출은 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> 경우 지정 된 목록 항목을 확장할 수 있고 자식 항목을 확인 하는 방법입니다. 개체 관리자를 호출 하 여 기호의 자식 목록 요청 UI 요소를 확장 하는 요청을 보내는 경우를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> 메서드. 필요에 따라 빌드되는 트리의 다른 부분을 사용 하 여 프로세스가 계속 됩니다.

> [!NOTE]
> 네이티브 코드 기호 공급자를 구현 하려면 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> 인터페이스입니다.

## <a name="see-also"></a>참고 항목
- [방법: 개체 관리자에 라이브러리 등록](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [방법: 라이브러리에서 제공하는 기호 목록을 개체 관리자에 노출](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [방법: 라이브러리의 기호 식별](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)