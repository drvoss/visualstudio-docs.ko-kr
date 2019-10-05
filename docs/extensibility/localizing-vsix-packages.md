---
title: VSIX 패키지 지역화 | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e0ef2cc0c2404a2148f471d12f313b158f3bd64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344568"
---
# <a name="localizing-vsix-packages"></a>VSIX 패키지 지역화

VSIX 패키지를 만들어 지역화할 수 있습니다는 *Extension.vsixlangpack* 각 대상 언어에 대 한 파일을 올바른 폴더에 놓습니다. 지역화 된 패키지를 설치 하면 확장의 지역화 된 이름은 지역화 된 설명과 함께 표시 됩니다. 지역화 된 라이선스 파일 또는 지역화 된 정보를 가리키는 URL을 제공 하는 경우도 표시 됩니다.

VSIX 패키지 콘텐츠를 추가 하는 VSPackage를 포함 하는 경우 메뉴 명령 또는 기타 UI 참조 [메뉴 명령 지역화](../extensibility/localizing-menu-commands.md) 새 UI 요소를 지역화 하는 방법에 대 한 정보에 대 한 합니다.

## <a name="directory-structure"></a>디렉터리 구조

 사용자가 확장을 설치 하면 **확장 및 업데이트** VSIX 패키지 이름이 대상 컴퓨터의 Visual Studio 로캘과 일치 하는 폴더에 대 한 최상위 수준 확인 합니다. 하는 경우 **확장 및 업데이트** 찾습니다는 *.vsixlangpack* 파일 폴더에서 해당 파일의 해당 값의 지역화 된 값 대체를 *.vsixmanifest*파일입니다. 이러한 값은 확장을 설치 하는 경우에 표시 됩니다. 다음 예제에서는 스페인어 (ES-ES) 및 프랑스어 (FR)로 지역화 된 VSIX 패키지에 대 한 디렉터리 구조를 보여 줍니다.

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> VSIX에서 지 원하는 프로젝트 템플릿을 합니다 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX 매니페스트를 생성 하 고 이름을 *source.extension.vsixmanifest*합니다. Visual Studio에서 프로젝트를 빌드하고, 하는 경우 해당 파일의 콘텐츠를 복사 Extension.VsixManifest VSIX 패키지에 합니다.

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack 파일

합니다 *Extension.vsixlangpack* 다음과 같이 파일을 [VSIX 언어 팩 스키마 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)합니다. 이 스키마에는 `PackageLanguagePackManifest`에 바로 뒤에 `Metadata` 자식 요소입니다. 메타 데이터 요소에 최대 6 개의 자식 요소를 포함할 수 있습니다 `DisplayName`, `Description`를 `MoreInfo`, `License`를 `ReleaseNotes`, 및 `Icon`합니다. 이러한 자식 요소에 해당 합니다 `DisplayName`, `Description`, `MoreInfo`, `License`를 `ReleaseNotes`, 및 `Icon` 의 자식 요소를 `Metadata` 요소의 *Extension.vsixmanifest*파일입니다.

Vsixlangpack 파일을 만들 때 설정 해야 합니다 `Include in Vsix` 속성을 `true`입니다. 그렇지 않으면 지역화 된 설치 텍스트는 무시 됩니다.

### <a name="to-set-the-include-in-vsix-property"></a>Vsix 속성에 포함 되는 설정

1. **솔루션 탐색기**Extension.vsixlangpack 파일을 마우스 오른쪽 단추로 클릭 한 다음 클릭 **속성**합니다.

2. 에 **속성 표에서**, 클릭 **Vsix에 포함**, 해당 값을 설정 하 고 `true`입니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 관련 부분을 *Extension.vsixmanifest* 파일입니다. 해당 파일은 또한 포함 *Extension.vsixlangpack* 스페인어 파일입니다. 언어 팩의 값이 대상 컴퓨터의 Visual Studio 로캘이 스페인어로 설정 된 경우 매니페스트에서 값을 대체 합니다.

### <a name="code"></a>코드

- [*Extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension.vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>참고자료

|제목|설명|
|-----------|-----------------|
|[VSIX 언어 팩 스키마 2.0 참조](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|VSIX 언어 팩에는.vsix 배포 파일이의 지역화 정보를 설명합니다.|
|[VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)|Vsix 패키지의 내용과 구조를 설명합니다.|
|[메뉴 명령 지역화](../extensibility/localizing-menu-commands.md)|확장의 다른 텍스트 리소스를 지역화 하는 방법을 보여 줍니다.|