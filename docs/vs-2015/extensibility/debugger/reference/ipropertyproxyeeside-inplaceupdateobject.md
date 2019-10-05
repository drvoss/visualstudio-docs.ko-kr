---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c91497815dd18dc138b2eadc462c43785830a033
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199521"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 데이터 개체를 사용 하 여 개체의 데이터를 업데이트 하 고 개체의 새 데이터를 나타내는 새 데이터 개체를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 새 데이터를 포함 하는 개체입니다.  
  
 `dataOut`  
 [out] 반환 된 새 `IEEDataStorage` 대체 데이터를 포함 하는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 실제로 개체의 데이터를 업데이트합니다. 반환 된 데이터 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체는 들어오는 데이터와 동일 하지 않아도 `IEEDataStorage` 개체가 아니라 반환된 된 개체 속성의 현재 값을 반영 해야 합니다.  
  
 들어오는 데이터 개체는 일반적으로 EE에서 구현 되지 않습니다. 그러나이 메서드에서 반환 되는 개체는 항상 EE 구현에 있어는 EE에서 구현 된 `IEEDataStorage` 어떤 클래스가 필요한 인터페이스입니다.  
  
 합니다 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) 메서드 들어오는 데이터 개체를 기준으로 데이터 개체를 만들지만 속성의 원래 데이터는 영향을 주지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
