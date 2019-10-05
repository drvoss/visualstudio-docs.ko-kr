---
title: 하나의 솔루션에 여러 DSL 포함
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d9e4ae8239994a7524cdd1da0b3cfe05ea42d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808186"
---
# <a name="multiple-dsls-in-one-solution"></a>하나의 솔루션에 여러 DSL 포함

여러 DSL이 함께 설치되도록 단일 솔루션의 일부분으로 패키지할 수 있습니다.

다양한 기술을 통해 여러 DSL을 통합할 수 있습니다. 자세한 내용은 [Visual Studio Modelbus를 사용 하 여 모델 통합](../modeling/integrating-models-by-using-visual-studio-modelbus.md) 고 [방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md) 하 고 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)합니다.

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>동일한 솔루션에 둘 이상의 DSL 작성

1. 새 **VSIX 프로젝트** 프로젝트입니다.

2. VSIX 솔루션 디렉터리에서 둘 이상의 DSL 프로젝트를 만듭니다.

   - 각 DSL에 대해 새 Visual Studio 인스턴스를 엽니다. 새 DSL을 만들고 VSIX 솔루션과 같은 솔루션 폴더를 지정합니다.

   - 각 DSL을 서로 다른 파일 확장명으로 만들어야 합니다.

   - 이름을 변경 합니다 **Dsl** 하 고 **DslPackage** 모두 다른 되도록 프로젝트. 예: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - 각 **DslPackage\*\source.extension.tt**을 올바른 Dsl 프로젝트 이름에이 줄을 업데이트 합니다.

      `string dslProjectName = "Dsl2";`

   - VSIX 솔루션에서 Dsl * 및 DslPackage 추가\* 프로젝트입니다. 각 쌍을 자체 솔루션 폴더에 배치할 수 있습니다.

2. DSL의 VSIX 매니페스트를 결합합니다.

   1. Open _YourVsixProject_**\source.extension.manifest**.

   2. 각 DSL에 대해 선택할 **콘텐츠 추가** 추가:

       - `Dsl*` 로 프로젝트를 **MEF 구성 요소**

       - `DslPackage*` 로 프로젝트를 **MEF 구성 요소**

       - `DslPackage*` 로 프로젝트를 **VS 패키지**

3. 솔루션을 빌드합니다.

   그러면 생성되는 VSIX가 두 DSL을 모두 설치합니다. F5 키를 사용 하 여 테스트 하거나 배포할 수 있습니다 _YourVsixProject_**\bin\Debug\\\*.vsix**합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio Modelbus를 사용하여 모델 통합](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)