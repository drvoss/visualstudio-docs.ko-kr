---
title: 데이터에 Windows Forms 컨트롤 바인딩
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 07c5853b673657c3ce8e90467a13bbac3f430b6e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698981"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms에 데이터를 바인딩하여 응용 프로그램의 사용자에 게 데이터를 표시할 수 있습니다. 이러한 데이터 바인딩된 컨트롤을 만들려면에서 항목을 이동할 수는 **데이터 원본** Visual Studio에서 Windows Forms 디자이너 창. 이 항목에서는 가장 일반적인 작업, 도구 및 데이터 바인딩된 Windows Forms 응용 프로그램을 만드는 데 관련 된 클래스의 일부를 설명 합니다.

 ![데이터 원본으로 작업을 끌어](../data-tools/media/raddata-data-source-drag-operation.png "raddata 데이터 원본 끌기 작업")

 Visual Studio에서 데이터 바인딩된 컨트롤을 만드는 방법에 대 한 일반 정보를 참조 하세요. [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)합니다. Windows Forms의 데이터 바인딩에 대 한 자세한 내용은 참조 하세요. [Windows Forms 데이터 바인딩](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)합니다.

## <a name="in-this-section"></a>단원 내용

- [데이터에 Windows Forms컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data.md)

- [데이터 바인딩된 컨트롤에서 데이터를 저장하기 전에 In-Process 편집 커밋](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Windows Forms 애플리케이션에서 조회 테이블 만들기](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [데이터 검색을 위한 Windows Form 만들기](../data-tools/create-a-windows-form-to-search-data.md)

- [단순 데이터 바인딩을 지원하는 Windows Forms 사용자 정의 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [복합 데이터 바인딩을 지원하는 Windows Forms 사용자 정의 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [조회 데이터 바인딩을 지원하는 Windows Forms 사용자 정의 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [폼 간에 데이터 전달](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource 구성 요소
 <xref:System.Windows.Forms.BindingSource> 구성 요소는 두가지 용도로 사용됩니다. 첫째, 폼의 컨트롤에 데이터 바인딩할 때 추상화 계층을 제공 합니다. 폼의 컨트롤에 바인딩된는 <xref:System.Windows.Forms.BindingSource> (데이터 원본에 직접 바인딩되는) 대신 구성 요소입니다.

 둘째,이 개체의 컬렉션을 관리할 수 있습니다. 에 형식을 추가 합니다 <xref:System.Windows.Forms.BindingSource> 해당 형식의 목록을 만듭니다.

 에 대 한 자세한 내용은 <xref:System.Windows.Forms.BindingSource> 구성 요소를 참조 하세요.

- [BindingSource 구성 요소](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [BindingSource 구성 요소 개요](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [BindingSource 구성 요소 아키텍처](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator 컨트롤
 이 구성 요소는 Windows 응용 프로그램에서 표시 되는 데이터를 탐색 하기 위한 사용자 인터페이스를 제공 합니다. 자세한 내용은 [BindingNavigator 컨트롤](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e)을 참조하세요.

## <a name="datagridview-control"></a>DataGridView 컨트롤
 사용을 표시 하 고 다양 한 종류의 데이터 원본에서 테이블 형식 데이터를 편집 합니다 <xref:System.Windows.Forms.DataGridView> 제어 합니다. 데이터를 바인딩할 수 있습니다는 <xref:System.Windows.Forms.DataGridView> 를 사용 하 여는 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 속성입니다. 자세한 내용은 [DataGridView 컨트롤 개요](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488)합니다.

## <a name="see-also"></a>참고 항목
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
