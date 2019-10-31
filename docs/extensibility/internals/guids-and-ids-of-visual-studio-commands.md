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
ms.openlocfilehash: f7670eacc875bf7c5437d9bb92cc1932753093bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186646"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio 명령의 Guid 및 Id
Visual Studio IDE (통합 개발 환경)에 포함 된 명령의 GUID 및 ID 값은 Visual Studio SDK의 일부로 설치 되는 vsct 파일에 정의 되어 있습니다. 자세한 내용은 [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)을 참조 하세요.

 *. Vsct* 파일에 정의 된 IDE 개체를 사용 하는 방법에 대 한 자세한 내용은 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)을 참조 하세요.

## <a name="find-a-command-definition"></a>명령 정의 찾기
 Visual Studio는 1000 개 이상의 명령을 정의 하므로 여기에 모두 나열 하는 것은 실용적이 지 않습니다. 대신 다음 단계에 따라 명령의 정의를 찾습니다.

### <a name="to-locate-a-command-definition"></a>명령 정의를 찾으려면

1. Visual Studio에서 *Visual STUDIO SDK 설치 경로 <\>\VisualStudioIntegration\Common\Inc\\* 폴더에서 다음 파일을 엽니다. *sharedcmddef.* vsct, *shellcmddef*, *VsDbgCmdUsed*, *Venusmenu*.

    대부분의 Visual Studio 명령은 *Sharedcmddef. vsct* 및 *shellcmddef vsct*에 정의 되어 있습니다. *VsDbgCmdUsed* 는 디버거와 관련 된 명령을 정의 하 고 *Venusmenu* 은 웹 개발과 관련 된 명령을 정의 합니다.

2. 명령이 메뉴 항목인 경우 메뉴 항목의 정확한 텍스트를 확인 합니다. 명령이 도구 모음의 단추인 경우 일시 중지할 때 표시 되는 도구 설명 텍스트를 확인 합니다.

3. **Ctrl**+**F** 를 눌러 **찾기** 대화 상자를 엽니다.

4. **찾을 내용** 상자에 2 단계에서 기록한 텍스트를 입력 합니다.

5. 열려 있는 **모든 문서가** **찾는 위치** 상자에 표시 되는지 확인 합니다.

6. [단추 요소의](../../extensibility/button-element.md)`<Strings>` 섹션에서 텍스트를 선택할 때까지 **다음 찾기** 단추를 클릭 합니다.

    명령이 표시 되는 `<Button>` 요소는 명령 정의입니다.

   명령 정의를 찾았으면 명령과 `guid` 및 `id` 값이 동일한 [Commandplacement 요소](../../extensibility/commandplacement-element.md) 를 만들어 다른 메뉴 또는 도구 모음에 명령 복사본을 넣을 수 있습니다. 자세한 내용은 [다시 사용할 수 있는 단추 그룹 만들기](../../extensibility/creating-reusable-groups-of-buttons.md)를 참조 하세요.

### <a name="special-cases"></a>특수 한 경우
 다음 경우에는 메뉴 텍스트 또는 도구 설명 텍스트가 명령 정의에 있는 것과 정확 하 게 일치 하지 않을 수 있습니다.

- **파일** 메뉴의 **인쇄** 명령과 같이 밑줄 친 문자가 포함 된 메뉴 항목입니다. 여기에는 *P* 에 밑줄이 그어집니다.

     메뉴 항목 이름에 앰퍼샌드 (&) 문자가 앞에 오는 문자는 밑줄로 표시 됩니다. 그러나 *. vsct* 파일은 앰퍼샌드 (&) 문자를 사용 하 여 특수 문자를 나타내는 XML로 작성 되며, 표시 되는 앰퍼샌드를 *&amp;amp;* 로 입력 해야 합니다. 따라서 *vsct* 파일에서 **인쇄** 명령은&amp;amp로 표시 됩니다 *. 인쇄*.

- **저장** \<현재 파일 이름\>및 동적으로 생성 된 메뉴 항목 (예: **최근 파일** 목록의 항목)과 같은 동적 텍스트가 있는 명령입니다.

     동적 텍스트를 검색 하는 신뢰할 수 있는 방법은 없습니다. 대신 [Visual studio 메뉴의 guid 및 id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 를 확인 하 고 [visual Studio 도구 모음의 guid 및](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)id를 조회 하 여 원하는 명령을 호스트 하는 그룹을 찾은 다음 해당 그룹의 id를 검색 합니다. 명령 정의에 해당 그룹이 [부모 요소인](../../extensibility/parent-element.md)경우의 부모를 설정 하는 `<CommandPlacement>` 요소에 대해 *sharedcmdplace.* Vsct 및 *shellcmdplace* 을 검색 합니다. 명령. *Sharedcmdplace. vsct*, *Shellcmdplace*및 는 *\<Visual Studio SDK 설치 경로\>\VisualStudioIntegration\Common\Inc\\* 폴더에 있습니다.

## <a name="see-also"></a>참조

- [Visual Studio 명령 테이블 (.vvsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
