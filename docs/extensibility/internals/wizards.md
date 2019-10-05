---
title: 마법사 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3b17d7ef3137c48ddda97e1b2b5bbf0e58cf5bb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312833"
---
# <a name="wizards"></a>마법사
일반적으로 추가 되도록 하려면 마법사를 만든 후의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (통합 개발 환경) 다른 사용자가 사용할 수 있도록 합니다. 그러면 추가 마법사에 표시 합니다 **새 프로젝트 추가** 또는 **새 항목 추가** 대화 상자. 보려는 **새 프로젝트 추가** 또는 **새 항목 추가** 대화 상자에서 공개 솔루션을 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**를 가리키고 **추가**, 및 누른 **새 프로젝트** 하거나 **새 항목**합니다.

 마법사에서 구현할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자가 열면 사용 가능한 값의 트리 뷰에서 선택 합니다 **새 프로젝트 추가** 대화 상자 또는 **새 항목 추가** 대화 상자에서 시기는 마우스 오른쪽 단추로 클릭 에 있는 항목 **솔루션 탐색기**합니다.

 프로그램 마법사에서 ite, 새 프로젝트의 이름을 지역화 하는 옵션을 제공할 수 있습니다 하 고 마법사를 선택할 때 표시 되는 아이콘을 확인할 수 있습니다. 다른 사용 가능한 항목을 기준으로 새 항목이 표시 되는 순서를 제어할 수도 있습니다. 항목을 사전순으로 구성할 수 없습니다.

 또한 마법사가 열릴 때 전달 되는 사용자 지정 매개 변수에 따라 다르게 시작 되는 마법사를 제공할 수 있습니다.

 이 섹션의에서 항목에서는를 구현 하는 파일에 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **새 프로젝트 추가** 하 고 **새 항목 추가** 대화 상자를 사용할 수 있는 마법사 및 템플릿 사이에서 마법사를 나열 합니다. 및 마법사에는 IDE에서 제대로 작동 하려면 충족 해야 하는 요구 사항

## <a name="in-this-section"></a>섹션 내용
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 개괄적으로 템플릿 디렉터리 설명 파일 및 폴더, 마법사.vsz 파일 및 대화 상자에서 프로젝트와 연결 된 템플릿 파일을 표시 하려면 IDE에서 작동 하는 방법에 대해 설명 합니다.

- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)

 IDE에서 마법사를 시작 하는 방법에 대해 설명 하 고.vsz 파일의 세 부분을 나열 합니다.

- [마법사 인터페이스(IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 에 대해 설명 합니다 `IDTWizard` 마법사 IDE에서 작업을 구현 해야 하는 인터페이스입니다.

- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)

 마법사를 구현 하는 방법 및 IDE 구현에 컨텍스트 매개 변수를 전달 하는 경우 어떤 일이 발생 하는지 설명 합니다.

- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)

 사용자 지정 매개 변수를 사용 하 여 마법사를 시작한 후 마법사의 작동을 제어 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 형식](../../extensibility/internals/project-types.md)

 새 프로젝트 형식을 디자인 하는 방법에 대 한 정보를 제공 하는 추가 항목에 대 한 링크를 제공 합니다.

- [프로젝트 확장](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 및 솔루션을 사용하여 코드 파일 및 리소스 파일을 구성하는 방법 및 소스 제어를 구현하는 방법을 설명합니다.