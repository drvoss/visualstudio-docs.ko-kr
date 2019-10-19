---
title: 속성을 삭제할 수 없음
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 29344a2443708d9ddaed3d90a186ab8424638664
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640497"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>\<property name> 속성을 삭제할 수 없음

\<property name> 속성은 \<class name> 및 \<class name> 간 상속의 **판별자 속성**으로 설정되어 있으므로 삭제할 수 없음

선택한 속성이 오류 메시지에 표시된 클래스 간 상속의 **판별자 속성**으로 설정되었습니다. 속성이 데이터 클래스 간 상속 구성에 참여 중인 경우에는 해당 속성을 삭제할 수 없습니다.

**판별자 속성**을 데이터 클래스의 다른 속성으로 설정하면 원하는 속성을 삭제할 수 있습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. **O/R 디자이너**에서 오류 메시지에 표시된 데이터 클래스를 연결하는 상속 선을 선택합니다.

2. **판별자** 속성을 다른 속성으로 설정합니다.

3. 속성 삭제를 다시 한 번 시도합니다.

## <a name="see-also"></a>참조

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)