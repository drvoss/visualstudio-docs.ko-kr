---
title: 중첩 프로젝트에 대 한 마법사 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721430"
---
# <a name="wizard-support-for-nested-projects"></a>중첩된 프로젝트에 대한 마법사 지원
IDE는 중첩 된 프로젝트용 부모 프로젝트에서 구현할 수 있는 두 가지 마법사 인 **새 프로젝트** 마법사와 **항목 추가** 마법사를 실행 합니다.

 사용자가 파일 메뉴에서 **프로젝트 추가** 를 선택 하 고 **새** 프로젝트를 클릭 하거나 **추가** 를 선택 하 고 솔루션 탐색기에서 **새 프로젝트** 를 마우스 오른쪽 단추로 클릭 하 여 **새 프로젝트** 마법사를 시작 하는 경우 IDE는 addproject를 실행 합니다.명령 및 부모 프로젝트의 **addproject** 명령 구현에서는 템플릿 프로젝트 파일 또는 컨텍스트 매개 변수 집합이 있는 마법사 파일 (.vsz)을 반환 합니다.

 마찬가지로, 부모 프로젝트의 **AddItem** 마법사 구현은 다른 컨텍스트 매개 변수 집합을 포함 하는 .vsz 파일을 반환 합니다.

 마법사에 대 한 자세한 내용은 [마법사 (를 참조 하세요. .Vsz 파일](../../extensibility/internals/wizard-dot-vsz-file.md), [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md) 및 [프로젝트 템플릿과 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)