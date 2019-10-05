---
title: 전역화 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781ff1e1c7d389baa43a54ee4413280f105ac1e1
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714996"
---
# <a name="globalization-warnings"></a>전역화 경고
전역화 경고에 대비한 라이브러리 및 응용 프로그램을 지원합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1300: MessageBoxOptions를 지정 합니다.](../code-quality/ca1300-specify-messageboxoptions.md)|오른쪽에서 왼쪽으로 읽기 순서를 사용하는 문화권에 대해 메시지 상자를 올바로 표시하려면 MessageBoxOptions 열거형의 RightAlign 및 RtlReading 멤버를 Show 메서드로 전달해야 합니다.|
|[CA1301: 중복 액셀러레이터를 방지 합니다.](../code-quality/ca1301-avoid-duplicate-accelerators.md)|액셀러레이터 키라고도 하는 선택키를 사용하면 Alt 키를 사용하여 키보드로 컨트롤에 액세스할 수 있습니다. 여러 컨트롤에는 중복 되는 선택키가 있으면, 액세스 키의 동작이 잘 정의 되지 않습니다.|
|[CA1302: 로캘별 문자열을 하드 코딩 하지 마십시오](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|System.Environment.SpecialFolder 열거형에는 특수 시스템 폴더를 참조하는 멤버가 포함되어 있습니다. 이러한 폴더의 위치는 운영 체제에 따라 값이 다를 수 있으며, 사용자가 위치 일부를 변경할 수 있고, 위치는 지역화됩니다. Environment.GetFolderPath 메서드는 Environment.SpecialFolder 열거형, 지역화 및 현재 실행 중인 컴퓨터에 대 한 적절 한 연관 된 위치를 반환 합니다.|
|[CA1303: 리터럴을 지역화 된 매개 변수로 전달 하지 마십시오](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|외부에 표시 되는 메서드는 문자열 리터럴 매개 변수로 전달.NET 생성자 또는 메서드를 하 고 해당 문자열은 지역화 될 수 있어야 합니다.|
|[CA1304: CultureInfo를 지정 합니다.](../code-quality/ca1304-specify-cultureinfo.md)|메서드 또는 생성자가 System.Globalization.CultureInfo 매개 변수를 받아들이는 오버로드가 있는 멤버를 호출하지만 CultureInfo 매개 변수를 사용하는 오버로드는 호출하지 않습니다. CultureInfo 또는 System.IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다.|
|[CA1305: IFormatProvider를 지정 합니다.](../code-quality/ca1305-specify-iformatprovider.md)|메서드 또는 생성자가 System.IFormatProvider 매개 변수를 받아들이는 오버로드가 있는 하나 이상의 멤버를 호출하지만 IFormatProvider 매개 변수를 사용하는 오버로드는 호출하지 않습니다. System.Globalization.CultureInfo 또는 IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다.|
|[CA1306: 데이터 형식에 대 한 로캘을 설정 하십시오.](../code-quality/ca1306-set-locale-for-data-types.md)|로캘은 숫자 값에 사용되는 서식, 통화 기호 및 정렬 순서 등과 같은 데이터의 문화권별 표현 요소를 결정합니다. DataTable 또는 DataSet를 만들 때는 로캘을 명시적으로 설정해야 합니다.|
|[CA1307: StringComparison 지정](../code-quality/ca1307-specify-stringcomparison.md)|문자열 비교 작업에서 StringComparison 매개 변수를 설정하지 않는 메서드 오버로드를 사용합니다.|
|[CA1308: 문자열을 대문자로 정규화 하십시오.](../code-quality/ca1308-normalize-strings-to-uppercase.md)|문자열은 대문자로 정규화되어야 합니다. 일부 문자는 소문자로 변환될 때 다시 대문자로 변환될 수 없습니다.|
|[CA1309: 서 수 StringComparison 사용](../code-quality/ca1309-use-ordinal-stringcomparison.md)|비언어 문자열 비교 작업에서는 StringComparison 매개 변수를 Ordinal 또는 OrdinalIgnoreCase로 설정하지 않습니다. 매개 변수가 명시적으로 StringComparison.Ordinal 또는 StringComparison.OrdinalIgnoreCase로 설정되기 때문에 코드 실행 속도, 정확도 및 신뢰도가 향상됩니다.|
|[CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|플랫폼 호출 멤버가 부분적으로 신뢰할 수 있는 호출자에 대 한 문자열 매개 변수가 있으며 문자열을 명시적으로 마샬링하지 않습니다. 이렇게 하면 보안상 위험할 수 있습니다.|