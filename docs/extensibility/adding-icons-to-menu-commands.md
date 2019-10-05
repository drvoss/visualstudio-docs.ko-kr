---
title: 메뉴 명령에 아이콘 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c54ee6b448e5830b478f10029a0d2d958e7699
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352370"
---
# <a name="add-icons-to-menu-commands"></a>메뉴 명령에 아이콘 추가
명령 메뉴와 도구 모음에서 나타날 수 있습니다. 도구 모음 명령 아이콘 및 텍스트 모두를 사용 하 여 일반적으로 나타납니다. 단순한 아이콘 (공간을 절약 하려면) 하는 동안 메뉴를 사용 하 여 표시할 명령에 대 한 일반적인 것입니다.

 아이콘은 16 x 16 픽셀 (높이) 및 8 비트 색 농도 (256 색) 또는 32 비트 색 농도 (true 색) 일 수 있습니다. 32 비트 컬러 아이콘 기본 설정 됩니다. 아이콘은 여러 비트맵 존재할 수 있지만 일반적으로 단일 비트맵의 가로 단일 행에 정렬 됩니다. 이 비트맵에 선언 되어는 *.vsct* 파일과 개별 아이콘 비트맵에서 사용할 수 있습니다. 에 대 한 참조를 [Bitmaps 요소](../extensibility/bitmaps-element.md) 대 한 자세한 내용은 합니다.

## <a name="add-an-icon-to-a-command"></a>명령에 아이콘 추가
 다음 절차는 메뉴 명령 사용 하 여 기존 VSPackage 프로젝트 있다고 가정 합니다. 이 작업을 수행 하는 방법을 알아보려면 참조 [메뉴 명령을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.

1. 32 비트 색 농도 사용 하 여 비트맵을 만듭니다. 아이콘은 항상 16 x 16 이므로이 비트맵에는 높은 16 픽셀 이어야 합니다 하 고 너비가 16 픽셀의 배수입니다.

     각 아이콘은 서로 옆에 있는 단일 행에 비트맵에 배치 됩니다. 알파 채널을 사용 하 여 각 아이콘의 transparency의 위치를 나타냅니다.

     8 비트 색 농도 사용 하는 경우 자홍을 사용 하 여 `RGB(255,0,255)`, 투명도로 합니다. 그러나 32 비트 컬러 아이콘은 기본 설정 됩니다.

2. 아이콘 파일을 복사 합니다 *리소스* VSPackage 프로젝트의 디렉터리입니다. 에 **솔루션 탐색기**, 프로젝트에 아이콘을 추가 합니다. (선택 **리소스**, 및 상황에 맞는 메뉴 클릭 **추가**, 다음 **기존 항목**, 아이콘 파일을 선택 하 고.)

3. 엽니다는 *.vsct* 파일을 편집기에서.

4. 추가 된 `GuidSymbol` 라는 이름의 요소 **testIcon**합니다. GUID를 만듭니다 (**도구** > **GUID 만들기**을 선택한 후 **레지스트리 형식** 클릭 **복사**)는 에붙여넣습니다`value` 특성입니다. 결과 다음과 같습니다.

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. 추가 `<IDSymbol>` 아이콘에 대 한 합니다. 합니다 `name` 특성은 아이콘의 ID 및 `value` 있으면의 스트립에서 위치를 나타냅니다. 하나의 아이콘의 경우 1을 추가 합니다. 결과 다음과 같습니다.

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. 만들기를 `<Bitmap>` 에 `<Bitmaps>` 부분을 *.vsct* 를 나타내는 아이콘이 포함 된 비트맵 파일.

    - 설정 된 `guid` 값의 이름으로는 `<GuidSymbol>` 이전 단계에서 만든 요소입니다.

    - 설정 된 `href` 비트맵 파일의 상대 경로 값 (이 예제의 **리소스\\< 아이콘 파일 이름\>** 합니다.

    - 설정 된 `usedList` 이전에 만든 IDSymbol 값입니다. 이 특성에는 VSPackage에 사용할 아이콘의 쉼표로 구분 된 목록을 지정 합니다. 목록에 없는 아이콘은 제외 된 폼 컴파일.

         비트맵 블록은 다음과 같이 표시 됩니다.

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. 기존 `<Button>` 요소를 설정 합니다 `Icon` 요소 이전에 만든 GUIDSymbol 및 IDSymbol 값입니다. 이 값을 가진 단추 요소의 예는 다음과 같습니다.

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. 아이콘을 테스트 합니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 명령을 찾습니다. 추가한 아이콘이 표시 됩니다.

## <a name="see-also"></a>참고자료
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [VSCT XML 스키마 참조](../extensibility/vsct-xml-schema-reference.md)