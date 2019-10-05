---
title: '&lt;fileAssociation&gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d3a43af5b2c7d50034cbed9d7da16e65b402f70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928520"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; 요소 (ClickOnce 응용 프로그램)
응용 프로그램과 연결할 파일 확장명을 식별 합니다.

## <a name="syntax"></a>구문

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `fileAssociation` 요소는 선택적입니다. 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`extension`|필수 요소. 응용 프로그램과 연결할 파일 확장명입니다.|
|`description`|필수 요소. 셸에 사용할 파일 형식을 설명입니다.|
|`progid`|필수 요소. 파일 형식을 고유 하 게 식별 하는 이름입니다.|
|`defaultIcon`|필수 요소. 이 확장을 사용 하 여 파일에 사용할 아이콘을 지정 합니다. 아이콘 파일을 사용 하 여 지정 해야 합니다 [ \<파일 > 요소](../deployment/file-element-clickonce-application.md) 내에서 합니다 [ \<어셈블리 > 요소](../deployment/assembly-element-clickonce-application.md) 이 요소를 포함 하는 합니다.|

## <a name="remarks"></a>설명
 이 요소에 대 한 XML 네임 스페이스 참조를 포함 해야 합니다 "urn: 스키마-microsoft-com:clickonce.v1"입니다. 경우는 `<fileAssociation>` 요소는 뒤에 야 합니다는 `<application>` 요소에서 부모 [ \<어셈블리 > 요소](../deployment/assembly-element-clickonce-application.md)합니다.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 기존 파일 연결을 덮어쓰지 않습니다. 그러나 ClickOnce 응용 프로그램은 현재 사용자의 파일 확장명을 재정의할 수 있습니다. ClickOnce 응용 프로그램을 제거한 후 사용자에 대해 파일 연결을 삭제 하는 ClickOnce 및 컴퓨터별 연결을 다시 활성화 되는 합니다.

## <a name="example"></a>예제
 다음 코드 예제를 보여 줍니다 `fileAssociation` 응용 프로그램의 요소를 사용 하 여를 배포 하는 텍스트 편집기 응용 프로그램에 대 한 매니페스트 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]합니다. 이 코드 예제도 포함 되어는 [ \<파일 > 요소](../deployment/file-element-clickonce-application.md) 필요는 `defaultIcon` 특성입니다.

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)