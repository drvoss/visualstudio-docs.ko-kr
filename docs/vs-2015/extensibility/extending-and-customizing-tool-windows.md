---
title: 확장 및 도구 Windows 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b232fa1275bce453e3b32cea6a5ff37fdd501c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204538"
---
# <a name="extending-and-customizing-tool-windows"></a>도구 창 확장 및 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio는 여러 가지 도구 창, 문서 창 및 대화 상자 창 예를 들어 windows 제공합니다. 속성 창, 출력 창 및 작업 목록 창에는 같은 다른 windows 도구 창의 종류가.입니다.  
  
## <a name="tool-windows"></a>도구 창  
 Visual Studio 도구 창에는 파일 기반 하지 않는 일반적으로 읽기 전용 창입니다. 이런 점에서 파일을 읽기/쓰기 모드로 표시하는 문서 창과는 다릅니다. **도구 상자**, **솔루션 탐색기**, **속성** 창 및 **웹 브라우저** 는 도구 창의 예입니다.  
  
 간단한 도구 창을 만드는 방법을 알아보려면 참조 [도구 창 추가](../extensibility/adding-a-tool-window.md)합니다.  
  
 등록 하는 도구 창이 Visual Studio를 사용 하 여 참조 하세요 [도구 창 등록](../extensibility/registering-a-tool-window.md)합니다.  
  
 도구 창은 기본적으로 단일 인스턴스입니다. 즉, 도구 창의 인스턴스를 한 번에 하나만 열 수 있습니다. 단일 인스턴스 도구 창이 열린 후 IDE를 닫을 때까지 열린 상태로 유지됩니다. 단일 인스턴스 도구 창을 닫으면 표시 유형만 변경 됩니다. 창의 여러 인스턴스가 동시에 열릴 수 있도록 다중 인스턴스 도구 창도 만들 수 있습니다. 참조 [다중 인스턴스 도구 창 만들기](../extensibility/creating-a-multi-instance-tool-window.md) 자세한 내용은 합니다.  
  
 도구 창 수 *동적*를 볼 수 있도록 관련된 된 UI 컨텍스트가 적용 될 때마다 의미 합니다. 자동 표시를 사용하면 IDE에서 창의 혼잡함을 줄일 수 있습니다. 자세한 내용은 [동적 도구 창 열기](../extensibility/opening-a-dynamic-tool-window.md)합니다.  
  
 도구 창을 문서 프레임에서 도킹, 부동 또는 탭할 수 있습니다. 도구 창 프레임이 IDE에서 제공되고 크기, 위치, 도킹 상태 및 기타 영구적 속성을 제어하는 데 사용됩니다. 도구 창에서 내용을 표시합니다. 기본 크기 및 위치는 도구 창이 처음 열릴 때만 적용되고 이후에는 도구 창 상태가 유지됩니다.  
  
 도구 창에서 WPF 사용자 컨트롤을 호스트하고 도구 모음을 지원할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 속성을 재정의하여 호스트된 컨트롤의 핸들을 반환할 수 있습니다.  
  
 도구 창에 다양 한 기능을 추가할 수 있습니다. 예를 들어, 도구 모음을 추가할 수 있습니다. [도구 창에 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md) 또는 바로 가기 메뉴: [도구 창의 바로 가기 메뉴를 추가](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)합니다. 도구 창 내에서 항목을 검색할 수 있는 검색 컨트롤을 추가할 수 있습니다. [도구 창에 검색 추가](../extensibility/adding-search-to-a-tool-window.md)합니다.  
  
 도구 창의 이벤트를 구독할 수 있습니다. [이벤트 구독](../extensibility/subscribing-to-an-event.md)합니다.  
  
## <a name="extending-existing-tool-windows"></a>기존 도구 Windows 확장  
 새 도구 창에 대 한 정보를 추가할 수 있습니다 **옵션** 페이지 및의 새 설정의 **속성** 페이지를 쓸 합니다 **작업 목록** 및 **출력**  windows. 자세한 내용은 [속성, 작업 목록, 출력 및 옵션 Windows 확장](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) 하 고 [확장 속성, 작업 목록, 출력 및 옵션 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)합니다.  
  
## <a name="modal-dialog-boxes"></a>모달 대화 상자  
 Visual Studio 확장에서 만들어야 모달 대화 상자에서 파생 시켜 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, 있으며 UI의 나머지 부분을 제어할 수 있습니다. 자세한 내용은 [만들기 및 모달 대화 상자 관리](../extensibility/creating-and-managing-modal-dialog-boxes.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [도구 창으로 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)
