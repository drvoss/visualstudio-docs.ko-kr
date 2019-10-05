---
title: '방법: 특정 Finder 메서드 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8fdd467f2b3a06398198f6fd8452c6a548bf0872
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431278"
---
# <a name="how-to-add-a-specific-finder-method"></a>방법: 특정 Finder 메서드 추가
  만들어 단일 엔터티 인스턴스를 반환할 수 있습니다는 *Specificfinder* 메서드. 비즈니스 데이터 연결 (BDC) 서비스는 사용자가 비즈니스 데이터 웹 파트 또는 외부 목록에서 엔터티를 선택할 때 특정 Finder 메서드를 실행 합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)합니다.

### <a name="to-create-a-specific-finder-method"></a>특정 Finder 메서드를 만들려면

1. 에 **BDC 디자이너**, 엔터티를 선택 합니다.

    엔터티를 추가 하는 방법에 대 한 자세한 합니다 **BDC 디자이너** Visual Studio에서 참조 [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)합니다.

2. 메뉴 모음에서 선택 **뷰** > **기타 Windows**를 **BDC 메서드 세부 정보**합니다.

    합니다 **BDC 메서드 세부 정보** 창이 열립니다. 해당 창에 대 한 자세한 내용은 참조 하세요. [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)합니다.

3. 에 **메서드를 추가** 목록에서 선택 **Specificfinder 메서드 만들기**합니다.

    Visual Studio 모델에는 다음 요소를 추가합니다. 이러한 요소에 표시 된 **BDC 메서드 세부 정보** 창입니다.

   - 메서드

   - 메서드에 대 한 입력된 매개 변수입니다.

   - 메서드에 대 한 반환 매개 변수입니다.

   - 각 매개 변수의 형식 설명자입니다.

   - 메서드에 대 한 메서드 인스턴스입니다.

     자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)합니다.

4. Visual Studio를 엽니다 **속성** 창입니다.

5. 엔터티 형식 설명자를 반환 매개 변수의 형식 설명자를 구성 합니다. 엔터티 형식 설명자를 만드는 방법에 대 한 자세한 내용은 [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)합니다.

   > [!NOTE]
   > 엔터티에 Finder 메서드를 추가한 경우이 단계를 수행할 필요가 없습니다. Visual Studio Finder 메서드에 정의 된 형식 설명자를 사용 합니다.

   > [!NOTE]
   > 엔터티 형식의 식별자 필드는 자동으로 생성 되는 데이터베이스 테이블의 필드를 나타내는 경우 설정 합니다 **읽기 전용** 식별자 필드의 속성 **True**합니다.

6. 에 **메서드 세부 정보** 창 메서드의 메서드 인스턴스를 선택 합니다.

7. 에 **속성 창**설정 합니다 **반환 매개 변수 이름** 속성 메서드의 반환 매개 변수의 이름. 메서드 인스턴스 속성에 대 한 자세한 내용은 참조 하세요. [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)합니다.

8. **솔루션 탐색기**, 엔터티에 대해 생성 된 서비스 코드 파일의 바로 가기 메뉴를 열고 선택한 후 **코드 보기**합니다.

    엔터티 서비스 코드 파일이 코드 편집기에서 열립니다. 엔터티 서비스 코드 파일에 대 한 자세한 내용은 참조 하세요. [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)합니다.

9. 특정 Finder 메서드 코드를 추가 합니다. 이 코드는 다음 작업을 수행합니다.

   - 데이터 원본에서 레코드를 검색합니다.

   - BDC 서비스에 엔터티를 반환합니다.

     다음 예제에서는 AdventureWorks 샘플 데이터베이스에서 SQL Server에 대 한 연락처를 반환합니다.

     > [!NOTE]
     > 값을 `ServerName` 필드 서버의 이름입니다.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>참고자료
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: Updater 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 메서드에 매개 변수를 추가 합니다.](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
