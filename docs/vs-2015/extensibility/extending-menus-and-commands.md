---
title: 메뉴 및 명령 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204529"
---
# <a name="extending-menus-and-commands"></a>메뉴 및 명령 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 작업 및 프로세스를 추가 하는 방법은 있습니다. 대부분의 명령 메뉴 또는 도구 모음에 표시 됩니다. VSPackage 프로젝트 템플릿은 기본적인 명령을 구현 하는 방법을 보여 줍니다. 약간 더 긴 하지만 여전히 기본적인 구현을 참조 하세요 [메뉴 명령을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.  
  
 Visual Studio 명령, 메뉴 및 도구 모음에 대 한 자세한 내용은 참조 하세요. [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)합니다.  
  
 명령, 메뉴 및 도구 모음 VSPackage 프로젝트의 일부인.vsct 파일에서 정의 됩니다. Visual Studio IDE 및.vsct 파일에 대 한 정보를 찾을 수 있습니다 [어떻게 Vspackage 추가 사용자 인터페이스 요소](../extensibility/internals/how-vspackages-add-user-interface-elements.md)합니다.  
  
 다음 항목에서는 여러 가지 명령, 메뉴 및 도구 모음을 추가 하는 방법을 설명 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 최상위 Visual Studio 메뉴 모음에 메뉴를 추가 하는 방법에 설명 합니다.  
  
 [메뉴 항목에 바로 가기 키 바인딩](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 바로 가기 키 (예: CTRL + 3) 메뉴 항목을 추가 하는 방법에 설명 합니다.  
  
 [메뉴에 하위 메뉴 추가](../extensibility/adding-a-submenu-to-a-menu.md)  
 위쪽 메뉴에 하위 메뉴를 추가 하는 방법에 설명 합니다.  
  
 [하위 메뉴에 가장 최근에 사용한 메뉴 목록 추가](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 가장 최근에 사용한 목록을 추가 하는 방법에 설명 합니다.  
  
 [다시 사용할 수 있는 단추 그룹 만들기](../extensibility/creating-reusable-groups-of-buttons.md)  
 여러 메뉴에 포함 될 수 있도록 명령 항목을 그룹화 하는 방법을 설명 합니다.  
  
 [메뉴 명령에 아이콘 추가](../extensibility/adding-icons-to-menu-commands.md)  
 아이콘의 도구 모음 및 메뉴 명령을 추가 하는 방법을 설명 합니다.  
  
 [메뉴 명령 텍스트 변경](../extensibility/changing-the-text-of-a-menu-command.md)  
 사용 방법을 설명 합니다 `TextChanges` 메뉴 항목을 동적으로 변경할 수 있도록 하는 플래그입니다.  
  
 [명령 모양 변경](../extensibility/changing-the-appearance-of-a-command.md)  
 동적으로 사용 하도록 설정 하거나 명령을 사용 하지 않도록 설정 하는 방법을 설명 합니다.  
  
 [사용자 인터페이스 업데이트](../extensibility/updating-the-user-interface.md)  
 최근 변경 내용을 반영 하는 사용자 인터페이스 업데이트를 적용 하는 방법에 설명 합니다.  
  
 [메뉴 명령 지역화](../extensibility/localizing-menu-commands.md)  
 메뉴 명령 지역화 하는 방법에 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원
