---
title: 형식 시각화 도우미 및 사용자 지정 뷰어 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f7e977df6236ea8c3310312114ba4fa30d5003a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344197"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>형식 시각화 도우미 및 사용자 지정 뷰어 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 형식 시각화 도우미 및 사용자 지정 뷰어 번호의 16 진수 덤프를 간단한 보다 의미 있는 방식으로 특정 형식의 데이터를 보려면 사용자를 허용 합니다. 식 계산기 (EE)는 특정 유형의 데이터 또는 변수를 사용 하 여 사용자 지정 뷰어를 연결할 수 있습니다. 이러한 사용자 지정 뷰어는 EE에서 구현 됩니다. EE 수 최종 사용자 또는 다른 타사 공급 업체에서 제공 되는 외부 형식 시각화 도우미 기능도 사용할 수 있습니다.

## <a name="discussion"></a>토론

### <a name="type-visualizers"></a>형식 시각화 도우미
 Visual Studio 조사식 창에 표시 되는 형식 시각화 도우미 및 모든 개체에 대 한 사용자 지정 뷰어 목록을 요청 합니다. 식 계산기 (EE)는 형식 시각화 도우미 및 사용자 지정 뷰어를 지원 하려는 모든 형식에 대 한 목록을 제공 합니다. 에 대 한 호출 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 하 고 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 형식 시각화 도우미 및 사용자 지정 뷰어를 액세스 하는 전체 과정을 시작 (참조 [시각화 및 데이터 보기](../../extensibility/debugger/visualizing-and-viewing-data.md)호출 시퀀스에 대 한 세부 정보에 대 한).

### <a name="custom-viewers"></a>사용자 지정 뷰어
 사용자 지정 뷰어는 특정 데이터 형식에 대 한 EE에서 구현 되 고 표시 됩니다는 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 인터페이스입니다. 사용자 지정 뷰어 유연 하지는 않습니다 형식 시각화 도우미,으로 해당 특정 사용자 지정 뷰어를 구현 하는 EE를 실행 하는 경우에 사용할 수 있기 때문입니다. 사용자 지정 뷰어 구현 형식 시각화 도우미에 대 한 지원을 구현 보다 쉽습니다. 그러나 형식 시각화 도우미를 지 원하는 유연 하 게 최대 최종 사용자에 게 해당 데이터를 시각화 합니다. 이 기사의 나머지 부분에는 형식 시각화 도우미만 관련이 있습니다.

## <a name="interfaces"></a>인터페이스
 EE Visual Studio에서 사용할 수 있도록 형식 시각화 도우미를 지원 하려면 다음 인터페이스를 구현 합니다.

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE 형식 시각화 도우미를 지원 하려면 다음 인터페이스를 사용 합니다.

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>참고자료
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [데이터 시각화 및 보기](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)