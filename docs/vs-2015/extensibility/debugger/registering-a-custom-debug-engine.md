---
title: 등록 사용자 지정 디버그 엔진 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703597"
---
# <a name="registering-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 해야 COM 규칙을 따르는 클래스 팩터리로 자체 등록할 뿐만 아니라 Visual Studio 레지스트리 하위 키를 통해 Visual Studio를 사용 하 여 등록 합니다.  
  
> [!NOTE]
> 일부분으로 빌드되는 TextInterpreter 샘플에서 디버그 엔진을 등록 하는 방법의 예제를 찾을 수 있습니다는 [자습서: ATL COM을 사용 하 여 디버그 엔진 구축](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)합니다.  
  
## <a name="dll-server-process"></a>DLL 서버 프로세스  
 일반적으로 디버그 엔진 자체 DLL에서 COM 서버로 구현 됩니다. 이 Visual Studio에서 액세스 하기 전에 디버그 엔진 해야 COM을 사용 하 여 해당 클래스 팩터리의 CLSID를 등록 하는 것을 의미 합니다. 디버그 엔진 등록 해야 자체 자체는 Visual Studio를 사용 하 여 모든 속성 (라고도 메트릭)을 설정 하기 위해 디버그를 지 원하는 엔진입니다. 디버그 엔진에 대 한 Visual Studio 레지스트리 하위 키에 기록 되는 메트릭의 선택한 디버그 엔진을 지 원하는 기능에 따라 달라 집니다.  
  
 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 설명 뿐만 아니라 레지스트리 위치는 디버그 엔진 등록 하는 데 필요한 유용한 기능 및 선언에 대 한 숫자를 포함 하는 dbgmetric.lib 라이브러리에 대해서도 설명 합니다 C++ 는 개발자 쉽게 레지스트리를 조작 합니다.  
  
### <a name="example"></a>예제  
 다음은 사용 하는 방법을 보여 주는 (TextInterpreter 샘플)에서 일반적인 예는 `SetMetric` Visual Studio 디버그 엔진 등록 (dbgmetric.lib)에서 작동 합니다. 전달 되는 메트릭 dbgmetric.lib에서 정의 됩니다.  
  
> [!NOTE]
> TextInterpreter는 기본 디버그 엔진; 구현 하지 않는-따라서 등록 하지 않습니다 및-다른 기능입니다. 전체 디버그 엔진의 전체 목록을 해야 `SetMetric` 통화 또는 해당 하는 디버그 엔진은 각 기능에 대 한 지원.  
  
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
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [자습서: ATL COM을 사용 하 여 디버그 엔진 구축](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
