---
title: 포트 가져오기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f980c9d14bc2d0c9728f87374828cf690737429c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436405"
---
# <a name="getting-a-port"></a>포트 가져오기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

포트는 프로세스를 실행 하는 컴퓨터에 대 한 연결을 나타냅니다. 해당 컴퓨터는 로컬 컴퓨터 또는 원격 컴퓨터 일 수 있습니다 (하는 가능한 경우 실행 될 수는 비 Windows 기반 운영 체제를 참조 하세요 [포트](../../extensibility/debugger/ports.md) 자세한).  
  
 포트는 표현 합니다 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스입니다. 포트에 연결 된 컴퓨터에서 실행 중인 프로세스에 대 한 정보를 가져오는 데 사용 됩니다.  
  
 디버그 엔진 프로세스 정보에 대 한 요청을 충족 하 고 포트를 사용 하 여 프로그램 노드를 등록 하기 위해 포트에 대 한 액세스를 해야 합니다. 예를 들어, 디버그 엔진 구현 하는 경우는 [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스를 구현 합니다 [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 메서드 필요한 프로세스에 대 한 포트를 질문할 수 있습니다 반환할 정보입니다.  
  
 Visual Studio 디버그 엔진에 필요한 포트를 제공 하 고 포트 공급자에서이 포트를 가져옵니다. 프로그램에 연결 되어 있으면 (또는 디버거 내에서 예외로 인해 예외가 throw 되는 작업을 트리거하는 Just in Time [JIT] 대화 상자)를 사용 하는 선택한 전송 (포트 공급자에 대 한 다른 이름) 제공 됩니다. 이 고, 그렇지 디버거 내에서 프로그램을 시작 하는 사용자, 프로젝트 시스템을 사용 하 여 포트 공급자를 지정 합니다. Visual Studio를 나타내는 포트 공급 업체를 인스턴스화합니다 하거나 이벤트에 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스를 하 고 새 포트를 호출 하 여 요청 [포트 추가](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 사용 하 여는 [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 인터페이스입니다. 그러면이 포트 하나 이상의 폼에서 디버그 엔진에 전달 됩니다.  
  
## <a name="example"></a>예제  
 이 코드 조각은 제공 된 포트를 사용 하는 방법을 보여 줍니다 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 에서 프로그램 노드를 등록 하려면 [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)합니다. 매개 변수 직접적인 관련이 없는이 개념 명확성을 위해 생략 되었습니다.  
  
> [!NOTE]
> 이 예제에서는 포트를 사용 하 여 시작 하 고 프로세스를 다시 시작 하 고 있다고 가정 합니다 [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) 인터페이스 포트에서 구현 됩니다. 이 이러한 작업을 수행 하는 유일한 방법은 아닙니다 및는 포트 하지도 참여할 이외의 프로그램 할 가능성이 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 권한을 부여 합니다.  
  
```cpp#  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [프로그램 등록](../../extensibility/debugger/registering-the-program.md)   
 [디버그할 프로그램을 사용 하도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [포트 공급자](../../extensibility/debugger/port-suppliers.md)   
 [포트](../../extensibility/debugger/ports.md)
