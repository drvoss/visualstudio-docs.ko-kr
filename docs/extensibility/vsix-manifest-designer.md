---
title: VSIX 매니페스트 디자이너 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c13d32ab6b91dce94bab307f6bbc6744f9c17a0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322847"
---
# <a name="vsix-manifest-designer"></a>VSIX 매니페스트 디자이너
VSIX 패키지 매니페스트 파일을 Visual Studio 확장에 대 한 설치 동작을 설정 하는 수정 합니다.

 합니다 **VSIX 매니페스트 디자이너** 기본 VSIX 스키마에 매핑됩니다. 디자이너에서 해당 컨트롤을 사용 하 여 스키마의 모든 요소를 설정할 수 있습니다. 스키마에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)합니다.

 열려는 **VSIX 매니페스트 디자이너**를 찾습니다는 *source.extension.vsixmanifest* 파일 **솔루션 탐색기**, 파일을 엽니다. 파일에 올바른 XML이 없으면 매니페스트 디자이너 열리지 않습니다.

> [!NOTE]
> 합니다 *source.extension.vsixmanifest* 파일에 출력 되 *extension.vsixmanifest* 패키지를 빌드할 때입니다.

## <a name="uielement-list"></a>UI 요소 목록
 합니다 **VSIX 매니페스트 디자이너** 스키마의 최상위 이러한 요소에 해당 하는 4 개의 섹션이 포함 되어 있습니다.

- 메타데이터

- 대상 설치

- 자산

- 종속성

  머리글 영역에는 다음과 같은 컨트롤을 포함합니다.

  **제품 이름** 확장 이름에 설명 합니다.

  **제품 ID** 이 패키지에 대 한 고유 id 정보를 지정 합니다.

  **작성자** 확장 작성자의 이름을 지정 합니다.

  **버전** 확장의 버전 번호를 지정 합니다.

  합니다 **메타 데이터** 탭에 다음과 같은 컨트롤을 포함 합니다.

  **설명을** 에 표시할 확장의 텍스트 설명이 **확장 관리자**합니다.

  **언어** 매니페스트에서 텍스트 데이터에 해당 하는 패키지에 대 한 기본 언어를 지정 합니다. `Language` 특성 예를 들어 en 리소스 어셈블리에 대 한 공용 언어 런타임 (CLR) 로캘 코드 규칙을 따르므로-, en, fr 합니다. 기본적으로 값은 중립, 모든 언어 버전의 Visual Studio에서 패키지가 실행 됩니다.

  **라이선스** 없는 경우 사용자 라이선스를 포함 하는 텍스트 파일을 지정 합니다.

  **아이콘** 그래픽 파일을 지정 합니다 ( *.png*합니다 *.bmp*를 *.jpeg*를 *.ico*)에 표시할 아이콘을 포함 하는 **확장 관리자**아이콘이 있는 경우. 아이콘 이미지는 32 x 32 픽셀 이어야 합니다. 또는 해당 차원에 크기가 조정 됩니다. 아이콘 없음이 지정 된 경우 **확장 관리자** 기본 아이콘을 사용 합니다.

  **미리 보기 이미지가** 그래픽 파일을 지정 합니다 ( *.png*, *.bmp*를 *.jpeg*를 *.ico*) 미리 보기 이미지를 포함 하는 에 표시할 **확장 관리자**미리 보기 이미지를 사용할 수 있는 경우. 미리 보기 이미지에는 200 x 200 픽셀 이어야 합니다. 미리 보기 이미지가 지정 된 경우 **확장 관리자** 기본 이미지를 사용 합니다.

  **태그** 검색 힌트에 사용 되는 텍스트 태그를 추가 합니다.

  **릴리스 정보** 파일을 지정 합니다 ( *.txt*합니다 *.rtf*) 릴리스 정보를 포함 하는 합니다. 또한 릴리스 정보를 표시 하는 웹 사이트의 URL을 사용 합니다.

  **시작 가이드** 파일을 지정 합니다 ( *.txt*하십시오 *.rtf*) VSIX 패키지에 확장 또는 콘텐츠를 사용 하는 방법에 대 한 정보를 포함 하는 합니다. 이 가이드에는 확장 설치가 완료 되 면 표시 됩니다. 또한이 가이드를 표시 하는 웹 사이트의 URL을 사용 합니다.

  **추가 정보 URL** 제품에 대 한 추가 정보를 포함 하는 웹 사이트의 URL을 지정 합니다.

  합니다 **설치 대상** 탭에 다음과 같은 컨트롤을 포함 합니다.

  **설치 유형에** 나열 **Visual Studio 확장** 하 고 **확장명 SDK** 설치 유형을 대상으로 합니다. 옵션은 선택한 유형에 따라 다릅니다.

  **Visual Studio 확장** 나열 된 **에서 InstallationTarget** 패키지를 설치할 수 있습니다 및 Visual Studio 제품에이 확장을 설치할 수 있습니다 하는 방법을 설명 하는 요소입니다. 각 제품 이름 및 버전 또는 버전 범위 별로 개별적으로 식별 됩니다. 제품을 목록에 추가, 수정 및 삭제 될 수 있습니다. 이름 및 제품의 버전에 해당 하는 **Id** 및 **버전** 관련 된 특성 **에서 InstallationTarget** 요소입니다.

  **버전 범위** 은 [12.0, 14.0] 다음 표기법을 사용 합니다.

- [-포함 하는 최소 버전

- ]-포함 하는 최대 버전

- (-단독 최소 버전

- )-최대 버전 전용

- 단일 버전 #-지정된 된 버전만

  **확장 SDK** 특정 제품 및 버전 범위가 지정 되지 않는 전역 설치를 지정 합니다. **대상 플랫폼 식별자** "Windows에서" 대상으로 하는 등의 플랫폼입니다. **대상 플랫폼 버전** 는 대상 플랫폼의 8.0과 같은 버전입니다. **SDK 이름** 하 고 **SDK 버전** 각각은 이름 및 SDK의 버전 번호입니다.

  **이 VSIX는 모든 사용자 용 으로만 설치 (설치 시 권한 상승이 필요한)** 확장이 모든 사용자에 대해 설치 된이 확인란을 선택 하면, 그렇지 않으면 현재 사용자에 대해서만 설치 합니다.

  **이 VSIX는 Windows 설치 관리자가 설치 되어** 확장이 Windows 설치 관리자가 설치 되어이 확인란을 선택 하면 ( *.msi* 파일)이 고, 그렇지 않으면 일반적인 VSIX 패키지 설치 됩니다 ( *.vsix*  파일).

  합니다 **자산** 탭에 다음과 같은 컨트롤을 포함 합니다.

  **자산 목록을** 확장 또는 콘텐츠 요소에 설명 하는 자산 요소를 나열이 화면을 패키지 합니다. 각 확장 또는 콘텐츠 요소는 원본, 형식 및 경로에서 별도로 나열 됩니다. 확장 및 콘텐츠 요소는 목록에 추가, 수정 및 삭제 될 수 있습니다. 유형 및 확장 또는 콘텐츠 요소의 경로에 해당 하는 `Type` 하 고 `Path` 연결 된 특성 `Asset` 요소. 다음과 같은 형식이 알려져 있습니다.

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  를 추가 하거나 자산을 편집 하려면 자산 프로젝트의 이름 및 파일 시스템에 현재 솔루션에서 프로젝트 또는 파일 인지 여부를 자산 형식에 지정 해야 합니다. 또한 포함할 폴더의 이름을 지정할 수 있습니다.

  고유한 형식의 만들고 고유한 이름을 부여할 수도 있습니다.

  합니다 **종속성** 탭에 다음과 같은 컨트롤을 포함 합니다.

  **이름, 원본 및 버전 범위** 이 패키지에 종속 된 다른 패키지는이 패키지의 종속성 요소를 나열 합니다. 종속성 패키지를 지정 하는 경우이 설치 되어 있어야이 패키지를 설치 합니다. 그렇지 않은 경우이 패키지 설치 해야 합니다.

  종속성 패키지 식별자, 이름, 버전 범위, 원본 및 해결 해야 할 종속성이 방법으로 지정 됩니다. 각 종속성 패키지 이름, 버전 및 소스에서 별도로 나열 됩니다. 종속성 패키지 있습니다 목록에 추가, 수정 하 고 삭제 합니다.

  식별자와 일치 해야 합니다는 `ID` 종속성 패키지 메타 데이터의 특성입니다. 원본은 현재 솔루션, 현재 설치 된 확장을 또는 파일에서 프로젝트를 수 있습니다. 합니다 **성은 종속성 해결** 중첩 된 패키지의 상대 경로 또는 종속성에 대 한 다운로드 위치의 URL을 설정할 수 있습니다. 에 해당 하는 ID, 버전 및 종속성 패키지의 해상도 `Id`, `Version`, 및 `Location` 관련 된 특성 `Dependency` 요소입니다.

## <a name="see-also"></a>참고자료
- [VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)