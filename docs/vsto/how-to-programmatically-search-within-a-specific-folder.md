---
title: '방법: 프로그래밍 방식으로 특정 폴더 내용 검색'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961903"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>방법: 프로그래밍 방식으로 특정 폴더 내용 검색
  이 코드 예제에서는 합니다 `Find` 및 `FindNext` 에 있는 전자 메일 메시지의 제목 필드에 텍스트를 검색 하는 방법의 **수신함**합니다. 이 메서드는 문자열 필터를 사용 하 여의 시작 문자로 문자 T에 대 한 확인 된 `Subject` 텍스트입니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>참고자료
- [폴더 작업](../vsto/working-with-folders.md)
- [Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)
- [방법: 프로그래밍 방식으로 이름으로 폴더 검색](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
