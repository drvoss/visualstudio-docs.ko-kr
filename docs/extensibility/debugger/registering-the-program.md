---
title: 프로그램 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60bc94efb9d3b2026de31c6018b466d432bf98f8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315952"
---
# <a name="register-the-program"></a>등록 프로그램
디버그 엔진에 대 한 포트를을 가져온 후 표시를 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스는 프로그램을 디버깅을 사용 하도록 설정 하는 다음 단계는 포트를 등록 합니다. 등록 되 면 프로그램은 다음 방법 중 하나에서 디버깅을 위해 제공 됩니다.

- 디버거를 실행 중인 응용 프로그램의 전체 디버깅 제어할 수 있는 프로세스에 연결입니다.

- -Just-in-time (JIT) 디버깅, 팩트 후 디버거를 독립적으로 실행 되는 프로그램의 디버깅 수 있습니다. 런타임 아키텍처는 오류를 catch 하는 경우 운영 체제 전에 디버거에 알립니다 때나 런타임 환경 메모리와 faulting 프로그램의 리소스를 해제 합니다.

## <a name="registering-procedure"></a>프로시저를 등록합니다.

### <a name="to-register-your-program"></a>프로그램을 등록 하려면

1. 호출 된 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 포트에서 구현 하는 메서드.

     `IDebugPortNotify2::AddProgramNode` 필요에 대 한 포인터를 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스입니다.

     일반적으로 운영 체제 또는 런타임 환경 프로그램이 로드 되 면 프로그램 노드에서 만듭니다. 디버그 엔진 (DE) 프로그램을 로드 하 라는 메시지가 표시 됩니다, 경우는 DE 만들고 프로그램 노드를 등록 합니다.

     다음 예제에서는 프로그램을 시작 하 고 포트를 사용 하 여 등록 하는 디버그 엔진을 보여 줍니다.

    > [!NOTE]
    > 이 코드 예제를 시작 하 고 프로세스를 다시 시작 하는 유일한 방법은 아닙니다. 이 코드는 주로 포트를 사용 하 여 프로그램을 등록 하는 예입니다.

    ```cpp
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

## <a name="see-also"></a>참고자료
- [포트 가져오기](../../extensibility/debugger/getting-a-port.md)
- [디버그할 프로그램을 사용 하도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)