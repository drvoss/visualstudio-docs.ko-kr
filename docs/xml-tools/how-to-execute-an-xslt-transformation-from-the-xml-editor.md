---
title: XSLT 변환 실행
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fb4aee348ae48a2078f7803a44d4746d3dbacc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668802"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>방법: XML 편집기에서 XSLT 변환 실행

XML 편집기에서는 XSLT 스타일 시트를 XML 문서에 연결 하 고, 변환을 수행 하 고, 출력을 볼 수 있습니다. XSLT 변환의 결과로 나타나는 출력이 새 문서 창에 표시됩니다.

**Output** 속성은 출력의 파일 이름을 지정 합니다. **Output** 속성이 비어 있으면 임시 디렉터리에 파일 이름이 생성 됩니다. 파일 확장명은 스타일 시트의 `xsl:output` 요소를 기반으로 하며, 일 수 있습니다. *xml*,. *txt* 또는. *htm*.

**Output** 속성이를 사용 하 여 파일 이름을 지정 하는 경우입니다. *htm* 또는. *html* 확장 프로그램은 웹 브라우저를 사용 하 여 XSLT 출력을 미리 봅니다. 다른 모든 파일 확장명은 Visual Studio에서 선택한 기본 편집기를 사용 하 여 열립니다. 예를 들어 파일 확장명이 인 경우입니다. *xml*편집기를 사용 하 여 Visual Studio에서 xml 편집기를 사용 합니다.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>XML 파일에서 XSLT 변환 실행

1. Xml 편집기에서 XML 문서를 엽니다.

2. XSLT 스타일시트를 XML 문서에 연결합니다.

    - XML 문서에 `xml-stylesheet` 처리 명령을 추가합니다. 예를 들어 문서 프롤로그에 다음 줄을 추가 합니다. `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       또는

    - **속성** 창을 사용 하 여 XSLT 스타일 시트를 추가 합니다. 편집기에서 XML 파일을 연 상태에서 편집기의 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. **속성** 창에서 **스타일 시트** 필드를 클릭 하 고 찾아보기 단추 (...)를 선택 합니다. XSLT 스타일 시트를 선택 하 고 **열기**를 선택 합니다.

3. 메뉴 모음에서 **XML**  > **디버깅 하지 않고 XSLT를 시작**합니다 .를 선택 합니다. 또는 **Ctrl** +**alt** +**f5**키를 누릅니다.

   XSLT 변환의 출력이 새 문서 창에 표시 됩니다.

   > [!NOTE]
   > XML 문서에 연결된 스타일시트가 없을 경우 대화 상자에서 사용할 스타일시트를 지정하라는 메시지가 나타납니다.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT 스타일 시트에서 XSLT 변환 실행

1. XML 편집기에서 XSLT 스타일 시트를 엽니다.

2. 문서 **속성** 창의 **입력** 필드에 XML 문서를 지정 합니다.

   > [!NOTE]
   > XML 문서는 변환에 사용되는 입력 문서입니다. XSLT 변환을 시작할 때 문서를 지정 하지 않으면 **파일 열기** 대화 상자가 표시 되 고 해당 시점에 문서를 지정할 수 있습니다.

3. 메뉴 모음에서 **XML**  > **디버깅 하지 않고 XSLT를 시작**합니다 .를 선택 합니다. 또는 **Ctrl** +**alt** +**f5**키를 누릅니다.

   XSLT 변환의 출력이 새 문서 창에 표시 됩니다.

## <a name="specify-an-output-file-name"></a>출력 파일 이름을 지정 하십시오.

XML 및 XSL 파일의 출력 파일 이름을 지정할 수 있습니다. **속성** 창을 열고 **출력** 필드에 파일 이름을 지정 합니다.

## <a name="see-also"></a>참조

- [XML 편집기](../xml-tools/xml-editor.md)