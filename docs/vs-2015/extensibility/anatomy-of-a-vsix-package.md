---
title: VSIX 패키지 분석 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86c2beeab5fba0224fbdfb104d01ee5c28bba158
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699137"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 패키지 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 패키지는 Visual Studio 확장을 설치 하 고 분류를 사용 하 여 메타 데이터와 함께 하나 이상의 Visual Studio 확장을 포함 하는.vsix 파일입니다. 해당 메타 데이터는 VSIX 매니페스트 및 [Content_Types].xml 파일에 포함 됩니다. VSIX 패키지 지역화 된 설치 프로그램 텍스트를 제공 하려면 하나 이상의 Extension.vsixlangpack 파일 포함 될 수도 있습니다 및 종속성을 설치 하는 추가 VSIX 패키지를 포함할 수 있습니다.  
  
 VSIX 패키지 형식으로 OPC Open Packaging Conventions () 표준을 따릅니다. 패키지 이진 파일에 포함 하 고 매니페스트 [Content_Types].xml 파일 및.vsix 파일을 지원 파일. 하나의 VSIX 패키지는 여러 프로젝트나 자신의 매니페스트는 여러 패키지의 출력을 포함할 수 있습니다.  
  
> [!NOTE]
> VSIX 패키지에 포함 된 파일의 이름은 공백을 포함할 수 없습니다 나으로 리소스 URI (Uniform Identifier), 예약 된 문자 아래에 정의 된 [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)합니다.  
  
## <a name="the-vsix-manifest"></a>VSIX 매니페스트  
 VSIX 매니페스트의 확장이 설치 되도록 하 고 다음과 같이 VSX 스키마에 대 한 정보를 포함 합니다. 자세한 내용은 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다. VSIX 매니페스트 예제를 참조 하세요. [PackageManifest 요소 (루트 요소, VSX 스키마)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)합니다.  
  
 VSIX 매니페스트의 이름은 `extension.vsixmanifest` .vsix 파일에 포함 된 경우.  
  
## <a name="the-content"></a>콘텐츠  
 VSIX 패키지 템플릿, 도구 상자 항목, Vspackage 또는 다른 유형의 Visual Studio에서 지원 되는 확장에 포함 될 수 있습니다.  
  
## <a name="language-packs"></a>언어 팩  
 VSIX 패키지를 한 번 또는 설치 하는 동안 지역화 된 텍스트를 제공 하는 더 많은 Extension.vsixlangpack 파일에 포함할 수 있습니다. 자세한 내용은 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)합니다.  
  
## <a name="dependencies-and-references"></a>종속성 및 참조  
 VSIX 패키지 참조로 다른 VSIX 패키지를 포함할 수 있습니다. 이러한 다른 패키지의 각 자체 VSIX 매니페스트를 포함 해야 합니다.  
  
 사용자가 종속성이 있는 확장을 설치 하려고 하는 경우 설치 관리자는 필요한 어셈블리 사용자 시스템에 설치 되어 있는지 확인 합니다. 필요한 어셈블리를 찾을 수 없는 경우 **확장 및 업데이트** 누락 된 어셈블리의 목록을 표시 합니다.  
  
 확장 매니페스트 하나 이상 포함 하는 경우 [참조](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) 요소인 **확장 및 업데이트** 시스템에 설치 된 확장에 대 한 각 참조의 매니페스트를 비교 하 고 설치 합니다 아직 설치 되지 않은 경우 확장을 참조 합니다. 이전 버전을 참조 되는 확장의 설치 된 경우 최신 버전으로 바꿉니다.  
  
 다중 프로젝트 솔루션에서 프로젝트를 동일한 솔루션에서 다른 프로젝트에 대 한 참조를 포함 하는 경우 해당 프로젝트의 종속성 VSIX 패키지에 포함 됩니다. 내부 프로젝트를 선택한 다음에 대 한 참조를 클릭 하 여이 동작을 재정의할 수 있습니다는 **속성** 창에서 설정 합니다 **출력 VSIX에 포함 된 그룹** 속성을 `BuiltProjectOutputGroup`입니다.  
  
 VSIX 패키지에 참조 된 어셈블리의 위성 Dll을 포함 하려면 추가 `SatelliteDllsProjectOutputGroup` 에 **출력 VSIX에 포함 된 그룹** 속성입니다.  
  
## <a name="installation-location"></a>설치 위치  
 설치 하는 동안 **확장 및 업데이트** %LocalAppData%\Microsoft\VisualStudio\14.0\Extensions 아래의 폴더에 VSIX 패키지 내용의 압축을 찾습니다.  
  
 기본적으로 설치 % LocalAppData % 사용자별 디렉터리 이므로 현재 사용자 에게만 적용 합니다. 그러나 설정 하는 경우는 [AllUsers](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) 매니페스트를 요소의 `True`, 아래에 확장을 설치할 수는... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions 되며 컴퓨터의 모든 사용자에 게 제공 됩니다.  
  
## <a name="contenttypesxml"></a>[Content_Types].xml  
 [Content_Types].xml 파일에는 확장 된.vsix 파일의 파일 형식을 식별합니다. Visual Studio 패키지를 설치 하는 동안이 파일을 사용 하지만 파일 자체를 설치 하지 않습니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [구조는 Content_types\].xml 파일](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)합니다.  
  
 [Content_Types].xml 파일을 여는 OPC Open Packaging Conventions () 표준 필요 합니다. OPC에 대 한 자세한 내용은 참조 하세요. [OPC: 새로운 표준에 대 한 패키징 Your 데이터](http://go.microsoft.com/fwlink/?LinkID=148207) MSDN 웹 사이트입니다.
