---
title: '방법: Atom를 만드는 개인 갤러리에 대 한 피드 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027a7f70240695e64051ef6c16fd3e5469d75900
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340881"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>방법: Atom 개인 갤러리에 대 한 피드 만들기
Atom (RSS) 피드를 확장을 포함 하는 피드를 추가 인트라넷 위치를 만들 수 있습니다 **확장 및 업데이트** 를 전용 갤러리로 합니다. 자세한 내용은 [Private galleries](../extensibility/private-galleries.md)(전용 갤러리)를 참조하세요.

## <a name="create-an-atom-feed"></a>Atom 피드 만들기
 Atom 피드를 전용 갤러리로 만들려면 먼저 확장이 수집 ( *.vsix* 파일)를 폴더에 있습니다. 원하는 경우 하위 폴더에 해당를 구성할 수 있습니다. 또한 다음 리소스를 해야 합니다.

- *atom.xml* 파일을 전용 갤러리로 확장을 사용할 수 있도록 합니다. 연결 하는 방법에 대 한 자세한 합니다 *atom.xml* 파일을 **확장 및 업데이트**를 참조 하세요 [전용 갤러리](../extensibility/private-galleries.md)합니다.

- 확장 (예를 들어, 스크린 샷)에서 추출 된 모든 이미지 파일이 있는 폴더입니다. 합니다 *atom.xml* 파일에서 사용할 수 있도록 이러한 이미지에 대 한 상대 링크 포함 **확장 및 업데이트**합니다.

  예를 들어 폴더에 다음 두 가지 확장 수집 했다는 것을 가정 합니다.

- *Template_Wizard_239.vsix*, 되는 빈 VSIX 프로젝트 템플릿.

- *SelectionHighlight.vsix*, 선택한 단어의 모든 인스턴스가 강조 표시 하는 도구인 합니다.

  콘텐츠를 *atom.xml* 파일이 다음 예와 비슷하게 표시 됩니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 두 링크 태그를 이미지의 생성 된 폴더에 스크린 샷을 참조 하는지 확인 합니다.

## <a name="see-also"></a>참고자료
- [전용 갤러리](../extensibility/private-galleries.md)
