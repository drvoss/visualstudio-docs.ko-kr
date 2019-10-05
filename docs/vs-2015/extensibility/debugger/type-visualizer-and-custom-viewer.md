---
title: 시각화 도우미 및 사용자 지정 뷰어를 입력 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185320"
---
# <a name="type-visualizer-and-custom-viewer"></a>형식 시각화 도우미 및 사용자 지정 뷰어
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

형식 시각화 도우미는 매우 구체적인 형식으로 데이터를 표시 하는 구성 요소입니다. 이 형식은 전적으로 시각화 도우미의 구현자, 최종 사용자 또는 제 3 자 공급 업체 시각화 도우미의 수입니다.  
  
 사용자 지정 뷰어는 데이터의 매우 구체적인 형식으로 표시 하는 사용자 지정 식 계산기의 부분입니다. 이 형식은 전적으로 식 계산기 (EE)의 구현자는 형식으로는 사용자 지정 뷰어 구현 자가 됩니다.  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>식 계산기에서 형식 시각화 도우미에 대 한 지원  
 EE 시각화 도우미에 액세스할 수 있는 인터페이스 집합을 지원 하 여 형식 시각화 도우미를 지원할 수 있습니다:와 같은 인터페이스 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 하 고 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)합니다. 단, EE는 자체 형식 시각화 도우미를 구현 하는 것에 대 한 책임: EE 단순히 외부 시각화 도우미에 액세스할 수 있도록 그 형식 정보입니다. 이러한 시각화 도우미는 EE와 함께 제공 되 고 최종 사용자도 또는 다른 타사 공급 업체에서 제공 하는 Visual Studio에서 해당 위치에 설치 될 수 있습니다.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>사용자 지정 뷰어에 식 계산기에 대 한 지원  
 EE 자체는 EE 보기 데이터 형식에 대 한 코드를 제공 하는 사용자 지정 뷰어를 기능도 사용할 수 있습니다. 사용자 지정 뷰어를 구현 합니다 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 인터페이스의 모든 형식으로 데이터를 보여 주는 모든 업무를 처리 하는 필요한; 뷰어에 표시를 완전히 제어할와 데이터를 수정할 수 있습니다. EE 제품 제공 되는 경우는 EE에서 제공 하는 모든 사용자 지정 뷰어가 제공 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)   
 [식 계산기](../../extensibility/debugger/expression-evaluator.md)   
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
