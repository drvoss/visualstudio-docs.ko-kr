---
title: 자동화 모델 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699501"
---
# <a name="automation-model-overview"></a>자동화 모델 개요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

자동화 모델 개체는 Visual Studio 추가 기능에서 이나 확장을 작성할 수 있습니다 집합이 이루어져 있습니다. 추가 기능에 Visual Studio 환경을 조작 하 고 일반적인 작업을 자동화할 수 있는 응용 프로그램. Visual Studio 확장 Visual Studio 구성 요소를 사용자 지정 만들거나 텍스트 편집기와 같은 표준 구성 요소의 기능을 추가할 수 있습니다.  
  
## <a name="objects-in-the-automation-model"></a>자동화 모델의 개체  
 자동화 모델 환경인의 주요 측면을 제어 하는 개체의 관련된 그룹을 구성 합니다. 다음은 광범위 한 자동화 모델을 구성 하는 개체 집합을 보여주는 다이어그램입니다.  
  
 ![Visual Studio 자동화 개체 차트](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio 자동화 개체  
  
 자세한 내용은 [Visual Studio 환경 확장](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)합니다.  
  
 환경의 서로 다른 기능 영역에 대 한 모델을 제공합니다. 예를 들어 코드에서 찾을 수 있는 다양 한 요소에 대 한 코드 모델을 있습니다. 다양 한 문서 요소에 대 한 문서 모델이 있습니다. 프로젝트 영역을 한 곳은 VSPackage 공급자 특정 유용 합니다. 새 프로젝트 형식을 거의 동일한 방법으로 자동화 모델에 기여 하는 경우가 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 고 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 자동화 모델에 기여 합니다. 프로세스를 간략하게 설명 [Vspackage에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-vspackages.md)합니다.  
  
 환경의 자동화 모델 확장을 고려할 수 있는 위치:  
  
- 프로젝트  
  
- 문서  
  
- 코드  
  
- 빌드  
  
  Automation에 대 한 자세한 내용은 참조 하세요. [Visual Studio의 자동화 및 확장성](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6)합니다. 이 문서 및 문서 링크, VSPackage에 대 한 자동화를 제공 해야 하는 방법에 대 한 결정을 내릴 수 있도록 제공 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 추가 기능 만들기](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
