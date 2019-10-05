---
title: 디버깅을 위한 SDK 도우미 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74b9047ef6df1e6bf20a5b5a95e40e27ed1b1926
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329210"
---
# <a name="sdk-helpers-for-debugging"></a>디버깅을 위한 SDK 도우미
이러한 함수 및 선언 기호 공급자, 식 계산기 및 디버그 엔진 구현에 대 한 전역 도우미 함수는 C++입니다.

> [!NOTE]
> 지금은이 기능 및 선언에 관리 되는 버전이 있습니다.

## <a name="overview"></a>개요
 Visual Studio에서 사용할 디버그 엔진, 식 계산기 및 기호 공급자에 대 한 순서에는 등록 되어야 합니다. 이 레지스트리 하위 키 및 "설정 메트릭" 라고도 하는 항목을 설정 하 여 작업 수행 다음 전역 함수는 이러한 메트릭을 업데이트 하는 프로세스가 용이 하도록 설계 되었습니다. 이러한 함수에 의해 업데이트 되는 각 레지스트리 하위 키의 레이아웃을 확인 하려면 레지스트리 위치에 섹션을 참조 하세요.

## <a name="general-metric-functions"></a>일반 메트릭 함수
 이들은 디버그 엔진에서 사용 되는 일반 함수입니다. 식 계산기에 대 한 함수를 특수화 하 고 기호 공급자는 나중에 자세히 설명 합니다.

### <a name="getmetric-method"></a>GetMetric 메서드
 레지스트리에서 메트릭 값을 검색합니다.

```cpp
HRESULT GetMetric(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD * pdwValue,
   LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszMachine|[in] 해당 등록을 쓸 수 있는 원격 컴퓨터의 이름 (`NULL` 로컬 컴퓨터를 의미).|
|pszType|[in] 메트릭 유형 중 하나입니다.|
|guidSection|[in] 특정 엔진, 계산기, 예외 등의 GUID입니다. 특정 요소에 대 한 메트릭 유형 아래 하위 섹션을 지정합니다.|
|pszMetric|[in] 가져올 메트릭입니다. 이 특정 값 이름에 해당 합니다.|
|pdwValue|[in] 메트릭 값의 저장소 위치입니다. 이 예에서 같이 DWORD, BSTR, GUID 또는 Guid의 배열을 반환할 수 있는 GetMetric의 여러 가지 특색이 있습니다.|
|pszAltRoot|[in] 사용 하는 대체 레지스트리 루트입니다. 로 `NULL` 기본값을 사용 하도록 합니다.|

### <a name="setmetric-method"></a>SetMetric 메서드
 레지스트리에 지정된 된 메트릭 값을 설정합니다.

```cpp
HRESULT SetMetric(
         LPCWSTR pszType,
         REFGUID guidSection,
         LPCWSTR pszMetric,
   const DWORD   dwValue,
         bool    fUserSpecific,
         LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszType|[in] 메트릭 유형 중 하나입니다.|
|guidSection|[in] 특정 엔진, 계산기, 예외 등의 GUID입니다. 특정 요소에 대 한 메트릭 유형 아래 하위 섹션을 지정합니다.|
|pszMetric|[in] 가져올 메트릭입니다. 이 특정 값 이름에 해당 합니다.|
|dwValue|[in] 메트릭 값의 저장소 위치입니다. (이 예제)의 DWORD, BSTR, GUID 또는 Guid의 배열에 저장할 수 있는 SetMetric의 여러 가지 특색이 있습니다.|
|fUserSpecific|[in] 메트릭을 사용자별와 로컬 컴퓨터 하이브 대신 사용자의 hive에 써야 하는 경우 TRUE입니다.|
|pszAltRoot|[in] 사용 하는 대체 레지스트리 루트입니다. 로 `NULL` 기본값을 사용 하도록 합니다.|

### <a name="removemetric-method"></a>RemoveMetric 메서드
 레지스트리에서 지정 된 메트릭을 제거합니다.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszType|[in] 메트릭 유형 중 하나입니다.|
|guidSection|[in] 특정 엔진, 계산기, 예외 등의 GUID입니다. 특정 요소에 대 한 메트릭 유형 아래 하위 섹션을 지정합니다.|
|pszMetric|[in] 제거할 메트릭입니다. 이 특정 값 이름에 해당 합니다.|
|pszAltRoot|[in] 사용 하는 대체 레지스트리 루트입니다. 로 `NULL` 기본값을 사용 하도록 합니다.|

### <a name="enummetricsections-method"></a>EnumMetricSections 메서드
 레지스트리에서 다양 한 메트릭 섹션을 열거합니다.

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszMachine|[in] 해당 등록을 쓸 수 있는 원격 컴퓨터의 이름 (`NULL` 로컬 컴퓨터를 의미).|
|pszType|[in] 메트릭 유형 중 하나입니다.|
|rgguidSections|[out에서] 채울 Guid의 미리 할당 된 배열입니다.|
|pdwSize|[in] 에 저장 될 수 있는 Guid의 최대 수는 `rgguidSections` 배열입니다.|
|pszAltRoot|[in] 사용 하는 대체 레지스트리 루트입니다. 로 `NULL` 기본값을 사용 하도록 합니다.|

## <a name="expression-evaluator-functions"></a>식 계산기 함수

|함수|설명|
|--------------|-----------------|
|GetEEMetric|레지스트리에서 메트릭 값을 검색합니다.|
|SetEEMetric|레지스트리에 지정된 된 메트릭 값을 설정합니다.|
|RemoveEEMetric|레지스트리에서 지정 된 메트릭을 제거합니다.|
|GetEEMetricFile|파일 이름을 지정 된 메트릭을에서 가져오고 로드 파일 내용을 문자열로 반환 합니다.|

## <a name="exception-functions"></a>예외 함수

|함수|설명|
|--------------|-----------------|
|GetExceptionMetric|레지스트리에서 메트릭 값을 검색합니다.|
|SetExceptionMetric|레지스트리에 지정된 된 메트릭 값을 설정합니다.|
|RemoveExceptionMetric|레지스트리에서 지정 된 메트릭을 제거합니다.|
|RemoveAllExceptionMetrics|모든 예외 메트릭 레지스트리에서 제거합니다.|

## <a name="symbol-provider-functions"></a>기호 공급자 함수

|함수|설명|
|--------------|-----------------|
|GetSPMetric|레지스트리에서 메트릭 값을 검색합니다.|
|SetSPMetric|레지스트리에 지정된 된 메트릭 값을 설정합니다.|
|RemoveSPMetric|레지스트리에서 지정 된 메트릭을 제거합니다.|

## <a name="enumeration-functions"></a>열거형 함수

|함수|설명|
|--------------|-----------------|
|EnumMetricSections|지정된 된 메트릭 형식에 대 한 모든 메트릭을 열거합니다.|
|EnumDebugEngine|등록 된 디버그 엔진을 열거합니다.|
|EnumEEs|등록 된 식 계산기를 열거합니다.|
|EnumExceptionMetrics|모든 예외 메트릭을 열거합니다.|

## <a name="metric-definitions"></a>메트릭 정의
 미리 정의 된 메트릭 이름에 대 한 이러한 정의 사용할 수 있습니다. 와이드 문자 문자열로 정의 된 모든 다양 한 레지스트리 키 및 값 이름에 해당 하는 이름을: 예를 들어 `extern LPCWSTR metrictypeEngine`합니다.

|미리 정의 된 메트릭 종류|설명: 에 대 한 기본 키를 하는 중...|
|-----------------------------|---------------------------------------|
|metrictypeEngine|모든 디버그 엔진 메트릭.|
|metrictypePortSupplier|모든 포트 공급자 메트릭입니다.|
|metrictypeException|모든 예외 메트릭입니다.|
|metricttypeEEExtension|모든 식 계산기 확장 합니다.|

|디버그 엔진 속성|설명|
|-----------------------------|-----------------|
|metricAddressBP|로 주소 중단점에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricAlwaysLoadLocal|로 항상 로컬로 디버그 엔진을 로드 하기 위해 0이 아닌 값입니다.|
|metricLoadInDebuggeeSession|사용 되지 않음|
|metricLoadedByDebuggee|로 또는 디버그 중인 프로그램에서 디버그 엔진 로드 항상는 0이 아닌 값입니다.|
|metricAttach|로 설정 하 고 기존 프로그램 첨부 파일에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricCallStackBP|로 호출 스택 중단점에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricConditionalBP|로 조건부 중단점의 설정에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricDataBP|로의 데이터에서 변경 중단점 설정에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricDisassembly|디스어셈블리 목록에 대 한 지원을 나타내는 데 0이 아닌 값으로 설정 합니다.|
|metricDumpWriting|로 설정 (의 덤프를 출력 장치로 메모리)를 작성 하는 덤프에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricENC|편집 하며 계속 하기 지원을 나타내는 데 0이 아닌 값으로 설정 합니다. **참고:**  사용자 지정 디버그 엔진을이 설정 안 또는 0을 항상 설정 해야 합니다.|
|metricExceptions|로 예외에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricFunctionBP|로 명명 된 중단점 (특정 함수 이름의 호출 될 때 중단 되는 중단점)에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricHitCountBP|로 설정 "지점 hit" 중단점 (특정 횟수 만큼 적중 된 후에 트리거되는 중단점)의 설정에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricJITDebug|Just-in-time 디버깅 (디버거를 시작할 실행 중인 프로세스에서 예외가 발생 하는 경우)에 대 한 지원을 나타내는 데 0이 아닌 값으로 설정 합니다.|
|metricMemory|사용 되지 않음|
|metricPortSupplier|구현 된 경우이 포트 공급자의 CLSID로 설정 합니다.|
|metricRegisters|사용 되지 않음|
|metricSetNextStatement|로 설정 (중간 문 실행을 건너뜁니다)는 다음 문을 설정에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricSuspendThread|로 스레드 실행을 일시 중단에 대 한 지원을 나타내는 데 0이 아닌 값입니다.|
|metricWarnIfNoSymbols|로 기호가 없는 경우 사용자에 알릴지를 나타내는 0이 아닌 값입니다.|
|metricProgramProvider|프로그램 공급자의 CLSID로 설정 합니다.|
|metricAlwaysLoadProgramProviderLocal|이 해야 함을 나타내려면 프로그램 공급자 항상 로드 로컬로에 0이 아닌 값으로 설정 합니다.|
|metricEngineCanWatchProcess|이 설정 디버그 엔진 프로그램 공급자 대신 이벤트 처리에 대 한 감시를 나타내려면 0이 아닌 합니다.|
|metricRemoteDebugging|이 설정 원격 디버깅에 대 한 지원을 나타내는 데 0이 아닌 합니다.|
|metricEncUseNativeBuilder|편집 하며 계속 하기에 대 한 빌드를 편집 및 계속 관리자에는 디버그 엔진의 encbuild.dll 사용 해야 함을 나타내려면 0이 아닌 값으로 설정 합니다. **참고:**  사용자 지정 디버그 엔진을이 설정 안 또는 0을 항상 설정 해야 합니다.|
|metricLoadUnderWOW64|64 비트 프로세스를 디버깅 하는 경우 wow 디버기 프로세스에 디버그 엔진을 로드 해야는 나타내려면 0이 아닌 값으로 설정 그렇지 않으면 디버그 엔진 (WOW64에서 실행 되 고)는 Visual Studio 프로세스에서 로드 됩니다.|
|metricLoadProgramProviderUnderWOW64|이 값을 설정 해야 함을 나타내려면 프로그램 공급자는 디버기 프로세스에 로드 된 wow; 64 비트 프로세스를 디버깅 하는 경우에 0이 아닌 값 그렇지 않은 경우 Visual Studio 프로세스에서 로드 됩니다.|
|metricStopOnExceptionCrossingManagedBoundary|이 설정 관리/비관리 코드 간에 예외가 throw 되 면 프로세스를 중지 해야 함을 나타내려면 0이 아닌 합니다.|
|metricAutoSelectPriority|디버그 엔진 (높은 값이 더 높은 우선 순위)의 자동 선택에 대 한 우선 순위를 설정 합니다.|
|metricAutoSelectIncompatibleList|자동 선택에서 무시할 디버그 엔진에 대 한 Guid를 지정 하는 항목을 포함 하는 레지스트리 키입니다. 이러한 항목은 숫자 (0, 1, 2 및 등) 문자열로 표현 된 GUID를 사용 하 여 합니다.|
|metricIncompatibleList|이 디버그 엔진을 사용 하 여 호환 되지 않는 디버그 엔진에 대 한 Guid를 지정 하는 항목을 포함 하는 레지스트리 키입니다.|
|metricDisableJITOptimization|이 설정 (관리 코드용)-just-in-time 최적화는 디버깅 중 비활성화 해야 나타내려면 0이 아닌 합니다.|

|식 계산기 속성|설명|
|-------------------------------------|-----------------|
|metricEngine|이 지 원하는 지정 된 식 계산기는 디버그 엔진 수를 보유 합니다.|
|metricPreloadModules|이 설정는 모듈을 미리 설치 해야 식 계산기를 프로그램에 대해 시작 될 때를 나타내는 0이 아닌 합니다.|
|metricThisObjectName|"This" 개체 이름으로 설정 합니다.|

|식 계산기 확장 속성|설명|
| - |-----------------|
|metricExtensionDll|이 확장을 지 원하는 dll의 이름입니다.|
|metricExtensionRegistersSupported|지원 되는 레지스터의 목록입니다.|
|metricExtensionRegistersEntryPoint|레지스터에 액세스 하기 위한 진입점입니다.|
|metricExtensionTypesSupported|지원 되는 형식의 목록입니다.|
|metricExtensionTypesEntryPoint|형식에 액세스 하기 위한 진입점입니다.|

|포트 공급자 속성|설명|
|------------------------------|-----------------|
|metricPortPickerCLSID|(포트를 선택 하 고 디버깅에 사용할 포트를 추가 하려면 대화 상자를 사용할 수 있음) 포트 선택기의 CLSID입니다.|
|metricDisallowUserEnteredPorts|포트 공급자에 게 사용자가 입력 한 포트를 추가할 수 없는 경우 0이 아닌 (이렇게 하면 포트 선택 대화 상자를 기본적으로 읽기 전용).|
|metricPidBase|프로세스 Id를 할당 하는 경우 포트 공급자에서 사용 하는 기본 프로세스 ID입니다.|

|미리 정의 된 SP 저장소 형식|설명|
|-------------------------------|-----------------|
|storetypeFile|기호는 별도 파일에 저장 됩니다.|
|storetypeMetadata|기호는 어셈블리에서 메타 데이터로 저장 됩니다.|

|기타 속성|설명|
|------------------------------|-----------------|
|metricShowNonUserCode|이 설정 nonuser 코드를 표시 하려면 0이 아닌 합니다.|
|metricJustMyCodeStepping|이 설정 단계별 사용자 코드에만 발생할 수 있다는 것을 나타내려면 0이 아닌 합니다.|
|metricCLSID|특정 메트릭 형식의 개체에 대 한 CLSID입니다.|
|metricName|특정 메트릭 형식의 개체에 대 한 친숙 한 이름입니다.|
|metricLanguage|언어 이름입니다.|

## <a name="registry-locations"></a>레지스트리 위치
 메트릭을 읽고 특히 레지스트리에 기록 된 `VisualStudio` 하위 키입니다.

> [!NOTE]
> 대부분의 경우 HKEY_LOCAL_MACHINE 키에 메트릭이 기록 됩니다. 그러나 때로는 HKEY_CURRENT_USER 됩니다 대상 키입니다. Dbgmetric.lib 두 키를 처리합니다. HKEY_CURRENT_USER 검색 메트릭의 가져올 때 가장 먼저 다음 HKEY_LOCAL_MACHINE입니다. 메트릭, 설정 되 면 매개 변수를 사용 하는 최상위 키를 지정 합니다.

 *[레지스트리 키]* \

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[version root]* \

 *[metric root]* \

 *[메트릭 유형]* \

 *[metric] = [metric value]*

 *[metric] = [metric value]*

 *[metric] = [metric value]*

|자리 표시자|설명|
|-----------------|-----------------|
|*[레지스트리 키]*|`HKEY_CURRENT_USER` 또는 `HKEY_LOCAL_MACHINE`|
|*[version root]*|Visual Studio 버전 (예를 들어 `7.0`, `7.1`, 또는 `8.0`). 그러나이 루트 수정할 수도 있습니다를 사용 하는 **/rootsuffix** 전환할 **devenv.exe**합니다. VSIP,이 한정자는 일반적으로 **Exp**이므로 버전 루트 것, 예를 들어 8.0Exp 합니다.|
|*[metric root]*|이 값은 `AD7Metrics` 또는 `AD7Metrics(Debug)`dbgmetric.lib의 디버그 버전 사용 여부에 따라 합니다. **참고:**  디버그와 릴리스 간에 차이가 있을 경우이 명명 규칙을 따라야 dbgmetric.lib 사용 여부 버전 레지스트리에서 반영 되어야 합니다.|
|*[메트릭 유형]*|쓸 메트릭 형식: `Engine`하십시오 `ExpressionEvaluator`, `SymbolProvider`등. 이러한 모든과 같이 정의 되어으로 dbgmetric.h `metricTypeXXXX`여기서 `XXXX` 특정 형식 이름입니다.|
|*[metric]*|메트릭을 설정 하기 위해 값을 할당할 수는 항목의 이름입니다. 메트릭의 실제 조직의 메트릭 유형에 따라 달라 집니다.|
|*[메트릭 값]*|메트릭을 할당할 값입니다. 값 (문자열, 숫자 등) 있어야 합니다. 형식 메트릭에 따라 달라 집니다.|

> [!NOTE]
> 형식의 저장 된 모든 Guid `{GUID}`합니다. 예를 들어, `{123D150B-FA18-461C-B218-45B3E4589F9B}`을 입력합니다.

### <a name="debug-engines"></a>디버그 엔진
 다음은 레지스트리에 디버그 엔진 메트릭의 조직입니다. `Engine` 디버그 엔진에 대 한 메트릭 유형 이름이 며 해당 *[메트릭 유형]* 위의 레지스트리 하위 트리.

 `Engine`\

 *[engine guid]* \

 `CLSID` =  *[클래스 guid]*

 *[metric] = [metric value]*

 *[metric] = [metric value]*

 *[metric] = [metric value]*

 `PortSupplier`\

 `0` =  *[포트 공급자 guid]*

 `1` =  *[포트 공급자 guid]*

|자리 표시자|설명|
|-----------------|-----------------|
|*[engine guid]*|디버그 엔진의 GUID입니다.|
|*[클래스 guid]*|이 디버그 엔진을 구현 하는 클래스의 GUID입니다.|
|*[포트 공급자 guid]*|있는 경우 포트 공급자의 GUID입니다. 많은 디버그 엔진 기본 포트 공급자를 사용 하 여 및 따라서 자체 공급자를 지정 하지 마세요. 이 경우 하위 키 `PortSupplier` 없어야 합니다.|

### <a name="port-suppliers"></a>포트 공급자
 다음은 레지스트리에 포트 공급자 메트릭의 조직입니다. `PortSupplier` 포트 공급자에 대 한 메트릭 유형 이름이 며 해당 *[메트릭 유형]* 합니다.

 `PortSupplier`\

 *[포트 공급자 guid]* \

 `CLSID` =  *[클래스 guid]*

 *[metric] = [metric value]*

 *[metric] = [metric value]*

|자리 표시자|설명|
|-----------------|-----------------|
|*[포트 공급자 guid]*|포트 공급자의 GUID|
|*[클래스 guid]*|이 포트 공급자를 구현 하는 클래스의 GUID|

### <a name="symbol-providers"></a>기호 공급자
 다음은 레지스트리에 기호 공급자 메트릭의 조직입니다. `SymbolProvider` 기호 공급자에 대 한 메트릭 유형 이름이 며 해당 *[메트릭 유형]* 합니다.

 `SymbolProvider`\

 *[기호 공급자 guid]* \

 `file`\

 `CLSID` =  *[클래스 guid]*

 *[metric] = [metric value]*

 *[metric] = [metric value]*

 `metadata`\

 `CLSID` =  *[클래스 guid]*

 *[metric] = [metric value]*

 *[metric] = [metric value]*

|자리 표시자|설명|
|-----------------|-----------------|
|*[기호 공급자 guid]*|기호 공급자의 GUID|
|*[클래스 guid]*|이 기호 공급자를 구현 하는 클래스의 GUID|

### <a name="expression-evaluators"></a>식 계산기
 다음은 레지스트리에 식 계산기 메트릭의 조직입니다. `ExpressionEvaluator` 식 계산기에 대 한 메트릭 유형 이름이 며 해당 *[메트릭 유형]* 합니다.

> [!NOTE]
> 에 대 한 메트릭 유형에 `ExpressionEvaluator` 식 계산기에 대 한 모든 메트릭 변경 사항 적절 한 식 계산기 메트릭 기능을 통해 진행 될를 가정 하는 대로 dbgmetric.h에에서 정의 되지 않은 (의 레이아웃을 `ExpressionEvaluator` 하위 키를 어느 정도 복잡 한 세부 정보 내 dbgmetric.lib 숨겨져 있으므로).

 `ExpressionEvaluator`\

 *[언어 guid]* \

 *[vendor guid]* \

 `CLSID` =  *[클래스 guid]*

 *[metric] = [metric value]*

 *[metric] = [metric value]*

 `Engine`\

 `0` =  *[디버그 엔진 guid]*

 `1` =  *[디버그 엔진 guid]*

|자리 표시자|설명|
|-----------------|-----------------|
|*[언어 guid]*|언어의 GUID|
|*[vendor guid]*|공급 업체의 GUID|
|*[클래스 guid]*|이 식 계산기를 구현 하는 클래스의 GUID|
|*[디버그 엔진 guid]*|이 식 계산기를 사용 하는 디버그 엔진을의 GUID|

### <a name="expression-evaluator-extensions"></a>식 계산기 확장
 다음은 레지스트리에 식 계산기 확장 메트릭의 조직입니다. `EEExtensions` 가 식에 대 한 메트릭 유형 이름을 계산기 확장 템플릿이며 *[메트릭 유형]* 합니다.

 `EEExtensions`\

 *[extension guid]* \

 *[metric] = [metric value]*

 *[metric] = [metric value]*

|자리 표시자|설명|
|-----------------|-----------------|
|*[extension guid]*|식 계산기 확장의 GUID|

### <a name="exceptions"></a>예외
 다음은 레지스트리에 예외 메트릭의 조직입니다. `Exception` 예외에 대 한 메트릭 유형 이름이 며 해당 *[메트릭 유형]* 합니다.

 `Exception`\

 *[디버그 엔진 guid]* \

 *[예외 유형]* \

 *[exception]* \

 *[metric] = [metric value]*

 *[metric] = [metric value]*

 *[exception]* \

 *[metric] = [metric value]*

 *[metric] = [metric value]*

|자리 표시자|설명|
|-----------------|-----------------|
|*[디버그 엔진 guid]*|예외를 지 원하는 디버그 엔진을의 GUID입니다.|
|*[exception types]*|처리할 수 있는 예외 클래스를 식별 하는 하위 키에 대 한 일반 제목입니다. 일반적인 이름은  **C++ 예외**합니다 **Win32 예외**를 **Common Language Runtime Exceptions**, 및 **네이티브 런타임 검사**. 이러한 이름은 특정 사용자에 게 예외 클래스를 식별 하도 사용 됩니다.|
|*[exception]*|예외에 대 한 이름을: 예를 들어 **_com_error** 하거나 **컨트롤 나누기**합니다. 이러한 이름은 사용자에 게 특정 예외를 식별 하도 사용 됩니다.|

## <a name="requirements"></a>요구 사항
 이러한 파일은 [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK 설치 디렉터리 (기본적으로 *[드라이브]* \Program Files\Microsoft Visual Studio 2010 SDK\\).

 헤더: includes\dbgmetric.h

 Library: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>참고자료
- [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)