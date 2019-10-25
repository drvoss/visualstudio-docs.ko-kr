---
title: 하나의 솔루션에 여러 Dsl이 있습니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668561"
---
# <a name="multiple-dsls-in-one-solution"></a>하나의 솔루션에 여러 DSL 포함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

여러 DSL이 함께 설치되도록 단일 솔루션의 일부분으로 패키지할 수 있습니다.

 다양한 기술을 통해 여러 DSL을 통합할 수 있습니다. 자세한 내용은 [Visual Studio를 사용 하 여 모델 통합 Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) 및 [How를 참조 하세요. @No__t_0 끌어서 놓기 처리기를 추가 하 고 [복사 동작을 사용자 지정](../modeling/customizing-copy-behavior.md)합니다.

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>같은 솔루션에서 둘 이상의 DSL을 작성하려면

1. 둘 이상의 DSL 솔루션과 VSIX 프로젝트를 만든 다음 모든 프로젝트를 단일 솔루션에 추가합니다.

   - 새 VSIX 프로젝트를 만들려면 다음을 수행 합니다. **새 프로젝트** 대화 상자에서 **시각적 개체 C#** , **확장성**, **VSIX 프로젝트**를 선택 합니다.

   - VSIX 솔루션 디렉터리에 둘 이상의 DSL 솔루션을 만듭니다.

        각 DSL에 대해 새 Visual Studio 인스턴스를 엽니다. 새 DSL을 만들고 VSIX 솔루션과 같은 솔루션 폴더를 지정합니다.

        각 DSL을 서로 다른 파일 확장명으로 만들어야 합니다.

   - **Dsl** 및 **dslpackage** 프로젝트의 이름을 모두 다른 것으로 변경 합니다. 예: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - 각 **Dslpackage \* \ source.extension.tt**에서이 줄을 올바른 Dsl 프로젝트 이름으로 업데이트 합니다.

        `string dslProjectName = "Dsl2";`

   - VSIX 솔루션에서 Dsl * 및 DslPackage \* 프로젝트를 추가 합니다.

        각 쌍을 자체 솔루션 폴더에 배치할 수 있습니다.

2. DSL의 VSIX 매니페스트를 결합합니다.

   1. _YourVsixProject_ **\source.extension.manifest**를 엽니다.

   2. 각 DSL에 대해 **콘텐츠 추가** 를 선택 하 고 추가 합니다.

       - 프로젝트를 **MEF 구성 요소로** `Dsl*`

       - 프로젝트를 **MEF 구성 요소로** `DslPackage*`

       - 프로젝트를 **VS 패키지로** `DslPackage*`

3. 솔루션을 빌드합니다.

   그러면 생성되는 VSIX가 두 DSL을 모두 설치합니다. F5 키를 사용 하 여 테스트 하거나 _YourVsixProject_ **\bin\debug \\ \*** 을 배포할 수 있습니다.

## <a name="see-also"></a>관련 항목:
 [Visual Studio Modelbus를 사용 하 여 모델을 통합 하는](../modeling/integrating-models-by-using-visual-studio-modelbus.md) 방법 [How: [복사 동작을 사용자 지정](../modeling/customizing-copy-behavior.md) 하 ](../modeling/how-to-add-a-drag-and-drop-handler.md) 끌어서 놓기 처리기 추가
