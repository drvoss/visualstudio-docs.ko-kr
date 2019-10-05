---
title: '방법: Customize a SharePoint Feature | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
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
ms.openlocfilehash: e7a00f3c58f917e7355a63ebca71c74127826a2e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429224"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>방법: SharePoint 기능 사용자 지정
  만들기 및 Visual Studio의 기능 디자이너를 사용 하 여 SharePoint 기능을 사용자 지정할 수 있습니다. 예를 들어, 기능 범위를 설정 하 고 다른 기능 종속성으로 추가할 수 있습니다. 기본적으로 기능 디자이너 솔루션 탐색기 또는 SharePoint 패키지 탐색기에서 새로운 기능을 추가 하면 열려 있습니다.

## <a name="opening-the-feature-designer"></a>기능 디자이너 열기
 추가 하거나 기능 디자이너를 사용 하는 기능을 SharePoint 프로젝트 항목을 제거할 수 있습니다.

#### <a name="to-open-the-feature-designer"></a>기능 디자이너를 열려면

1. **솔루션 탐색기**를 확장 하 고 **기능**합니다.

2. 두 번 클릭 합니다 *Feature1* , 항목을 선택 하거나 바로 가기 메뉴를 열고 합니다 *Feature1* 항목을 선택한 **뷰 디자이너**합니다.

## <a name="view-the-packaged-manifest-file"></a>패키지 매니페스트 파일을 보려면
 기능 디자이너를 사용 하 여 수정 하 고 기능에 대 한 패키지 매니페스트 파일을 생성할 수 있습니다 (*feature.xml*). 그런 다음 Visual Studio에서이 파일에 대 한 XML 코드를 볼 수 있습니다.

#### <a name="to-view-the-packaged-manifest-file"></a>패키지 매니페스트 파일을 보려면

1. 에 **기능 디자이너**를 선택 합니다 **매니페스트** 탭 합니다.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>솔루션 탐색기를 사용 하 여 패키지 된 매니페스트 파일을 보려면

1. **솔루션 탐색기**를 선택 합니다 **모든 파일 표시** 아이콘입니다.

2. 기능을 확장, FeatureName 확장, FeatureName.feature를 확장 한 다음 엽니다는  *\<FeatureName >. Template.xml 파일* 파일입니다.

    > [!NOTE]
    > 기능 템플릿을 매니페스트 XML 파일을 열면 파일을 자동으로 유효성을 검사 및 오류 목록 창에 표시 되는 경고를 무시할 수 있습니다.

## <a name="change-the-manifest-template"></a>매니페스트 템플릿을 변경합니다
 Visual Studio XML 편집기 또는 매니페스트 템플릿 창에서 기능 매니페스트 파일에 대 한 XML 코드를 변경할 수 있습니다. XML 코드를 변경 된 기능에 대 한 패키지 매니페스트 파일에 병합 됩니다. 예를 들어, 다음 기능 속성을 사용자 지정 매니페스트 템플릿을 변경 하는 것이 좋습니다.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML 편집기를 사용 하 여 매니페스트 템플릿을 변경 하려면

1. **기능 디자이너**, 선택는 **매니페스트** 탭을 확장 합니다 **옵션 편집** 노드를 선택한 후를 **XML 편집기에서 엽니다** 링크.

     변경 내용은 XML에 패키지 된 매니페스트 파일에 병합 됩니다.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>매니페스트 템플릿 창을 사용 하 여 매니페스트 템플릿을 변경 하려면

1. 에 **기능 디자이너**, 선택는 **매니페스트** 탭을 확장 하 고는 **옵션 편집** 노드를 선택한 후 변경 매니페스트 템플릿 창에 표시 되는 XML.

     변경 내용이 xml에 표시 된 **패키지 매니페스트 미리 보기** 창입니다.

## <a name="overwrite-the-packaged-manifest-file"></a>패키지 매니페스트 파일 덮어쓰기
 기능 디자이너를 사용 하지 않도록 설정 하 고 만들 수 있습니다 합니다 *feature.xml* 파일을 수동으로 백업 합니다. 처음으로이 절차를 수행 하는 기능 디자이너의 현재 설정은 기능 템플릿 XML 파일에 저장 됩니다. 그런 다음 수정 하거나 XML 코드를 덮어쓸 수 있습니다.

> [!NOTE]
> 를 추가 하거나 기능 디자이너를 사용 하지 않도록 설정 하는 동안 XML 파일에서 SharePoint 프로젝트 항목을 제거 하는 경우 이러한 프로젝트 항목 패키징되 지 않습니다.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>디자이너를 사용 하지 않도록 설정 하 여 패키지 매니페스트 파일을 덮어쓸 수

1. 에 **기능 디자이너**를 선택 합니다 **매니페스트** 탭 합니다.

2. 확장을 **옵션 편집** 노드를 선택 합니다 **덮어쓰기 생성 된 XML 및 편집 매니페스트 XML 편집기에서** 링크를 선택한 후는 **예** 단추.

     현재 패키지 매니페스트 파일을 사용 하 여 업데이트 됩니다.

## <a name="enable-the-feature-designer"></a>기능 디자이너를 사용 하도록 설정
 사용자 지정 기능 디자이너를 다시 활성화할 수 있습니다 합니다 *feature.xml* 파일입니다.

#### <a name="to-re-enable-the-designer"></a>디자이너를 다시 사용 하도록 설정

1. 에 **기능 디자이너**, 선택는 **매니페스트 편집 내용을 삭제 하 고 디자이너를 다시 설정** 링크를 선택한 후는 **예** 단추입니다.

2. 원본 텍스트를 사용 하 여 템플릿을 새로 고쳐집니다 및 XML의 변경 내용이 손실 됩니다.

## <a name="see-also"></a>참고자료
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
