---
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3a21e640d6661f8066609bdc344299ccbd63d52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147503"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

식 계산기 (EE) 특정 데이터 개체의 복사본을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 복사할 데이터를 보유 하는 개체입니다.  
  
 `dataOut`  
 [out] 반환 된 새 `IEEDataStorage` 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드에 제공 되는 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 바이트 배열을 나타내는 개체입니다. 이 들어오는 데이터 개체는 일반적으로 EE에서 구현 되지 않습니다. 그러나이 메서드에서 반환 되는 개체는 항상 EE 구현에 있어는 EE에서 구현 된 `IEEDataStorage` 어떤 클래스가 필요한 인터페이스입니다.  
  
 들어오는 제공한 데이터 참고 `IEEDataStorage` 개체는 동일한 데이터를 보내는 이어야 `IEEDataStorage` 개체입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
