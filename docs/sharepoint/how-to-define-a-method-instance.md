---
title: '방법: 메서드 인스턴스 정의 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 318744ec1a1a9214ce0385fc56fb1c0cf340339b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814113"
---
# <a name="how-to-define-a-method-instance"></a>방법: 메서드 인스턴스 정의
  모델의 모든 메서드에 대 한 메서드 인스턴스를 하나 이상 정의 해야 합니다.

 메서드 인스턴스를 사용 하 여 추가 합니다 **BDC 메서드 세부 정보** 창입니다. 메서드 인스턴스를 추가 하면 Visual Studio 추가 `<MethodInstance>` 프로젝트에서 모델 파일의 xml 요소입니다. 특성에 대 한 자세한를 `<MethodInstance>` 요소를 참조 하세요 [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)합니다.

### <a name="to-define-a-method-instance"></a>메서드 인스턴스 정의

1. 에 **BDC 메서드 세부 정보** 창에서 메서드의 노드를 확장 한 다음 확장을 **인스턴스** 노드.

2. 에 **메서드 인스턴스 추가** 목록에서 선택 **Finder 인스턴스 만들기**합니다.

     새 메서드 인스턴스 아래에 표시 된 **인스턴스** 노드.

3. 메뉴 모음에서 선택 **뷰** > **속성 창**합니다.

4. 에 **속성** 창 메서드 인스턴스의 속성을 설정 합니다. 각 속성에 대 한 자세한 내용은 참조 하세요. [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)합니다.

## <a name="see-also"></a>참고자료
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [방법: 메서드에 매개 변수를 추가 합니다.](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
