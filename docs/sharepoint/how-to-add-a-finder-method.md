---
title: '방법: Finder 메서드 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 49f494fa2c0fb35f7d2a65dc2ccb6b6d2d761cbe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428721"
---
# <a name="how-to-add-a-finder-method"></a>방법: Finder 메서드 추가
  웹 파트 또는 목록에서 엔터티 목록을 표시 하려면 데이터 연결 (BDC (비즈니스) 서비스를 사용 하려면 만들어야 합니다는 *Finder* 메서드. Finder 메서드는 엔터티 인스턴스 컬렉션을 반환 하는 특수 메서드입니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)합니다.

### <a name="to-create-a-finder-method"></a>Finder 메서드를 만들려면

1. 에 **BDC 디자이너**, 엔터티를 선택 합니다.

    자세한 내용은 [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)합니다.

2. 메뉴 모음에서 선택 **뷰** > **기타 Windows** > **BDC 메서드 세부 정보**합니다.

    합니다 **BDC 메서드 세부 정보** 창이 열립니다. 에 대 한 자세한 내용은 합니다 **BDC 메서드 세부 정보** 창 참조 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)합니다.

3. 에 **메서드를 추가** 목록에서 선택 **Finder 메서드 만들기**합니다.

    Visual Studio에는 메서드, 반환 매개 변수 및 형식 설명자를 추가합니다.

4. 엔터티 컬렉션 형식 설명자 형식 설명자를 구성 합니다. 엔터티 컬렉션 형식 설명자를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)합니다.

   > [!NOTE]
   > 엔터티에 Specificfinder 메서드를 추가한 경우이 단계를 수행할 필요가 없습니다. Visual Studio Specificfinder 메서드에 정의 된 형식 설명자를 사용 합니다.

5. **솔루션 탐색기**, 엔터티에 대해 생성 된 서비스 코드 파일의 바로 가기 메뉴를 열고 선택한 후 **코드 보기**합니다. 서비스 코드 파일에 대 한 자세한 내용은 참조 하세요. [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)합니다.

6. Finder 메서드 코드를 추가 합니다. 이 코드는 다음 작업을 수행합니다.

   - 데이터 원본에서 데이터를 검색합니다.

   - BDC 서비스에 엔터티 목록을 반환합니다.

     컬렉션을 반환 하는 다음 예제에서는 `Contact` SQL Server에 대 한 AdventureWorks 예제 데이터베이스에서 데이터를 사용 하 여 엔터티.

   > [!NOTE]
   > 값을 `ServerName` 필드 서버의 이름입니다.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>참고자료
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: Updater 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [방법: 메서드에 매개 변수를 추가 합니다.](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
