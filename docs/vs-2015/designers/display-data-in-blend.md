---
title: Blend에서 데이터 표시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2ed51eaef8594695d4d594401ab9375563525b10
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294576"
---
# <a name="display-data-in-blend"></a>Blend에서 데이터 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

페이지의 레이아웃을 사용자 지정할 때 디자이너에서 예제 데이터를 볼 수 있습니다. 예제 데이터는 처음부터 새로 또는 기존 클래스를 사용하여 생성할 수 있습니다. 예제 데이터 실행 시 앱에 표시되는 *라이브 데이터* 에 연결할 수도 있습니다.

 **항목 내용:**

- [예제 데이터 생성](#Scratch)

- [클래스에서 예제 데이터 생성](#Existing)

- [WPF 애플리케이션에 라이브 데이터 표시](#LiveWPF)

- [스토어 또는 Phone 앱에 라이브 데이터 표시](#LiveStore)

## <a name="Scratch"></a> 예제 데이터 생성
 예제 데이터를 생성하려면 XAML 문서를 엽니다. In the **Data** panel, choose the **Create sample data**![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") button, and then choose **New Sample Data**.

 **데이터** 패널에서 데이터 구조를 정의한 다음 모든 페이지의 UI 요소에 바인딩합니다.

 ![](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png "496d7ebc-fe46-42f6-95a8-57b0e5be5d49")

 If you want your sample data to appear in your pages when you run the app, choose **Data source options** ![](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png "ae1fd260-4f84-420d-b196-45fde357d81d"), and then choose **Enable When Running Application**.

 ![](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png "05d5356d-91bb-4e6b-b3f7-29b76852c4b3")

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create sample data from scratch](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Mixing up some data binding with Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="Existing"></a> 클래스에서 예제 데이터 생성
 데이터 구조를 설명하는 클래스를 이미 만들었으면 이 클래스에서 예제 데이터를 생성할 수 있습니다.

 To generate sample data from a class, open a XAML document, and then in the **Data** panel, click the **Create sample data**![](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png "30540d76-7256-43ce-b5d9-4b2edf3d339f") button, and then click **Create Sample Data from Class**.

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create sample data from a class](https://channel9.msdn.com/Shows/Inside+Windows+Phone/IWP54--Windows-Phone-Data-Binding-and-the-Magic-of-XAML).

 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Mixing up some data binding with Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="LiveWPF"></a> WPF 애플리케이션에 라이브 데이터 표시
 **Watch a short video:** ![Configure Installed Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Create an XML data source](https://www.youtube.com/watch?v=RjQueappjqk&feature=youtube_gdata).

## <a name="LiveStore"></a> 스토어 또는 Phone 앱에 라이브 데이터 표시
 [데이터 및 파일(XAML) 작업](https://msdn.microsoft.com/library/windows/apps/xaml/br229562.aspx)을 참조하세요.

## <a name="see-also"></a>관련 항목:
 [Blend for Visual Studio를 사용하여 UI 만들기](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
