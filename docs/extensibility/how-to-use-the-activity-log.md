---
title: '방법: 활동 로그를 사용 하 여 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 53888f85a41fdd5bef3985c4da986609a032e377
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309345"
---
# <a name="how-to-use-the-activity-log"></a>방법: 활동 로그 사용
Vspackage는 활동 로그에 메시지를 작성할 수 있습니다. 이 기능은 소매 환경에서 Vspackage를 디버깅 하는 데 특히 유용 합니다.

> [!TIP]
> 활동 로그는 항상 켜져 있습니다. Visual Studio는 최근 100 개의 항목 뿐만 아니라 일반적인 구성 정보만 있는 처음 10 개 항목을 롤링 버퍼를 유지 합니다.

## <a name="to-write-an-entry-to-the-activity-log"></a>활동 로그에 항목을 기록 하려면

1. 이 코드를 삽입 합니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드 또는 VSPackage 생성자를 제외한 다른 모든 메서드에서:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     이 코드는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 서비스 및 캐스팅을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 인터페이스입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 현재 작품의 문화적 컨텍스트를 사용 하 여 활동 로그에 정보 항목을 씁니다.

2. (일반적으로 때나 명령을 호출 하는 창이 열린) VSPackage 로드 되 면 텍스트 활동 로그에 기록 됩니다.

## <a name="to-examine-the-activity-log"></a>활동 로그를 검사 하려면

1. Visual Studio를 실행 합니다 [로그](../ide/reference/log-devenv-exe.md) 세션 중 ActivityLog.xml 디스크에 쓸 수 있는 명령줄 스위치입니다.

2. Visual Studio를 닫으면 Visual Studio 데이터에 대 한 하위 폴더에서 활동 로그를 확인:

   <em> *%AppData%</em>\Microsoft\VisualStudio\\\<version>\ActivityLog.xml*.

3. 임의의 텍스트 편집기를 사용 하 여 활동 로그를 엽니다. 다음은 일반적인 항목:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>강력한 프로그래밍

활동 로그 서비스 이기 때문에 활동 로그 VSPackage 생성자에서 사용할 수 없는 경우

쓰기 직전 활동 로그를 가져와야 합니다. 캐시 하거나 나중에 사용에 대 한 활동 로그를 저장 하지 마십시오.

## <a name="see-also"></a>참고자료

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [VSPackage 문제 해결](../extensibility/troubleshooting-vspackages.md)
- [VSPackage](../extensibility/internals/vspackages.md)
