---
title: 프로그래밍 방식으로 연락처에서 전자 메일 주소를 찾으려면
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26e32314db68ae064edac5537222447625cb051d
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328976"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>방법: 프로그래밍 방식으로 연락처에서 전자 메일 주소 검색
  이 예제에서는 메일 주소에 도메인 이름 **example.com** 이 있는 연락처에 대한 연락처 폴더를 검색합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 사항이 필요합니다.

- 메일 주소에 도메인 이름 **example.com** (예: `somebody@example.com`) 및 이름과 성이 있는 연락처입니다.

## <a name="see-also"></a>참고자료
- [연락처 항목 작업](../vsto/working-with-contact-items.md)
- [방법: 프로그래밍 방식으로 전자 메일 보내기](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [방법: 프로그래밍 방식으로 Outlook 연락처 액세스](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [방법: 프로그래밍 방식으로 Outlook 연락처에 항목 추가](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
