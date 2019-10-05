---
title: '방법: LinqToXmlDataBinding 예제 빌드 및 실행'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d53f8d08222eb35660f7a4454164d6b821a976d9
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714839"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>방법: LinqToXmlDataBinding 예제 빌드 및 실행

이 항목에서는 LinqToXmlDataBinding Visual Studio 프로젝트를 만들고 실행하는 방법과 생성되는 LinqToXmlDataBinding WPF(Windows Presentation Foundation) 예제 프로그램을 실행하는 방법을 보여 줍니다.

Visual Studio에 대한 자세한 내용은 [Visual Studio IDE 개요](../get-started/visual-studio-ide.md)를 참조하세요.

## <a name="create-the-project"></a>프로젝트를 만듭니다.

1. Visual Studio를 열고 이름이 **LinqToXmlDataBinding**인 C# **WPF 앱**을 만듭니다.

   프로젝트는 .NET Framework 3.5 이상을 대상으로 지정해야 합니다.

1. 이미 존재하지 않는 경우 다음 .NET 어셈블리에 대한 프로젝트 참조를 추가합니다.

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. **Ctnrl**+**Shift**+**B**를 눌러 솔루션을 빌드한 다음, **F5**를 눌러 솔루션을 실행합니다. 프로젝트가 오류 없이 컴파일되고 일반 WPF 애플리케이션으로 실행됩니다.

## <a name="add-code-to-the-project"></a>프로젝트에 코드 추가

1. **솔루션 탐색기**에서 소스 파일 **Window1.xaml**의 이름을 **L2XDBForm.xaml**로 바꿉니다. 종속 원본 파일 **Window1.xaml.cs**의 이름이 **L2XDBForm.xaml.cs**로 자동으로 바뀝니다.

1. **L2XDBForm.xaml** 파일의 소스 코드를 [L2DBForm.xaml 소스 코드](../designers/l2dbform-xaml-source-code.md) 항목의 코드 섹션으로 바꿉니다. 이 파일 작업을 하려면 XAML 소스 뷰를 사용하세요.

1. 위와 마찬가지로 **L2XDBForm.xaml.cs** 파일의 소스를 [L2DBForm.xaml.cs 소스 코드](../designers/l2dbform-xaml-cs-source-code.md)에 있는 코드로 바꿉니다.

1. **App.xaml** 파일에서 모든 `Window1.xaml` 문자열을 `L2XDBForm.xaml`로 바꿉니다.

1. **Ctrl**+**Shift**+**B**를 눌러 솔루션을 빌드합니다.

## <a name="run-the-program"></a>프로그램 실행

LinqToXmlDataBinding 프로그램을 사용하여 포함된 XML 요소로 저장된 책 목록을 보고 조작할 수 있습니다.

### <a name="to-run-the-program-and-view-the-book-list"></a>프로그램을 실행하고 책 목록을 보려면

**F5**(**디버깅 시작**) 또는 **Ctrl**+**F5**(**디버그하지 않고 시작**)를 눌러 LinqToXmlDataBinding을 실행합니다. **LINQ to XML을 사용한 WPF 데이터 바인딩**이라는 제목의 프로그램 창이 나타납니다.

- UI의 맨 위 섹션에 책 목록을 나타내는 원시 **XML**이 표시됩니다. 이 섹션은 마우스나 키보드를 통해 조작할 수 없도록 하는 WPF <xref:System.Windows.Controls.TextBlock> 컨트롤을 사용하여 표시됩니다.

- **Book List**라는 두 번째 세로 섹션에는 일반 텍스트로 정렬된 책 목록이 표시됩니다. 이 섹션에는 마우스나 키보드를 통해 선택할 수 있도록 하는 <xref:System.Windows.Controls.ListBox> 컨트롤이 사용됩니다.

### <a name="to-add-and-delete-books-from-the-list"></a>목록에서 책을 추가하고 삭제하려면

- 새 책을 목록에 추가하려면 마지막 **Add New Book** 섹션에서 **ID** 및 **Value**<xref:System.Windows.Controls.TextBox> 컨트롤에 값을 입력하고 **Add Book** 단추를 클릭합니다. 책이 책 목록과 XML 목록에 모두 추가됩니다. 이 프로그램에서는 입력 값의 유효성을 검사하지 않습니다.

- 목록에서 기존 책을 삭제하려면 **Book List** 섹션에서 책을 선택한 다음 **Remove Selected Book** 단추를 클릭합니다. 해당 책 항목이 책 목록과 원시 XML 소스 목록에서 모두 제거됩니다.

### <a name="to-edit-an-existing-book-entry"></a>기존 책 항목을 편집하려면

1. 두 번째 **Book List** 섹션에서 책 항목을 선택합니다. 현재 값이 세 번째 **Edit Selected Book** 섹션에 표시됩니다.

1. 키보드를 사용하여 값을 편집합니다. <xref:System.Windows.Controls.TextBox> 컨트롤이 포커스를 잃으면 변경 사항이 즉시 XML 소스 목록과 책 목록에 자동으로 전파됩니다.

## <a name="see-also"></a>참고 항목

- [LINQ to XML 예제를 사용한 WPF 데이터 바인딩](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [연습: LinqToXmlDataBinding 예제](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Visual Studio IDE 개요](../get-started/visual-studio-ide.md)