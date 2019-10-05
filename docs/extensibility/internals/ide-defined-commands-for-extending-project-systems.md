---
title: 프로젝트 시스템 확장을 위한 IDE 정의 명령 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49a79a46fdcc6c969a489efb12eefb6bbc674126
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311885"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>프로젝트 시스템 확장을 위한 IDE 정의 명령
프로젝트 시스템을 확장 하려는 경우 명령을 사용 하 여 하 고 명령에서 제공 하는 그룹 수는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 다음 섹션에서는 프로젝트 시스템 확장에 특히 유용한 명령 항목을 나열 합니다.

## <a name="command-menus"></a>명령 메뉴
 다음 표에서 유용한 위치 프로젝트 extender를 호출 하는 고급 명령을 추가 하는 명령 메뉴를 보여 줍니다.

|명령 메뉴|설명|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|합니다 **프로젝트** 최상위 메뉴.|
|IDM_VS_TOOL_PROJWIN|합니다 **솔루션 탐색기** 도구 모음입니다.|

## <a name="shortcut-menus"></a>바로 가기 메뉴
 다음 표에서 단일 노드가 선택 되었을 때 적용 되는 바로 가기 메뉴를 보여 줍니다.는 **솔루션 탐색기**, 때나의 여러 형식이 같은 멤버를 선택 합니다 **솔루션 탐색기**, 하는 경우 선택한 모든 노드는 동일한 형식입니다.

|바로 가기 메뉴|설명|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|프로젝트 노드를 선택한 경우에 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|파일을 선택 하는 경우 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|폴더를 선택 하는 경우 적용 됩니다.|
|IDM_VS_CTXT_WEBREFFOLDER|웹 참조 폴더가 선택 된 경우 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"참조"를 호출 하는 참조 루트 노드를 선택한 경우에 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|참조 노드를 선택 합니다; 적용 됩니다. 여기에 어셈블리, COM 및 프로젝트 참조만 포함 됩니다. 웹 참조를 포함 하지 않습니다.|

 다음 표에서 경우 적용 되는 바로 가기 메뉴에서 선택 합니다 **솔루션 탐색기** 여러 계층에 걸쳐

|바로 가기 메뉴|설명|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|현재 선택 영역에 솔루션 노드 및 루트 프로젝트 노드를 포함 하는 경우 적용 됩니다.|
|IDM_VS_CTXT_XPROJ_SLNITEM|현재 선택 영역에 솔루션 노드 및 프로젝트 항목을 포함 하는 경우 적용 됩니다.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|현재 선택 영역 루트 노드가 여러 개 프로젝트만 구성 되어 있을 때 적용 됩니다.|
|IDM_VS_CTXT_XPROJ_PROJITEM|현재 선택 영역 루트 프로젝트 노드와 프로젝트 항목의 조합을 포함 하는 경우 적용 됩니다. 또한 선택한 솔루션 노드를 포함할 수 있습니다.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|현재 선택 영역에 솔루션의 여러 프로젝트에서 프로젝트 항목을 포함 하는 경우 또는 동일한 프로젝트에서 다른 형식의 항목을 선택할 때 적용 됩니다.|

## <a name="command-groups"></a>명령 그룹
 다음 표에서 프로젝트를 확장 하 고를 통해 액세스할 수 있는 경우 사용할 수 있는 명령 그룹을 보여 줍니다.는 <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> 바로 가기 메뉴.

|명령 그룹|설명|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|빌드, 다시 작성 및 배포 프로젝트에 대 한 명령입니다.|
|IDG_VS_CTXT_COMPILELINK|컴파일 및 연결 프로젝트에 대 한 명령입니다.|
|IDG_VS_CTXT_PROJECT_CONFIG|프로젝트 구성을 설정 하 고 빌드 순서는 명령입니다.|
|IDG_VS_CTXT_PROJECT_ADD|프로젝트에 항목을 추가 하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_START|F5 키를 사용 하 여 연결 된 시작 프로젝트를 설정 하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_SAVE|프로젝트 항목을 저장 하기 위한 명령입니다.|
|IDG_VS_CTXT_PROJECT_DEBUG|디버깅에 대 한 명령입니다.|
|IDG_VS_CTXT_PROJECT_SCC|소스 제어에 대 한 명령입니다.|
|IDG_VS_CTXT_PROJECT_TRANSFER|명령은 잘라내기, 복사 및 붙여넣기 작업입니다.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|에 대 한 액세스를 제공 하는 명령 합니다 **프로젝트 속성** 대화 상자.|

## <a name="see-also"></a>참고 항목
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [MenuCommand 및 OleMenuCommand](../../extensibility/menucommands-vs-olemenucommands.md)
- [다시 사용할 수 있는 단추 그룹 만들기](../../extensibility/creating-reusable-groups-of-buttons.md)