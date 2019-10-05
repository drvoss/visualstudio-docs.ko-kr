---
title: '방법: 포함 목록 보안 구성'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ef4d25088e56f2223cb392dbc00c8454e1a291ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826381"
---
# <a name="how-to-configure-inclusion-list-security"></a>방법: 포함 목록 보안 구성
  관리자 권한이 있는 경우 구성할 수 있습니다는 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트 컨트롤에 최종 사용자가 신뢰 결정 포함 목록에 저장 하 여 Office 솔루션을 설치 하는 옵션이 제공 됩니다 여부. 포함 목록에 대 한 자세한 내용은 [포함 목록을 사용 하 여 Office 신뢰 솔루션](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 5 개의 각 영역에 있는 솔루션의 경우 다음 옵션을 설정할 수 있습니다.

- 사용 하도록 설정 된 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트 키와 포함 목록입니다. 모든 인증서로 서명 된 Office 솔루션에 신뢰를 부여할 최종 사용자를 허용할 수 있습니다.

- 제한 된 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트 키와 포함 목록입니다. 최종 사용자가 게시자를 식별 하는 사용할 수 있지만 이미 신뢰할 수 있는 인증서로 서명 된 Office 솔루션을 설치할 수 있습니다.

- 사용 하지 않도록 설정 된 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트 키와 포함 목록입니다. 최종 사용자가 명시적으로 신뢰할 수 있는 인증서로 서명 되어 있지 않은 모든 Office 솔루션 설치를 방지할 수 있습니다.

## <a name="enable-the-inclusion-list"></a>포함 목록을 사용 하도록 설정
 최종 사용자가 설치 하 고 해당 영역에서 제공 되는 모든 Office 솔루션 실행 옵션을 표시 하려는 경우 영역에 대 한 포함 목록을 사용 하도록 설정 합니다.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>레지스트리 편집기를 사용 하 여 포함 목록을 사용 하도록 설정 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. 에 **열기** 상자에 입력 **regedt32.exe**를 클릭 하 고 **확인**합니다.

2. 다음 레지스트리 키를 찾습니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     키가 없으면 만듭니다.

3. 다음 하위 키를 추가 **문자열 값**이미 없는, 연관 된 값을 사용 하는 경우.

    |문자열 값의 하위 키|값|
    |-------------------------|-----------|
    |**인터넷**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Disabled**|
    |**MyComputer**|**사용**|
    |**LocalIntranet**|**사용**|
    |**TrustedSites**|**사용**|

     기본적으로 **인터넷** 기본값이 **AuthenticodeRequired** 및 **UntrustedSites** 기본값이 **사용 안 함**합니다.

### <a name="to-enable-the-inclusion-list-programmatically"></a>프로그래밍 방식으로 포함 목록을 사용 하도록 설정 하려면

1. Visual Basic 또는 Visual C# 콘솔 응용 프로그램을 만듭니다.

2. 엽니다는 *Program.vb* 또는 *Program.cs* 편집에 대 한 파일을 다음 코드를 추가 합니다.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. 애플리케이션을 빌드 및 실행합니다.

## <a name="restrict-the-inclusion-list"></a>포함 목록을 제한합니다
 솔루션 사용자 신뢰 여부를 결정 하 라는 메시지가 표시 됩니다 전에 알려진 id가 있는 Authenticode 인증서로 서명 될 수 있도록 포함 목록을 제한 합니다.

### <a name="to-restrict-the-inclusion-list"></a>포함 목록을 제한 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. 에 **열기** 상자에 입력 **regedt32.exe**를 클릭 하 고 **확인**합니다.

2. 다음 레지스트리 키를 찾습니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     키가 없으면 만듭니다.

3. 다음 하위 키를 추가 **문자열 값**이미 없는, 연관 된 값을 사용 하는 경우.

    |문자열 값의 하위 키|값|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabled**|
    |**인터넷**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     기본적으로 **인터넷** 기본값이 **AuthenticodeRequired** 및 **UntrustedSites** 기본값이 **사용 안 함**합니다.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>포함 목록을 프로그래밍 방식으로 제한 하려면

1. Visual Basic 또는 Visual C# 콘솔 응용 프로그램을 만듭니다.

2. 엽니다는 *Program.vb* 또는 *Program.cs* 편집에 대 한 파일을 다음 코드를 추가 합니다.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. 애플리케이션을 빌드 및 실행합니다.

## <a name="disable-the-inclusion-list"></a>포함 목록을 사용 하지 않도록 설정
 최종 사용자에 게 알려지고 신뢰할 수 있는 인증서로 서명 된 솔루션에만 설치할 수 있도록 포함 목록을 비활성화할 수 있습니다.

### <a name="to-disable-the-inclusion-list"></a>포함 목록을 사용 하지 않도록 설정

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. 에 **열기** 상자에 입력 **regedt32.exe**를 클릭 하 고 **확인**합니다.

2. 이 존재 하지 않는 경우 다음 레지스트리 키를 만듭니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. 다음 하위 키를 추가 **문자열 값**이미 없는, 연관 된 값을 사용 하는 경우.

    |문자열 값의 하위 키|값|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabled**|
    |**인터넷**|**Disabled**|
    |**MyComputer**|**Disabled**|
    |**LocalIntranet**|**Disabled**|
    |**TrustedSites**|**Disabled**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>포함 목록을 프로그래밍 방식으로 사용 하지 않도록 설정

1. Visual Basic 또는 Visual C# 콘솔 응용 프로그램을 만듭니다.

2. 엽니다는 *Program.vb* 또는 *Program.cs* 편집에 대 한 파일을 다음 코드를 추가 합니다.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. 애플리케이션을 빌드 및 실행합니다.

## <a name="see-also"></a>참고자료
- [포함 목록을 사용 하 여 Office 솔루션 신뢰](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
