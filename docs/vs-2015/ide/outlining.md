---
title: 개요 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db33392deb16664e48c3b2d90df883294d5cfbaa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441160"
---
# <a name="outlining"></a>개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

더하기 기호(+) 아래에 표시되도록 코드 영역을 축소하여 일부 코드를 뷰에서 숨길 수 있습니다. 더하기 기호를 클릭하면 축소된 영역이 확장됩니다. 또는 Ctrl+M+M을 눌러 영역을 축소한 다음 Ctrl+M+M을 눌러 다시 확장할 수 있습니다. 코드 바로 왼쪽에 표시되는 개요 여백의 영역에서 아무 줄이나 두 번 클릭하여 개요 영역을 축소할 수도 있습니다. 축소된 영역을 마우스로 가리키면 축소된 영역의 내용을 도구 설명으로 확인할 수 있습니다.  
  
 여백을 마우스로 가리키면 개요 여백의 영역도 강조 표시됩니다. 일부 색 구성에서는 기본 강조 색이 다소 희미하게 보일 수도 있습니다. **도구/옵션/환경/글꼴 및 색/축소 가능한 영역**에서 변경할 수 있습니다.  
  
 개요 보기로 표시된 코드에서 작업하는 경우 작업할 섹션을 확장하고, 작업이 완료되면 축소한 다음 다른 섹션으로 이동할 수 있습니다. 개요를 표시하지 않으려는 경우 **개요 표시 중지** 명령을 사용하여 내부 코드에 영향을 주지 않고 개요 정보를 제거할 수 있습니다.  
  
 **편집** 메뉴의 **실행 취소** 및 **다시 실행** 명령은 이러한 작업에 영향을 줍니다. **복사**, **잘라내기**, **붙여넣기** 및 끌어서 놓기 작업은 개요 정보를 유지하지만 축소 가능한 영역의 상태는 유지되지 않습니다. 예를 들어 축소된 영역을 복사하는 경우 **붙여넣기** 작업은 복사된 텍스트를 확장된 영역으로 붙여넣습니다.  
  
> [!CAUTION]
> 개요 보기로 표시된 영역을 변경하는 경우 개요가 손실될 수 있습니다. 예를 들어 삭제 또는 찾기/바꾸기 작업으로 인해 영역의 끝이 지워질 수 있습니다.  
  
 **편집/개요** 하위 메뉴에서 다음 명령을 찾을 수 있습니다.  
  
|||  
|-|-|  
|선택 영역 숨기기|(Ctrl+M, Ctrl+H) - 정상적으로 개요에 사용할 수 없는 선택한 코드 블록(예: `if` 블록)을 축소합니다. 사용자 지정 영역을 제거하려면 **현재 숨기기 중지**(또는 Ctrl+M, Ctrl+U)를 사용합니다. Visual Basic에서 사용할 수 없습니다.|  
|개요 확장/축소|- 중첩된 축소 섹션에 커서가 있는 경우 가장 안쪽 개요 섹션의 현재 숨김 또는 확장 상태를 반대로 바꿉니다.|  
|전체 개요 영역 표시/숨기기|(Ctrl+M, Ctrl+L) - 모든 영역을 동일한 축소 또는 확장 상태로 설정합니다. 일부 영역은 확장되고 일부 영역은 축소된 경우 축소된 영역이 확장됩니다.|  
|개요 표시 중지|(Ctrl+M, Ctrl+P) - 문서 전체에 대한 개요 정보를 모두 제거합니다.|  
|현재 영역 숨기기 중지|(Ctrl+M, Ctrl+U) - 현재 선택한 사용자 정의 영역에 대한 개요 정보를 제거합니다. Visual Basic에서 사용할 수 없습니다.|  
|정의 부분만 보이기|(Ctrl+M, Ctrl+O) - 모든 형식의 멤버를 축소합니다.|  
|블록 축소: \<논리적 경계>|(Visual C++) 삽입 지점이 포함된 함수의 영역을 축소합니다. 예를 들어 삽입 지점이 루프 안에 있는 경우 루프가 숨겨집니다.|  
|모두 축소: \<논리적 구조>|(Visual C++) 함수 내부의 모든 구조를 축소합니다.|  
  
 Visual Studio SDK를 사용하여 확장 또는 축소할 텍스트 영역을 정의할 수도 있습니다. [연습: 개요](../extensibility/walkthrough-outlining.md)를 참조하세요.
