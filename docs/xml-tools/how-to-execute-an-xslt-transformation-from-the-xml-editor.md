---
title: XSLT 변환 실행
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001942"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>방법: XML 편집기에서 XSLT 변환 실행

XML 편집기에서 XSLT 스타일 시트를 XML 문서를 사용 하 여 연결 하 고, 변환 수행 하 고, 출력을 볼 수 있습니다. XSLT 변환의 결과로 나타나는 출력이 새 문서 창에 표시됩니다.

합니다 **출력** 속성 출력 파일 이름을 지정 합니다. 경우는 **출력** 속성을 비워 두면를 임시 디렉터리에 파일 이름이 생성 됩니다. 파일 확장명을 기반으로 합니다 `xsl:output` 스타일에서 요소 수 고. *xml*합니다. *txt* 또는. *htm*합니다.

경우는 **출력** 사용 하는 파일을 지정 하는 속성을. *htm* 또는. *html* 확장 XSLT 출력은 웹 브라우저를 사용 하 여 미리 보기. 다른 모든 파일 확장명은 Visual Studio에서 선택한 기본 편집기를 사용 하 여 열립니다. 예를 들어 다음과 같이 파일 확장명은. *xml*, Visual Studio XML 편집기를 사용 합니다.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>XML 파일에서 XSLT 변환 실행

1. XML 편집기에서 XML 문서를 엽니다.

2. XSLT 스타일시트를 XML 문서에 연결합니다.

    - XML 문서에 `xml-stylesheet` 처리 명령을 추가합니다. 예를 들어, 문서 프롤로그에 다음 줄을 추가 합니다. `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       또는

    - 사용 하 여 XSLT 스타일 시트를 추가 합니다 **속성** 창입니다. 편집기에에서 열려 있는 XML 파일을 사용 하 여 편집기의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**합니다. 에 **속성** 창 합니다 **스타일 시트** 필드 및 찾아보기 단추 (...)를 선택 합니다. XSLT 스타일 시트를 선택 하 고 선택한 **열려**합니다.

3. 메뉴 모음에서 선택 **XML** > **디버깅 하지 않고 XSLT 시작**합니다. 또는 키를 누릅니다 **Ctrl**+**Alt**+**F5**합니다.

   XSLT 변환의 출력은 새 문서 창에 표시 됩니다.

   > [!NOTE]
   > XML 문서에 연결된 스타일시트가 없을 경우 대화 상자에서 사용할 스타일시트를 지정하라는 메시지가 나타납니다.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT 스타일 시트에서 XSLT 변환 실행

1. XML 편집기에서 XSLT 스타일 시트를 엽니다.

2. XML 문서를 지정 합니다 **입력** 문서의 필드 **속성** 창입니다.

   > [!NOTE]
   > XML 문서는 변환에 사용되는 입력 문서입니다. XSLT 변환을 시작 되 면 문서를 지정 하지 않으면 합니다 **파일 열기** 대화 상자가 나타나고 해당 시점에 문서를 지정할 수 있습니다.

3. 메뉴 모음에서 선택 **XML** > **디버깅 하지 않고 XSLT 시작**합니다. 또는 키를 누릅니다 **Ctrl**+**Alt**+**F5**합니다.

   XSLT 변환의 출력은 새 문서 창에 표시 됩니다.

## <a name="specify-an-output-file-name"></a>출력 파일 이름을 지정 합니다.

XML 및 XSL 파일에 대 한 출력 파일 이름을 지정할 수 있습니다. 열기는 **속성** 창에 파일 이름을 지정 합니다 **출력** 필드.

## <a name="see-also"></a>참고자료

- [XML 편집기](../xml-tools/xml-editor.md)