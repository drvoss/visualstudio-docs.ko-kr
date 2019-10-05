---
title: 핵심 편집기 내에서 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203946"
---
# <a name="inside-the-core-editor"></a>핵심 편집기 내부
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기가 텍스트 정보를 쿼리하고 수정할 수 있는 여러 구성 요소 집합입니다. 핵심 편집기 기존 API를 사용 하 여 사용자 지정 하면, 편집기 어댑터를 통해 라우팅되는 이러한 사용자 지정을 사용 하 여 계속 수 있습니다. 하지만 좋습니다, 새 편집기 API로 사용자 지정을 적용 하는.  
  
 다음 영역은 핵심 편집기의 몇 가지 중요 한 측면을 보여 줍니다.  
  
- 텍스트 버퍼  
  
- 텍스트 보기  
  
- 코드 창  
  
- 텍스트 마커  
  
- 텍스트 관리자  
  
- 언어 서비스와의 통합  
  
## <a name="in-this-section"></a>섹션 내용  
 [레거시 API를 사용하여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 사용 하는 방법에 대 한 단계별 지침을 제공 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 편집기 코어의 인스턴스를 만들려고 합니다.  
  
 [레거시 API를 사용하여 텍스트 버퍼에 액세스](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 버퍼에 액세스 하는 데 사용 되 고 텍스트 버퍼 개체에 의해 구현 된 인터페이스의 목록을 제공 하는 연결 된 시스템에서는 코어 편집기에서 텍스트 버퍼의 역할에 설명 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>합니다.  
  
 [레거시 API의 텍스트 버퍼 이벤트](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 텍스트 버퍼 이벤트 알림에 사용 되는 인터페이스의 목록을 제공 합니다.  
  
 [방법: 레거시 API를 사용하여 텍스트 버퍼 이벤트에 등록](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 텍스트 버퍼 이벤트를 알리기 위해 하는 방법을 설명 합니다.  
  
 [텍스트 관리자를 사용하여 글로벌 설정 모니터링](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 핵심 편집기 구성 요소를 사용 하 여 전역 기본 설정 정보를 공유 하면 텍스트 관리자가 사용 하는 방법 및 텍스트 관리자 이벤트에 대 한 알림을 수신 하는 방법을 설명 합니다.  
  
 [레거시 API를 사용하여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 핵심 편집기에서 텍스트 보기의 역할을 설명 하 고 구현한 인터페이스를 나열 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 개체입니다.  
  
 [레거시 API를 사용하여 코드 Windows 사용자 지정](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 코드 창을 텍스트 뷰를 포함 하는 데 사용 됩니다, 코드 창 장식을 수 있도록 코드 창 관리자는 사용 하는 방법에 대해 설명 및 새 뷰에 대 한 알림을 제공 하는 방법에 대 한 정보를 제공 합니다.  
  
 [레거시 API를 사용하여 보기 설정 변경](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 보기 설정 하는 방법 및 강제 설정을 제거 하는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [언어 서비스 및 핵심 편집기](../extensibility/language-services-and-the-core-editor.md)  
 컨트롤 코드 장식 하도록 언어 서비스의 인스턴스화를 설명합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [연습: 코어 편집기 만들기 및 편집기 파일 형식 등록](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 관리 코드에서 핵심 편집기를 시작 하는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [드롭다운 표시줄](../extensibility/drop-down-bar.md)  
 드롭다운 표시줄 코드 창에는 및 드롭다운 표시줄을 구현할 때 사용 되는 인터페이스를 설명 하는 방법을 설명 합니다.  
  
 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)  
 텍스트 마커 및 코어 편집기에서 사용 되는 방법의 개념을 설명 하 고 액세스 하 고 텍스트 마커를 관리 하는 데 사용 되는 인터페이스를 나열 합니다.  
  
 [방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)  
 텍스트 마커를 만드는 방법 및 바로 가기 메뉴를 사용자 지정 명령을 추가 하는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)  
 사용자 지정 텍스트 마커를 만드는 방법 및 표식 유형 서비스로 제공 하는 방법에 대 한 단계별 지침을 제공 합니다.
