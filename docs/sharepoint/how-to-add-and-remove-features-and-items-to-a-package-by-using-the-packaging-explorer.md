---
title: '패키징 탐색기: 추가 및 제거 기능 및 패키지에는 항목'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f01ecb67cb82ffe325ea471ad5fb5913c8e4d28
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401556"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>방법: 추가 및 패키징 탐색기를 사용 하 여 패키지에 기능과 항목 제거
  SharePoint 항목 및 기능을 배포 하는 패키지를 구성 하려면 패키징 탐색기를 사용할 수 있습니다. .Wsp 파일 내에서 SharePoint 프로젝트 항목 및 기능을 조정할 수 있습니다.

 또는 보기 기능 활성화 순서를 변경 하려면 순서를 패키징 디자이너를 사용할 수 있습니다. 자세한 내용은 [방법: 추가 및 패키지 디자이너를 사용 하 여 패키지에 기능과 항목 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)합니다.

## <a name="open-the-packaging-explorer"></a>패키징 탐색기를 열려면
 Visual Studio 솔루션에 하나 이상의 SharePoint 프로젝트가 있으면 패키징 탐색기를 열려면 다음 절차를 사용할 수 있습니다. 또는 패키징 탐색기를 자동으로 열립니다 기능 또는 패키지 디자이너를 볼 때. 모든 기능 및 패키지 디자이너를 닫은 후 패키징 탐색기를 닫습니다.

#### <a name="to-open-the-packaging-explorer"></a>패키징 탐색기를 열려면

1. 메뉴 모음에서 선택 **뷰** > **기타 Windows** > **패키징 탐색기**합니다.

     합니다 **패키징 탐색기** 에 표시 되는 **도구 상자**합니다.

## <a name="adding-a-feature-to-a-package"></a>패키지에 기능 추가
 패키징 탐색기를 사용 하 여 패키지에 신규 및 기존 기능을 추가할 수 있습니다.

#### <a name="to-add-a-sharepoint-feature"></a>SharePoint 기능을 추가 하려면

1. 엽니다는 **패키징 탐색기**선택한를 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가 기능**합니다.

#### <a name="to-move-an-existing-sharepoint-feature"></a>기존 SharePoint 기능을 이동 하려면

1. 열기는 **패키징 탐색기**, 다음 단계 중 하나를 수행 합니다.

    - 끌어서를 **기능** 다른 프로젝트에 프로젝트 하나에서 합니다.

    - 기능에 대 한 바로 가기 메뉴를 열고 **잘라내기**에서 이동 기능을 선택한 후 원하는 프로젝트에 대 한 바로 가기 메뉴를 열고 **붙여넣기**합니다.

    > [!NOTE]
    > 솔루션에 SharePoint 프로젝트가 두 개 이상 있는 경우 이 절차를 사용합니다.

## <a name="validate-a-feature-or-package"></a>기능 또는 패키지 유효성 검사
 파일의 유효성을 검사 하 여 SharePoint 기능 및 패키지의 잠재적 문제를 식별할 수 있습니다. 경고 및 오류 출력 창과 오류 목록 창에 표시 됩니다.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>SharePoint 기능 또는 패키지의 유효성을 검사 하려면

1. 엽니다는 **패키징 탐색기**합니다.

2. 기능 또는 패키지에 대 한 바로 가기 메뉴를 열고 선택한 **유효성 검사**합니다.

## <a name="see-also"></a>참고자료
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
