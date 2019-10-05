---
title: 다른 데이터 연결을 사용 하 여 디자이너에 추가 된 개체
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c85e0c17eeb4cfbd786faac338c8b908c5a7f363
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260933"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>디자이너에 추가 하려는 개체가 디자이너 보다 다양 한 데이터 연결을 사용 하 여

디자이너에 추가하려는 개체가 디자이너에서 현재 사용 중인 데이터 연결이 아닌 다른 데이터 연결을 사용합니다. 디자이너에서 사용 중인 연결을 바꾸시겠습니까?

항목을 추가 하는 경우는 **Object Relational Designer** (**O/R 디자이너**), 모든 항목이 하나의 공유 데이터 연결을 사용 합니다. 디자인 화면에는 화면의 모든 개체에 대해 하나의 연결을 사용하는 <xref:System.Data.Linq.DataContext>가 표시됩니다. 디자이너에서 현재 사용하는 데이터 연결과 다른 데이터 연결을 사용하는 디자이너에 개체를 추가하면 이 메시지가 나타납니다. 이 오류를 해결하려면 기존 연결 유지를 선택하세요. 이 항목을 선택하면 선택한 개체가 추가되지 않습니다. 또는 개체 추가를 선택하고 <xref:System.Data.Linq.DataContext> 연결을 새 연결로 다시 설정할 수 있습니다.

## <a name="connection-options"></a>연결 옵션

- 선택한 개체에서 사용 하는 연결을 사용 하 여 기존 연결을 바꾸려면 클릭 **예**합니다.

   선택한 개체에 추가 됩니다는 **O/R 디자이너**, 및 *datacontext.connection이* 새 연결으로 설정 됩니다.

   > [!NOTE]
   > 클릭 하면 **예**, 모든 엔터티 클래스에 **O/R 디자이너** 새 연결에 매핑됩니다.

- 계속 하려면 기존 연결 및 선택한 개체를 추가 하는 취소를 사용 하려면 클릭 하십시오 **No**합니다.

   작업이 취소됩니다.  *DataContext.Connection*이 기존 연결로 설정되어 있습니다.

## <a name="see-also"></a>참고자료

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
