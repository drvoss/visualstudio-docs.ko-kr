---
title: 프로젝트 지 속성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c0f81d3cb4cc1e3404087f6ad4b8ecac34b9ec0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328334"
---
# <a name="project-persistence"></a>프로젝트 지속성
지 속성은 프로젝트에 대 한 주요 디자인 고려 사항. 파일을 나타내는 프로젝트 항목을 사용 하는 대부분의 프로젝트 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 도 해당 데이터는 파일 기반 프로젝트를 지원 합니다. 프로젝트 및 프로젝트 파일을 소유한 파일 모두 유지 해야 합니다. IDE 자체 또는 프로젝트 항목을 저장 하려면 프로젝트에 지시 합니다.

 프로젝트 템플릿에서 프로젝트 팩터리에 전달 됩니다. 템플릿은 특정 프로젝트 형식의 요구 사항에 따라 모든 프로젝트 항목의 초기화를 지원 해야 합니다. 이러한 템플릿은 프로젝트 파일로 저장 고 나중에 솔루션을 통해 IDE에 의해 관리 되는 수 있습니다. 자세한 내용은 [만들 프로젝트 인스턴스에서 사용 하 여 프로젝트 팩터리](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) 하 고 [솔루션](../../extensibility/internals/solutions-overview.md)합니다.

 프로젝트 항목에는 파일 기반 또는 파일 기반이 아닌 수 있습니다.

- 로컬 또는 원격 파일 기반 항목 수 있습니다. C# 웹 프로젝트에서 예를 들어 원격 시스템에서 파일에 대 한 연결 유지를 로컬로 파일 자체는 원격 시스템에 유지 하는 반면 합니다.

- 파일 기반이 아닌 항목 데이터베이스 또는 저장소에 항목을 저장할 수 있습니다.

## <a name="commit-models"></a>모델을 커밋
 프로젝트 항목이 있는 위치를 결정 한 후 적절 한 커밋 모델을 선택 해야 합니다. 예를 들어, 로컬 파일을 사용 하 여 파일 기반 모델에서 각 프로젝트를 저장 자율적으로 합니다. 저장소 모델에서 하나의 트랜잭션에서 여러 개의 항목을 저장할 수 있습니다. 자세한 내용은 [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)합니다.

 프로젝트 파일 이름 확장명을 확인 하려면 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 인터페이스를 구현 하는 개체의 클라이언트를 사용 하도록 설정 하는 정보를 제공 하는 **다른 이름으로 저장** 대화 상자-즉,에 맞게를 **형식으로 저장**  드롭 다운 목록 및 초기 파일 이름 확장명을 관리 합니다.

 호출 하 여 IDE `IPersistFileFormat` 인터페이스 프로젝트는 프로젝트를 유지 해야 함을 나타내려면 프로젝트에 항목을 적절 하 게 합니다. 따라서 개체는 해당 파일 및 형식으로의 모든 측면을 담당합니다. 이 개체의 형식 이름을 포함합니다.

 항목이 없는 파일인 경우 `IPersistFileFormat` 는 여전히 어떻게 파일 기반이 아닌 항목이 유지 됩니다. 프로젝트 파일에 대 한.vbp 파일과 같은 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트나.vcproj 파일에 대 한 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트도 유지 되어야 합니다.

 에 대 한 작업을 저장 IDE 검사는 실행 중인 document 테이블 (RDT) 하 고 계층에는 명령을 전달 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 하며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 인터페이스입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> 메서드 항목 수정 되었는지 여부를 확인 하기 위해 구현 됩니다. 항목이 있으면는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> 메서드는 수정 된 항목을 저장 합니다.

 메서드는 `IVsPersistHierarchyItem2` 인터페이스는 사용 하 여 항목을 다시 로드 될 수 있는지 여부를 항목 수를 다시 로드 하는 경우 확인할 수 있습니다. 또한는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> 하면 변경 된 항목이 저장 되지 않고 삭제 하도록 메서드를 구현할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)