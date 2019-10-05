---
title: '방법: 프로그래밍 방식으로 Outlook 폴더를 사용 하 여 웹 페이지에 연결'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e83f8b7f6bcdb790b5e545aa76426bc05f0735f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817311"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>방법: 프로그래밍 방식으로 Outlook 폴더를 사용 하 여 웹 페이지에 연결
  이 예제에서는 라는 폴더에 대 한 확인 `HtmlView` Microsoft Office Outlook에서. 폴더가 없으면 코드는 폴더를 만들고 웹 페이지를 할당 합니다. 폴더가 있으면 폴더의 내용을 표시 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>참고자료
- [폴더 작업](../vsto/working-with-folders.md)
- [방법: 프로그래밍 방식으로 이름으로 폴더 검색](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [방법: 프로그래밍 방식으로 사용자 지정 폴더 항목 만들기](../vsto/how-to-programmatically-create-custom-folder-items.md)
