---
title: 디버그 인터페이스 액세스 SDK | Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915f594a984af41da167e0fd3d58beb2f6ddd978
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554911"
---
# <a name="debug-interface-access-sdk"></a>디버그 인터페이스 액세스 SDK

Microsoft 디버그 인터페이스 액세스 소프트웨어 개발 키트 (DIA SDK)는 Microsoft 사후 컴파일러 도구에서 생성 한 프로그램 데이터베이스 (.pdb) 파일에 저장 된 디버그 정보에 대 한 액세스를 제공 합니다. 사후 컴파일러 도구에서 생성 된.pdb 파일의 형식에서 상수 수정, 때문에 형식을 노출 하지 않습니다. DIA API를 사용 하는.pdb 파일에 저장 된 디버그 정보를 찾아 검색 하는 응용 프로그램을 개발할 수 있습니다. 예를 들어, 이러한 응용 프로그램 스택 추적 정보를 보고 하 고 성능 데이터를 분석할 수 있습니다.

## <a name="in-this-section"></a>단원 내용

[시작](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

DIA SDK의 개요 기능을 제공 하 고 필요한 헤더 및 라이브러리 파일 DIA SDK가 설치 하는 위치를 지정 합니다.

[.Pdb 파일 쿼리](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

DIA API를 사용 하 여.pdb 파일을 쿼리 하는 방법에 지침을 제공 합니다.

[기호 및 기호 태그](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

DIA API에서 기호 및 기호 태그를 사용 하는 방법을 설명 합니다.

[참조](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

인터페이스, 메서드, 열거형 및 DIA API의 구조를 포함합니다.

[Dia2dump 샘플](../../debugger/debug-interface-access/dia2dump-sample.md)

DIA API 검색 및 찾아보기 디버그 정보를 사용 하는 방법을 보여 줍니다.
