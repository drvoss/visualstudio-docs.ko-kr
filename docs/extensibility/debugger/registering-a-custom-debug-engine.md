---
title: 등록 사용자 지정 디버그 엔진 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90400a9bf750eb80e40d6558fed382e18e7824ef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316051"
---
# <a name="register-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 등록
디버그 엔진 해야 다음 COM 규칙 하는 클래스 팩터리로 자체 등록할 뿐만 아니라 Visual Studio 레지스트리 하위 키를 통해 Visual Studio를 사용 하 여 등록 합니다.

> [!NOTE]
> 일부분으로 빌드되는 TextInterpreter 샘플에서는 디버그 엔진을 등록 하는 방법의 예제를 찾을 수 있습니다는 [자습서: ATL COM을 사용 하 여 디버그 엔진 구축](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)합니다.

## <a name="dll-server-process"></a>DLL 서버 프로세스
 디버그 엔진은 일반적으로 설정 자체 DLL에서 COM 서버로 합니다. 따라서 디버그 엔진 Visual Studio에서 액세스 하려면 먼저 COM을 사용 하 여 해당 클래스 팩터리의 CLSID를 등록 해야 합니다. 그런 다음 디버그 엔진 등록 해야 자체 (라고도 메트릭으로) 속성을 설정 하려면 Visual Studio를 사용 하 여 디버그 엔진 지원 합니다. Visual Studio 레지스트리 하위 키를 기록 하는 메트릭 선택한 디버그 엔진을 지 원하는 기능에 따라 달라 집니다.

 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 뿐만 아니라 레지스트리 위치는 디버그 엔진 등록 하는 데 필요한 설명에 대해서도 설명 합니다 *dbgmetric.lib* 라이브러리의 유용한 기능 및 선언 수를 포함 하는 에 대 한 C++ 쉽게 레지스트리를 조작 하는 개발자.

### <a name="example"></a>예제
 (TextInterpreter 샘플)에서 다음 예제에서는 사용 하는 방법을 보여 줍니다 합니다 `SetMetric` 함수 (에서 *dbgmetric.lib*), Visual Studio 디버그 엔진 등록 합니다. 에 전달 되는 메트릭도 정의 되어 *dbgmetric.lib*합니다.

> [!NOTE]
> TextInterpreter는 기본 디버그 엔진; 설정 하지 않습니다-따라서 등록 하지 않습니다 및-다른 기능입니다. 전체 디버그 엔진의 전체 목록을 해야 `SetMetric` 통화 또는 해당 하는 디버그 엔진은 각 기능에 대 한 지원.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>참고자료
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [자습서: ATL COM을 사용 하 여 디버그 엔진 구축](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)