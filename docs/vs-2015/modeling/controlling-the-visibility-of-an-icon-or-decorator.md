---
title: 아이콘 또는 데코레이터의 가시성 제어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8d4dc21c2c6329730d678fa574f11d86bed8cdc4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159619"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>아이콘 또는 데코레이터의 가시성 제어
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *데코레이터* 아이콘 또는 셰이프를 도메인 특정 언어 (DSL)에 표시 되는 텍스트 줄. 데코레이터 표시를 확인 하 고 상태 모델의 속성에 따라 사라질 수 있습니다. 예를 들어 개인을 나타낼 셰이프를에서 사용자의 성별, 자녀 수에 따라 표시 되는 서로 다른 아이콘이 있을 수 있습니다.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>아이콘 또는 데코레이터의 가시성 제어  
 다음 절차를 이미 정의한 모양과 매핑도 도메인 클래스를 가정 합니다. 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다.  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>에 아이콘이 나 텍스트 데코레이터의 가시성 제어  
  
1. DSL 정의 다이어그램에서 아이콘을 표시 하려는 텍스트 decorator 모양 클래스에 추가 합니다.  
  
   1. 모양 클래스를 마우스 오른쪽 **추가**, 데코레이터의 필요한 종류를 클릭 하 고 있습니다.  
  
   2. 데코레이터의 설정 **위치** 속성입니다. 둘 이상의 decorator 동일한 위치에 있을 수 있습니다. 예를 들어 남자와 여자 같은 위치에 공유 아이콘이 있을 수 있습니다.  
  
   3. 설정 된 **기본 아이콘** 는 아이콘 데코레이터의 속성입니다.  
  
2. 모양 클래스와 DSL 정의 다이어그램에서 도메인 클래스 사이의 회색 선 인 다이어그램 요소 맵을 선택 합니다.  
  
3. DSL 정보 창에서에 **Decorator 맵** 탭 decorator를 선택 합니다. 예를 들어 MaleDecorator 합니다.  
  
4. 확인 합니다 **표시 유형 필터** 상자입니다.  
  
5. 도메인 속성 표시 여부를 제어 해야 하는 즉시 도메인 클래스의 경우 둡니다 **필터 속성 경로** 빈 합니다.  
  
    그렇지 않으면 드롭다운 메뉴를 클릭을 관계 또는 속성이 있는 클래스를 이동 합니다.  
  
   - 오류 보고서를 방지 하려면으로 표시 된 관계를 통해 이동 하지 해야 "*" 탐색 도구에서.  
  
6. 설정 된 **필터 속성** 도메인 속성에 있습니다. 예를 들어 성별입니다.  
  
7. 에 **표시 유형 항목** 목록, 데코레이터 표시 되어야 하는이 도메인 속성의 값을 추가 합니다. 예를 들어, 남성입니다.  
  
8. 각 아이콘에 대 한 단계를 반복 합니다.  
  
9. **모든 템플릿 변환**, 빌드 및 실행 및 테스트 다이어그램을 엽니다.  
  
10. 제어 속성 값을 변경 하면 decorator 나타나고 사라집니다.  
  
    자주 표시에 대 한 값의 간단한 집합 보다 더 복잡 한 수식으로 제어 해야 합니다. 예를 들어, 특정 형식의 링크의 수에 따라 달라 집니다 아이콘이 또는 있는지 여부에 종속 되도록 특정 범위에서 숫자는 합니다. 이 경우 다음 절차를 따르십시오.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>수식에 따라 데코레이터의 가시성 제어  
  
1. 도메인 클래스에는 계산된 도메인 속성을 추가 합니다. 에 **속성** 창에서 다음 값을 설정 합니다.  
  
     **IsBrowsable =** `False` **-사용자 속성을 숨깁니다.**  
  
     **종류 =** `Calculated` **-즉, 해당 값을 계산 하는 코드를 제공 합니다**  
  
     **이름을** 예를 들어 **DecoratorControl**  
  
     **Type** = `Boolean`  
  
     자세한 내용은 [사용자 지정 저장소 속성 및 계산](../modeling/calculated-and-custom-storage-properties.md)합니다.  
  
2. 데코레이터 표시 여부를 제어 하 고 새 속성을 확인 합니다.  
  
    1. 셰이프에 도메인 클래스에서 회색 선 인 다이어그램 요소 맵을 선택 합니다. 에 **DSL 세부 정보** 창을 열려면 합니다 **DecoratorMap** 탭 합니다.  
  
    2. 확인 합니다 **표시 유형 필터** 상자입니다.  
  
    3. **필터 속성**, 선택 된 컨트롤 속성 **DecoratorControl**합니다.  
  
    4. 아래 **표시 유형 항목**, 입력 `True`합니다.  
  
3. 클릭 **모든 템플릿 변환** 솔루션 탐색기 도구 모음에서입니다.  
  
4. 클릭 **솔루션 빌드** 에 **빌드** 메뉴.  
  
5. 에 표시 되는 오류 보고서를 두 번 클릭 합니다. "*YourClass* 없습니다 정의 GetDecoratorControlValue..."입니다.  
  
     텍스트 편집기 Dsl\GeneratedCode\DomainClasses.cs에 열립니다. 강조 표시 된 오류 위에 메서드를 추가 하도록 요청 하는 주석입니다.  
  
6. 네임 스페이스, 클래스와 메서드가 누락 된 note 합니다.  예를 들어 Company.FamilyTree.Person.GetDecoratorControlValue() 합니다.  
  
7. 별도 코드 파일에서 누락 된 메서드를 포함 하는 partial 클래스 정의 작성 합니다. 예를 들어:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     프로그램 코드를 사용 하 여 모델을 사용자 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [탐색 및 업데이트 프로그램 코드에서 모델](../modeling/navigating-and-updating-a-model-in-program-code.md)합니다.  
  
8. 다시 작성 하 고 솔루션을 실행 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [모양 및 연결선 정의](../modeling/defining-shapes-and-connectors.md)   
 [다이어그램에 배경 이미지 설정](../modeling/setting-a-background-image-on-a-diagram.md)   
 [탐색 및 프로그램 코드에서 모델 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [도메인별 언어를 사용자 지정하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
