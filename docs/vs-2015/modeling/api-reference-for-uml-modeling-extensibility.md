---
title: UML 모델링 확장성에 대 한 API 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12eadb9844df5da78b11367708fed715f1c13672
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159679"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>UML 모델링 확장성을 위한 API 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로그램 코드를 작성하여 Visual Studio에서 만든 모델을 읽고 수정할 수 있습니다. API 참조는 이 작업에 도움이 되는 특정 클래스에 대한 정보를 제공합니다. 자세한 작업 지향 정보 항목을 참조 하세요 [확장: UML 모델 및 다이어그램](../modeling/extend-uml-models-and-diagrams.md)합니다. UML 모델을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.  
  
## <a name="assemblies"></a>어셈블리  
  
|어셈블리|수행할 수 있는 기능|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|-읽기 및 IUseCase, IAssociation 등과 같은 모델 요소를 변경 합니다.<br />-요소 간의 관계를 탐색 합니다.<br /><br /> 네임스페이스 및 형식은 UML 사양에 정의된 것과 일치합니다.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-모델 요소의 새 인스턴스 만들기<br />-액세스 하 고 모양 및 다이어그램을 수정 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [UML 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md)   
 [Visual Studio용 모델링 SDK에 대한 API 참조](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
