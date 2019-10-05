---
title: Visual Studio 2015 SDK의 소스 제어의 새로운 기능 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e12776c21d345d60992eeff4963498bcd7d56678
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323257"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK에 대 한 소스 제어의 새로운 기능

에 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], 소스 제어 VSPackage를 구현 하 여 긴밀히 통합된 원본 제어 솔루션을 제공할 수 있습니다. 이 섹션에서는 소스 제어 Vspackage의 기능을 설명 하 고 구현 하는 단계 개요를 제공 합니다.

## <a name="the-source-control-vspackage"></a>소스 제어 VSPackage

Visual Studio는 두 가지 유형의 원본 제어 솔루션을 지원합니다. Visual Studio의 모든 버전에 통합할 수도 있습니다는 원본 제어 플러그 인 API 기반 플러그 인입니다. 심층 통합을 제공 하는 소스 제어 VSPackage를 만들 수도 있습니다 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 경로 높은 수준의 숙련도 및 자율성을 필요로 하는 원본 제어 솔루션에 적합 합니다.

VSPackage Visual Studio에 거의 모든 종류의 기능을 추가할 수 있습니다. 소스 제어 VSPackage에 소스 제어 시스템을 사용 하 여 백 엔드 통신을 사용자에 게 UI에서 Visual Studio에 대 한 전체 소스 제어 기능을 제공 합니다.

소스 제어 VSPackage를 구현 하는 "양자 택일" 전략에 필요 합니다. 소스 제어 VSPackage의 작성자 인터페이스 뿐만 아니라 상당한 노력을 구현 하는 다양 한 원본 제어 인터페이스 및 새 UI 요소 (대화 상자, 메뉴 및 도구 모음)는 전체 소스 제어 기능을 처리 하기 위해 투자 해야 합니다. Visual Studio를 사용 하 여 성공적으로 통합 하는 모든 패키지의 필요 합니다.

다음 단계를 소스 제어 패키지를 구현 하는 데 필요한 사항을의 일반적인 개요를 제공 합니다. 자세한 내용은 참조 하세요 [소스 제어 VSPackage를 만드는](../../extensibility/internals/creating-a-source-control-vspackage.md)합니다.

1. 개인 원본 제어 서비스 proffers 된 VSPackage를 만듭니다.

2. Visual Studio에서 제공 되는 원본 제어와 관련 된 서비스에서 인터페이스 구현 (예를 들어 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> 인터페이스).

3. 소스 제어 VSPackage를 등록 합니다.

4. 모든 소스 제어 메뉴 항목, 대화 상자, 도구 모음 및 상황에 맞는 메뉴를 포함 하 여 UI를 구현 합니다.

5. 모든 소스 제어와 관련 된 이벤트 이며 VSPackage에서 처리 해야 하는 경우 소스 제어 VSackage 전달 됩니다.

6. 소스 제어 VSPackage 구현 같은 이벤트를 수신 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> Track 프로젝트 문서 TPD () 이벤트 뿐만 아니라 인터페이스 (구현 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 인터페이스) 필요한 조치를 취합니다.

## <a name="see-also"></a>참고자료

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [개요](../../extensibility/internals/source-control-integration-overview.md)
- [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)