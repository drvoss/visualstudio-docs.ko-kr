---
title: 레이어 다이어그램의 확장 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6361651672e72df6661f030a4b6c8e451fdaea89
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738770"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>레이어 다이어그램의 확장명 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 레이어 모델 확장을 만들 때 발생할 수 있는 몇 가지 문제를 해결합니다.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>F5 키를 눌러 내 확장을 디버그할 때 내 명령, 제스처 처리기, 유효성 검사 확장 또는 사용자 지정 속성이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 실험적 인스턴스의 레이어 다이어그램에 나타나지 않습니다.  
  
1. 실험적 인스턴스에서 확장 솔루션을 엽니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 및는 **빌드** 메뉴에서 클릭 **솔루션 다시 빌드**합니다.  
  
2. 키를 눌러 **F5** 하거나 **ctrl+f5** 의 실험적 인스턴스를 시작 하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. 레이어 다이어그램을 열고 확장을 테스트합니다.  
  
   필요한 경우 다음 절차를 계속 진행합니다.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>이전 버전의 확장이 실행됩니다.  
  
1. 실행 중인 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 실험적 인스턴스가 없는지 확인합니다.  
  
2. 폴더를 삭제 합니다: %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache  
  
   > [!NOTE]
   >  % LocalAppData %는 일반적으로 *DriveName*: \Users\\*UserName*\AppData\Local입니다.  
  
   필요한 경우 다음 절차를 계속 진행합니다.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>이전 버전의 유효성 검사 결과가 나타나거나, 내 유효성 검사 메서드가 호출되지 않습니다.  
  
1.  실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 **빌드** 메뉴에서 클릭 **솔루션 정리**합니다. 캐시된 이전 유효성 검사 분석 결과가 지워집니다.  
  
2.  모델의 레이어가 코드 요소와 연결되었는지, 그리고 모델에 종속성 링크가 하나 이상 있는지 확인합니다. 유효성을 검사할 항목이 없는 경우에는 유효성 검사가 호출되지 않습니다.  
  
3.  일반 중단점은 별도 프로세스로 실행되기 때문에 유효성 검사 메서드에서 작동하지 않습니다. 메서드를 단계별로 실행하려는 경우 `System.Diagnostics.Debugger.Launch()` 호출을 삽입해야 합니다.  
  
4.  **source.extension.vsixmanifest** 레이어 유효성 검사 프로젝트에서 모두 추가 되어 있는지 확인 한 **MEF 구성 요소** 항목 및 **사용자 지정 확장 형식** 아래에 있는 항목 **콘텐츠**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레이어 다이어그램 확장](../modeling/extend-layer-diagrams.md)



