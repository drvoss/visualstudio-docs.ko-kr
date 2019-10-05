---
title: 프로젝트 형식을 만들어야 하는 경우 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8be01ef0592deab48d923828ccfd3f86f1311a4d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323059"
---
# <a name="when-to-create-project-types"></a>프로젝트 형식을 만들어야 하는 경우
사용자 지정 하는 기본 제공 새 프로젝트 형식 만들기 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자에 대 한 합니다. 그러나 새 프로젝트 형식을 만들 필요 하지 않습니다 모든 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 지정 합니다. 다음 지침은 새 프로젝트 형식을 시나리오에 필요한 지 여부를 결정 하는 데 도움이 됩니다.

## <a name="create-a-new-project-type"></a>새 프로젝트 형식 만들기
 사용자 지정 하려는 경우 프로젝트 유형을 만들어야 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다음 방법 중 하나 이상의 역할을 합니다.

- 빌드에서 participate, 배포, 구성 및 소스 제어 합니다.

- 디버깅 지원을 제공 합니다.

- 프로젝트 항목에 표시할 **솔루션 탐색기**합니다.

- 사용 된 **프로젝트 열기** 또는 **새 프로젝트** 대화 상자.

- 프로젝트 중첩을 지원 합니다.

## <a name="extend-an-existing-project-type"></a>기존 프로젝트 형식 확장
 사용할 수 있는 새 프로젝트 형식을 만들 수도 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 수정 하거나 기존 프로젝트 형식의 동작을 확장 하려면 다음 방법의 예를 들어 빌드 프로세스에 대 한 수정 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트:

- 하나의 단위로 여러 파일을 사용 합니다.

- 하위 항목의 계층으로 단일 파일을 표시 합니다.

- 편집기 관련 명령을 컨텍스트를 표시 합니다.

- 편집기에 대 한 서비스 컨텍스트를 표시 합니다.

## <a name="use-an-existing-project-type"></a>기존 프로젝트 형식 사용
 새 프로젝트를 만드는 경우에 따라 필요 하지 않습니다. 다음 테이블에 대 한 프로젝트 형식을 만들려면 없는 작업을 보여 줍니다.

|작업|설명|
|----------|-----------------|
|명령 처리|모든 VSPackage 명령을 처리할 수 있습니다.|
|편집기를 작성합니다.|사용자 지정 편집기를 등록할 수 있습니다. 자세한 내용은 [문서 Windows 및 편집기](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)합니다.|
|Windows를 소유합니다.|새 프로젝트 형식을 추가 하지 않고 windows 도구 및 문서를 만들 수 있습니다.|
|속성 창에서 속성을 노출|모든 개체 속성을 노출할 수 있습니다.|

## <a name="create-a-project-subtype"></a>프로젝트 하위 형식 만들기
 새 프로젝트 형식을 만들 필요 없이 관리 되는 프로젝트 형식을 확장 하려면 프로젝트 하위 형식에 사용할 수 있습니다. 프로젝트 하위 형식 COM 집계를 사용 하 여 Microsoft에서 작성 된 관리 되는 프로젝트를 확장 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 또는 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]합니다. COM 집계를 사용 하 여 관리 되는 프로젝트 시스템 구현의 대부분 다시 사용할 수 있으며 인터페이스를 지 원하는 사용 하 여 집계를 통해 특정 시나리오에도 사용자 지정할 수 있습니다. 프로젝트 하위 형식에 대 한 자세한 내용은 참조 하세요. [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)합니다.

## <a name="see-also"></a>참고 항목
- [문서 Windows 및 편집기](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)