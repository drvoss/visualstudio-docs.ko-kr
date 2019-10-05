---
title: 구조는 Content_types].xml 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e94e8cd065908671446486d2ec00e167d8fb4f4e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697104"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>구조는 Content_types].xml 파일
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 패키지에서 원하는 콘텐츠 종류에 대 한 정보를 포함합니다. Visual Studio는 패키지를 설치 하려면 [Content_Types].xml 파일을 사용 하지만 파일 자체를 설치 하지 않습니다.  
  
> [!NOTE]
> [Content_Types].xml 파일 형식을의 일부인이 항목에서는 VSIX 패키지에 사용 되는 [Content_Type].xml 파일에만 적용 되는 *OPC Open Packaging Conventions ()* 표준입니다. 자세한 내용은 참조 하세요. [OPC: 새로운 표준에 대 한 패키징 Your 데이터](http://go.microsoft.com/fwlink/?LinkID=148207) MSDN 웹 사이트입니다.  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 루트 요소 및 해당 특성 및 자식 요소를 설명합니다.  
  
### <a name="root-element"></a>루트 요소  
  
|요소|설명|  
|-------------|-----------------|  
|`Types`|VSIX 패키지에 파일 형식을 열거 하는 자식 요소를 포함 합니다.|  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`Xmlns`|(필수) 이 [Content_Types].xml 파일에 사용 된 스키마의 위치입니다.|  
  
### <a name="attribute-name-attribute"></a>{0} 특성 이름} 특성  
  
|                           값                           |                설명                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | 콘텐츠 형식 스키마의 위치입니다. |
  
### <a name="child-elements"></a>자식 요소  
 합니다 `Types` 요소를 포함할 수 있는 모든 수 `Default` 요소입니다.  
  
|요소|설명|  
|-------------|-----------------|  
|`Default`|VSIX 패키지의 콘텐츠 형식을 설명합니다. 패키지의 파일 형식은 모두 있어야 자체 `Default` 요소입니다.|  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`Extension`|VSIX 패키지에 있는 파일의 파일 이름 확장명입니다.|  
|`ContentType`|파일 이름 확장명을 사용 하 여 연결 콘텐츠의 종류를 설명 합니다.|  
  
### <a name="attribute-name-attribute"></a>{0} 특성 이름} 특성  
 Visual Studio에서 다음 인식할 `ContentType` 연결 된 값 `Extension` 형식입니다.  
  
|확장명|ContentType|  
|---------------|-----------------|  
|txt|텍스트/일반|  
|pkgdef|텍스트/일반|  
|Xml|text/xml|  
|vsixmanifest|text/xml|  
|htm 또는 html|text/html|  
|rtf|응용 프로그램/서식 있는 텍스트|  
|pdf|application/pdf|  
|GIF|image/gif|  
|jpg 또는 jpeg|image/jpg|  
|Tiff|image/tiff|  
|vsix|application/zip|  
|zip|application/zip|  
|dll|application/octet-stream|  
|다른 모든 파일 형식|application/octet-stream|  
  
## <a name="example"></a>예제  
  
### <a name="description"></a>설명  
 [Content_Types].xml 파일에는 일반적인 VSIX 패키지를 설명합니다.  
  
### <a name="code"></a>코드  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>참고 항목  
 [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: 데이터 패키징을 위한 새로운 표준](http://go.microsoft.com/fwlink/?LinkID=148207)
