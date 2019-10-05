---
title: XML 명령 테이블 디자인 (합니다. Vsct) 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc088ac5c534e77de2aae919019396ccf2c344e2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312108"
---
# <a name="design-xml-command-table-vsct-files"></a>XML 명령 테이블 (.vsct) 파일 디자인
XML 명령 테이블 ( *.vsct*) 파일에는 레이아웃 및 VSPackage에 대 한 명령 항목의 모양을 설명 합니다. 명령 항목 단추, 콤보 상자, 메뉴, 도구 모음 및 명령 항목 그룹에 포함 됩니다. 이 문서에서는 XML 명령 테이블 파일, 메뉴 및 명령 항목에 미치는 및 만드는 방법을 설명 합니다.

## <a name="commands-menus-groups-and-the-vsct-file"></a>명령, 메뉴, 그룹 및.vsct 파일
 합니다 *.vsct* 파일 명령, 메뉴 및 명령 그룹을 구성 합니다. XML 태그를 *.vsct* 나타내는 명령 단추, 명령 배치 및 비트맵과 같은 연결 된 다른 항목과 함께 이러한 각 항목 파일입니다.

 실행 하 여 새 VSPackage를 만들 때 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 패키지 템플릿은 템플릿 생성을 *.vsct* 메뉴 명령, 도구 창 또는 선택 항목에 따라 사용자 지정 편집기에 대 한 필요한 요소를 사용 하 여 파일입니다. 이렇게 *.vsct* 파일 특정 VSPackage의 요구 사항에 맞게 수정할 수 있습니다. 수정 하는 방법에 대 한 예제는 *.vsct* 파일을 참조 하세요 [메뉴와 명령을 확장](../../extensibility/extending-menus-and-commands.md)합니다.

 새를 만들려면 비어 *.vsct* 파일 내용은 [방법: 만들기는 *.vsct* 파일](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)합니다. 만들어지면 명령 항목 레이아웃을 설명 하는 파일에 XML 요소, 특성 및 값 추가 합니다. XML 스키마를 자세한 참조를 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)합니다.

## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 및.vsct 파일 간의 차이점
 XML의 의미를 태그 하는 동안를 *.vsct* 파일은 이제 사용 되지 않는 이러한 태그 동일 *.ctc* 파일 형식으로 구현과 약간 다릅니다.:

- 새  **\<extern >** 태그는 다른 참조 *.h* 에 대 한 파일과 같은 컴파일할 파일의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 도구 모음입니다.

- 하는 동안 *.vsct* 파일 지원 합니다 **포함 /** 문을으로 *.ctc* 도 새 기능을 수행 하는 파일  **\<가져올 >** 요소입니다. 차이점은 **/include** 제공 *모든* 정보의 하는 동안  **\<가져오기 >** 이름만에서 제공 합니다.

- 하는 동안 *.ctc* 파일에 전처리기 지시문을 정의 하는 헤더 파일이 필요, 필요 하지 않습니다 *.vsct* 파일입니다. 대신에 지시문에 있는 기호 테이블에 배치 합니다  **\<기호 >** 맨 아래에 있는 요소를 *.vsct* 파일입니다.

- *.vsct* 파일 기능을  **\<주석 >** 태그 정보 등도 사진 같은 모든 정보를 포함할 수 있습니다.

- 값은 항목에는 특성으로 저장 됩니다.

- 명령 플래그를 개별적으로 저장 하거나 누적 될 수 있습니다.  그러나 IntelliSense,에서 작동 하지 않습니다 누적된 명령 플래그입니다. 명령 플래그에 대 한 자세한 내용은 참조는 [CommandFlag 요소](../../extensibility/command-flag-element.md)합니다.

- 분할 드롭다운, combos 등과 같은 여러 형식을 지정할 수 있습니다.

- Guid의 유효성을 검사 하지 않습니다.

- 각 UI 요소에 함께 표시 되는 텍스트를 나타내는 문자열입니다.

- 부모 선택 사항입니다. 생략 하면 값 *알 수 없는 그룹* 사용 됩니다.

- 합니다 *아이콘* 인수는 선택 사항입니다.

- 섹션을 비트맵입니다. 이 섹션은 동일를 *.ctc* 파일을 제외 하 여에서 가져온 Href 통해 파일 이름을 지정할 수 있습니다 합니다 *vsct.exe* 컴파일 타임에 컴파일러.

- ResID: 이전 리소스 ID 수와 여전히 작동 동일 비트맵 *.ctc* 파일입니다.

- HRef: 비트맵 리소스의 파일 이름을 지정할 수 있습니다 하는 새 메서드. 사용 하는 섹션을 생략할 수는 모두를 사용 하는 가정 합니다. 정의 된 모든 리소스 및 파일에 대 한 다음 모든 네트워크 공유에서 로컬 리소스에 대 한 컴파일러는 먼저 검색 하는 **/I** 전환 합니다.

- 키 바인딩: 더 이상 에뮬레이터를 지정 해야 합니다. 하나를 지정 않을 경우 컴파일러는 편집기 및 에뮬레이터 동일 합니다.

- Keychord: Keychord 삭제 되었습니다. 새 형식이 *Mod1, Key1, Key2, Mod2*합니다.  문자, 16 진수 또는 VK 상수를 지정할 수 있습니다.

새 컴파일러 *vsct.exe*를 둘 다 컴파일합니다 *.ctc* 하 고 *.vsct* 파일. 그러나 이전 *ctc.exe* 컴파일러, 인식 하지 못하거나 컴파일 *.vsct* 파일입니다.

사용할 수는 *vsct.exe* 기존 변환할 컴파일러 *.cto* 파일을 *.vsct* 파일입니다. 자세한 내용은 [방법: 기존.cto 파일에서.vsct 파일 만들기](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)합니다.

## <a name="the-vsct-file-elements"></a>.Vsct 파일 요소
 명령 테이블에는 다음 계층 구조 및 요소에 있습니다.

- [CommandTable 요소](../../extensibility/commandtable-element.md): 모든 명령, 메뉴 그룹 및 VSPackage와 사용 하 여 연결 된 메뉴를 나타냅니다.

- [Extern 요소](../../extensibility/extern-element.md): 사용 하 여 병합할 모든 외부.h 파일 참조를 *.vsct* 파일입니다.

- [요소를 포함](../../extensibility/include-element.md): 와 함께 컴파일할 하려는 모든 추가 헤더 (.h) 파일을 참조 하 *.vsct* 파일입니다. A *.vsct* 파일이 포함 될 수 있습니다 *.h* 명령, 메뉴 그룹 및 메뉴 IDE 또는 다른 VSPackage에서 제공 하는 정의 하는 상수를 포함 하는 파일입니다.

- [Commands 요소](../../extensibility/commands-element.md): 모든 실행 될 수 있는 개별 명령을 나타냅니다. 각 명령에는 다음 4 명의 자식 요소가 있습니다.

- [Menus 요소](../../extensibility/menus-element.md): 모든 메뉴 및 VSPackage에서 도구 모음을 나타냅니다. 메뉴는 명령 그룹에 대 한 컨테이너입니다.

- [Groups 요소](../../extensibility/groups-element.md): 모든 VSPackage에서 그룹을 나타냅니다. 그룹은 개별 명령 컬렉션입니다.

- [Buttons 요소](../../extensibility/buttons-element.md): 모든 명령 단추 및 VSPackage에서 메뉴 항목을 나타냅니다. 단추는 명령과 사용 하 여 연결할 수 있는 시각적 컨트롤입니다.

- [Bitmaps 요소](../../extensibility/bitmaps-element.md): 모든 VSPackage에서 단추에 대 한 비트맵의 모든 나타냅니다. 비트맵은 컨텍스트에 따라 명령 단추, 또는 옆에 표시 되는 그림입니다.

- [CommandPlacements 요소](../../extensibility/commandplacements-element.md): VSPackage의 메뉴에 개별 명령 해야 위치할 추가 위치를 나타냅니다.

- [VisibilityConstraints 요소](../../extensibility/visibilityconstraints-element.md): 시간에 또는 특정 대화 상자 또는 창 표시 될 때와 같은 특정 컨텍스트에서 명령을 전혀 표시 여부를 지정 합니다. 메뉴와이 요소의 값이 있는 명령에 지정된 된 컨텍스트 활성 상태일 때에 표시 됩니다. 기본 동작은 모든 시간에 명령이 표시 됩니다.

- [KeyBindings 요소](../../extensibility/keybindings-element.md): 명령에 대 한 키 바인딩을 지정합니다. 즉, 하나 이상의 키 조합와 같은 명령을 실행 하려면 눌러야 하는 **Ctrl**+**S**입니다.

- [UsedCommands 요소](../../extensibility/usedcommands-element.md): 알립니다는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 현재 VSPackage를 활성화할 때 지정된 된 명령을 다른 코드에 의해 구현 되는 있지만 제공 명령을 구현 하는 환경입니다.

- [Symbols 요소](../../extensibility/symbols-element.md): 기호 이름 및 패키지에 명령의 모든 GUID Id를 포함 합니다.

## <a name="vsct-file-design-guidelines"></a>.vsct 파일 디자인 지침
 성공적으로 디자인 하는 *.vsct* 파일에서 이러한 지침을 따릅니다.

- 명령을 그룹에만 배치할 수 있습니다, 그룹 메뉴에만 배치할 수 있습니다 및 메뉴 그룹에만 배치할 수 있습니다. 메뉴만 그룹 IDE에 실제로 표시 되 고 명령을 가져오지 않습니다.

- 하위 메뉴에 직접 할당할 수 없습니다 있지만 메뉴에 다시 할당 된 그룹에 할당 되어야 합니다.

- 하나의 부모/자식 관리 그룹 또는 해당 정의 지시문의 부모 필드를 사용 하 여 메뉴 명령, 하위 메뉴 및 그룹을 할당할 수 있습니다.

- 지시문의 부모 필드를 통해서만 명령 테이블을 구성 하는 것은 중요 한 제한이 있습니다. 개체를 정의 하는 지시문은 하나의 부모만 인수를 사용할 수 있습니다.

- 고유한 개체의 새 인스턴스를 만들려면 새 지시문을 사용 해야 명령, 그룹 또는 하위 메뉴를 다시 사용 `GUID:ID` 쌍입니다.

- 각 `GUID:ID` 쌍은 고유 해야 합니다. 에 의해 처리 됩니다, 예를 들어, 배치 된 상황에 맞는 메뉴 또는 도구 모음, 메뉴 명령을 다시 사용 된 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스입니다.

- 명령 및 하위 메뉴도 여러 그룹에 할당할 수 있으며 그룹을 사용 하 여 여러 메뉴에서 할당할 수는 [Commands 요소](../../extensibility/commands-element.md)합니다.

## <a name="vsct-file-notes"></a>.vsct 파일 정보
 변경한 경우는 *.vsct* 파일 컴파일와 네이티브 위성 DLL에에서 배치, 후 실행 해야 **devenv.exe /setup /nosetupvstemplates**합니다. 따라서 강제로 다시 읽어야 실험적 레지스트리 및 설명 하는 내부 데이터베이스에서 지정 하는 VSPackage 리소스 수행 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다시 작성 됩니다.

 개발 하는 동안 여러 VSPackage 프로젝트를 만들고 IDE의 혼동 혼란을 일으킬 수 있는 실험적 레지스트리 하이브에 등록에 대 한 가능성이 있습니다. 이 해결 하려면 실험적 하이브에 등록 된 모든 Vspackage 및 해당 IDE에 수행한 변경 내용을 제거 하려면 기본 설정으로 재설정할 수 있습니다. 실험 하이브를 재설정 하려면 Visual Studio SDK를 사용 하 여 제공 되는 CreateExpInstance.exe 도구를 사용 합니다. 찾을 수 있습니다.

 *%PROGRAMFILES(x86)%\Visual Studio\\\<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 명령을 사용 하 여 도구를 실행할 **CreateExpInstance /Reset**합니다. 이 도구를 제거 함을 실험적 하이브에서 일반적으로 사용 하 여 설치 된 모든 등록 된 Vspackage를 기억 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

## <a name="see-also"></a>참고자료
- [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)