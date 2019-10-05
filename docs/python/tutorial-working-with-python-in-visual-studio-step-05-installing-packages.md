---
title: Visual Studio 자습서 5단계에서 Python 패키지 설치
titleSuffix: ''
description: Visual Studio의 Python 기능에 대한 핵심 연습의 5단계로, Python 환경에서 패키지를 관리하는 Visual Studio의 기능을 보여줍니다.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bf38def7be9607868df8f9c116266632ffcad710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831241"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>5단계: Python 환경에서 패키지 설치

**이전 단계: [디버거에서 코드 실행](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python 개발자 커뮤니티에서는 사용자 소유의 프로젝트에 통합할 수 있는 유용한 패키지가 무수히 만들어졌습니다. Visual Studio는 Python 환경에서 패키지를 관리하기 위한 UI를 제공합니다.

1. **보기** > **다른 창** > **Python 환경** 메뉴 명령을 선택합니다. **Python 환경** 창이 **솔루션 탐색기**에 대한 피어로 열리고 사용할 수 있는 다양한 환경을 표시합니다. 목록에는 Visual Studio 설치 관리자를 사용하여 설치한 환경과 별도로 설치한 환경이 모두 포함됩니다. 굵게 표시된 환경은 새 프로젝트에 사용되는 기본 환경입니다.

   ![Python 환경 창](media/environments/environments-default-view-blue.png)

2. 환경의 **개요** 탭에서는 환경의 설치 폴더 및 인터프리터와 함께 해당 환경에 대한 **대화형** 창에 빠르게 액세스할 수 있습니다. 예를 들어 **대화형 창 열기**를 선택하면 Visual Studio에서 해당 특정 환경에 대한 **대화형** 창이 나타납니다.

3. **패키지** 탭을 선택하면 현재 환경에 설치되어 있는 패키지 목록이 표시됩니다.

   ![환경에 설치된 패키지](media/environments/environments-installed-packages-blue.png)

4. 검색 필드에 해당 이름을 입력하여 `matplotlib`를 설치한 다음, **pip install**을 선택합니다.

   ![환경에 matplotlib 설치](media/environments/environments-add-matplotlib1.png)

5. 메시지가 표시되면 권한 상승에 동의하여 수행합니다.

6. 패키지가 설치된 후 **Python 환경** 창에 나타납니다. 패키지의 오른쪽에 있는 **X**를 누르면 제거됩니다.

   ![환경에 matplotlib 설치 완료](media/environments/environments-add-matplotlib2.png)

   작은 진행률 표시줄은 환경 아래에 표시되어 Visual Studio에서 새로 설치된 패키지에 대한 IntelliSense 데이터베이스를 빌드 중임을 나타낼 수 있습니다. **IntelliSense** 탭에 더 자세한 정보가 표시됩니다. 해당 데이터베이스가 완료될 때까지 자동 완성 및 구문 검사와 같은 IntelliSense 기능은 해당 패키지에 대한 편집기에서 활성화되지 않습니다.

   Visual Studio 2017 버전 15.6 이상에서는 IntelliSense 작업에 다른 더 빠른 방법을 사용하며, **IntelliSense** 탭에 해당 효과에 대한 메시지를 표시합니다.

7. **파일** > **새로 만들기** > **프로젝트**에서 **Python 애플리케이션** 템플릿을 선택하여 새 프로젝트를 만듭니다. 표시되는 코드 파일에서 이전 자습서 단계와 같이 코사인 웨이브를 만드는, 이번에만 도표로 표시된 다음 코드를 붙여넣습니다.

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

8. 디버거를 사용하거나(**F5**) 디버거를 사용하지 않고(**Ctrl**+**F5**) 프로그램을 실행하여 출력을 확인합니다.

   ![matplotlib의 출력 예제](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [Git 작업](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Python 환경](managing-python-environments-in-visual-studio.md)
