---
title: 자동화 모델 개요 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186729"
---
# <a name="automation-model-overview"></a>자동화 모델 개요
자동화 모델은 Visual Studio 추가 기능 또는 확장을 작성할 수 있는 개체 집합으로 구성 됩니다. 추가 기능은 Visual Studio 환경을 조작 하 고 일반적인 작업을 자동화할 수 있는 응용 프로그램입니다. Visual Studio 확장은 사용자 지정 Visual Studio 구성 요소를 만들거나 텍스트 편집기와 같은 표준 구성 요소의 기능에 추가할 수 있습니다.

## <a name="objects-in-the-automation-model"></a>자동화 모델의 개체
 자동화 모델은 공통 환경의 주요 패싯을 제어 하는 개체의 관련 그룹으로 구성 됩니다. 다음 다이어그램에서는 자동화 모델을 구성 하는 다양 한 Visual Studio 개체 집합을 보여 줍니다.

 ![Visual Studio 자동화 개체 차트](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 자세한 내용은 [Visual Studio 환경 확장](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)을 참조 하세요.

 환경은 다양 한 기능 영역에 대 한 모델을 제공 합니다. 예를 들어 코드에서 찾을 수 있는 다양 한 요소에 대 한 코드 모델이 있습니다. 다양 한 문서 요소에 대 한 문서 모델이 있습니다. 프로젝트 영역인 VSPackage 공급자에 게는 특정 한 영역이 있습니다. 자동화 모델에 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 하 고 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 하는 것과 거의 동일한 방법으로 자동화 모델에 기여할 수 있도록 새 프로젝트 형식이 필요할 수 있습니다. 이 프로세스는 [vspackage에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-vspackages.md)에서 간략하게 설명 합니다.

 환경에 대 한 자동화 모델 확장을 고려할 수 있는 위치:

- 프로젝트

- 문서

- 코드

- 빌드

자동화에 대 한 자세한 내용은 [Visual Studio의 자동화 및 확장성](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015)을 참조 하세요. 이 문서와이 문서에 링크를 제공 하는 문서는 VSPackage에 대 한 자동화를 제공 하는 방법에 대 한 의사 결정을 내리는 데 도움이 됩니다.

## <a name="see-also"></a>참조
- [방법: 추가 기능 만들기](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)