---
title: 인터페이스 (디버그 인터페이스 액세스 SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5eaf63ac57610e9ebde6703f0b5c15bf9607fdde
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150866"
---
# <a name="interfaces-debug-interface-access-sdk"></a>인터페이스(디버그 인터페이스 액세스 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

메서드는 Vtable 순서의 인터페이스 페이지의 내용에 대 한 테이블의 각 인터페이스에서 사전순으로 나열 됩니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 DIA SDK 디버그 개체에 대 한 가상 및 상대 가상 주소를 계산 하는 방법에 대 한 제어를 제공 합니다.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 디버깅 기호가 소스에 액세스를 시작 합니다.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 디버그 데이터 스트림에서 레코드에 대 한 액세스를 제공합니다.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 데이터 원본에 포함 된 다양 한 디버그 스트림을 열거 합니다.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 데이터 원본에 포함 된 다양 한 프레임 데이터 요소를 열거 합니다.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 데이터 원본에 포함 된 다양 한 삽입 된 소스를 열거 합니다.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 데이터 원본에 포함 된 다양 한 줄 번호를 열거 합니다.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 데이터 원본에 포함 된 다양 한 섹션 기여도 열거 합니다.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 데이터 원본에 포함 된 다양 한 세그먼트를 열거 합니다.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 데이터 원본에 포함 된 다양 한 원본 파일을 열거 합니다.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 사용 가능한 다양 한 스택 프레임을 열거합니다.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 데이터 원본에 포함 된 다양 한 기호를 열거 합니다.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 데이터 원본에 포함 된 다양 한 기호를 주소로 열거 합니다.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 데이터 원본에 포함 된 다양 한 테이블을 열거 합니다.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 스택 프레임의 세부 정보를 표시합니다.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 모듈 또는 이미지의 기본 위치와 메모리 오프셋의 세부 정보를 표시합니다.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 액세스는 프로그램 원본 코드 DIA 데이터 원본에 저장 합니다.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 소스 파일 줄 번호를 이미지 문자의 바이트 블록을 매핑하는 프로세스를 설명 하는 액세스 정보입니다.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 콜백 프로시저 찾기, 위치 시도의 진행률을 보고 하기 위한 사용자 인터페이스를 지원할 DIA 기호에서 받습니다.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 콜백 프로시저 찾기, 찾기 프로세스에 적용할 제한 수 있도록 DIA 기호에서 받습니다.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 DIA 속성 집합의 영구 속성을 읽을 수 있습니다.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 클라이언트 응용 프로그램을 파일 위치에서 지정 된 실행 파일의 바이트를 제공할 수 있습니다.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 클라이언트 응용 프로그램을 상대 가상 주소에 지정 된 대로 실행 파일의 바이트를 제공할 수 있습니다.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 섹션에 기여도 설명 하는 데이터를 검색, 즉, 인접 한 메모리 블록을 제공한 이미지에는 compiland 합니다.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 섹션 수에서 데이터를의 주소 공간 세그먼트를 매핑합니다.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 디버그 기호에 대 한 쿼리 컨텍스트를 제공 합니다.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 원본 파일을 나타냅니다.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 스택 프레임의 속성을 표시 합니다.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 PDB 파일을 사용 하 여 스택을 수행 하는 방법 안내를 제공 합니다.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 호출 사이의 스택 컨텍스트를 유지 관리 합니다 [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 메서드.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 프로그램 디버그 데이터베이스 (PDB) 파일을 사용 하 여 스택을 지원 합니다.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 기호 인스턴스의 속성을 설명합니다.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 DIA 데이터 원본 테이블을 열거합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 열거형 및 DIA SDK의 다양 한 인터페이스에서 사용 되는 구조를 설명 합니다.  
  
 [상수(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 DIA SDK에서 사용할 수 있는 상수를 설명합니다.  
  
## <a name="see-also"></a>참고 항목  
 [참조](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
