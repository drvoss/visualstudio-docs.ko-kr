---
title: 메뉴 항목에 바로 가기 키 바인딩 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9bfcf3a94a5615df892ab0ad88dca44c16e97b8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352178"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>메뉴 항목에 바로 가기 키 바인딩
바로 가기 키 사용자 지정 메뉴 명령을 바인딩할 항목을 방금 추가 된 *.vsct* 파일 패키지에 대 한 합니다. 이 항목에서는 바로 가기 키 사용자 지정 단추, 메뉴 항목 또는 도구 모음 명령에 매핑하는 방법 및 기본 편집기에서 키보드 매핑을 적용 하거나 사용자 지정 편집기를 제한 하는 방법을 설명 합니다.

 기존 Visual Studio 메뉴 항목에 바로 가기 키에 할당 하려면을 참조 하세요 [식별 하 고 바로 가기 키 사용자 지정](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)합니다.

## <a name="choose-a-key-combination"></a>키 조합을 선택합니다
 대부분의 키보드 바로 가기는 Visual Studio에서 이미 사용 됩니다. 할당 하지 말아야 하 동일한 바로 가기 둘 이상의 명령에 중복 바인딩이 감지 하기 어려운 고 예기치 않은 결과가 발생할 수 있습니다. 따라서 것 할당 하려면 해당 바로 가기의 가용성을 확인 하는 것이 좋습니다.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>바로 가기 키의 가용성을 확인 하려면

1. 에 **도구** > **옵션** > **환경** 창 **키보드**합니다.

2. 했는지 **에서 사용 하 여 새 바로 가기를** 로 설정 된 **전역**합니다.

3. 에 **바로 가기 키 누르기** 상자를 사용 하려는 바로 가기 키를 입력 합니다.

    Visual Studio에서 바로 가기 이미 사용 되는 경우는 **에서 현재 사용 하는 바로 가기** 상자 바로 가기 현재 호출 하는 명령에 표시 됩니다.

4. 매핑되지 않은 것을 찾을 때까지 다양 한 키 조합을 시도 합니다.

   > [!NOTE]
   > 바로 가기 키를 사용 하는 **Alt** 메뉴를 열고 하 고 직접 명령을 실행할 수 있습니다. 따라서 합니다 **에서 현재 사용 하는 바로 가기** 포함 하는 바로 가기를 입력 상자를 비워 둘 수 있습니다 **Alt**합니다. 바로 가기 열리지 메뉴 닫아 확인할 수 있습니다 합니다 **옵션** 대화 상자 및 키를 눌러 합니다.

   다음 절차는 메뉴 명령 사용 하 여 기존 VSPackage를 있다고 가정 합니다. 그렇게 도움이 필요한 경우 잠시 살펴 [메뉴 명령을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>명령에 바로 가기 키를 할당 하려면

1. 엽니다는 *.vsct* 파일 패키지에 대 한 합니다.

2. 빈 `<KeyBindings>` 섹션을 `<Commands>` 아직 제공 되지 경우.

   > [!WARNING]
   > 키 바인딩에 대 한 자세한 내용은 참조 하세요. [Keybinding](../extensibility/keybinding-element.md)합니다.

    에 `<KeyBindings>` 섹션에서 만들기를 `<KeyBinding>` 항목입니다.

    설정 합니다 `guid` 및 `id` 특성을 호출 하려는 명령입니다.

    설정 된 `mod1` 특성을 **제어**, **Alt**, 또는 **Shift**합니다.

    키 바인딩 섹션을 다음과 같이 표시 됩니다.

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   바로 가기 키는 두 개 이상의 키가 필요한 경우 설정 합니다 `mod2` 고 `key2` 특성입니다.

   대부분의 경우 **Shift** 해서는 안 두 번째 한정자 없이 이미를 눌러 하므로 대부분의 영숫자 키 대문자 또는 기호를 입력 합니다.

   가상 키 코드를 사용 하면 함수 키 예를 들어, 그와 관련 된 문자를 갖지 않는 특수 키에 액세스 하며 **백스페이스** 키입니다. 자세한 내용은 [가상 키 코드로](https://docs.microsoft.com/windows/desktop/inputdev/virtual-key-codes)입니다.

   명령을 사용할 수 있도록 Visual studio에서 편집기를 설정 합니다 `editor` 특성을 `guidVSStd97`입니다.

   명령에서 사용자 지정 편집기 에서만에서 사용할 수 있도록 설정 합니다 `editor` 의해 생성 된 사용자 지정 편집기의 이름으로 특성는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 는 VSPackage를 만들 때 패키지 템플릿은 사용자 지정 편집기를 포함 합니다. 이름 값을 찾으려면 확인 합니다 `<Symbols>` 에 대 한 섹션을 `<GuidSymbol>` 노드입니다 `name` 특성으로 끝나는 "`editorfactory`." 사용자 지정 편집기의 이름입니다.

## <a name="example"></a>예제
 이 예에서는 바로 가기 키를 바인딩합니다 **Ctrl**+**Alt**+**C** 명명 된 명령에 `cmdidMyCommand` 라는패키지`MyPackage`.

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>예제
 이 예에서는 바로 가기 키를 바인딩합니다 **Ctrl**+**B** 라는 명령 `cmdidBold` 라는 프로젝트 `TestEditor`합니다. 명령이입니다 다른 편집기 및 사용자 지정 편집기 에서만에서 사용할 수 있습니다.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>참고자료
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)