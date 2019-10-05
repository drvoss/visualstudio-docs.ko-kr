---
title: 여러 프로젝트 연결 간 설정 적용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 480ccaac58e67a959454e9d4afa9aa57e817c693
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315837"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>여러 프로젝트 연결 간 설정 적용
소스 제어 플러그 인을 여러 프로젝트 또는 여러 연결 컨텍스트 간에 동일한 소스 제어 작업을 실행 하 일괄 처리 작업을 사용할 수는 원본 제어 플러그 인 API 버전 1.2를 사용 하 여 작성. 중복 제거, 프로젝트별 사용자 환경에서 대화 상자에 일괄 처리를 사용할 수 있습니다.

 원본 제어 플러그 인 API 버전 1.1 (예를 들어 두 웹 프로젝트에서 다른 파일 공유 컴퓨터)를 사용 하 여 빌드된 둘 이상의 연결을 소스 제어 플러그 인에 속하는 여러 항목을 선택 하 고 체크 아웃 하는 사용자, 사용자가 표시 됩니다 동일 대화 상자의 반복적으로 합니다. 이 시나리오를 클릭할 경우에 발생 합니다 **모든 항목에 적용** IDE에는 각 연결 컨텍스트에 대 한 상태로 다시 설정 하기 때문에 대화 상자에서 확인란 합니다.

## <a name="new-capability-flag"></a>새 기능 플래그
 합니다 `SccBeginBatch` 집합 함수는 `SCC_CAP_BATCH` 를 일괄 처리 작업이 진행에서 중임을 나타내는 플래그입니다.

## <a name="new-functions"></a>새 함수
새 함수를 다음 일괄 처리 작업을 지원합니다.

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

`SCCBeginBatch` 함수 그룹의 원본 제어 작업을 시작 합니다. `SccEndBatch` 함수 그룹을 닫습니다. 그룹을 중첩할 수 있습니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)