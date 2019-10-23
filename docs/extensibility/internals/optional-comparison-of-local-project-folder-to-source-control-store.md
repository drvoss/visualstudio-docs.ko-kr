---
title: 프로젝트 폴더를 소스 제어 저장소와 비교 | Microsoft Docs
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
ms.openlocfilehash: 45bd5b105a2fd24078bc85d8cf5b044351cd78be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726119"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>로컬 프로젝트 폴더와 소스 제어 저장소의 선택적 비교
소스 제어 플러그 인 API 1.2에서 [Sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) 및 [Scctdiff](../../extensibility/sccdirdiff-function.md)함수를 사용 하 여 로컬 프로젝트 폴더와 소스 제어를 비교할 수 있습니다.

 **솔루션 탐색기**내에서 개별 파일 대신 폴더를 선택 하면 **버전 비교** 바로 가기 메뉴에서 소스 제어 플러그 인의 새 [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) 및 [scctdiff](../../extensibility/sccdirdiff-function.md) 를 호출 합니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>새 함수
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 @No__t_0 함수는를 사용 하 여 작업 디렉터리가 원본에서 제어 되는지 여부를 확인 하기 `SccDirDiff` 전에 호출 됩니다. @No__t_0 함수는 현재 로컬 디렉터리와 해당 소스 제어 폴더 간의 차이점을 표시 합니다. 이 명령은 원본 제어 플러그 인에 디렉터리에 대 한 변경 내용 목록을 표시 하도록 요청 합니다. 소스 제어 플러그 인은 차이를 표시 하는 자체 UI를 제공 합니다.

> [!NOTE]
> 이 함수는 [Sccdiff](../../extensibility/sccdiff-function.md)와 동일한 명령 플래그를 사용 합니다. 원본 제어 플러그 인 공급자는 디렉터리에 대 한 "빠른 diff" 작업을 지원 하지 않도록 선택할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)