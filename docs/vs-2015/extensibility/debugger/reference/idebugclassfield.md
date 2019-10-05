---
title: IDebugClassField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2bd5dfaea68abae6730a97efdff088ca6e7c7a00
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696984"
---
# <a name="idebugclassfield"></a>IDebugClassField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 형식으로 클래스를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 기호 공급자를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스입니다. 이 인터페이스는 클래스 형식을 나타내는 특수화입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 여러 가지 인터페이스를 비롯 하 여이 인터페이스를 반환할 수 있는 방법이 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)를 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), 및 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)합니다. 또한 사용할 수 있습니다 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 에서이 인터페이스를 가져올 수 합니다 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드 플래그를 반환 합니다. `FIELD_TYPE_CLASS`합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 메서드 외에도 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서이 인터페이스에서 다음을 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|이 클래스의 기본 클래스에 대 한 열거자를 만듭니다.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|특정 인터페이스를 클래스에 정의 된 경우를 결정 합니다.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|이 클래스의 중첩 된 클래스에 대 한 열거자를 만듭니다.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|이 클래스를 포함 하는 클래스를 가져옵니다.|  
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|이 클래스에서 구현 된 인터페이스에 대 한 열거자를 만듭니다.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|이 클래스의 생성자에 대 한 열거자를 만듭니다.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|기본 인덱서의 이름을 가져옵니다.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|이 클래스의 중첩 된 열거자에 대 한 열거자를 만듭니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
