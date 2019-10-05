---
title: 원본 제어 플러그 인 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01e7a0ca8a509d430a0794a2cedb4b2e9d869585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331819"
---
# <a name="source-control-plug-ins"></a>소스 제어 플러그 인
소스 제어 플러그 인 SDK 참조 섹션에는 소스 제어 시스템으로 통합 될 수 있도록 전체 인터페이스 사양을 포함 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 구문 및 의미 체계의 소스 제어 플러그 인 인터페이스를 구현 해야 하는 다양 한 함수 및 데이터 형식 지정을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 (IDE)입니다.

## <a name="in-this-section"></a>섹션 내용
- [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md) 원본 제어 플러그 인 API를 사용 하 여 준수 하기 위해 소스 제어 플러그 인에서 구현 해야 하는 함수를 나열 합니다.

- [IDE에서 콜백 함수 구현](../extensibility/callback-functions-implemented-by-the-ide.md) 소스 제어 플러그 인이 특정 명령이 실행 되는 동안 IDE를 다시 정보를 전달 하는 함수에 설명 합니다.

- [열거자](../extensibility/enumerators.md) 소스 제어 플러그 인에 대해 알아야 하는 원본 제어 플러그 인 API의 열거자 데이터 형식을 나열 합니다.

- [기능 플래그](../extensibility/capability-flags.md) 에 대해 설명 합니다는 `SCC_CAP_xxx` 는 공급자의 기능을 나타내는 플래그입니다.

- [특정 명령에서 사용 하는 비트](../extensibility/bitflags-used-by-specific-commands.md) 특정 명령의 컨텍스트에서 유용한 플래그를 나열 합니다.

- [오류 코드](../extensibility/error-codes.md) 함수를 반환 하는 일반적인 오류 값을 나열 `SCCTRN`합니다.

- [사용 된 원본 제어 플러그 인을 찾기 위한 키로 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) 소스 제어 플러그 인을 찾을 레지스트리 액세스에 대 한 키에 설명 합니다.

- [MSSCCPRJ 합니다. SCC 파일](../extensibility/mssccprj-scc-file.md) IDE에 불투명 한 정보를 포함 하는 같지만 버전 제어에서 솔루션이 나 프로젝트를 찾으려면 소스 제어 플러그 인에서 사용 되는 클라이언트 쪽 파일에 설명 합니다.

- [원본 제어 플러그 인을 구현 하기 위한 모범 사례](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) 원본 제어 플러그 인 API를 구현 하는 동안 기억해 야 하는 중요 한 기술 미리 알림의 컬렉션을 제공 합니다.

- [문자열 길이 제한](../extensibility/restrictions-on-string-lengths.md) 제한 원본 제어 플러그 인 API에서 다양 한 함수에서 사용 되는 문자열의 길이에 대해 설명 합니다.

- [용어집](../extensibility/source-control-plug-in-glossary.md) 유용한 용어 및 소스 제어 플러그 인 SDK 설명서를 읽기에 대 한 해당 정의 제공 합니다.

- [방법: 소스 제어 플러그 인에 대 한 경고 하는 호환성 설정 해제](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) 경고를 사용 하지 않도록 설정 하는 방법에 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그 인 샘플](https://www.microsoft.com/download/details.aspx?id=55984) 샘플 원본 제어 플러그 인 기능을 제공 합니다.

- [테스트 소스 제어 플러그 인에 대 한 가이드](../extensibility/internals/test-guide-for-source-control-plug-ins.md) 를 소스 제어 플러그 인 관련 된 테스트 절차를 설명 합니다.

- [원본 제어 플러그 인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md) 를 사용 하는 동안 소스 제어 기능을 제공 하는 소스 제어 플러그 인을 만드는 방법을 설명 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 소스 제어 사용자 인터페이스 (UI).

- [Visual Studio SDK 참조](../extensibility/visual-studio-sdk-reference.md) 참조 항목의 목록을 제공 합니다.