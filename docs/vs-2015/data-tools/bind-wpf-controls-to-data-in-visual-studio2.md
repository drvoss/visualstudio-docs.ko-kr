---
title: 데이터에 WPF 컨트롤 바인딩 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e37d17cbe67bd1e4e64e306831f38996a7f93c80
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697964"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio에서 데이터에 WPF 컨트롤 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 바인딩된을 만들 수 있습니다 [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] 를 사용 하 여 컨트롤을 **데이터 원본** 창입니다. 먼저 데이터 소스를 추가 합니다 **데이터 원본** 창입니다. 다음 항목을 끌어를 **데이터 원본** 창에는**WPF 디자이너**.

## <a name="adding"></a> 데이터 소스 창에 데이터 소스 추가
 데이터 바인딩된 컨트롤을 만들 수 있습니다, 전에 먼저 데이터 소스를를 추가 해야 합니다 **데이터 원본** 창입니다.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>데이터 소스 창에 데이터 소스를 추가하려면

1. 에 **보기** 메뉴에서 **기타 Windows**를 클릭 하 고 **데이터 원본**합니다.

2. **새 데이터 원본 추가**를 클릭하고 **데이터 원본 구성 마법사** 완료합니다.

3. 다음 작업 중 하나를 수행하여 데이터 바인딩된 컨트롤을 만듭니다.

    - [데이터의 단일 필드에 바인딩되는 컨트롤 만들기](#simple)합니다.

    - [데이터의 여러 필드에 바인딩되는 컨트롤 만들기](#complex)합니다.

    - [여러 데이터 필드에 바인딩되는 컨트롤 집합을 만들기](#details)합니다.

    - [디자이너에서 기존 컨트롤에 데이터 바인딩](#existing)합니다.

## <a name="simple"></a> 데이터의 단일 필드에 바인딩되는 컨트롤 만들기
 데이터 소스를 추가한 후 합니다 **데이터 원본** 창에서 같은 데이터의 단일 필드를 표시 하는 새 데이터 바인딩된 컨트롤을 만들 수 있습니다는 <xref:System.Windows.Controls.ComboBox> 또는 <xref:System.Windows.Controls.TextBox>합니다.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>단일 데이터 필드에 바인딩되는 컨트롤을 만들려면

1. 에 **데이터 원본** 창에서 테이블 또는 개체를 나타내는 항목을 확장 합니다. 바인딩할 열이나 속성을 나타내는 자식 항목을 찾습니다. 시각적 예제를 참조 하세요 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)합니다.

2. 원하는 경우 만들 컨트롤을 선택합니다. 각 항목에는 **데이터 원본** 창 디자이너로 항목을 끌 때 만들어지는 기본 컨트롤이 있습니다. 기본 컨트롤은 항목의 기본 데이터 형식에 따라 달라집니다.

     다른 컨트롤을 선택하려면 항목 옆의 드롭다운 화살표를 클릭하고 컨트롤을 선택합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.

3. 디자이너에서 유효한 컨테이너로 항목을 끕니다. 유효한 컨테이너에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 만들고 새 데이터 바인딩된 컨트롤을 적절 한 제목의 <xref:System.Windows.Controls.Label> 컨테이너에 있습니다. 또한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]는 컨트롤을 데이터에 바인딩하기 위한 코드와 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]도 생성합니다. 자세한 내용은 [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

## <a name="complex"></a> 여러 데이터 필드에 바인딩되는 컨트롤 만들기
 데이터 소스를 추가한 후 합니다 **데이터 원본** 창에서 같은 데이터의 여러 필드를 표시 하는 새 데이터 바인딩된 컨트롤을 만들 수 있습니다는 <xref:System.Windows.Controls.DataGrid> 또는 <xref:System.Windows.Controls.ListView>합니다.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>여러 데이터 필드에 바인딩되는 컨트롤을 만들려면

1. 에 **데이터 원본** 창에서 테이블 또는 개체를 나타내는 항목을 선택 합니다. 시각적 예제를 참조 하세요 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)합니다.

2. 원하는 경우 만들 컨트롤을 선택합니다. 기본적으로 각 항목에 **데이터 원본** create로 설정 된 데이터 테이블 또는 개체를 나타내는 창을 <xref:System.Windows.Controls.DataGrid> (프로젝트가.NET Framework 4를 대상으로) 하는 경우 또는 <xref:System.Windows.Controls.ListView> (.NET Framework의 이전 버전)에 대 한 합니다.

     다른 컨트롤을 선택하려면 항목 옆의 드롭다운 화살표를 클릭하고 컨트롤을 선택합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.

    > [!NOTE]
    > 특정 열이나 속성을 표시하지 않으려면 항목을 확장하여 해당 자식을 표시합니다. 열 이나 속성을 표시 한 다음 클릭 하지 않으려면는 옆에 있는 드롭다운 화살표를 클릭 **None**합니다.

3. <xref:System.Windows.Controls.Grid>와 같은 디자이너의 유효한 컨테이너로 항목을 끌어 옵니다. 유효한 컨테이너에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 컨테이너에 새 데이터 바인딩된 컨트롤을 만듭니다. 또한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]는 컨트롤을 데이터에 바인딩하기 위한 코드와 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]도 생성합니다. 자세한 내용은 [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

## <a name="details"></a> 여러 데이터 필드에 바인딩되는 컨트롤 집합 만들기
 데이터 소스를 추가한 후 합니다 **데이터 원본** 창 컨트롤의 집합에 데이터 테이블이 나 개체를 바인딩할 수 있습니다. 테이블이나 개체의 각 열 또는 속성에 대해 서로 다른 컨트롤이 만들어집니다.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>여러 데이터 필드에 바인딩되는 컨트롤 집합을 만들려면

1. 에 **데이터 원본** 창에서 테이블 또는 개체를 나타내는 항목을 선택 합니다. 시각적 예제를 참조 하세요 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)합니다.

2. 선택한 항목 옆의 드롭다운 화살표를 클릭 **세부 정보**합니다.

    > [!NOTE]
    > 특정 열이나 속성을 표시하지 않으려면 항목을 확장하여 해당 자식을 표시합니다. 열 이나 속성을 표시 한 다음 클릭 하지 않으려면는 옆에 있는 드롭다운 화살표를 클릭 **None**합니다.

3. <xref:System.Windows.Controls.Grid>와 같은 디자이너의 유효한 컨테이너로 항목을 끌어 옵니다. 유효한 컨테이너에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 새 데이터 바인딩된 컨트롤을 컨테이너에 만듭니다. 각 컨트롤은 적절한 제목을 가진 <xref:System.Windows.Controls.Label> 컨트롤과 함께 서로 다른 열이나 속성에 바인딩됩니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 데이터에 컨트롤을 바인딩하는 코드와 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]도 생성합니다. 자세한 내용은 [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

## <a name="existing"></a> 디자이너에서 기존 컨트롤에 Binddata
 데이터 소스를 추가한 후 합니다 **데이터 원본** 창 디자이너에서 기존 컨트롤에 바인딩할 데이터를 추가할 수 있습니다.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>디자이너의 기존 컨트롤에 데이터를 바인딩하려면

1. 에 **데이터 원본** 창에서 다음 절차 중 하나를 사용 합니다.

    - <xref:System.Windows.Controls.DataGrid> 또는 <xref:System.Windows.Controls.ListView>와 같이 여러 데이터 필드를 표시하는 기존 컨트롤에 대한 데이터 바인딩을 추가하려면 컨트롤에 바인딩할 테이블이나 개체를 나타내는 항목을 선택합니다.

    - <xref:System.Windows.Controls.ComboBox> 또는 <xref:System.Windows.Controls.TextBox>와 같이 단일 데이터 필드를 표시하는 기존 컨트롤에 대한 데이터 바인딩을 추가하려면 데이터가 포함된 테이블 또는 개체를 나타내는 항목을 확장한 다음 컨트롤에 바인딩할 데이터를 나타내는 항목을 선택합니다.

2. 선택한 항목을 끌어 합니다 **데이터 원본** 디자이너에서 기존 컨트롤에 창. 컨트롤은 유효한 놓기 대상이어야 합니다. 자세한 내용은 [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 생성 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 및 데이터에 컨트롤을 바인딩하는 코드입니다. 자세한 내용은 [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.

    > [!NOTE]
    > 컨트롤이 이미 데이터에 바인딩된 경우 컨트롤의 데이터 바인딩이 가장 최근에 컨트롤로 끌어 온 항목으로 다시 설정됩니다.

## <a name="see-also"></a>참고 항목
 [Visual Studio에서 데이터에 WPF 컨트롤을 바인딩할](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [WPF 응용 프로그램에서 조회 테이블 만들기](../data-tools/create-lookup-tables-in-wpf-applications.md) [WPF 응용 프로그램에서 관련된 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md) [데이터집합에바인딩할WPF컨트롤](../data-tools/bind-wpf-controls-to-a-dataset.md) [WCF 데이터 서비스에 WPF 바인딩 컨트롤](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [연습: WPF 응용 프로그램에서 관련된 데이터 표시](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
