---
title: VSIX 패키지 지역화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439766"
---
# <a name="localizing-vsix-packages"></a>VSIX 패키지 지역화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

대상 언어별로 Extension.vsixlangpack 파일을 만들고 올바른 폴더에 배치 하 여 VSIX 패키지를 지역화할 수 있습니다. 지역화 된 패키지를 설치 하면 확장의 지역화 된 이름은 지역화 된 설명과 함께 표시 됩니다. 지역화 된 라이선스 파일 또는 지역화 된 정보를 가리키는 URL을 제공 하는 경우도 표시 됩니다.  
  
 VSIX 패키지 콘텐츠를 추가 하는 VSPackage를 포함 하는 경우 메뉴 명령 또는 기타 UI 참조 [메뉴 명령 지역화](../extensibility/localizing-menu-commands.md) 새 UI 요소를 지역화 하는 방법에 대 한 정보에 대 한 합니다.  
  
## <a name="directory-structure"></a>디렉터리 구조  
 사용자가 확장을 설치 하면 **확장 및 업데이트** VSIX 패키지 이름이 대상 컴퓨터의 Visual Studio 로캘과 일치 하는 폴더에 대 한 최상위 수준 확인 합니다. 하는 경우 **확장 및 업데이트** .vsixlangpack 찾을 폴더에 파일,.vsixmanifest 파일에서 해당 값에 대해 해당 파일에서 지역화 된 값을 대체 합니다. 이러한 값은 확장을 설치 하는 경우에 표시 됩니다. 다음 예제에서는 스페인어 (ES-ES) 및 프랑스어 (FR)로 지역화 된 VSIX 패키지에 대 한 디렉터리 구조를 보여 줍니다.  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types].xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
> VSIX에서 지 원하는 프로젝트 템플릿을 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] VSIX 매니페스트를 생성 하 고 source.extension.vsixmanifest 라는 이름을 지정 합니다. Visual Studio에서 프로젝트를 빌드하고, 하는 경우 해당 파일의 콘텐츠를 복사 Extension.VsixManifest VSIX 패키지에 합니다.  
  
## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack 파일  
 Extension.vsixlangpack 파일은 다음과 같습니다 합니다 [VSIX 언어 팩 스키마](../extensibility/vsx-language-pack-schema-reference.md)합니다. 이 스키마에는 [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) 루트 요소가 있고 이러한 4 명의 자식 요소: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)합니다 [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), 및 [라이선스](../extensibility/license-element-vsix-language-pack-schema.md)합니다. 이러한 자식 요소에 해당 합니다 `Name`, `Description`, `MoreInfoURL`, 및 `License` 의 자식 요소는 `Identifier` Extension.vsixmanifest 파일의 요소입니다.  
  
 Vsixlangpack 파일을 만들 때 설정 해야 합니다 `Include in Vsix` 속성을 `true`입니다. 그렇지 않으면 지역화 된 설치 텍스트는 무시 됩니다.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Vsix 속성에 포함 되는 설정  
  
1. **솔루션 탐색기**Extension.vsixlangpack 파일을 마우스 오른쪽 단추로 클릭 한 다음 클릭 **속성**합니다.  
  
2. 속성 그리드에서 클릭 **Vsix에 포함**, 해당 값을 설정 하 고 `true`입니다.  
  
## <a name="example"></a>예제  
  
### <a name="description"></a>설명  
 다음 예제에서는 스페인어에 대 한 해당 Extension.vsixlangpack 파일과 함께 Extension.vsixmanifest 파일의 관련 부분을 보여 줍니다. 언어 팩의 값이 대상 컴퓨터의 Visual Studio 로캘이 스페인어로 설정 된 경우 매니페스트에서 값을 대체 합니다.  
  
### <a name="code"></a>코드  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>참고 항목  
 [VSIX LanguagePack 요소](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)
