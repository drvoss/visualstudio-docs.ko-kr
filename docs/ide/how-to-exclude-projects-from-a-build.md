---
title: '방법: 빌드에서 프로젝트 제외'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54e65c411afe9815696112dfbcc99bcb9433c4db
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416871"
---
# <a name="how-to-exclude-projects-from-a-build"></a>방법: 빌드에서 프로젝트 제외

포함된 일부 프로젝트를 빌드하지 않고도 솔루션을 빌드할 수 있습니다. 예를 들어, 빌드를 중단하는 프로젝트를 제외할 수 있습니다. 그런 다음 문제를 조사하고 해결한 후 프로젝트를 빌드할 수 있습니다.

다음 방법을 사용하여 프로젝트를 제외할 수 있습니다.

- 활성 솔루션 구성에서 일시적으로 제거

- 해당 프로젝트를 포함하지 않는 솔루션 구성 만들기

자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>활성 솔루션 구성에서 프로젝트를 일시적으로 제거하려면

1. 메뉴 모음에서 **빌드** > **구성 관리자**를 선택합니다.

2. **프로젝트 컨텍스트** 테이블에서 빌드에서 제외할 프로젝트를 찾습니다.

3. 해당 프로젝트의 **빌드** 열에서 확인란의 선택을 취소합니다.

4. **닫기** 단추를 선택한 후 솔루션을 다시 빌드합니다.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>프로젝트가 제외된 솔루션 구성을 만들려면

1. 메뉴 모음에서 **빌드** > **구성 관리자**를 선택합니다.

2. **활성 솔루션 구성** 목록에서 **\<새로 만들기>** 를 선택합니다.

3. **이름** 상자에 솔루션 구성의 이름을 입력합니다.

4. **다음에서 설정 복사** 목록에서 새 구성의 기반으로 사용할 솔루션 구성(예: **디버그**)을 선택한 다음 **확인** 단추를 선택합니다.

5. **구성 관리자** 대화 상자에서 제외할 프로젝트에 대한 **빌드** 열의 확인란을 선택 취소하고 **닫기** 단추를 선택합니다.

6. **표준** 도구 모음에서 새 솔루션 구성이 **솔루션 구성** 상자의 활성 구성인지 확인합니다.

7. 메뉴 모음에서 **빌드** > **솔루션 다시 빌드**를 선택합니다.

## <a name="see-also"></a>참고 항목

- [빌드 구성 이해](../ide/understanding-build-configurations.md)
- [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)
- [방법: 여러 구성 동시 빌드](../ide/how-to-build-multiple-configurations-simultaneously.md)