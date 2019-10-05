---
title: 작업 주석
description: 코드에 작업 주석 추가
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62987054"
---
# <a name="task-comments"></a>작업 주석

코드를 작성할 때는 미완성 코드, 의심스러운 코드 또는 경고가 포함된 빠른 해결 방법에 명시적으로 주석을 다는 것이 일반적인 사례입니다. Mac용 Visual Studio에서 제공하는 기본 신호 토큰은 TODO, HACK, FIXME 및 UNDONE입니다. 다음 이미지에 설명된 대로 **Visual Studio > 기본 설정 > 환경 > 작업**에서 개인화된 토큰을 정의할 수 있습니다.

![작업 목록 기본 설정](media/source-editor-image10.png)

새 작업 주석을 추가하려면 작업 키워드가 포함된 주석을 추가합니다. 예:

```csharp
//TODO: Finish this for all properties.
```

Mac용 Visual Studio는 **작업 목록** 패드에서 이러한 표식을 강조 표시하여 주의를 환기합니다. 작업 목록 패드를 표시하려면 **보기 > 패드 > 작업**으로 이동할 수 있습니다.

![작업 목록 패드](media/source-editor-image11.png)

## <a name="see-also"></a>참고 항목

- [작업 목록 사용(Windows의 Visual Studio)](/visualstudio/ide/using-the-task-list)