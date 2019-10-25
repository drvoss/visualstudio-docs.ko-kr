---
title: 시작 (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dd6a98f377ba295d6a866c9db95671de4ff16ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745098"
---
# <a name="getting-started-debug-interface-access-sdk"></a>시작(디버그 인터페이스 액세스 SDK)
DIA (디버그 인터페이스 액세스) SDK에서는 DIA API를 사용 하는 방법을 설명 하는 샘플 및 지침 설명서를 제공 합니다. DIA SDK의 인터페이스 및 메서드를 사용 하 여 .pdb 및 dbg 파일을 열고 해당 콘텐츠를 검색 하 여 기호, 값, 특성, 주소 및 기타 디버깅 정보를 검색 하는 사용자 지정 응용 프로그램을 개발할 수 있습니다. 이 SDK는 응용 프로그램에 C++ 있는 기호와 연결 된 속성에 대 한 참조 테이블도 제공 합니다.

 DIA SDK를 최대한 활용 하려면 다음에 대해 잘 알고 있어야 합니다.

- C++프로그래밍 언어

- COM 프로그래밍

- 샘플을 컴파일하기 위한 Visual Studio IDE (통합 개발 환경)

  DIA SDK은 일반적으로 Visual Studio와 함께 설치 되며 기본 위치는 *[drive]* \Files\Microsoft Visual studio 9.0 \ DIA SDK입니다. 설치의 일부로 DIA SDK를 구현 하는 msdia90는 자동으로 등록 되므로 프로그램에 `dia2.h`를 포함 하 고 `diaguids.lib`에 연결 하는 데에만 사용 해야 합니다.

  헤더: include\dia2.h

  라이브러리: lib\diaguids.lib

  DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>단원 내용

[개요](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

DIA의 기본 아키텍처를 검토 합니다.

[.Pdb 파일 쿼리](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

DIA API를 사용 하 여 .pdb 파일을 쿼리 하는 방법에 대 한 단계별 지침을 제공 합니다.

## <a name="see-also"></a>참조

- [디버그 인터페이스 액세스 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)