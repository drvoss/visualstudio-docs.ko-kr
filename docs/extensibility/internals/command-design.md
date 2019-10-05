---
title: 명령 디자인 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1644cfa71296c4233cf17b6b225933aeeb3d477
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342170"
---
# <a name="command-design"></a>명령 디자인
VSPackage에 명령을 추가할 때 표시할 경우, 사용 가능한 경우 및 처리 하는 방법 지정 해야 합니다.

## <a name="define-commands"></a>명령 정의
 새 명령을 정의 하려면 Visual Studio 명령 테이블을 포함 합니다 ( *.vsct*) VSPackage 프로젝트 파일에에서 있습니다. Visual Studio 패키지 템플릿을 사용 하 여 VSPackage를 만든 경우 프로젝트는 이러한 파일 중 하나가 포함 되어 있습니다. 자세한 내용은 [Visual Studio 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)합니다.

 Visual Studio는 모든 병합 합니다 *.vsct* 찾습니다 파일 명령을 표시할 수 있도록 합니다. 이러한 파일 이진 VSPackage 별개 이기 때문에 Visual Studio 명령을 찾기 위해 패키지를 로드 하지 않아도 됩니다. 자세한 내용은 [사용자 인터페이스 요소를 추가 하는 방법: Vspackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)합니다.

 Visual Studio에서 사용 하 여 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 명령과 메뉴 리소스를 정의 하는 등록 특성입니다. 자세한 내용은 [명령 구현](../../extensibility/internals/command-implementation.md)합니다.

 명령에서 다양 한 다른 방법으로 런타임 시 변경할 수 있습니다. 이러한 표시 또는 숨김, 사용 하도록 설정 하거나 해제할 수 있습니다. 다른 텍스트 또는 아이콘을 표시 하거나 다른 값이 포함 수 있습니다. Visual Studio에서 VSPackage를 로드 하기 전에 상당한 사용자 지정을 수행할 수 있습니다. 자세한 내용은 [사용자 인터페이스 요소를 추가 하는 방법: Vspackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)합니다.

## <a name="command-handlers"></a>명령 처리기
 명령을 만들 때 명령을 실행 하는 이벤트 처리기를 제공 해야 합니다. 사용자가 명령을 선택,이 적절 하 게 라우팅해야 합니다. 명령 라우팅 사용 또는 비활성화, 숨기기 또는 표시 및 사용자가 작업을 수행 하도록 선택한 경우 실행 하려면 올바른 VSPackage에 전송 하는 작업을 의미 합니다. 자세한 내용은 [명령 라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)합니다.

## <a name="visual-studio-command-environment"></a>Visual Studio 명령 환경
 Visual Studio는 임의 개수의 Vspackage 호스트할 수 있습니다 하 고 각 명령 집합 자체에 기여할 수 있습니다. 환경에는 현재 작업에 적합 한 명령만 표시 합니다. 자세한 내용은 [가용성 명령을](../../extensibility/internals/command-availability.md) 하 고 [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)합니다.

 새 명령, 메뉴, 도구 모음 또는 바로 가기 메뉴를 정의 하는 VSPackage는 네이티브 또는 관리 되는 어셈블리에서 리소스를 참조 하는 레지스트리 항목을 통해 설치 시 Visual studio 명령 정보를 제공 합니다. 각 리소스는 이진 데이터 리소스를 참조 합니다 ( *.cto*)는 Visual Studio 명령 테이블을 컴파일할 때 생성 되는 파일 ( *.vsct*) 파일입니다. 이 통해 Visual Studio의 모든 설치 된 VSPackage를 로드 하지 않고도 병합 된 명령 집합, 메뉴 및 도구 모음을 제공 합니다.

### <a name="command-organization"></a>명령 조직
 환경에는 그룹, 우선 순위 및 메뉴 명령을 배치합니다.

- 예를 들어 그룹은의 관련된 명령 논리적 컬렉션의 **잘라내기**를 **복사**, 및 **붙여넣기** 명령 그룹입니다. 그룹은 메뉴에 표시 되는 명령입니다.

- 우선 순위 그룹의 개별 명령을 메뉴에 표시 된 순서를 결정 합니다.

- 메뉴 그룹에 대 한 컨테이너로 사용 합니다.

  환경에서는 일부 명령, 그룹 및 메뉴에 미리 정의 합니다. 자세한 내용은 [기본 명령, 그룹 및 도구 모음 배치](../../extensibility/internals/default-command-group-and-toolbar-placement.md)합니다.

  명령 기본 그룹에 할당할 수 있습니다. 기본 그룹 및 주 메뉴 구조의 명령의 위치를 제어 합니다 **사용자 지정** 대화 상자. 명령을 여러 그룹에 나타날 수 있습니다. 예를 들어 주 메뉴, 바로 가기 메뉴 및 도구 모음 명령 수 있습니다. 자세한 내용은 [사용자 인터페이스 요소를 추가 하는 방법: Vspackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)합니다.

### <a name="command-routing"></a>명령 라우팅
 호출 하 고 vspackage의 명령 라우팅 프로세스 개체 인스턴스에서 메서드를 호출 하는 프로세스에서 서로 다릅니다.

 환경 (전역)은 가장 바깥쪽 컨텍스트를 순차적으로 컨텍스트에서 가장 안쪽 (local) 명령은 현재 선택 영역을 기반으로 하는 명령을 라우팅합니다. 첫 번째는 명령을 실행할 수 있는 컨텍스트가 처리 하는 것입니다. 자세한 내용은 [명령 라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)합니다.

 명령을 사용 하 여 환경에서 대부분의 경우 처리는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스입니다. 명령 라우팅 체계를 통해 명령을 처리 하는 많은 다른 개체를 수 있으므로 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Microsoft ActiveX 컨트롤, 창 보기 구현, 문서 개체 프로젝트 계층 구조에 포함 되어 이러한; 임의 개수의 개체에서 구현 될 수 있습니다. 및 VSPackage 개체 자체 (예: 전역 명령)을 추가 합니다. 일부 특수 한 경우에 예를 들어, 명령 라우팅 계층에서의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 인터페이스를 구현 해야 합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[명령 구현](../../extensibility/internals/command-implementation.md)|VSPackage에서 명령을 구현 하는 방법에 설명 합니다.|
|[명령 가용성](../../extensibility/internals/command-availability.md)|Visual Studio 컨텍스트에 사용할 수 있는 명령을 확인 하는 방법을 설명 합니다.|
|[명령 라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio 명령 라우팅 아키텍처 다른 Vspackage에서 처리 명령을 사용 하는 방법을 설명 합니다.|
|[명령 배치 지침](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio 환경에서 명령을 배치 하는 방법을 제안 합니다.|
|[Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Vspackage는 Visual Studio 명령 아키텍처 수 최대한 활용 하는 방법을 설명 합니다.|
|[기본 명령, 그룹 및 도구 모음 배치](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Vspackage Visual Studio에 포함 된 명령 수 최대한 활용 하는 방법을 설명 합니다.|
|[Vspackage 관리](../../extensibility/managing-vspackages.md)|Visual Studio에서 Vspackage를 로드 하는 방법을 설명 합니다.|
|[Visual Studio 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|XML을 기반으로 하는 방법에 대 한 정보를 제공 *.vsct* 레이아웃 및 모양을 Vspackage의 명령에 대해 설명 하는 데 사용 되는 파일입니다.|