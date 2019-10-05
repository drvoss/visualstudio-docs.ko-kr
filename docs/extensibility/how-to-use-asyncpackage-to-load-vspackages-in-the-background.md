---
title: '방법: AsyncPackage를 사용 하 여 백그라운드에서 Vspackage를 로드 합니다. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: 64514a6d43d580fbda142dfa65bb3a2d384dff4e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324778"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>방법: AsyncPackage를 사용 하 여 백그라운드에서 Vspackage를 로드 합니다.
디스크 I/O 로드 되 고 VS 패키지 초기화 될 수 있습니다. 이러한 I/O UI 스레드에서 발생 하는 경우에 응답성 문제를 발생할 수 있습니다. Visual Studio 2015에 도입 된이 문제를 해결 합니다 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 백그라운드 스레드에서 로드 패키지를 사용 하도록 설정 하는 클래스입니다.

## <a name="create-an-asyncpackage"></a>AsyncPackage 만들기
 VSIX 프로젝트를 만들어 시작할 수 있습니다 (**파일** > **새로 만들기** > **프로젝트** > **시각적 C#**   >  **확장성** > **VSIX 프로젝트**)를 VSPackage 프로젝트에 추가 하 고 (프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**  >  **새 항목**  >   **C# 항목** > **확장성**  >   **Visual Studio 패키지**). 그런 다음 서비스를 만들려면 하 고 해당 서비스 패키지를 추가할 수 있습니다.

1. 패키지를 파생 <xref:Microsoft.VisualStudio.Shell.AsyncPackage>합니다.

2. 해당 쿼리 않을 패키지를 로드 하는 서비스 제공 하려면:

    Visual studio 패키지 임을 나타내려면 백그라운드 로드가에 안전 하 고이 동작을 옵트인 하 여 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 설정 해야 **AllowsBackgroundLoading** 속성을 true로 특성 생성자에서.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Visual Studio에 안전 하 게 백그라운드 스레드에서 서비스를 인스턴스화할 수 임을 나타내려면를 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> 속성을 true로 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 생성자입니다.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. UI 컨텍스트를 통해 로드 하는 경우 지정 해야 **PackageAutoLoadFlags.BackgroundLoad** 에 대 한는 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 플래그 값 (0x2) 패키지의 자동 로드 항목의 값으로 기록 합니다.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. 재정의 해야 비동기 초기화 작업을 수행 하는 경우 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>합니다. 제거 된 `Initialize()` VSIX 템플릿에서 제공 하는 메서드. (합니다 `Initialize()` 의 메서드 **AsyncPackage** 봉인 되어). 중 하나를 사용할 수는 <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> 비동기 서비스 패키지를 추가 하는 방법입니다.

    참고: 호출 `base.InitializeAsync()`, 소스 코드를 변경할 수 있습니다.

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. 주의 해야 Rpc (원격 프로시저 호출)를 만들지 않는 비동기 초기화 코드에서 (에서 **InitializeAsync**). 호출할 때 발생할 수 있습니다 이러한 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 직접 또는 간접적으로 합니다.  사용 하 여 UI 스레드는 차단 동기화 로드 필요한 경우 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>합니다. 기본 차단 모델 Rpc 사용 하지 않도록 설정 합니다. 이 비동기 작업에서 RPC를 사용 하려는 경우 있습니다 됩니다 경우 교착 상태가 UI 스레드는 자체 패키지를 로드 될 때까지 기다리는 것을 의미 합니다. 일반적인 대안은 같이 사용 하 여 필요한 경우 코드를 UI 스레드로 마샬링하 **조인 가능 작업 팩터리**의 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 또는 RPC를 사용 하지 않는 다른 메커니즘입니다.  사용 하지 마세요 **ThreadHelper.Generic.Invoke** 하거나 일반적으로 UI 스레드를 얻기 위해 기다리는 호출 스레드를 차단 합니다.

    참고: 사용 하지 않아야 **GetService** 하거나 **QueryService** 에서 프로그램 `InitializeAsync` 메서드. 사용 하는 경우에 먼저 UI 스레드로 전환 해야 합니다. 대신 사용 하는 것 <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> 에서 프로그램 **AsyncPackage** (캐스팅 하도록 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   C#:  AsyncPackage를 만듭니다.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>기존 VSPackage AsyncPackage 변환
 작업의 대부분은 새 동일 **AsyncPackage**합니다. 위의 1 ~ 5 단계를 수행 합니다. 또한 수행할 다음 권장 사항 사용 하 여 특별 한 주의가 필요 합니다.

1. 제거 해야 합니다 `Initialize` 패키지에서 제공 되었던 재정의 합니다.

2. 교착 상태를 방지 합니다. 있을 수 있습니다 Rpc 코드에서 숨겨집니다. 이제 백그라운드 스레드에서 발생합니다. 있는지 확인 하는 경우 RPC (예를 들어 **GetService**) 중 하나 (1) 주 스레드가 전환 해야, (2) 사용 하 여 비동기 버전의 경우 API가 있습니다 (예를 들어, **GetServiceAsync**).

3. 너무 자주 스레드 간에 전환 하지 마세요. 로드 하는 시간을 줄이기 위해 백그라운드 스레드에서 발생할 수 있는 작업을 지역화 하려고 합니다.

## <a name="querying-services-from-asyncpackage"></a>AsyncPackage에서 서비스를 쿼리합니다.
 **AsyncPackage** 수도 있고 호출자에 따라 비동기적으로 로드 되지 않을 수 있습니다. 예를 들어,

- 호출자가 호출 되는 경우 **GetService** 하거나 **QueryService** (둘 다 동기 Api) 또는

- 호출자가 호출 되는 경우 **IVsShell::LoadPackage** (또는 **IVsShell5::LoadPackageWithContext**) 또는

- 로드 컨텍스트를 UI에 의해 트리거되는 하지만 UI 컨텍스트 메커니즘은 비동기적으로 로드 수를 지정 하지 않았습니다.

  그런 다음 패키지 동기적으로 로드 됩니다.

  패키지에에서 남아 있을 기회 (비동기 초기화 단계) UI 스레드에서 작업 하지만 해당 작업의 완료에 대 한 UI 스레드가 차단 됩니다. 호출자에 게 사용 하는 경우 **IAsyncServiceProvider** 서비스에 대 한 비동기적으로 쿼리 한 다음 부하 및 초기화를 수행 하려면 결과 작업 개체에서 즉시 차단 하지는 비동기적으로 가정 합니다.

  C#:  서비스를 비동기적으로 쿼리 하는 방법:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
