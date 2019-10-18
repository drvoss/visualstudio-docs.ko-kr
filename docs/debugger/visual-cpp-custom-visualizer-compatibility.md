---
title: Visual C/C++ 사용자 지정 시각화 도우미 호환성
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430624"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ 사용자 지정 시각화 도우미 호환성

Visual Studio 2019부터에는 C++ 메모리를 많이 사용 하는 구성 요소를 호스트 하는 데 외부 64 비트 프로세스를 사용 하는 향상 된 디버거가 포함 되어 있습니다. 이 업데이트의 일부로 C/C++ 식 계산기에 대 한 특정 확장을 새 디버거와 호환 되도록 업데이트 해야 합니다.

현재C++ 레거시 c/EE 추가 기능 또는 C/C++ 사용자 지정 시각화 도우미를 사용 하는 경우 **도구**  > **옵션**  > **디버깅**으로 이동한 다음 **로드 디버그를 선택 취소 하 여 외부 프로세스의 사용을 해제할 수 있습니다. 외부 프로세스의 기호 (네이티브 전용)** 입니다. 이 옵션의 선택을 취소 하면 IDE (devenv.exe) 프로세스 내의 메모리 사용량이 크게 증가 합니다. 따라서 규모가 많은 프로젝트를 디버깅할 것으로 예측 되는 경우 확장의 소유자에 게 문의 하 여이 디버깅 옵션과 호환 되도록 하는 것이 좋습니다.

레거시 C/C++ EE 추가 기능 또는 c/C++ 사용자 지정 시각화 도우미의 소유자 인 경우 [concord 확장성 샘플 wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)의 작업자 프로세스에서 확장 로드를 옵트아웃 하는 방법에 대 한 자세한 정보를 찾을 수 있습니다. [C/C++ 사용자 지정 시각화 도우미 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)도 찾을 수 있습니다.