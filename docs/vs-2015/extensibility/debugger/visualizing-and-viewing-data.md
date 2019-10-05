---
title: 데이터 시각화 및 보기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 719a2b3d073d90ff3977496c7f98ebecb1ab48a7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696306"
---
# <a name="visualizing-and-viewing-data"></a>데이터 시각화 및 보기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

개발자에 게 신속 하 게 의미 있는 방식으로 시각화 도우미 및 데이터를 제공 하는 사용자 지정 뷰어를 입력 합니다. 식 계산기 (EE) 수 뿐만 아니라 타사 형식 시각화 도우미를 지원 뿐만 아니라 자체 사용자 지정 뷰어를 제공 합니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 얼마나 많은 형식 시각화 도우미 및 사용자 지정 뷰어는 호출 하 여 개체의 형식과 연결을 결정 합니다 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 메서드. Visual Studio를 호출 하는 경우 하나 이상의 형식 시각화 도우미 또는 사용자 지정 뷰어에서 사용할 수는 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 뷰어와 시각화 도우미의 목록을 검색 하는 방법 (목록을 실제로 `CLSID`구현 하는 s를 시각화 도우미 및 뷰어) 사용자에 게 표시 합니다.  
  
## <a name="supporting-type-visualizers"></a>형식 시각화 도우미를 지원합니다.  
 인터페이스는 EE 형식 시각화 도우미를 지원 하기 위해 구현 해야 하는 여러 가지가 있습니다. 이러한 인터페이스 두 광범위 한 범주로 구분 될 수 있습니다: 형식 시각화 도우미 및 속성 데이터를 액세스 하는 것입니다.  
  
### <a name="listing-type-visualizers"></a>목록 형식 시각화 도우미  
 EE 지원 구현에서 형식 시각화 도우미 목록 `IDebugProperty3::GetCustomViewerCount` 고 `IDebugProperty3::GetCustomViewerList`입니다. 이러한 메서드 호출이 해당 메서드에 전달 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 하 고 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)합니다.  
  
 합니다 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) 를 호출 하 여 가져온 [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)합니다. 이 메서드는 [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) 인터페이스에서 가져온 합니다 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 인터페이스에 전달 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` 도 필요 합니다 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) 하 고 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 인터페이스에 전달 된 `IDebugParsedExpression::EvaluateSync`합니다. 만드는 데 필요한 인터페이스를 최종를 `IEEVisualizerService` 인터페이스는를 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) EE를 구현 하는 인터페이스입니다. 이 인터페이스를 시각화 되 고 속성을 변경할 수 있습니다. 모든 속성 데이터에 캡슐화 되어는 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 인터페이스는 EE에서 에서도 구현 됩니다.  
  
### <a name="accessing-property-data"></a>속성 데이터에 액세스  
 통해 이루어집니다 속성 데이터에 액세스 하는 [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스입니다. 이 인터페이스를 가져오려면 Visual Studio는 다음과 같이 호출 됩니다. [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 가져올 속성 개체에는 [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스 (구현 하는 동일한 개체에 구현 된 [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스)를 호출 하는 [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 메서드를 `IPropertyProxyEESide` 인터페이스입니다.  
  
 내부 / 외부로 데이터를 모두 전달 합니다 `IPropertyProxyEESide` 인터페이스에 캡슐화 됩니다 합니다 [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) 인터페이스입니다. 이 인터페이스 바이트 배열을 나타내고 EE와 Visual Studio에서 구현 됩니다. 속성의 데이터를 변경 하는 경우 Visual Studio 만듭니다는 `IEEDataStorage` 새 데이터 및 호출을 보유 하는 개체 [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) 새 얻기 위해 해당 데이터 개체를 사용 하 여 `IEEDataStorage` 차례로 하는 개체 전달할 [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) 속성의 데이터를 업데이트 합니다. `IPropertyProxyEESide::CreateReplacementObject` 구현 하는 자체 클래스를 인스턴스화하는 EE를 허용 합니다 `IEEDataStorage` 인터페이스입니다.  
  
## <a name="supporting-custom-viewers"></a>사용자 지정 뷰어를 지원합니다.  
 플래그 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` 에 설정 된 합니다 `dwAttrib` 필드를 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조 (에 대 한 호출에서 반환 된 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) 개체에 연결 하는 사용자 지정 뷰어 있음을 나타내기 위해 .를 사용 하 여 이 플래그를 설정 하는 경우 Visual Studio 가져옵니다 합니다 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 에서 인터페이스를 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 사용 하 여 인터페이스 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)합니다.  
  
 사용자가 사용자 지정 뷰어를 선택 하는 경우 Visual Studio 뷰어를 사용 하 여 사용자 지정 뷰어를 인스턴스화합니다 `CLSID` 에서 제공 하는 `IDebugProperty3::GetCustomViewerList` 메서드. Visual Studio 호출 [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 사용자에 게 값을 표시 합니다.  
  
 일반적으로 `IDebugCustomViewer::DisplayValue` 데이터의 읽기 전용 보기를 표시 합니다. 변경 데이터를 허용 하려면 EE 속성 개체에 변경 데이터를 지 원하는 사용자 지정 인터페이스를 구현 해야 합니다. `IDebugCustomViewer::DisplayValue` 메서드가 사용자 지정 인터페이스를 사용 하 여 데이터 변경을 지원 합니다. 사용자 지정 인터페이스 메서드를 찾습니다는 `IDebugProperty2` 변수로 전달 된 인터페이스는 `pDebugProperty` 인수입니다.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>둘 다를 지 원하는 형식 시각화 도우미 및 사용자 지정 뷰어  
 형식 시각화 도우미 및 사용자 지정 뷰어에 EE 지원할 수는 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 하 고 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 메서드. EE에서 반환 된 값 수가 제공 하는 사용자 지정 뷰어를 추가 하는 먼저 합니다 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 메서드. 둘째, EE 추가 합니다 `CLSID`에서 반환 된 목록에는 자체 사용자 지정 뷰어에 2!s 합니다 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)   
 [형식 시각화 도우미 및 사용자 지정 뷰어](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
