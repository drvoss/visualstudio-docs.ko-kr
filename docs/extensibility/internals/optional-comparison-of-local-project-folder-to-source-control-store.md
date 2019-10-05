---
title: 프로젝트 폴더와 소스 제어 저장소 비교 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d675868e10a99a192681c52495ad3b37e384d390
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350697"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>로컬 프로젝트 폴더와 소스 제어 저장소의 선택적 비교
원본 제어 플러그 인 API 1.2 로컬 프로젝트 폴더 및 소스 제어 간의 비교 함수를 사용 하 여 이루어집니다 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) 하 고 [SccDirDiff](../../extensibility/sccdirdiff-function.md)합니다.

 내 **솔루션 탐색기**폴더를 선택 하 여 개별 파일을 대신 하는 경우를 **버전 비교** 바로 가기 메뉴를 호출 하는 새 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) 및[ SccDirDiff](../../extensibility/sccdirdiff-function.md) 소스 제어 플러그 인입니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>새 함수
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 합니다 `SccDirQueryInfo` 하기 전에 함수가 호출 될 `SccDirDiff` 소스 제어 작업 디렉터리 인지 확인 하려면. `SccDirDiff` 함수는 현재 로컬 디렉터리와 해당 소스 제어 폴더 간의 차이 표시 합니다. 이 명령은 디렉터리 변경 내용 목록을 표시 하려면 플러그 인 소스 제어를 요청 합니다. 소스 제어 플러그 인 차이점을 표시 하는 자체 UI를 제공 합니다.

> [!NOTE]
> 이 함수는 동일한 명령 플래그를 사용 [SccDiff](../../extensibility/sccdiff-function.md)합니다. 원본 제어 플러그 인 공급자 디렉터리에 대 한 "빠른 diff" 작업을 지원 하지 않도록 선택할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)