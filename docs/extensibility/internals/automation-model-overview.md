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
ms.openlocfilehash: 42b1237825eaa3fe2dec9ffa0142b78bc4693976
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326309"
---
# <a name="automation-model-overview"></a>자동화 모델 개요
자동화 모델 개체는 Visual Studio 추가 기능에서 이나 확장을 작성할 수 있습니다 집합이 이루어져 있습니다. 추가 기능에 Visual Studio 환경을 조작 하 고 일반적인 작업을 자동화할 수 있는 응용 프로그램. Visual Studio 확장 Visual Studio 구성 요소를 사용자 지정 만들거나 텍스트 편집기와 같은 표준 구성 요소의 기능을 추가할 수 있습니다.

## <a name="objects-in-the-automation-model"></a>자동화 모델의 개체
 자동화 모델 환경인의 주요 측면을 제어 하는 개체의 관련된 그룹을 구성 합니다. 다음 다이어그램은 광범위 한 자동화 모델을 구성 하는 Visual Studio 개체 집합을 보여 줍니다.

 ![Visual Studio 자동화 개체 차트](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 자세한 내용은 [Visual Studio 환경 확장](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)합니다.

 환경의 서로 다른 기능 영역에 대 한 모델을 제공합니다. 예를 들어 코드에서 찾을 수 있는 다양 한 요소에 대 한 코드 모델을 있습니다. 다양 한 문서 요소에 대 한 문서 모델이 있습니다. 프로젝트 영역을 한 곳은 VSPackage 공급자 특정 유용 합니다. 새 프로젝트 형식을 거의 동일한 방법으로 자동화 모델에 기여 하는 경우가 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 고 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 자동화 모델에 기여 합니다. 프로세스를 간략하게 설명 [Vspackage에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-vspackages.md)합니다.

 환경의 자동화 모델 확장을 고려할 수 있는 위치:

- 프로젝트

- 문서

- 코드

- 빌드

Automation에 대 한 자세한 내용은 참조 하세요. [Visual Studio의 자동화 및 확장성](../extensibility-in-visual-studio.md)합니다. 이 문서 및 문서 링크, VSPackage에 대 한 자동화를 제공 해야 하는 방법에 대 한 결정을 내릴 수 있도록 제공 합니다.

## <a name="see-also"></a>참고자료
- [방법: 추가 기능 만들기](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)