---
title: 요소 (VSIX 언어 팩 스키마) 라이선스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a079dee3fc01995d70f77a9fa9791a5ab0f42561
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680587"
---
# <a name="license-element-vsix-language-pack-schema"></a>License 요소 (VSIX 언어 팩 스키마)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

선택 사항입니다. 지역화 된 버전의 확장에 대 한 라이선스 파일의 경로입니다.  
  
## <a name="syntax"></a>구문  
  
```  
<License>FilePath\license.txt</License>  
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
 표시할 지역화 된 라이센스 파일의 상대 경로입니다.  
  
## <a name="remarks"></a>설명  
 경우는 `License` 요소가 정의 된 설치 중 지정된 된 라이선스 파일의 텍스트가 표시 됩니다 하 고 사용자가 계속 하려면 라이선스를 허용 해야 합니다.  
  
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
