---
title: 규칙 집합을 사용 하 여 지정 된 C++ 실행 하는 규칙 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e8361ec9f93ff150d3fd29bce315f635bd00048b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142151"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>규칙 집합을 사용하여 실행할 C++ 규칙 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 하 고 [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]를 만들고 사용자 지정을 수정할 수 있습니다 *규칙 집합* 코드 분석을 사용 하 여 연결 된 특정 프로젝트 요구 사항에 맞게 합니다. 사용자 지정 C++ 규칙 집합을 만들기 위해서는 C/C++ 프로젝트를 Visual Studio IDE에서 열어야 합니다. 그런 다음 규칙 집합 편집기에서 표준 규칙 집합을 열고, 특정 규칙을 추가 또는 제거하고, 필요에 따라 코드 분석으로 규칙이 위반된 것으로 확인될 때 발생하는 작업을 변경합니다.  
  
 새 사용자 지정 규칙 집합을 만들려면 새 파일 이름을 사용 하 여 저장 합니다. 사용자 지정 규칙 집합을 프로젝트에 자동으로 할당 됩니다.  
  
## <a name="opening-the-rule-set-editor"></a>열 규칙 집합 편집기  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>단일 기존 규칙 집합에서 사용자 지정 규칙을 만들려면  
  
1. 솔루션 탐색기에서 프로젝트에 대 한 바로 가기 메뉴를 열고 선택한 후 **속성**합니다.  
  
2. 에 **속성** 탭에서 **코드 분석**합니다.  
  
3. 에 **규칙 집합** 드롭 다운 목록에서 다음 중 하나를 수행 합니다.  
  
   - 사용자 지정하려는 규칙 집합을 선택합니다.  
  
     \- 또는 -  
  
   - 선택할  **\<찾아보기... >** 목록에 없는 기존 규칙 집합을 지정 하려면.  
  
4. 선택할 **열려** 규칙 규칙 집합 편집기에 표시를 합니다.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>규칙을 수정 하려면 규칙 집합 편집기에서 설정  
  
- 규칙 집합의 표시 이름을 변경 하는 **뷰** 메뉴 선택 **속성 창**합니다. 표시 이름을 입력 합니다 **이름을** 상자입니다. 표시 이름을 파일 이름에서 다를 수 있는지 확인 합니다.  
  
- 사용자 지정 규칙 집합에 그룹의 모든 규칙을 추가할 그룹의 확인란을 선택 합니다. 그룹의 모든 규칙을 제거 하려면 확인란의 선택을 취소 합니다.  
  
- 특정 규칙을 사용자 지정 규칙 집합을 추가 하려면 규칙의 확인란을 선택 합니다. 규칙 집합에서 규칙을 제거 하려면 확인란의 선택을 취소 합니다.  
  
- 코드 분석에서 규칙이 위반 될 때 수행할 동작을 변경 하려면 선택 합니다 **동작** 규칙에 대 한 필드를 다음 값 중 하나를 선택 합니다.  
  
     **경고** -경고를 생성 합니다.  
  
     **오류** -오류를 생성 합니다.  
  
     **None** -규칙을 사용 하지 않도록 설정 합니다. 이 작업을 규칙 집합에서 규칙을 제거 하는 것 같습니다.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>그룹화, 필터링 또는 규칙을 사용 하 여 규칙 집합 편집기에서 필드를 변경 하려면 편집기 도구 모음 설정  
  
- 모든 그룹의 규칙을 확장 하려면 선택할 **모두 확장**합니다.  
  
- 모든 그룹의 규칙을 축소 하려면 선택할 **모두 축소**합니다.  
  
- 규칙에서 그룹화 되는 필드를 변경 하려면 필드를 선택 합니다 **Group By** 목록입니다. 그룹화 되지 않은 규칙을 표시 하려면 선택  **\<없음 >** 합니다.  
  
- 를 추가 하거나 규칙 열의 필드를 제거 하려면 **열 옵션**합니다.  
  
- 현재 솔루션에 적용 되지 않는 규칙을 숨기려면 선택 **현재 솔루션에 적용 되지 않는 규칙 숨기기**합니다.  
  
- 오류 작업이 할당 되는 규칙 표시 / 숨김을 전환 하려면 **코드 분석 오류를 생성할 수 있는 규칙 표시**합니다.  
  
- 경고 작업이 할당 되어 있는 규칙 표시 / 숨김을 전환 하려면 **코드 분석 경고를 생성할 수 있는 규칙 표시**합니다.  
  
- 할당 된 규칙 표시 / 숨김을 전환 하는 **None** 작업을 선택 **활성화 되지 않은 규칙 표시**합니다.  
  
- 를 추가 하거나 Microsoft 기본 규칙 집합을 현재 규칙 집합을 제거 하려면 **자식 규칙 집합을 추가 또는 제거**합니다.
