---
title: 새로운&#39;의 원본 제어 플러그 인 API 버전 1.3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93626066441226e7f41963e60e3417e8cc12da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323100"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>새로운&#39;의 원본 제어 플러그 인 API 버전 1.3
원본 제어 플러그 인 API 버전 1.3 고급 제어 기능을 제공 하려면 다음 새 함수를 소개 합니다.

## <a name="changes"></a>변경 내용
 다음 함수는 새 원본 제어 플러그 인 api 버전 1.3:

|함수|개요|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|추가 기능 비트를를 보고 될 수 있습니다.|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|최신 버전을 로컬 디스크에 보다 버전 제어 데이터베이스에 있는 파일을 검사할 수 있습니다.|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|지정 된 파일에 대 한 이름 변경 (이름 바꾸기, 추가 및 삭제)의 상태를 검사할 수|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|버전 제어 데이터베이스에 있는 디렉터리 및 파일을 검사할 수 있습니다.|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|현재 프로젝트에 버전 제어 데이터베이스에서 지정된 된 파일 목록을 추가합니다|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|자동 가져오기"(사용자 인터페이스 표시 됨) 지정된 된 파일의 수행|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|사용자 고유의 옵션에 대 한 액세스를 허용합니다.|

## <a name="see-also"></a>참고 항목
- [시작](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)