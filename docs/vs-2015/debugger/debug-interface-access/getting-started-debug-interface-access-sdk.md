---
title: (디버그 인터페이스 액세스 SDK)를 시작 하기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164168"
---
# <a name="getting-started-debug-interface-access-sdk"></a>시작(디버그 인터페이스 액세스 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 인터페이스 액세스 (DIA) SDK 지침 설명서와 DIA API를 사용 하는 방법을 보여 주는 샘플을 제공 합니다. .Pdb 및.dbg 파일을 열고 기호, 값, 특성, 주소 및 기타 디버깅 정보에 대 한 해당 콘텐츠를 검색 하는 사용자 지정 응용 프로그램을 개발할 DIA SDK의 인터페이스 및 메서드를 사용 합니다. 기호를 사용 하 여 연결 속성에 대 한이 SDK 참조 테이블에도 C++ 응용 프로그램입니다.  
  
 가장 DIA SDK를 사용 하려면 다음을 사용 하 여 알아두어야 하 합니다.  
  
- C++프로그래밍 언어  
  
- COM 프로그래밍  
  
- Visual Studio 통합된 개발 환경 (IDE) 예제를 컴파일하기 위해  
  
  DIA SDK가 Visual Studio를 사용 하 여 정상적으로 설치 및 해당 기본 위치가 *[드라이브]* \Program Files\Microsoft Visual Studio 9.0\DIA SDK. 설치의 일부로, DIA SDK를 구현 하는 msdia90.dll를 자동으로 등록 됩니다 있으므로 포함 하는 것이 사용 하기 위해 수행 해야 하는 모든 `dia2.h` 프로그램에 대 한 링크 `diaguids.lib`합니다.  
  
  헤더: include\dia2.h  
  
  라이브러리: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>섹션 내용  
 [개요](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 동안의 기본 아키텍처를 검토합니다.  
  
 [.Pdb 파일 쿼리](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 DIA API를 사용 하 여.pdb 파일을 쿼리 하는 방법에 대 한 단계별 지침을 제공 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버그 인터페이스 액세스 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
