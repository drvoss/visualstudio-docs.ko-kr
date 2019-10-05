---
title: 전달 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c7154395be43f6a0b07e9f2557d94fa594ef5ba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150791"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio 확장 전달
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**참고**: Visual Studio Marketplace를 Visual Studio 갤러리 교체 되 고 있습니다. 자세한 내용은이 항목의 최신 버전을 참조 하세요.

확장 프로그램 개발을 완료 한 후 다른 컴퓨터에 설치 친구 및 동료와 공유할 또는 Visual Studio 갤러리에 게시할 수 있습니다. 이 섹션에서는 게시 하 고 확장 프로그램을 유지 하기 위해 수행 해야 하는 모든 항목 설명:.vsix 파일을 게시, 지역화, 및 업데이트를 사용 합니다.

## <a name="working-with-vsix-extensions"></a>VSIX 확장을 사용 하 여 작업
 빈 VSIX 프로젝트를 만들고 다음을 다른 항목 템플릿을 추가 하 여 VSIX 확장을 만들 수 있습니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)합니다.

 패키지 프로젝트 템플릿, 템플릿, Vspackage, 프레임 워크 MEF (Managed Extensibility) 구성 요소 항목을 VSIX 형식을 사용할 수 있습니다 **도구 상자** 컨트롤, 어셈블리 및 사용자 지정 형식 (예: 사용자 지정 시작 페이지). VSIX 형식은 파일 기반 배포를 사용합니다. VSIX 패키지에 대 한 자세한 내용은 참조 하십시오 [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)합니다.

 VSIX 형식 코드 조각 기능을 지원 하지 않습니다. 전역 어셈블리 캐시 (GAC)에 또는 시스템 레지스트리에 쓰기와 같은 다른 시나리오도 지원 하지 않습니다. GAC에 설치의 레지스트리에서 작성 해야 할 경우 Windows 설치 관리자를 사용 해야 합니다. 자세한 내용은 [Windows에 대 한 확장 준비 Installer 배포](../extensibility/preparing-extensions-for-windows-installer-deployment.md)합니다.

## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Visual Studio 갤러리에 확장 게시
 .Vsix 파일을 메일 또는 서버에 배치 하면 다른 사용자에 게 확장 프로그램을 배포할 수 있습니다. 하지만 가장 좋은 방법은 코드의 많은 사람들이 참여에 배치 하는 것은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)합니다. Visual Studio 갤러리 확장을 통해 Visual Studio 사용자에 게 사용할 수 **확장 및 업데이트**합니다. 자세한 내용은 [Visual Studio 확장명 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)을 참조하세요.

 Visual Studio 갤러리에 확장을 업로드 하는 방법을 보여 주는 전체 예제를 참조 하세요. [연습: Visual Studio 확장 기능 게시](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)합니다.

## <a name="private-galleries"></a>Private Galleries
 컨트롤, 템플릿 및 도구를 개발할 때 인트라넷의 개인 갤러리에 게시 하 여 조직과 공유할 수 있습니다. 자세한 내용은 [Private Galleries](../extensibility/private-galleries.md)를 참조하세요.

## <a name="localizing-your-extension"></a>확장 프로그램을 지역화
 다른 로캘에서 확장 프로그램 해제 하려는 경우이 지역화 하는 것이 좋습니다. 와 관련 된 내용을 설명은 참조 하세요 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)합니다.

## <a name="updating-and-versioning-your-extension"></a>업데이트 및 버전 관리 확장 프로그램
 확장 프로그램을 게시 한 후 한 번 업데이트 해야 할 때 제공 됩니다. Visual Studio 갤러리에 게시 된 확장을 업데이트 하는 방법을 알아보려면 참조 [방법: 확장 업데이트](../extensibility/how-to-update-a-visual-studio-extension.md)합니다.

 Visual Studio의 여러 버전을 지원 하도록 확장 프로그램을 설정할 수 있습니다. 자세한 내용은 [Visual Studio의 여러 버전을 지 원하는](../extensibility/supporting-multiple-versions-of-visual-studio.md)합니다.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[VSIX 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)|VSIX 프로젝트 템플릿을 사용 하 여 사용자 지정 프로젝트 템플릿을 설치 하는 방법에 설명 합니다.|
|[VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)|VSIX 패키지의 구성 요소를 설명합니다.|
|[VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)|패키지 및 확장을 게시 하는 방법에 대 한 단계별 지침을 제공 합니다.|
|[VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)|Extension.vsixlangpack 파일을 사용 하 여 설치 프로세스에 대 한 지역화 된 텍스트를 제공 하는 방법에 설명 합니다.|
|[방법: 확장 업데이트](../extensibility/how-to-update-a-visual-studio-extension.md)|시스템에서 확장을 업데이트 하는 방법 및 기존 Visual Studio 확장에 업데이트를 배포 하는 방법을 설명 합니다.|
|[방법: VSIX 패키지에 종속성 추가](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSIX 배포 패키지에 대 한 참조를 추가 하는 방법에 설명 합니다.|
|[Windows Installer 배포에 대한 확장 준비](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Windows Installer를 사용 하 여 확장 프로그램을 배포 하는 방법에 설명 합니다.|
|[VSIX 패키지 서명](../extensibility/signing-vsix-packages.md)|VSIX 패키지에 서명 하는 방법에 설명 합니다.|
|[전용 갤러리](../extensibility/private-galleries.md)|확장에 대 한 전용 갤러리를 만드는 방법에 설명 합니다.|
|[여러 버전의 Visual Studio 지원](../extensibility/supporting-multiple-versions-of-visual-studio.md)|여러 버전의 Visual Studio에 확장 지원이 방법을 보여 줍니다.|
