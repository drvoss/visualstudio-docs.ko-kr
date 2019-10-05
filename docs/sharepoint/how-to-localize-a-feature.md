---
title: '방법: 기능 지역화 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f6e796cc00478ee823c345fd02738f8677c36373
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813669"
---
# <a name="how-to-localize-a-feature"></a>방법: 기능 지역화
  기능 제목 및 설명을 기본적으로 하드 코드 된 문자열 값을 사용합니다. 기능 제목 및 설명을 지역화 하려면 지역화 된 리소스를 참조 하는 식을 사용 하 여 문자열을 대체 합니다.

## <a name="localize-a-feature"></a>기능 지역화

#### <a name="to-localize-a-feature"></a>기능을 지역화 하려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **Feature1** 노드를 선택한 후 **기능 리소스 추가**합니다.

2. 에 **리소스 추가** 대화 상자에서 **고정 언어** 기본 언어 기능 리소스 파일에 대 한 문화권에 따라 목록에서.

3. 지역화된 언어마다 이전 단계를 반복하여 지역화된 기능 리소스 파일에 대해 선택한 언어를 선택합니다.

     기본 언어와 지원할 지역화된 언어마다 하나씩 별도의 기능 리소스 파일이 만들어집니다.

4. 리소스 편집기에서 각 리소스 파일을 연 다음 문자열 ID와 그 값을 모두 입력합니다.

     예를 들어 기본 기능 리소스 파일의 문자열 ID를 입력 **제목** 값으로 **내 기능 제목의**, 및 두 번째 문자열의 ID **설명** 값 **내 기능 설명**합니다. 지역화된 각 리소스 파일에 대해 기본 기능 리소스에서 사용된 동일한 문자열 ID를 사용하지만 값의 지역화된 문자열을 입력합니다.

5. 모든 리소스 값을 입력 한 후 기능에 대 한 바로 가기 메뉴를 열고 (예를 들어 *Feature1.feature*)를 선택한 후 **뷰 디자이너** 기능 기능 디자이너에서 열려면 합니다.

6. 지역화 하는 **제목** 및 **설명** 기능에서 필드 형식을 사용 하 여 다음 해당 상자에 값을 입력 합니다.

     `$Resources:` *String ID*

     $Resources 예를 들어, 입력:**제목** 에 **기능 제목** 상자 및 $Resources:**설명을** 에 **기능 설명** 상자 .

     문자열 ID는 리소스 파일에서 사용되는 것과 일치해야 합니다.

7. 선택 된 **F5** 키를 빌드하고 응용 프로그램을 실행 합니다.

8. SharePoint에서 엽니다는 **사이트 작업** 메뉴에서 선택 **사이트 설정**를 선택한 후는 **사이트 작업** 섹션을 선택 합니다 **사이트 기능 관리** 링크.

9. Sharepoint의 기본값과에서 표시 언어를 변경 합니다.

     지역화 기능 제목 및 설명에는 응용 프로그램에 나타납니다. 지역화 된 리소스를 표시 하려면 SharePoint 서버에 리소스 파일의 문화권과 일치 하는 언어 팩 설치 되어 있어야 합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)
- [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)
- [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)
