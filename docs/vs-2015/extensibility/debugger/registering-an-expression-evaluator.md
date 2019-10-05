---
title: 식 계산기 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3595daa51fddf5c9c027d5643382918d85f83cc1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435684"
---
# <a name="registering-an-expression-evaluator"></a>식 계산기 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 식 계산기 (EE) Windows COM 환경과 Visual Studio를 사용 하 여 클래스 팩터리로 자체를 등록 해야 합니다. EE 디버그 엔진 (DE) 주소 공간 또는 따라 엔터티 인스턴스화하는 EE에서 Visual Studio 주소 공간을 삽입할 수 있도록 DLL로 구현 됩니다.  
  
## <a name="managed-code-expression-evaluator"></a>관리 코드 식 계산기  
 EE VSIP 프로그램에 대 한 호출에 의해 시작 일반적으로 COM 환경과 자체를 등록 하는 dll을 클래스 라이브러리로 구현 되는 관리 코드 **regpkg.exe**합니다. COM 환경에 대 한 레지스트리 키를 작성 하는 실제 프로세스는 자동으로 처리 됩니다.  
  
 기본 클래스의 메서드를 사용 하 여 표시할지를 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, com DLL이 등록 되 면 호출 될 메서드 임을 나타내는 이 등록 메서드를 자주 호출 `RegisterClass`, Visual Studio를 사용 하 여 DLL을 등록 하는 작업을 수행 합니다. 해당 `UnregisterClass` (표시 합니다 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>)를 수행한 `RegisterClass` DLL을 제거 하는 경우.  
  
 동일한 레지스트리 항목을 관리 되지 않는 코드에서 작성 하는 EE와 이루어집니다. 유일한 차이점은 있는지 도우미 함수가 같은 `SetEEMetric` 에 작업을 수행 합니다. 이 등록 또는 등록 취소 프로세스의 예는 다음과 같습니다.  
  
### <a name="example"></a>예제  
 이 함수는 EE 관리 되는 코드를 등록 하 고 Visual Studio를 사용 하 여 자체 등록을 취소 하는 방법을 보여 줍니다.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>관리 되지 않는 코드 식 계산기  
 EE DLL를 구현 하는 `DllRegisterServer` COM 환경 뿐만 아니라 Visual Studio를 사용 하 여 자체를 등록 하는 함수입니다.  
  
> [!NOTE]
> VSIP 설치 EnVSDK\MyCPkgs\MyCEE 아래에 있는 파일 dllentry.cpp에서 MyCEE 코드 샘플 레지스트리 코드를 찾을 수 있습니다.  
  
### <a name="dll-server-process"></a>DLL 서버 프로세스  
 DLL server는 EE 등록 하는 경우:  
  
1. 해당 클래스 팩터리를 등록 `CLSID` 일반 COM 규칙에 따라 합니다.  
  
2. 도우미 함수를 호출 `SetEEMetric` EE 메트릭을 다음 표에 나와 있는 Visual Studio를 사용 하 여 등록 합니다. 함수 `SetEEMetric` 및 아래에 지정 된 메트릭은 dbgmetric.lib 라이브러리의 일부입니다. 참조 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 세부 정보에 대 한 합니다.  
  
    |메트릭|설명|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` EE 클래스 팩터리|  
    |`metricName`|표시할 수 있는 문자열로 EE의 이름|  
    |`metricLanguage`|평가 하도록 설계 되었습니다 EE 되는 언어의 이름|  
    |`metricEngine`|`GUID`이 EE를 사용 하는 디버그 엔진 (DE) s|  
  
    > [!NOTE]
    > `metricLanguage``GUID` 이름에서 언어를 식별 하는 합니다 `guidLang` 인수를 `SetEEMetric` 언어를 선택 하는. 컴파일러가 디버그 정보 파일을 생성할 때 적절 한 작성 해야 `guidLang` 는 DE 사용 하는 EE에서 알 수 있도록 합니다. 일반적으로 DE이이 언어에 대 한 기호 공급자를 요청 `GUID`, 디버그 정보 파일에 저장 된 합니다.  
  
3. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 아래에 키를 만들어 Visual Studio를 사용 하 여 등록\\*X.Y*여기서 *X.Y* 등록 하도록 Visual Studio의 버전입니다.  
  
### <a name="example"></a>예제  
 이 함수는 어떻게 관리 되지 않는 코드를 보여 줍니다 (C++) EE를 등록 하 고 Visual Studio를 사용 하 여 자체 등록을 취소 합니다.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
