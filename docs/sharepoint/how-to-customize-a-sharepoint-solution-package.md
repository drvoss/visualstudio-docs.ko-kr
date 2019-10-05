---
title: '방법: SharePoint 솔루션 패키지 사용자 지정 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
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
ms.openlocfilehash: 0aa124d25e279b7e44292645d81d80829f5d3f8f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420193"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>방법: SharePoint 솔루션 패키지 사용자 지정
  패키지 디자이너를 사용 하 여를 만들고 패키지를 사용자 지정할 수 있습니다 (*.wsp*). 예를 들어 웹 서버의 솔루션이 배포 될 때 다시 설정 및 배포 서버 유형을 설정 하는 경우 지정할에 SharePoint 프로젝트 항목 및 기능을 추가할 수 있습니다.

## <a name="open-the-package-designer"></a>패키지 디자이너를 열으십시오

#### <a name="to-open-the-package-designer"></a>패키지 디자이너를 열려면

- **솔루션 탐색기**를 두 번 클릭 **패키지**를 선택 하거나 **뷰 디자이너** 에 대 한 바로 가기 메뉴에서 **패키지**.

## <a name="view-the-packaged-manifestffile"></a>패키지에 포함 된 manifestfFile 보기
 수정 하 고 패키지 매니페스트 파일을 생성할 패키지 디자이너를 사용할 수 있습니다. 그런 다음 Visual Studio에서이 파일에 대 한 XML 코드를 볼 수 있습니다.

#### <a name="to-view-the-xml-source-file"></a>XML 소스 파일을 보려면

1. 에 **패키지 디자이너**, 선택 **매니페스트**합니다.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>솔루션 탐색기를 사용 하 여 패키지 된 매니페스트 파일을 보려면

1. **솔루션 탐색기**에서 **모든 파일 표시**를 선택합니다.

2. 패키지를 확장 하 고 패키지를 확장 한 다음이 엽니다는 *Package.Template.xml* 파일입니다.

    > [!NOTE]
    > 패키지 템플릿에 대 한 매니페스트 XML 파일을 열면 파일을 자동으로 확인 되 면 및 오류 목록 창에 표시 되는 경고를 무시할 수 있습니다.

## <a name="change-the-manifest-template"></a>매니페스트 템플릿을 변경합니다
 Visual Studio XML 편집기에서 매니페스트 템플릿 창에 패키지 된 매니페스트 파일에 대 한 XML 코드를 변경할 수 있습니다. XML 코드를 변경 된 패키지에 대 한 패키지 매니페스트 파일에 병합 됩니다.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML 편집기를 사용 하 여 매니페스트 템플릿을 변경 하려면

1. **패키지 디자이너**, 선택는 **매니페스트** 탭을 확장 합니다 **옵션 편집** 노드를 선택한 후를 **XML 편집기에서 엽니다** 링크.

     변경 내용은 XML에 패키지 된 매니페스트 파일에 병합 됩니다.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>매니페스트 템플릿 창을 사용 하 여 매니페스트 템플릿을 변경 하려면

1. 에 **패키지 디자이너**, 선택는 **매니페스트** 탭을 확장 하 고는 **옵션 편집** 노드를 선택한 후 변경 매니페스트 템플릿 창에 표시 되는 XML.

     변경 내용이 xml에 표시 된 **패키지 매니페스트 미리 보기** 창입니다.

## <a name="overwrite-the-packaged-manifest-file"></a>패키지 매니페스트 파일 덮어쓰기
 패키지 디자이너를 사용 하지 않도록 설정 하 고 만들 수 있습니다 합니다 *manifest.xml* 파일을 수동으로 백업 합니다. 이 절차를 수행 하는 처음으로 패키지 디자이너의 현재 설정은 패키지 템플릿 XML 파일에 저장 됩니다. 그런 다음 수정 하거나 XML 코드를 덮어쓸 수 있습니다.

> [!NOTE]
> 를 추가 하거나 패키지 디자이너를 사용 하지 않도록 설정 하는 동안 XML 파일에서 SharePoint 프로젝트 항목 및 기능을 제거 하는 경우 이러한 프로젝트 항목 및 기능은 패키지 되지 않습니다.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>디자이너를 사용 하지 않도록 설정 하 여 패키지 매니페스트 파일을 덮어쓸 수

1. 에 **패키지 디자이너**를 선택 합니다 **매니페스트** 탭 합니다.

2. 확장을 **옵션 편집** 노드를 선택 합니다 **덮어쓰기 생성 된 XML 및 편집 매니페스트 XML 편집기에서** 링크를 선택한 후는 **예** 단추.

     현재 패키지 매니페스트 파일을 사용 하 여 업데이트 됩니다.

## <a name="enable-the-package-designer"></a>패키지 디자이너를 사용 하도록 설정
 사용자 지정 하는 패키지 디자이너를 다시 활성화할 수 있습니다 합니다 *manifest.xml* 파일입니다.

#### <a name="to-re-enable-the-designer"></a>디자이너를 다시 사용 하도록 설정

1. 에 **패키지 디자이너**, 선택는 **매니페스트 편집 내용을 삭제 하 고 디자이너를 다시 설정** 링크를 선택한 후는 **예** 단추입니다.

     원본 텍스트를 사용 하 여 템플릿을 새로 고쳐집니다 및 XML의 변경 내용이 손실 됩니다.

## <a name="see-also"></a>참고자료
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
