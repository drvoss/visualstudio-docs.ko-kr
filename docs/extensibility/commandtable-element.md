---
title: CommandTable 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bb10232c725eb2f538df73f6a7ca98e534a4c14
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341814"
---
# <a name="commandtable-element"></a>CommandTable 요소
CommandTable는의 루트 요소는 *.vsct* 파일입니다. VSPackage는 IDE를 제공 하는 명령의 형식과 실제 레이아웃을 정의 하는 파일입니다. 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자에 명령이 포함할 수 있습니다. 자세한 내용은 [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)합니다.

## <a name="syntax"></a>구문

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

| 특성 | 설명 |
|-----------| - |
| xmlns | 필수 요소. XML 네임 스페이스:<br /><br /> xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| language | 선택 사항입니다. Language 특성 모두의 기본 언어를 지정 하려면 사용할 수 \<문자열 > 명령 테이블에 있는 요소입니다.  언어를 지정 하지 않으면 현재 프로세스의 언어가 사용 됩니다.<br /><br /> language="en-us" |

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Extern 요소](../extensibility/extern-element.md)|선택 사항입니다. 컴파일러에 대 한 전처리기 지시문을 포함합니다.|
|[요소를 포함 합니다.](../extensibility/include-element.md)|선택 사항입니다. 컴파일에 포함할 파일 경로 포함 합니다.|
|[요소를 정의 합니다.](../extensibility/define-element.md)|선택 사항입니다. 지정 된 이름과 값을 기호를 정의 합니다.|
|[Commands 요소](../extensibility/commands-element.md)|선택 사항입니다. 모든 다른 요소를 포함 하는 VSPackage에 대 한 모든 명령을 정의 하는 부모 요소입니다.|
|[CommandPlacements 요소](../extensibility/commandplacements-element.md)|선택 사항입니다. 명령 모음에서 명령이 있는 배치를 정의 합니다.|
|[VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)|선택 사항입니다. 도구 모음 및 명령 정적 표시 여부를 결정 합니다.|
|[KeyBindings 요소](../extensibility/keybindings-element.md)|선택 사항입니다. 명령에 대 한 바로 가기 키 조합을 지정 합니다.|
|[UsedCommands 요소](../extensibility/usedcommands-element.md)|선택 사항입니다. 필요에 따라 다른 Vspackage에서 원래 지원 되는 기능의 자체 버전을 구현 하기 위해 VSPackage를 허용 합니다.|
|[Symbols 요소](https://www.microsoft.com/download/details.aspx?id=55984)|선택 사항입니다. 컴파일러에 대 한-Guid, Id 등-모든 기호 데이터를 포함합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|없음||

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)