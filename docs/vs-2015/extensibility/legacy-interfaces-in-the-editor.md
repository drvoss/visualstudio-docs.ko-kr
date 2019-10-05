---
title: 편집기에서 레거시 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180285"
---
# <a name="legacy-interfaces-in-the-editor"></a>편집기의 레거시 인터페이스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

레거시 인터페이스에서 Visual Studio 편집기에 액세스할 수 있습니다. 라고 하는 어댑터를 포함 하는 Visual Studio SDK *shim*, 이러한 인터페이스 새 편집기와 상호 작용할 수 있도록 합니다. 그럼에도 불구 하 고 새 편집기 API를 사용 하도록 레거시 코드를 업데이트 하는 것이 좋습니다. 코드를 더 잘 수행 됩니다 및 Windows Presentation Foundation (WPF) 등의 프레임 워크 MEF (Managed Extensibility) 새 기술을 사용할 수 있습니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[레거시 코드를 편집기로 조정](../extensibility/adapting-legacy-code-to-the-editor.md)|새 편집기에 코드를 조정 하는 방법에 설명 합니다.|  
|[편집기 어댑터를 사용하는 새롭거나 변경된 동작](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|편집기의 이전 버전의 편집기 어댑터의 동작 차이점에 대해 설명 합니다.|  
|[핵심 편집기 내부](../extensibility/inside-the-core-editor.md)|편집기의 이전 버전의 다양 한 구성 요소를 설명합니다.|  
|[레거시 API를 사용하여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|레거시 API를 사용 하 여 핵심 편집기를 인스턴스화하는 방법을 설명 합니다.|  
|[편집기 팩터리](../extensibility/editor-factories.md)|기존 API를 사용 하 여 편집기 팩터리를 사용 하는 방법에 설명 합니다.|  
|[방법: 편집기 파일 형식 등록](../extensibility/how-to-register-editor-file-types.md)|파일 이름 확장명을 편집기에 연결 하는 방법에 설명 합니다.|  
|[연습: 코어 편집기 만들기 및 편집기 파일 형식 등록](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|핵심 편집기를 만들고 파일 이름 확장명을 링크 하는 방법을 설명 합니다.|  
|[방법: 편집기의 컨텍스트 제공](../extensibility/how-to-provide-context-for-editors.md)|편집기에 대 한 컨텍스트를 제공 하는 방법에 설명 합니다.|  
|[언어 서비스 및 핵심 편집기](../extensibility/language-services-and-the-core-editor.md)|언어 서비스 및 편집기 간의 상호 작용을 설명합니다.|  
|[레거시 API를 사용하여 텍스트 버퍼에 액세스](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|기존 API를 사용 하 여 텍스트 버퍼에 액세스 하는 방법을 설명 합니다.|  
|[레거시 API를 사용하여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|기존 API를 사용 하 여 텍스트 보기에 액세스 하는 방법에 설명 합니다.|  
|[레거시 API를 사용하여 코드 Windows 사용자 지정](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|기존 API를 사용 하 여 코드 창을 사용자 지정 하는 방법에 설명 합니다.|  
|[레거시 API를 사용하여 텍스트 레이어에 액세스](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|기존 API를 사용 하 여 텍스트의 다른 계층에 액세스 하는 방법에 설명 합니다.|  
|[레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)|기존 API를 사용 하 여 텍스트 마커를 추가 하는 방법에 설명 합니다.|  
|[레거시 API를 사용하여 편집기 컨트롤 및 메뉴 사용자 지정](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|기존 API를 사용 하 여 편집기 컨트롤을 사용자 지정 하는 방법에 설명 합니다.|  
|[레거시 API를 사용하여 실행 취소 및 다시 실행 관리](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|실행 취소를 관리 하 고 기존 API를 사용 하 여 다시 실행 하는 방법에 설명 합니다.|  
|[방법: 찾기 및 바꾸기 메커니즘 구현](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|기존 API를 사용 하 여 바꾸고 찾기를 관리 하는 방법에 설명 합니다.|  
|[방법: 파일 변경 알림 표시 안 함](../extensibility/how-to-suppress-file-change-notifications.md)|기존 API를 사용 하 여 파일 변경 알림 표시 안 함 하는 방법에 설명 합니다.|  
|[사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)|사용자 지정 편집기 및 디자이너를 만드는 방법에 설명 합니다.|  
|[레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)|사용자 지정 기능을 제공 하는 기능에 대 한 문서에 대 한 링크를 제공 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 언어 서비스에 대 한 지원을 추가 하 여 핵심 편집기입니다.|  
|[글꼴 및 색 사용](../extensibility/using-fonts-and-colors.md)|레거시 인터페이스를 사용 하 여 글꼴 및 색을 사용 하는 방법에 설명 합니다.|
