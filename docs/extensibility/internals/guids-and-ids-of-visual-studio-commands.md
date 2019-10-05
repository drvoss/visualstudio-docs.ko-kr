---
title: Visual Studio 명령의 Guid 및 Id | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89274600d05b787182ac447902555f7d703851c2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329181"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Guid 및 Id의 Visual Studio 명령
Visual Studio 통합된 개발 환경 (IDE)에 포함 된 명령의 GUID 및 ID 값은 Visual Studio SDK의 일부로 설치 되는.vsct 파일에서 정의 됩니다. 자세한 내용은 [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)합니다.

 에 정의 된 IDE 개체를 사용 하는 방법에 대 한 자세한 내용은 *.vsct* 파일을 참조 하십시오 [메뉴와 명령을 확장](../../extensibility/extending-menus-and-commands.md)합니다.

## <a name="find-a-command-definition"></a>명령 정의 찾기
 Visual Studio에서는 1,000 개 보다 많은 명령을 정의 하므로 여기서 모두 나열 하는 것이 불가능 합니다. 대신 명령 정의를 찾으려면 다음이 단계를 수행 합니다.

### <a name="to-locate-a-command-definition"></a>명령 정의 찾을 수

1. Visual Studio에서 다음 파일을 엽니다는 *< Visual Studio SDK 설치 경로\>\VisualStudioIntegration\Common\Inc\\*  폴더: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    대부분의 Visual Studio 명령에 정의 된 *SharedCmdDef.vsct* 하 고 *ShellCmdDef.vsct*합니다. *VsDbgCmdUsed.vsct* 디버거를 관련 된 명령 정의 하 고 *Venusmenu.vsct* 웹 개발에 관련 된 명령을 정의 합니다.

2. 명령 메뉴 항목을 이면 메뉴 항목의 정확한 텍스트를 note 합니다. 명령 모음의 단추 이면 note에서 멈출 때 표시 되는 도구 설명 텍스트입니다.

3. 키를 눌러 **Ctrl**+**F** 열려는 합니다 **찾기** 대화 상자.

4. 에 **찾을 내용** 상자에 2 단계에서 적어둔 텍스트를 입력 합니다.

5. 확인 **모든 열린 문서** 에 표시 되는 **찾는 위치** 상자입니다.

6. 클릭는 **다음 찾기** 텍스트에서 선택 될 때까지 단추를 `<Strings>` 섹션을 [단추 요소](../../extensibility/button-element.md).

    `<Button>` 명령에 표시 되는 요소는 명령을 정의 합니다.

   명령 정의 발견 하면에 넣을 수 명령의 복사본이 다른 메뉴 또는 도구 모음을 만들어를 [CommandPlacement 요소](../../extensibility/commandplacement-element.md) 는 동일 `guid` 고 `id` 명령으로 값입니다. 자세한 내용은 [단추의 다시 사용할 수 있는 그룹을 만들](../../extensibility/creating-reusable-groups-of-buttons.md)합니다.

### <a name="special-cases"></a>특별 한 경우
 다음 경우에 메뉴 텍스트 또는 도구 설명 텍스트를 다 명령 정의에 포함 된 내용입니다.

- 같은 밑줄이 그어진 문자를 포함 하는 메뉴 항목의 **인쇄** 명령을 **파일** 나타나는 메뉴에서를 *P* 밑줄이 표시 됩니다.

     앰퍼샌드 뒤에 나오는 문자 (&) 문자 메뉴 항목 이름에 표시 되는 밑줄이 있습니다. 그러나 *.vsct* 파일은 xml에서는 앰퍼샌드 (&) 문자를 사용 하 여 특수 문자를 표시 하 고 표시할 앰퍼샌드로 철자가 같아야는 필요한  *&amp;amp;* 합니다. 따라서를 *.vsct* 파일을 **인쇄** 명령으로 표시 됩니다  *&amp;a m p; 인쇄*합니다.

- 명령와 같은 동적 텍스트입니다 **저장** \<현재 파일 이름을\>, 및 동적 메뉴 항목, 항목 등에서 생성 합니다 **최근에 사용한 파일** 목록.

     동적 텍스트를 검색할 신뢰할 수 있는 방법은 없습니다. 대신 참조 하 여 원하는 명령을 호스트 하는 그룹을 찾을 [Guid 및 Id의 Visual Studio 메뉴](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 하거나 [Guid 및 Id의 Visual Studio 도구 모음](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), 해당 그룹의 ID 검색 합니다. 명령 정의와 그룹에 없으면 해당 [부모 요소](../../extensibility/parent-element.md)를 검색 *SharedCmdPlace.vsct* 하 고 *ShellCmdPlace.vsct* (또는  *VsDbgCmdPlace.vsct* 디버거 명령에 대 한)에 대 한는 `<CommandPlacement>` 명령의 부모를 설정 하는 요소입니다. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, 및 *VsDbgCmdPlace.vsct* 에 *\<Visual Studio SDK 설치 경로\>\ VisualStudioIntegration\Common\Inc\\* 폴더입니다.

## <a name="see-also"></a>참고자료
- [Menucommand 및 OleMenuCommand](../../extensibility/menucommands-vs-olemenucommands.md)
- [Visual Studio 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
