---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147092"
---
안전 하지 않은 deserializers는 신뢰할 수 없는 데이터를 역직렬화 하는 동안에 취약 합니다. 공격자는 악의적인 의도 사용 하 여 개체를 삽입할 예기치 않은 형식이 serialize 된 데이터를 수정할 수 있습니다. 안전 하지 않은 역직렬 변환기가 공격 수, 예를 들어, 기본 운영 체제에서 명령을 실행, 네트워크를 통해 통신 또는 파일을 삭제 합니다.