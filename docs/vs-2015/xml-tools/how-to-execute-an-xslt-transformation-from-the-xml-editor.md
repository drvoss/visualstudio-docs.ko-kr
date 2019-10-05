---
title: '방법: XML 편집기에서 XSLT 변형을 실행 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8085864ebdb73e8233322a2f91a044dec95dc126
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431046"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>방법: XML 편집기에서 XSLT 변환 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 편집기에서 XSLT 스타일시트를 XML 문서에 연결하고 변형을 수행하며 출력을 볼 수 있습니다. XSLT 변환의 결과로 나타나는 출력이 새 문서 창에 표시됩니다.  
  
 합니다 **출력** 속성 출력 파일 이름을 지정 합니다. 경우는 **출력** 속성을 비워 두면를 임시 디렉터리에 파일 이름이 생성 됩니다. 파일 확장명은 스타일시트에 있는 `xsl:output` 요소를 기반으로 하며 .xml, .txt 또는 .htm일 수 있습니다.  
  
 경우는 **출력** .htm 파일을 사용 하 여 파일을 지정 하는 속성 또는.html 확장명 XSLT 출력을 사용 하 여 미리 보기 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer입니다. 다른 모든 파일 확장명은 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio에서 선택한 기본 편집기를 사용하여 열립니다. 예를 들어, 파일 확장명이 .xml인 경우 Visual Studio에서는 XML 편집기를 사용합니다.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>XML 문서에서 XSLT 변형을 실행하려면  
  
1. XML 편집기에서 XML 문서를 엽니다.  
  
2. XSLT 스타일시트를 XML 문서에 연결합니다.  
  
    - XML 문서에 `xml-stylesheet` 처리 명령을 추가합니다. 예를 들어, 문서 프롤로그에 다음 `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` 줄을 추가합니다.  
  
         또는  
  
    - 사용 하 여 XSLT 스타일 시트를 추가 합니다 **속성** 창입니다. 문서의 **속성 창**를 클릭 합니다 **찾아보기** 단추를 **스타일 시트** 필드, XSLT 스타일 시트를 선택 하 고, 클릭 **엽니다**.  
  
3. 클릭 합니다 **ShowXSL 출력** 단추를 **XML 편집기** 도구 모음입니다.  
  
    > [!NOTE]
    > XML 문서에 연결된 스타일시트가 없을 경우 대화 상자에서 사용할 스타일시트를 지정하라는 메시지가 나타납니다.  
    >   
    >  XSLT 변환의 결과로 나타나는 출력이 새 문서 창에 표시됩니다.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT 스타일시트에서 XSLT 변형을 실행하려면  
  
1. XML 편집기에서 XSLT 스타일시트를 엽니다.  
  
2. XML 문서를 지정 합니다 **입력** 문서의 필드 **속성** 창입니다.  
  
    > [!NOTE]
    > XML 문서는 변환에 사용되는 입력 문서입니다. XSLT 변환을 시작 되 면 문서를 지정 하지 않으면 합니다 **파일 열기** 대화 상자가 나타나고 해당 시점에 문서를 지정할 수 있습니다.  
  
3. 클릭 합니다 **ShowXSLT 출력** 단추를 **XML 편집기** 도구 모음입니다.  
  
     XSLT 변환의 결과로 나타나는 출력이 새 문서 창에 표시됩니다.  
  
### <a name="to-provide-a-different-output-file-name"></a>다른 출력 파일 이름을 지정하려면  
  
1. 에 파일 이름을 지정 합니다 **출력** 문서의 필드 **속성** 창입니다.  
  
2. 클릭 합니다 **ShowXSLT 출력** 단추를 **XML 편집기** 도구 모음입니다.  
  
     XSLT 변환 결과로 나타나는 출력이 새 문서 창에 표시 되 고 출력 창에 사용 되는 편집기의 파일 확장명에 따라 달라 집니다 하 **출력** 문서 속성입니다.  
  
## <a name="see-also"></a>참고 항목  
 [XML 편집기](../xml-tools/xml-editor.md)
