---
title: Guid 및 명령 Id | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2feef3cbe72b7eb8db96052236fe483733e22273
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538140"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio 명령의 GUID 및 ID
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 통합된 개발 환경 (IDE)에 포함 된 명령의 GUID 및 ID 값은 Visual Studio SDK의 일부로 설치 되는.vsct 파일에서 정의 됩니다. 자세한 내용은 [IDE-Defined 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)합니다.

 .Vsct 파일에 정의 된 IDE 개체를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 메뉴 및 명령을](../../extensibility/extending-menus-and-commands.md)합니다.

## <a name="finding-a-command-definition"></a>명령 정의 찾기
 Visual Studio에서는 명령 하나 천 개를 정의 하므로 여기서 모두 나열 하는 것이 불가능 합니다. 대신 명령 정의를 찾으려면 다음이 단계를 수행 합니다.

#### <a name="to-locate-a-command-definition"></a>명령 정의 찾을 수

1. Visual Studio에서 다음 파일을 엽니다는 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Common\Inc\ 폴더: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.

    대부분의 Visual Studio 명령 SharedCmdDef.vsct ShellCmdDef.vsct에 정의 됩니다. VsDbgCmdUsed.vsct 디버거를 관련 된 명령 정의 및 Venusmenu.vsct 웹 개발에 관련 된 명령을 정의 합니다.

2. 명령 메뉴 항목을 이면 메뉴 항목의 정확한 텍스트를 note 합니다. 명령 모음의 단추 이면 note에서 멈출 때 표시 되는 도구 설명 텍스트입니다.

3. CTRL + F를 눌러 엽니다는 **찾을** 대화 상자.

4. 에 **찾을 내용** 상자에 2 단계에서 적어둔 텍스트를 입력 합니다.

5. 확인 **모든 열린 문서** 에 표시 되는 **찾는 위치** 상자입니다.

6. 클릭는 **다음 찾기** 단추에 텍스트를 선택할 때까지 `<Strings>` 부분을 [Button 요소](../../extensibility/button-element.md).

    `<Button>` 명령에 표시 되는 요소는 명령을 정의 합니다.

   명령 정의 발견 하면에 넣을 수 명령의 복사본이 다른 메뉴 또는 도구 모음을 만들어를 [CommandPlacement 요소](../../extensibility/commandplacement-element.md) 는 동일 `guid` 고 `id` 명령으로 값입니다. 자세한 내용은 [단추가의 다시 사용할 수 있는 그룹 만들기](../../extensibility/creating-reusable-groups-of-buttons.md)합니다.

### <a name="special-cases"></a>특별 한 경우
 다음 경우에 메뉴 텍스트 또는 도구 설명 텍스트를 다 명령 정의에 포함 된 내용입니다.

- 같은 밑줄이 그어진 문자를 포함 하는 메뉴 항목의 **인쇄** 명령을 **파일** 메뉴, P 밑줄이 표시 됩니다.

     메뉴 항목 이름에 '&' 문자 뒤에 나오는 문자는 표시는 밑줄이 있습니다. .Vsct 파일 특수 문자를 나타내기 위해 '&' 문자를 사용 하며 철자 표시 되는 앰퍼샌드를 입력 해야 하는 XML로 작성 됩니다 있지만 '&amp;'. 따라서.vsct 파일에에서는 **인쇄** 명령으로 표시 됩니다. '&amp;인쇄 '.

- 명령와 같은 동적 텍스트입니다 **저장** *현재 파일 이름을*, 및 동적 메뉴 항목, 항목 등에서 생성 합니다 **최근에 사용한 파일** 목록.

     동적 텍스트를 검색할 신뢰할 수 있는 방법은 없습니다. 대신 참조 하 여 원하는 명령을 호스트 하는 그룹을 찾을 [Guid 및 Visual Studio 메뉴의 Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 하거나 [Guid 및 Id의 Visual Studio 도구 모음](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), 해당 그룹의 ID 검색 합니다. 명령 정의와 그룹에 없으면 해당 [부모 요소](../../extensibility/parent-element.md), SharedCmdPlace.vsct 및 ShellCmdPlace.vsct (또는 디버거 명령에 대 한 VsDbgCmdPlace.vsct)에 대 한 검색을 `<CommandPlacement>` 의 부모를 설정 하는 요소는 명령입니다. SharedCmdPlace.vsct, ShellCmdPlace.vsct, andVsDbgCmdPlace.vsct에는 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Common\Inc\ 폴더입니다.

## <a name="see-also"></a>참고 항목
 [MenuCommand 및 OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
