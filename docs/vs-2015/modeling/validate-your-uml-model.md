---
title: UML 모델 유효성 검사 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f795928677f4a232c3ae3cec0d3bab9d9266cb35
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437454"
---
# <a name="validate-your-uml-model"></a>UML 모델 유효성 검사
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 그릴 수 있는 일부 UML 모델은 프로젝트에서 잘못된 것으로 간주할 수 있습니다. 예를 들어 사용 사례의 행위자를 나타내는 수명선이 있는 시퀀스 다이어그램에 항상 사용 사례가 연결되도록 할 수 있습니다. 설치 또는 정의할 수 있습니다 *제약 조건* 이와 같은 요구 사항에 맞게 팀 데 도움이 되는 합니다. 제약 조건은 사용자가 모델을 저장하거나 열 때 적용할 수 있는 메뉴 명령으로 호출할 수 있습니다.  
  
 제약 조건은 팀에서 UML 모델을 해석 및 사용하는 방법에 따라 달라지므로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에는 제공되지 않습니다. 그러나 고유한 제약 조건을 정의하고 다른 사용자가 정의한 제약 조건을 설치할 수 있습니다. 참조 제약 조건을 정의 및 패키지에 배포 하는 방법에 알아보려면 [UML 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)합니다.  
  
## <a name="invoking-validation"></a>유효성 검사 호출  
 유효성 검사 확장을 설치한 경우 확장이 제공하는 제약 조건이 적용될 수 있는 경우는 다음과 같습니다. 일부 제약 조건은 이러한 몇몇 사례에서만 적용되도록 설정됩니다.  
  
- **유효성 검사 명령입니다.** 언제 든 지 유효성 검사를 호출 하려면 **UML 모델 유효성 검사** 에 **아키텍처** 메뉴.  
  
  > [!NOTE]
  > 유효성 검사 제약 조건이 설치된 경우에만 명령이 나타납니다.  
  
- **모델을 저장 합니다.** 모델을 저장할 때 유효성 검사 제약 조건이 적용될 수 있습니다. 이들 제약 조건을 사용하면 프로젝트 해석에 따라 잘못된 모델을 저장하지 않게 할 수 있습니다.  
  
   오류가 있으면 모델을 저장할지 묻는 메시지가 표시됩니다. 오류를 수정하거나 모델을 그대로 저장하도록 선택할 수 있습니다.  
  
- **모델을 열면 됩니다.** 모델을 저장할 때 있던 오류 메시지를 복원하기 위해, 모델을 열 때 유효성 검사 메서드가 적용될 수 있습니다. 모델의 다른 파트에서 작업 중인 사용자가 적용한 변경 내용 간 불일치로 인해 오류가 도입될 수도 있습니다. 자세한 내용은 [모델 및 다이어그램 내보내기 공유](../modeling/share-models-and-exporting-diagrams.md)합니다.  
  
  유효성 검사 오류는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 창에 보고됩니다.  
  
  다이어그램에서 잘못된 요소를 선택하려면 오류를 두 번 클릭합니다. 이 방법은 잘못된 요소가 열린 다이어그램에 표시된 경우에만 사용할 수 있습니다.  
  
## <a name="installing-validation-constraints"></a>유효성 검사 제약 조건 설치  
 제약 조건은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장(VSIX) 파일 내에 패키지됩니다. 일반적으로 제약 조건 집합은 메뉴 명령, 프로필, 도구 상자 항목 등의 기타 정의를 포함하는 확장의 파트입니다.  
  
#### <a name="to-install-a-visual-studio-extension"></a>Visual Studio 확장을 설치하려면  
  
1. 두 번 클릭 합니다 **.vsix** Windows 탐색기 (또는 파일 탐색기)의 파일입니다.  
  
2. 이미 실행 중인 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 인스턴스를 다시 시작합니다.  
  
## <a name="disabling-and-uninstalling-validation-constraints"></a>유효성 검사 제약 조건 사용 안 함 및 제거  
 제약 조건이 적용되지 않은 모델을 사용하려는 경우 제약 조건이 포함된 확장을 일시적으로 사용하지 않도록 설정할 수 있습니다. 이 방법으로 여러 가지 확장을 사용하거나 사용하지 않도록 설정하여 서로 다른 시간에 다양한 모델을 사용할 수 있습니다.  
  
#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Visual Studio 확장을 사용하지 않도록 설정하거나 제거하려면  
  
1. 에 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **도구** 메뉴에서 클릭 **확장 및 업데이트**합니다.  
  
2. 클릭 확장과 **사용 안 함** 일시적으로 확장을 사용 하지 않도록 설정 합니다. 다시 활성화할 수 있습니다이 나중에 돌아가서 합니다 **확장 및 업데이트** 창입니다.  
  
     \- 또는 -  
  
     클릭 **제거** 확장을 제거 하려면.  
  
3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 다시 시작합니다.  
  
## <a name="see-also"></a>참고 항목  
 [UML 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)   
 [앱 용 모델 만들기](../modeling/create-models-for-your-app.md)   
 [개발 프로세스에서 모델 사용](../modeling/use-models-in-your-development-process.md)
