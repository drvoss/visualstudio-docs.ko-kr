---
title: VS 셸 배포
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934308"
---
# <a name="vs-shell-deployment"></a>VS 셸 배포

Visual Studio를 확인할 수는 격리 된 셸 있습니다 도메인 특정 언어 및 해당 솔루션 표시 방법을 상호 작용 해야 하는 기능입니다. Visual Studio 격리 셸에 대 한 자세한 내용은 참조 하세요. [격리 셸 사용자 지정](https://vspartner.com/pages/vsshells)합니다.

배포 대상으로는 Visual Studio Shell을 설정 합니다.

1. 에 **DslPackage** 프로젝트를 열고 **source.extension.tt**합니다.

2. 아래 `<SupportedProducts>` 삽입:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   바꿉니다 *MyIsolatedShell* 격리 셸 패키지의 이름입니다.