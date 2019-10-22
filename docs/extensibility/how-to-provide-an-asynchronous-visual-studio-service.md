---
title: '방법: 비동기 Visual Studio 서비스 제공 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c34995a49a785061c67f1324c9c9cd5b5316178
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633116"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>방법: 비동기 Visual Studio 서비스 제공
UI 스레드를 차단 하지 않고 서비스를 가져오려면 비동기 서비스를 만들어 백그라운드 스레드에서 패키지를 로드 해야 합니다. 이러한 목적을 위해 <xref:Microsoft.VisualStudio.Shell.Package> 대신 <xref:Microsoft.VisualStudio.Shell.AsyncPackage>를 사용 하 고 비동기 패키지의 특별 한 비동기 메서드를 사용 하 여 서비스를 추가할 수 있습니다.

 동기 Visual Studio 서비스를 제공 하는 방법에 대 한 자세한 내용은 [방법: 서비스 제공](../extensibility/how-to-provide-a-service.md)을 참조 하세요.

## <a name="implement-an-asynchronous-service"></a>비동기 서비스 구현

1. Vsix 프로젝트 만들기 (**파일**  > **새**  > **프로젝트**  > **Visual C#**   > **확장성** 0**vsix 프로젝트**). 프로젝트 이름을 **Testasync**로 합니다.

2. 프로젝트에 VSPackage를 추가 합니다. **솔루션 탐색기** 에서 프로젝트 노드를 선택 하 고 **추가**  > **새 항목**  > **시각적 C# 항목**  > **확장성**  > **visual Studio 패키지**를 클릭 합니다. 이 파일의 이름을 *TestAsyncPackage.cs*로 합니다.

3. *TestAsyncPackage.cs*에서 `Package` 대신 `AsyncPackage`에서 상속 하도록 패키지를 변경 합니다.

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. 서비스를 구현 하려면 다음 세 가지 유형을 만들어야 합니다.

    - 서비스를 식별 하는 인터페이스입니다. 이러한 인터페이스 중 상당수는 비어 있습니다. 즉, 서비스를 쿼리 하는 데에만 사용 되는 메서드는 없습니다.

    - 서비스 인터페이스를 설명 하는 인터페이스입니다. 이 인터페이스는 구현 될 메서드를 포함 합니다.

    - 서비스와 서비스 인터페이스를 둘 다 구현 하는 클래스입니다.

5. 다음 예제에서는 세 가지 형식의 매우 기본적인 구현을 보여 줍니다. 서비스 클래스의 생성자는 서비스 공급자를 설정 해야 합니다. 이 예제에서는 패키지 코드 파일에 서비스를 추가 합니다.

6. 패키지 파일에 다음 using 지시문을 추가 합니다.

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. 다음은 비동기 서비스 구현입니다. 생성자에서 동기 서비스 공급자 대신 비동기 서비스 공급자를 설정 해야 합니다.

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>서비스 등록
 서비스를 등록 하려면 서비스를 제공 하는 패키지에 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>를 추가 합니다. 동기 서비스를 등록 하는 것과는 다른 패키지와 서비스 모두에서 비동기 로드를 지원 하는지 확인 해야 합니다.

- PackageRegistrationAttribute에 대 한 자세한 내용은 **AllowsBackgroundLoading = true** 필드를 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>에 추가 해야 합니다 .이에 대 한 자세한 내용은 [vspackage 등록 및 등록 취소](../extensibility/registering-and-unregistering-vspackages.md)를 참조 하세요.

- 서비스 인스턴스를 비동기식으로 초기화할 수 있도록 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>에 **Isasyncqueryable 수 있는 = true** 필드를 추가 해야 합니다.

  다음은 비동기 서비스 등록을 사용 하는 `AsyncPackage`의 예제입니다.

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>서비스 추가

1. *TestAsyncPackage.cs*에서 `Initialize()` 메서드를 제거 하 고 `InitializeAsync()` 메서드를 재정의 합니다. 서비스를 추가 하 고 서비스를 만드는 콜백 메서드를 추가 합니다. 서비스를 추가 하는 비동기 이니셜라이저의 예는 다음과 같습니다.

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. VisualStudio에 대 한 참조를 추가 합니다. *14.0*에 대 한 참조를 추가 합니다.

3. 서비스를 만들고 반환 하는 비동기 메서드로 콜백 메서드를 구현 합니다.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>서비스 사용
 이제 서비스를 가져오고 해당 메서드를 사용할 수 있습니다.

1. 이는 이니셜라이저에 표시 되지만 서비스를 사용 하려는 모든 위치에서 서비스를 가져올 수 있습니다.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     컴퓨터에 적합 한 파일 이름 및 경로로 `userpath`를 변경 하는 것을 잊지 마세요.

2. 코드를 빌드하고 실행 합니다. Visual Studio의 실험적 인스턴스가 표시 되 면 솔루션을 엽니다. 이렇게 하면 `AsyncPackage` autoload 됩니다. 이니셜라이저가 실행 되 면 지정한 위치에서 파일을 찾아야 합니다.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>명령 처리기에서 비동기 서비스 사용
 메뉴 명령에서 비동기 서비스를 사용 하는 방법에 대 한 예제는 다음과 같습니다. 여기에 표시 된 절차를 사용 하 여 비동기 이외의 다른 메서드에서 서비스를 사용할 수 있습니다.

1. 프로젝트에 메뉴 명령을 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **추가**  > **새 항목**  > **확장성**  > **사용자 지정 명령**을 선택 합니다. 명령 파일의 이름을 *TestAsyncCommand.cs*로 합니다.

2. 사용자 지정 명령 템플릿은 명령을 초기화 하기 위해 *TestAsyncPackage.cs* 파일에 `Initialize()` 메서드를 다시 추가 합니다. @No__t_0 메서드에서 명령을 초기화 하는 줄을 복사 합니다. 다음과 같이 표시됩니다.

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     이 줄을 *AsyncPackageForService.cs* 파일의 `InitializeAsync()` 메서드로 이동 합니다. 비동기 초기화에 있기 때문에 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>를 사용 하 여 명령을 초기화 하기 전에 주 스레드로 전환 해야 합니다. 이제 다음과 같이 표시 됩니다.

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. @No__t_0 메서드를 삭제 합니다.

4. *TestAsyncCommand.cs* 파일에서 `MenuItemCallback()` 메서드를 찾습니다. 메서드의 본문을 삭제 합니다.

5. Using 지시문을 추가 합니다.

    ```csharp
    using System.IO;
    ```

6. @No__t_0 라는 비동기 메서드를 추가 합니다 .이 메서드는 서비스를 가져오고 해당 메서드를 사용 합니다.

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. @No__t_0 메서드에서이 메서드를 호출 합니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. 솔루션을 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 되 면 **도구** 메뉴로 이동 하 여 **Testasynccommand 호출** 메뉴 항목을 찾습니다. 이를 클릭 하면 TextWriterService가 지정 된 파일에 기록 합니다. 명령을 호출 하면 패키지도 로드 되므로 솔루션을 열 필요가 없습니다.

## <a name="see-also"></a>참조
- [사용 및 서비스 제공](../extensibility/using-and-providing-services.md)
