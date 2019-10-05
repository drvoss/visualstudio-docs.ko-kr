---
title: 관련된 서비스 및 인터페이스 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c5b040a8c5d0cbe2daff07f279cfd6a78cbd2b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157398"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>관련 서비스 및 인터페이스(소스 제어 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 섹션에서는 소스 제어 VSPackage 관련 인터페이스의 모든를 나열 합니다 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]합니다. 소스 제어 VSPackage 이러한 인터페이스의 일부를 구현 하 고 소스 제어 작업을 위해 다른 사용자를 사용 합니다.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>소스 제어 Vspackage에 대 한 구현 된 인터페이스  
 다음 인터페이스에 설명 된를 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], 소스 제어 VSPackage는 원하는 기능 집합에 따라 하위 집합을 구현 합니다. 일부 인터페이스 표시 된 필요한과 모든 소스 제어 VSPackage에 의해 구현 되어야 합니다.  
  
 패키지를 구현 하지 않는 해당 인터페이스에 대 한 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 기본 구현을 제공 합니다. 기본 구현은 없습니다 VSPackage 등록 된 경우 및 프로젝트가으로 디자인 되었다는 참고 제어 됩니다. 올바르게 작성 된 소스 제어 VSPackage는 해당 인터페이스의 기본 구현을 유지 하는 것이 아니라 모든 필요한 인터페이스를 구현 합니다.  
  
 소스 제어 VSPackage는 다음과 같은 인터페이스의 일부 또는 전부를 캡슐화 하는 개인 서비스를 구현 해야 합니다.  
  
 인터페이스는:  
  
- 필수: 적절 한 엔터티 (소스 제어 VSPackage를 원본 제어 스텁 프로젝트) 인터페이스를 구현 해야 합니다.  
  
- 권장: 엔터티는이 인터페이스를 구현 해야 합니다. 그렇지 않으면 소스 제어 기능 제한 될 수 있습니다.  
  
- 선택 사항: 엔터티가이 인터페이스를 다양 한 기능 집합을 구현할 수 있습니다.  
  
|인터페이스|용도|에 의해 구현|구현?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|편집기는 수정 하거나 파일을 저장 하기 전에이 인터페이스를 호출 합니다. 소스 제어 VSPackage 파일을 체크 아웃 하거나 거부할 수 작업을 체크 아웃 하지 못하면 합니다.|소스 제어 VSPackage|권장|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|이 인터페이스는 등록 및 소스 제어를 사용 하 여 프로젝트의 등록을 취소 하 고 기본 소스 컨트롤 문자 모양에 대 한 지원을 제공 하는 같은 프로젝트에 대 한 기본 소스 제어 기능을 제공 합니다.|소스 제어 VSPackage|필수|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|이 인터페이스에서 가져온 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 를 사용 하 여는 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 함수 또는 간단히 구현 하는 개체를 캐스팅 하 여 `IVsHierarchy` 를 `IVsSccProject2`합니다. 현재 소스 제어 상태 또는 위치를 프로젝트에 게 알리는 또는 프로젝트에서 소스 제어에서 파일 가져오기에 대 한 사용 됩니다.|Project|필수|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|통합 모듈을 현재 활성 VSPackage를 설정 하려면이 인터페이스를 사용 합니다.|소스 제어 VSPackage|필수|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|이 인터페이스는 구독 모델을 기반으로 합니다. 모든 VSPackage를 사용 하 여 한다는 것을 문서 이벤트를 수신 하 고 주의 사항은 이러한 셸에서 발생 된 이벤트에 신호를 보낼 수 있습니다. 구현 되 고 처리 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 구현 하는 이벤트를 다시 전달 하는 `IVsTrackProjectDocumentsEvents2` VSPackage에 있습니다.|원본 제어 스텁|필수|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|이 인터페이스는 일괄 처리, 동기화 된 읽기/쓰기 작업 및 고급 제공 `OnQueryAddFiles` 메서드.|원본 제어 스텁|필수|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**솔루션 탐색기** 프로젝트 파일 및 폴더를 변경 하거나 프로젝트에서 삭제할 때 또는 프로젝트에 새 파일이 추가 될 때이 인터페이스를 호출 합니다. 소스 제어 VSPackage 프로젝트 파일을 체크 아웃 하거나 작업을 취소할 수 있습니다.|소스 제어 VSPackage|권장|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**솔루션 탐색기** 프로젝트 IVstrackProjectDocuments3 인터페이스의 메서드 호출에 대 한 응답에서이 인터페이스를 호출 합니다. 소스 제어 VSPackage 동기화 일괄 처리 작업을 추적할 수 읽기/쓰기 작업을 여러분과 함께 더 많은 고급 `OnQueryAddFiles` 메서드.|소스 제어 VSPackage|권장|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|이 인터페이스는 인 리스트 먼 트 관리 웹 프로젝트에 대 한 지원을 제공 합니다.|소스 제어 VSPackage|권장|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|이 인터페이스는 프로젝트에서 소스 제어 파일에 대 한 도구 설명이 검색에 사용 됩니다.|소스 제어 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|이 인터페이스는 네임 스페이스 확장 지원을 제공합니다.|소스 제어 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage에 네임 스페이스 확장을 통합 하려면이 인터페이스를 사용 합니다 **새로 만들기**, **열려**, 또는 **저장** 대화 상자. 따라서 프로젝트 자동으로 생성, 소스 제어에 추가 하거나 추가할 수를 저장 하면 소스 제어에 작업 적용 됩니다.|소스 제어 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|추가 문자 모양이의 노드에 대 한 원본 제어 문자 모양으로 정의 하려면이 인터페이스를 사용 하는 VSPackage **솔루션 탐색기**합니다.|소스 제어 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|합니다 **추가** 웹 프로젝트 대화 상자는이 인터페이스를 사용 합니다. 소스 제어 위치 및 소스 제어 리포지토리에 해당 위치에서 이전에 추가한 웹 프로젝트를 열면 검색에 대 한 메서드를 제공 합니다.|소스 제어 VSPackage|권장|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|이 인터페이스는 비동기 (백그라운드) 소스 제어에서 프로젝트 로드에 대 한 지원을 제공합니다.|소스 제어 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|이 인터페이스를 사용 하 여 시작한 비동기 로딩의 진행률을 확인 하는 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>합니다.|Project|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|이 인터페이스는 현재 소스 제어 VSPackage를 쿼리 하기 위해 IDE를 허용 합니다. IDE는 VSPackage 등록 된 활성 원본 컨트롤이 없는 경우에 의미가 있는 소스 제어 설정의 값을 쿼리 합니다. 이 인터페이스를 구현 되 고 처리 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.|원본 제어 스텁|필수|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|이 인터페이스는 소스 제어 VSPackage를 등록 하는 중에 사용 됩니다.|원본 제어 스텁|필수|  
|<xref:EnvDTE.SourceControl>|이 인터페이스는 자동화에 사용 됩니다. 따라서 모든 UI를 표시 하지 않고 실행할 수 있는 함수에만 노출 합니다.|소스 제어 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|이 인터페이스는 소스 제어 설정을 솔루션 (.sln) 파일에 저장 됩니다. 소스 제어 위치 및 소스 제어 상태 플래그의 설정에 포함 됩니다.|소스 제어 VSPackage|권장|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|솔루션 옵션 (.suo) 파일에 소스 제어 설정을 저장 하려면이 인터페이스 사용 됩니다. 이 현재 사용자의 인 리스트 먼 트 위치와 같은 사용자 고유의 소스 제어 설정을 포함할 수 있습니다.|소스 제어 VSPackage|권장|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|이 인터페이스는 이벤트를 모니터링 하려면 솔루션을 닫기 또는 프로젝트를 열 때 소스 제어에서 새 파일을 시작 하기 전에 프로젝트 파일을 체크 인하고 등의 작업을 수행 하기 위해 사용 됩니다.|소스 제어 VSPackage|권장|  
  
## <a name="see-also"></a>참고 항목  
 [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
