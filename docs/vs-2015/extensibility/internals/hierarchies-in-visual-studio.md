---
title: 계층 구조
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22943d3049ff0e24d00c7c29750e7dcd0efaf846
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158365"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio의 계층 구조
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 로 프로젝트를 표시 하는 통합된 개발 환경 (IDE)를 *계층*합니다. IDE에서 계층은 각 노드에 연결 된 속성 집합에 있는 노드의 트리입니다. A *계층 프로젝트* 은 프로젝트의 항목, 항목의 관계 및 항목의 관련된 속성 및 명령을 포함 하는 컨테이너입니다.

 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 계층 인터페이스를 사용 하 여 프로젝트 계층 구조를 관리할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스 명령을 표준 명령 처리기 대신 적절 한 계층 구조 창에 프로젝트 항목에서 호출을 리디렉션합니다.

## <a name="project-hierarchies"></a>프로젝트 계층 구조
 각 프로젝트 계층 확인 및 편집할 수 있는 항목을 포함 합니다. 이러한 항목 프로젝트 유형에 따라 달라 집니다. 예를 들어, 데이터베이스 프로젝트를 저장된 프로시저, 데이터베이스 뷰 및 데이터베이스 테이블을 포함할 수 있습니다. 반면, 프로그래밍 언어 프로젝트를 소스 파일 및 비트맵 및 대화 상자에 대 한 리소스 파일 가능성이 포함 됩니다. 제공 하는 몇 가지 추가 유연성을 프로젝트 계층 구조를 만들 때 계층 중첩 될 수 있습니다.

 새 프로젝트 형식을 만들면 프로젝트 형식에 편집할 수 있는 항목의 전체 집합을 제어 합니다. 그러나 프로젝트는 없는 편집 지원 항목을 포함할 수 있습니다. 예를 들어, 시각적 개체 C++ 프로젝트에도 Visual HTML 파일을 포함할 수 있습니다 C++ HTML 파일 형식에 대 한 모든 사용자 지정된 편집기를 제공 하지 않습니다.

 계층에 포함 된 항목의 지 속성을 관리 합니다. 계층의 구현 계층 내에서 항목의 지 속성에 영향을 주는 모든 특수 속성을 제어 해야 합니다. 예를 들어, 항목 파일 대신 저장소에서 개체를 나타내면 계층 구현에서는 해당 개체의 지 속성을 제어 해야 합니다. 자체 IDE 사용자 입력에 따라 항목을 저장 하는 계층 구조를 전달 하지만 IDE는 해당 항목을 저장 하는 데 필요한 모든 작업을 제어 하지 않습니다. 대신, 컨트롤에서 프로젝트가 있습니다.

 사용자가 편집기에서 항목을 열면, 해당 항목을 제어 하는 계층 선택한 활성 계층이 있습니다. 선택한 계층 항목에서 작동 하려면 사용 가능한 명령의 집합을 결정 합니다. 이 방식으로 사용자 포커스 추적 사용자의 현재 컨텍스트를 반영 하 여 계층을 사용 하도록 설정 합니다.

## <a name="see-also"></a>참고 항목
 [프로젝트 형식](../../extensibility/internals/project-types.md) [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md) [VSSDK 샘플](../../misc/vssdk-samples.md)
