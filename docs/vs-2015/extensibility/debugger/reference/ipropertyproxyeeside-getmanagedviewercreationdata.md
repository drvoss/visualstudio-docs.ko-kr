---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5161894875ac683e5a6e49ae623bd6025531006
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199523"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

해당 뷰어를 인스턴스화하기 위해이 속성 형식에 대 한 뷰어에 대 한 정보를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `assemName`  
 [out] 이 개체를 보유 하는 어셈블리의 이름을 반환 합니다.  
  
 `assemBytes`  
 [out] 반환 된 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) (이 경우 null 값을 사용할 수 없는 바이트)이이 개체의 어셈블리 바이트를 포함 하는 개체입니다.  
  
 `assemPdb`  
 [out] 반환 된 `IEEDataStorage` 기호를 포함 하는 개체 (이 null 값인 경우 기호 저장소가 없으면 사용할 수 있는 경우)이이 개체에 대 한 정보를 저장 합니다.  
  
 `className`  
 [out] 이 개체가 포함 된 클래스 이름을 반환 합니다.  
  
 `alr`  
 [out] 값을 반환 합니다 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) 어셈블리의 위치를 나타내는 열거형입니다.  
  
 `replacementOk`  
 [out] 0이 아닌 값을 반환 합니다 (`TRUE`)이이 개체의이 값을 변경할 수 있습니다; 경우에 0 (`FALSE`) 개체가 읽기 전용인 경우.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 관리 되는 뷰어를 인스턴스화할 형식 시각화 도우미에서 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
