---
title: 상황에 맞는 메뉴 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184270"
---
# <a name="context-menus"></a>상황에 맞는 메뉴
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

상황에 맞는 메뉴 클라이언트 영역의 활성 지역에서 단추로 클릭할 때 표시 되 고 마우스 오른쪽 단추를 놓을 때의 선택을 취소 합니다.  
  
## <a name="editor-context-menus"></a>편집기 상황에 맞는 메뉴  
 가로채서 `ECMD_SHOWCONTEXTMENU`, 언어 서비스 편집기에 표시 되는 상황에 맞는 메뉴를 제어할 수 있습니다. 위치에 전달 될 때 고유한 상황에 맞는 메뉴를 표시 하려면이 명령을 처리 하 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>입니다. 이 명령은 처리 하면 IDE 편집기에 대해 제공 된 표준 상황에 맞는 메뉴를 표시 합니다. 또한 표식 당 기준 상황에 맞는 메뉴의 콘텐츠를 제어할 수 있습니다. 이 대 한 자세한 내용은 참조 하세요. [레거시 API를 사용 하 여 텍스트 마커를 사용 하 여](../extensibility/using-text-markers-with-the-legacy-api.md) 하 고 [레거시 언어 서비스 명령 가로채기](../extensibility/internals/intercepting-legacy-language-service-commands.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)   
 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
