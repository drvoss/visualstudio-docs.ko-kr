---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b70701aa9c4b339749554601e2a565c17697c6a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186506"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

관리 코드에 관련 된 메서드를 사용 하 여 COM + 기호 공급자를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 구분 기호가 식 계산기 (EE)에 게 유용한 인터페이스와 디버그 엔진 (DE)에서 사용할 수는 없는 경우에 다음 방법 아마도 관심을 가질 만한 DE 개발자만: AreSymbolsLoaded GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols, 하며 UpdateSymbols 합니다.  
  
## <a name="methods"></a>메서드  
 메서드 외에도 합니다 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|응용 프로그램 도메인 식별자를 지정 하는 지정된 된 모듈의 디버그 기호가 로드 하는 경우를 결정 합니다.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|지정된 된 기본 형식에서 형식을 만듭니다.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|디버그 주소 배열에 지정된 된 모듈에 문서 위치를 매핑합니다.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|검색의 디버그 주소 지정 된 경우 지정된 된 배열에 대 한 정보를 입력 합니다.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|모듈 및 응용 프로그램 도메인을 지정 된 어셈블리의 이름을 검색 합니다.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|지정 된 프로그래밍 언어로 구현 되는 지정된 된 특성을 사용 하 여 클래스를 검색 합니다.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|지정 된 모듈의 지정된 된 특성을 사용 하 여 클래스를 검색합니다.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|응용 프로그램 진입점을 검색합니다.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|지정 된 줄 오프셋을 나타내는 함수 내에서 주소를 검색 합니다.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|레이아웃의 지역 변수는 메서드 집합을 검색합니다.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|해당 메타 데이터 개체를 지정 하는 지정된 된 토큰을 사용 하 여 연결 된 이름을 반환 합니다.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|지정된 된 모듈에 대 한 지정 된 부모 특성을 사용 하 여 디버그 기호를 검색합니다.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|비관리 코드에서 사용할 기호 판독기를 검색 합니다.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|해당 디버그 주소 지정 된 기호 형식으로 검색 합니다.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|지정 된 디버그 주소에서 함수는 삭제를 확인 합니다.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|지정 된 디버그 주소는 유효 하지 않은 간주 됩니다 결정 합니다.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|지정한 디버거 주소의 코드 숨겨지는지 여부를 결정 합니다.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|메모리의 지정 된 디버그 기호를 로드합니다.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|로드는 데이터 스트림을 지정 된 기호를 디버그 합니다.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|지정된 된 데이터 스트림에 있는 현재 디버그 기호를 바꿉니다.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|메모리에서 지정된 된 모듈에 대 한 디버그 기호를 언로드합니다.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|지정된 된 데이터 스트림에와 메모리의 디버그 기호를 업데이트합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: Sh.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
