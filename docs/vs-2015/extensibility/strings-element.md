---
title: 요소 문자열 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0eae2fd7490269d713beb9950163071dd3ba32f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160559"
---
# <a name="strings-element"></a>Strings 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Strings 요소 있어야 적어도 **ButtonText** 자식 요소입니다. 다른 모든 자식 요소는 선택적입니다. 잘못 된 XML과 같은 문자 '&' 및 ' <' 엔터티로 코딩 해야 합니다 ('&amp;'및'&lt;' 등).  
  
 텍스트 문자열에서 앰퍼샌드는 명령에 대 한 바로 가기 키를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|language|선택 사항입니다. Language=".".|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|ButtonText|이 필드 및 명령 정의에서 5 다음 텍스트 필드를 통해 다양 한 메뉴에 나타나는 텍스트를 지정할 수 있습니다. 기본적으로 `ButtonText` 메뉴 컨트롤러에 필드가 나타납니다. `ButtonText` 다른 텍스트 필드는 비어 있는 경우 또한 필드의 기본값이 됩니다. `ButtonText` 기타 텍스트 필드에 지정 된 경우에 필드를 비워 둘 수 없습니다.|  
|ToolTipText|`ToolTipText` 필드를 메뉴 항목에 대 한 도구 설명에 표시 되는 텍스트를 지정 합니다.<br /><br /> 경우는 `ToolTipText` 필드가 비어는 `ButtonText` 필드를 사용 합니다.|  
|MenuText|`MenuText` 필드는 하위 메뉴 또는 바로 가기 메뉴에서 도구 모음, 주 메뉴에 있는 경우 명령에 대해 표시 되는 텍스트를 지정 합니다. 경우는 `MenuText` 필드가 비어 있는 경우 통합된 개발 환경 (IDE)에서 사용 하는 `ButtonText` 필드입니다. `MenuText` 필드 지역화를 위해 사용할 수도 있습니다.<br /><br /> 바로 가기 메뉴를 `MenuText` 필드는 IDE에서 바로 가기 메뉴를 사용자 지정할 수 있는 바로 가기 메뉴 도구 모음에 표시 되는 이름입니다. 따라서 프로그램 바로 가기 메뉴 이름에 특정 수 예를 들어, "바로 가기" 대신 "위젯 패키지 바로 가기 메뉴"를 사용 합니다.<br /><br /> 경우는 `MenuText` 필드를 지정 하지 않으면는 `ButtonText` 필드를 사용 합니다.|  
|CommandName|`CommandName` 키보드 범주에 표시 되는 텍스트를 지정 하는 필드를 **명령** 탭에 **사용자 지정** 대화 상자 (클릭 하 여 사용할 수 있습니다 **사용자지정**에 **도구** 메뉴).|  
|CanonicalName|영어 `CanonicalName` 필드에 입력할 수 있는 영어 텍스트에서 명령의 이름을 지정 합니다 **명령** 메뉴 항목을 실행 하는 창입니다. IDE, 숫자, 밑줄 또는 마침표를 포함된 하지 않은 모든 문자를 제거 합니다. 이 텍스트 다음에 연결 된 `ButtonText` 명령을 정의 하는 필드. 예를 들어 **새 프로젝트** 에 **파일** 메뉴 명령을 File.NewProject 됩니다.<br /><br /> 경우 영어 `CanonicalName` 필드를 지정 하지 않으면 다음을 사용 하 여 IDE를 `ButtonText` 필드 및 문자, 숫자, 밑줄 및 마침표를 제외한 모든 구획입니다. 예를 들어, 단추 텍스트 "& 정의 명령..."가 DefineCommands, 앰퍼샌드, 공간, 및 줄임표 제거 됩니다.<br /><br /> 경우는 `TextChanges` 플래그를 지정 하 고 해당 명령을 인식 명령의 텍스트를 변경 합니다 **명령** 창은 변경 되지 않습니다; 원래의 정규 형식이 그대로 유지 됩니다 `ButtonText` 또는 영어 `CanonicalName` 필드입니다.|  
|LocCanonicalName|합니다 `LocCanonicalName` 필드의 영어를 동일 하 게 작동 하며 `CanonicalName` 필드에는 하지만 지역화 된 명령 텍스트를 지정할 수 있습니다. 정식 두 필드를 지정할 수 있습니다. IDE에 입력 된 텍스트 구문 분석 하기 때문에 합니다 **명령** 창과 연결 명령 한국어와 영어 이외의 언어로 텍스트를 사용 하 여 동일한 명령과 사용 하 여 연결할 수 있습니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[Button 요소](../extensibility/button-element.md)|사용자가 상호 작용할 수 있는 요소를 정의 합니다.|  
|[Menu 요소](../extensibility/menu-element.md)|단일 메뉴 항목을 정의합니다.|  
|[Combo 요소](../extensibility/combo-element.md)|콤보 상자에 표시 되는 명령을 정의 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
