---
title: 특정 명령에 사용 되는 비트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47dd3b1c75ab7ff206714509a82449d744a02952
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333530"
---
# <a name="bitflags-used-by-specific-commands"></a>특정 명령에 사용 되는 비트
단일 값에 하나 이상의 비트를 설정 하 여 원본 제어 플러그 인 API 함수 개수의 동작을 수정할 수 있습니다. 이러한 값을 비트 라고 합니다. 원본 제어 플러그 인 API에서 사용 하는 다양 한 비트는 사용 하는 함수에 의해 그룹화 여기서 자세히 나와 있습니다.

## <a name="checked-out-flag"></a>체크 아웃 플래그
 에 대 한이 플래그를 설정할 수 있습니다 합니다 [SccAdd](../extensibility/sccadd-function.md) 하거나 [SccCheckin](../extensibility/scccheckin-function.md)합니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|파일을 체크 아웃을 유지 합니다.|

## <a name="add-flags"></a>플래그 추가
 사용 하는 이러한 플래그를 [SccAdd](../extensibility/sccadd-function.md)합니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|소스 제어 플러그 인은 텍스트 또는 이진 파일 인지를 자동으로 검색 해야 합니다.|
|`SCC_FILETYPE_TEXT`|0x01|파일 형식은 텍스트입니다.|
|`SCC_FILETYPE_BINARY`|0x04|이진 파일 형식이입니다. **참고:** `SCC_FILETYPE_TEXT` 고 `SCC_FILETYPE_BINARY` 플래그는 함께 사용할 수 없습니다. 정확히 하나 또는 둘 다 설정 합니다.|
|`SCC_ADD_STORELATEST`|0x02|최신 버전 (델타 없음)만 저장 합니다.|

## <a name="diff-flags"></a>비교 플래그
 합니다 [SccDiff](../extensibility/sccdiff-function.md) 이러한 플래그를 사용 하 여 비교 작업의 범위를 정의 합니다. `SCC_DIFF_QD_xxx` 플래그는 함께 사용할 수 없습니다. 이들 중 하나가 지정 된 경우 제공 될 시각적 피드백은 합니다. "빠른 diff" (QD) 플러그 인을 결정 하지 않는 파일은 다른 경우에 다른 방법입니다. 하나도 이러한 플래그는 지정 된 경우 "visual diff" 이루어집니다. 자세한 파일 차이 계산 하 고 표시 합니다. 요청 된 QD 지원 되지 않는 경우, 다음 가장 적합 한 플러그 인 이동 합니다. 예를 들어, IDE는 체크섬이를 요청 하는 경우 플러그 인 지원 하지 않는 플러그 인은 전체 내용이 확인 (여전히 보다 훨씬 더 빠르게 시각적 표시).

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|대/소문자 차이 무시 합니다.|
|`SCC_DIFF_IGNORESPACE`|0x0004|공백 차이 무시 합니다. **참고:**  합니다 `SCC_DIFF_IGNORECASE` 고 `SCC_DIFF_IGNORESPACE` 플래그는 선택 사항 비트입니다.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|전체 파일 콘텐츠를 비교 하 여 QD입니다.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|체크섬에서 QD 합니다.|
|`SCC_DIFF_QD_TIME`|0x0040|파일 날짜/시간 스탬프에 의해 QD 합니다.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|모든 QD 비트를 확인 하는 데 사용 하는 마스크입니다. 함수에 전달 되지 않습니다. 세 가지 QD 비트는 함께 사용할 수 없습니다. 항상 QD 없는 UI 표시를 의미합니다.|

## <a name="populatelist-flag"></a>PopulateList 플래그
 이 플래그를 사용 하 여는 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 에 `fOptions` 매개 변수입니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE는 파일이 아닌 디렉터리를 전달 합니다.|

## <a name="populatedirlist-flags"></a>PopulateDirList 플래그
 사용 하는 이러한 플래그를 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 에 `fOptions` 매개 변수입니다.

|옵션 값|값|설명|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|한 수준의 디렉터리 (기본값은)에 대 한 디렉터리를 검사 합니다.|
|SCC_PDL_RECURSIVE|0x0001|재귀적으로 각 지정 된 디렉터리 아래에 있는 모든 디렉터리를 검사 합니다.|
|SCC_PDL_INCLUDEFILES|0x0002|검사 프로세스에서 파일 이름을 포함 합니다.|

## <a name="openproject-flags"></a>OpenProject 플래그
 사용 하는 이러한 플래그를 [SccOpenProject](../extensibility/sccopenproject-function.md) 에 `dwFlags` 매개 변수입니다.

|옵션 값|값|설명|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|프로젝트 소스 제어에 없는 경우 만듭니다. 이 플래그를 설정 하지 않으면 만들려면 프로젝트에 대 한 사용자에 게 (하지 않는 한 `SCC_OP_SILENTOPEN` 플래그가 지정 된).|
|SCC_OP_SILENTOPEN|0x00000002L|사용자에 게 프로젝트를 만들려면 반환 `SCC_E_UNKNOWNPROJECT`합니다.|

## <a name="get-flags"></a>플래그 가져오기
 사용 하는 이러한 플래그를 [SccGet](../extensibility/sccget-function.md) 하며 [SccCheckout](../extensibility/scccheckout-function.md)합니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE는 파일이 아닌 디렉터리를 전달: 이러한 디렉터리의 모든 파일을 가져옵니다.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE는 디렉터리를 전달 합니다. 이러한 디렉터리와 모든 해당 하위 디렉터리를 가져옵니다.|

## <a name="noption-values"></a>nOption 값
 사용 하는 이러한 플래그를 [SccSetOption](../extensibility/sccsetoption-function.md) 에 `nOption` 매개 변수입니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|이벤트 큐의 상태를 설정 합니다.|
|`SCC_OPT_USERDATA`|0x00000002L|사용자 데이터에 대 한 지정 `SCC_OPT_NAMECHANGEPFN`합니다.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE는 취소를 처리할 수 있습니다.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|이름 변경에 대 한 콜백을 설정 합니다.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|소스 제어 플러그 인 UI 체크 아웃을 사용 하지 않도록 설정 하 고 작업 디렉터리를 설정 하지 마십시오.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|작업 디렉터리를 지정 하려면 소스 제어 시스템에서 추가 합니다. 직계 하위 항목이 있으면 연결된 된 프로젝트를 공유 하려고 합니다.|

## <a name="dwval-bitflags"></a>dwVal 비트
 사용 하는 이러한 플래그를 [SccSetOption](../extensibility/sccsetoption-function.md) 에 `dwVal` 매개 변수입니다.

|플래그|값|설명|사용한 `nOption` 값|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|이벤트 큐 작업을 일시 중단합니다.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|이벤트 큐 로깅을 사용합니다.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(기본값) 어떠한 취소 모드입니다. 필요한 경우 플러그 인이 제공 해야 합니다.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE는 취소를 처리합니다.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(기본값) 플러그 인 UI에서 체크 아웃 확인 작업 디렉터리 설정 됩니다.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|없는 플러그 인 UI 체크 아웃, 작업 디렉터리가 없습니다.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)