---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41add9a334dd6e78a476134845db7d31664755c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871084"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
이 개체에 대 한 원본 데이터를 초기화 하 고 초기 데이터를 포함 하는 개체를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dataOut`  
 [out] 반환 된 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 무엇이 든 반환할 수 있도록 개체를 초기화 하는 데 필요한를 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체의 데이터에 대 한 인터페이스입니다. 이렇게 하면 개체의 데이터를 표시 하 고, 형식 시각화 도우미에서 허용 되는 경우 변경 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)