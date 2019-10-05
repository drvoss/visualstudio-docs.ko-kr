---
title: LocalizedName 요소 (VSIX 언어 팩 스키마) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fcbda9f8c7a98d0830c898c81471854efc3a6403
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686148"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>LocalizedName 요소 (VSIX 언어 팩 스키마)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

필수 요소. 확장을 설치의 지역화 된 이름입니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|없음||  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|없음||  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[VSIX LanguagePack 요소](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|필수 요소. VSIX 언어 팩에 대 한 루트 요소를 제공합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 필수 요소. 대상 언어의 언어 팩의 이름입니다.  
  
## <a name="element-information"></a>요소 정보  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    네임스페이스    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   스키마 이름   |                 VSIX 언어 팩 스키마                 |
| 유효성 검사 파일 |                VSIXLanguagePackSchema.xsd                 |
|  비워 둘 수 있습니다.   |                      적용할 수 없음                       |
  
## <a name="see-also"></a>참고 항목  
 [VSX 언어 팩 스키마 참조](../extensibility/vsx-language-pack-schema-reference.md)   
 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)   
 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
