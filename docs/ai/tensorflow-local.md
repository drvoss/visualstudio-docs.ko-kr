---
title: 로컬로 tensorflow 모델 학습
description: 'AI Tools for Visual Studio에서 로컬로 tensorflow 모드 실행 '
keywords: ai, visual studio, tensorflow, 로컬
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 4bca48113349607de2f5ada53356f1d24eb82088
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933991"
---
# <a name="train-a-tensorflow-model-locally"></a>로컬로 tensorflow 모델 학습

이 빠른 시작에서는 Visual Studio Tools for AI에서 로컬로 [MNIST](http://yann.lecun.com/exdb/mnist/) 데이터 집합을 통해 TensorFlow 모델을 학습합니다.

MNIST 데이터베이스에는 60,000개의 학습 예제 집합과 직접 작성한 10,000개의 테스트 예제 집합이 있습니다.

## <a name="prerequisites"></a>전제 조건

시작하기 전에 다음이 설치되었는지 확인합니다.

### <a name="google-tensorflow"></a>Google TensorFlow

터미널에서 다음 명령을 실행합니다.

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy 및 SciPy
[NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) 및 [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy)를 설치합니다.

### <a name="download-sample-code"></a>샘플 코드 다운로드
TensorFlow, CNTK, Theano 등에 대한 심층 학습을 시작하기 위해 이 [GitHub 리포지토리](https://github.com/Microsoft/samples-for-ai)를 다운로드합니다.

## <a name="open-solution-and-train-model"></a>솔루션을 열고 모델 학습

- Visual Studio를 시작하고 **파일 > 열기 > 프로젝트/솔루션**을 선택합니다.

- 다운로드한 샘플 리포지토리에서 **Tensorflow Examples** 폴더를 선택하고 **TensorflowExamples.sln** 파일을 엽니다.

   ![프로젝트 열기](media/tensorflow-local/open-project.png)

   ![솔루션 열기](media/tensorflow-local/open-solution.png)

- **솔루션 탐색기**에서 MNIST 프로젝트를 찾아 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

- **시작**을 클릭합니다.

- 출력은 콘솔에 인쇄됩니다.

   ![콘솔의 샘플 출력](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [클라우드에서 TensorFlow 모델 학습](tensorflow-vm.md)