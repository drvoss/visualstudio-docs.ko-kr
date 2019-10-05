---
title: '방법: 기능 종속성 추가 및 제거 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9373ed07ec49bd41dad343dc447b4b2026793492
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967008"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>방법: 기능 종속성 추가 및 제거
  SharePoint 기능 기능이 나 데이터에 대 한 다른 기능에 달라질 수 있습니다. 이러한 경우 기능에 대 한 종속성으로 이러한 다른 기능을 표시할 수 있습니다. 이 이렇게 하면 SharePoint 서버는 기능이 활성화 되기 전에 종속 기능 활성화 되는지를 확인 합니다.

## <a name="add-dependencies"></a>종속성 추가
 종속성으로 솔루션의 다른 기능을 추가할 수 있습니다. 이 이렇게 할 수 있습니다 필수 기능 설치 되 고 기능을 설치 하기 전에 활성화 해야 합니다.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>솔루션에 기능 종속성을 추가 하려면

1. 기능 디자이너를 열고 확장 합니다 **기능 활성화 종속성** 노드를 선택한 후 합니다 **추가** 단추입니다.

2. 에 **기능 활성화 종속성 추가** 대화 상자를 선택 합니다 **솔루션의 기능에 대 한 종속성을 추가할** 옵션 단추를 종속성으로 추가 하려는 기능의 제목을 선택 차례로 선택 된 **추가** 단추입니다.

     선택 하는 동안 여러 제목을 선택 하 여 둘 이상의 기능을 추가할 수 있습니다 합니다 **Ctrl** 키입니다.

## <a name="addi-custom-dependencies"></a>사용자 지정 종속성 Addi
 종속성으로 SharePoint 서버에 이미 배포 된 기능을 추가할 수 있습니다. 이러한 방식으로 SharePoint 활성화 프로세스는 기능을 설치 하기 전에 모든 종속 기능도 활성화 되는지를 있는지 확인 합니다.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>기능 ID로 종속성을 추가 하려면

1. 기능 디자이너를 열고 확장 합니다 **기능 활성화 종속성** 노드를 선택한 후 합니다 **추가** 단추입니다.

2. 에 **기능 활성화 종속성 추가** 대화 상자를 선택 합니다 **사용자 지정 종속성 추가** 옵션 단추.

3. 에 **기능 ID** 텍스트 상자에 활성화 종속성을 표시 하 고 다음을 선택 하는 기능에 대 한 GUID를 입력 합니다 **추가** 단추.

## <a name="edit-custom-dependencies"></a>사용자 지정 종속성 편집
 이전에 추가한 사용자 지정 종속성을 편집할 수 있습니다. 그러나 솔루션 수 있습니다만의 수, 제거 된 종속 기능 편집할 수 없습니다.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>솔루션의 기능에 대 한 종속성을 변경 하려면

1. 기능 디자이너를 열고 다음를 확장 합니다 **기능 활성화 종속성** 노드.

2. 편집 및 선택 하려는 기능의 이름을 선택 합니다 **편집** 단추입니다.

3. 에 **사용자 지정 기능 활성화 종속성 편집** 대화 상자에서 제목, 기능 ID 또는 설명을 변경 하 고 선택한 합니다 **제출** 단추입니다.

## <a name="remove-dependencies"></a>종속성 제거

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>솔루션의 기능에 대 한 종속성을 제거 하려면

1. 기능 디자이너에서 확장를 **기능 활성화 종속성** 노드를 제거 및 선택한 하려는 기능의 이름을 선택 합니다 **제거** 단추입니다.

## <a name="see-also"></a>참고자료
- [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)
- [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
