---
title: 프로젝트를 추가 하 고 프로젝트 항목 템플릿 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38ab7a0a14c5a4e832aec330852546b64a41fd0c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315856"
---
# <a name="add-project-and-project-item-templates"></a>프로젝트 및 프로젝트 항목 템플릿 추가
표준을 사용 하 여 새 프로젝트 및 프로젝트 항목을 추가 하는 것에 대 한 지원을 제공 해야 프로젝트 형식을 사용자를 만들 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개발 환경 (IDE) 대화 상자를 통합 합니다. 프로젝트 및 프로젝트 항목을 추가 하는 방법은 다음 항목에 설명 합니다.

## <a name="in-this-section"></a>단원 내용
- [프로젝트 컨텍스트](../../extensibility/internals/project-context.md)

 프로젝트는 대부분의 환경에서 다소 무엇에 대 한 컨텍스트 정보를 설명 합니다.

- [프로젝트 우선 순위](../../extensibility/internals/project-priority.md)

 일반적으로 프로젝트 항목에 대 한 프로젝트 항목을 여는 데 사용 되는 모호성을 방지 하려면 한 프로젝트의 구성원 인지에 대해 설명 합니다.

- [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)

 프로젝트는 프로젝트 항목을 열 때 사용 하는 편집기를 결정 하는 데는 두 가지 유형의 역할 프로젝트에서 파일을 열에 사용할 수 있는 편집기에 대 한 정보를 제공 합니다.

- [프로젝트 및 항목 템플릿을 등록합니다](../../extensibility/internals/registering-project-and-item-templates.md)

 발생 하는 상황에 대해 설명 하면는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트가 만들어집니다.

- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 항목을 추가 하기 위한 프로세스에 설명 합니다 **새 항목 추가** 대화 상자.

- [새 프로젝트 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 VSPackage에서 사용할 수 있는 사용자 지정 템플릿을 포함 하는 새 디렉터리를 등록 하는 예제를 제공 합니다.

- [새 항목 추가 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 에 대 한 디렉터리의 새 집합을 등록 하는 예제를 제공 합니다 **새 항목 추가** 대화 상자.

- [프로젝트 시스템 확장을 위한 IDE 정의 명령](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 다양 한 프로젝트 시스템 확장에 사용 되는 명령 항목을 나열 합니다.

- [일반적으로 프로젝트를 확장 하는 데 사용 되는 개체에 대 한 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 확장 하는 데 사용 되는 개체에 대 한 Catid를 나열 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]하십시오 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 시스템.

## <a name="related-sections"></a>관련 단원
- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)

 기본적으로 프로젝트에 대 한 특정 편집기에 바인딩된 항목을 열기 위한 단계별 지침을 제공 합니다.

- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)

 표준 편집기 열기에 대 한 단계별 지침을 제공 합니다.

- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

 프로젝트 하위 형식 개념 항목에 대 한 링크를 제공 합니다. 기존 프로젝트 하위 형식 확장할 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 고 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트입니다.

- [프로젝트 형식](../../extensibility/internals/project-types.md)

 새 프로젝트 형식을 디자인 하는 방법에 대 한 정보를 제공 하는 추가 항목에 대 한 링크를 제공 합니다.