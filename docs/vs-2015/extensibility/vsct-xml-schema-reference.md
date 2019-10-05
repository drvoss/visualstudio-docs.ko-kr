---
title: VSCT XML 스키마 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e56de828d3b357762da98cde3b9591033c6b5d19
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441472"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 스키마 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

각 요소 및 특성 명령 테이블 컴파일러 스키마 요소의 표 허용 되는 자식을 사용 하 여 제공합니다.  
  
 XML 기반 명령 테이블 (.vsct) 구성 파일을 통합된 개발 환경 (IDE)에 VSPackage가 제공 하는 명령 요소를 정의 합니다. 이러한 요소에는 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자 포함 됩니다.  
  
> [!NOTE]
> VSCT 컴파일러인.vsct 파일에서 전처리기를 실행할 수 있습니다. 일반적으로이 C++ 전처리기를 정의할 수 있습니다 포함에 사용 되는 동일한 구문을 사용 해야 하는 매크로 C++ 파일입니다. 이 예가.vsct에서 제공 됩니다 파일을 **새 프로젝트** VSPackage 프로젝트에 대해 만들어집니다.  
  
## <a name="optional-elements"></a>선택적 요소  
 일부 VSCT 요소는 선택 사항입니다. 경우는 `Parent` 인수를 지정 하지 않으면 Group_Undefined:0 암시 됩니다. 경우는 `Icon` 인수를 지정 하지 않으면 guidOfficeIcon:msotcidNoIcon 암시 됩니다. 바로 가기 키를 정의할 때 일반적으로 사용 되지 않는 에뮬레이션, 선택 사항입니다.  
  
 비트맵 항목의 비트맵 스트립에서 위치를 지정 하 여 컴파일 시간에 포함 될 수는 `href` 인수입니다. 비트맵 스트립 DLL의 리소스에서 추출 되지 않고 병합 중에 복사 됩니다. 경우는 `href` 인수를 제공 합니다 `usedList` 인수 선택적 되며 모든 슬롯 비트맵 스트립에서 사용 되는 것으로 간주 됩니다.  
  
 모든 GUID 및 ID 값을 기호화 된 이름을 사용 하 여 정의 되어야 합니다. 이러한 이름은 VSCT 또는 헤더 파일에서 정의할 수 있습니다 \<기호 > 섹션입니다. 기호화 된 이름을 로컬 이어야를 통해 포함 \<Include > 요소에서 참조 또는 \<Extern > 요소입니다. 기호화 된 이름에 지정 된 헤더 파일에서 가져온는 \<Extern > 요소의 단순 패턴을 따릅니다.이 경우 #define 기호 값입니다. 값으로 해당 기호 이전에 정의 된 다른 기호를 수 있습니다. GUID 정의 하거나 OLE 따라야 합니다. 또는 C++ 형식입니다. ID 값은 다음 줄에 표시 된 대로 10 진수 또는 16 진수 0 x 뒤에 나오는 수 있습니다.  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }  
  
  XML 주석을 사용할 수 있지만 라운드트립 그래픽 사용자 인터페이스 (GUI) 도구를 삭제 될 수 있습니다. 내용을 \<주석 > 요소 형식에 관계 없이 유지 관리 되도록 보장 됩니다.  
  
## <a name="schema-hierarchy"></a>스키마 계층 구조  
 .Vsct 파일에 다음과 같은 주요 요소가 있습니다.  
  
 [CommandTable 요소](../extensibility/commandtable-element.md)  
  
 [Extern 요소](../extensibility/extern-element.md)  
  
 [Include 요소](../extensibility/include-element.md)  
  
 [Define 요소](../extensibility/define-element.md)  
  
 [Commands 요소](../extensibility/commands-element.md)  
  
 [CommandPlacements 요소](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings 요소](../extensibility/keybindings-element.md)  
  
 [UsedCommands 요소](../extensibility/usedcommands-element.md)  
  
 [Parent 요소](../extensibility/parent-element.md)  
  
 [Icon 요소](../extensibility/icon-element.md)  
  
 [Strings 요소](../extensibility/strings-element.md)  
  
 [Command Flag 요소](../extensibility/command-flag-element.md)  
  
 [Symbols 요소](../extensibility/symbols-element.md)  
  
 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>참고 항목  
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSPackage의 명령 라우팅](../extensibility/internals/command-routing-in-vspackages.md)
