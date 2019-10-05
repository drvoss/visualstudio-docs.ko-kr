---
title: 모듈을 사용 하 여 솔루션에 파일을 포함 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 569f1027163d5651d184254b4e6f57a02df2a39a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007843"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>모듈을 사용 하 여 솔루션에 파일을 포함
  새 마스터 페이지와 같은 해당 파일 형식에 관계 없이 SharePoint 서버에 파일을 배포 하려는 경우가 있습니다. 이 위해 사용할 수 있습니다 *모듈* (혼동 해서는 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 코드 모듈). 모듈은 SharePoint 솔루션의 파일에 대 한 컨테이너입니다. 솔루션을 배포 하면 모듈의 파일을 SharePoint 서버에서 지정된 된 된 폴더에 복사 됩니다.

## <a name="module-items-and-elements"></a>모듈 항목과 요소
 모듈을 만들려면 프로젝트에 추가 선택 하 여 합니다 **새 항목 추가** 대화 상자. 그런 다음 수정 해당 *Elements.xml* 파일 시스템에 그리고 SharePoint 서버에 복사 해야 하는 위치에 배포 하려는 파일의 이름을 포함 합니다.

 예로 *Elements.xml* 모듈에 대 한 파일:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 다음 기본 파일을 포함 하는 새로 만든 모듈:

|파일 이름|설명|
|---------------|-----------------|
|*Elements.xml*|모듈 정의 파일입니다.|
|*Sample.txt*|모듈에 있는 파일의 예제로 사용 되는 자리 표시자 파일입니다.|

 합니다 *Elements.xml* 파일에는 다음 요소가 포함 되어 있습니다.

|요소 이름|설명|
|------------------|-----------------|
|요소|모든 모듈에 정의 된 요소를 포함 합니다.|
|Module|모듈 요소에는 단일 특성인 *이름*, 형식에서 모듈의 이름을 지정 하는 `<Module Name="Module1">`합니다.<br /><br /> 모듈의 이름을 변경한 경우 (또는 해당 *폴더 이름을* 속성), Module 요소의 이름을 수동으로 업데이트 해야 합니다.<br /><br /> 모듈 요소에서 파일에 대 한 하위 디렉터리를 지정 하는 경우 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) 자동으로에 일치 하는 디렉터리 구조를 만듭니다.|
|파일|File 요소에 두 개의 매개 변수 *경로* 하 고 *Url*합니다.<br /><br /> 경로: SharePoint 솔루션 파일의 위치와 이름입니다. 형식 인지 `Path="Module1\Sample.txt"`합니다.<br /><br /> -Url: SharePoint 서버에서 파일을 배포할 위치입니다. 형식 인지 `Url="Module1/Sample.txt"`합니다.<br /><br /> 형식: 두 설정이 포함 된 선택적 특성: *GhostableInLibrary* 하 고 *Ghostable*합니다. 형식 인지 `Type="GhostableInLibrary"`합니다. 지정 *GhostableInLibrary* 라이브러리에 추가 될 때 파일을 함께 목록 항목을 함께 SharePoint의 문서 라이브러리에 파일을 추가할 것을 의미 합니다. 지정 *Ghostable* 파일을 SharePoint 문서 라이브러리 외부로 추가할 수 있습니다.|

 배포 하려는 각 파일에는 별도 필요한 `<File>` 의 요소 항목 *Elements.xml*합니다.

## <a name="see-also"></a>참고자료
- [방법: 모듈을 사용 하 여 파일 포함](../sharepoint/how-to-include-files-by-using-a-module.md)
- [어떻게: 파일을 프로 비전](http://go.microsoft.com/fwlink/?LinkID=144271)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint를 위한 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
