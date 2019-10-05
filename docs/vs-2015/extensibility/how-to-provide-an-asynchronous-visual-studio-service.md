---
title: '방법: 비동기 서비스를 제공 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204109"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>방법: 비동기 Visual Studio 서비스 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UI 스레드를 차단 하지 않고 서비스를 가져오려는 경우 비동기 서비스를 만들고 백그라운드 스레드에서 패키지를 로드 해야 합니다. 이 목적을 위해 사용할 수는 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 아닌 <xref:Microsoft.VisualStudio.Shell.Package>, 비동기 패키지의 특수 비동기 메서드를 사용 하 여 서비스를 추가 하 고

 동기 Visual Studio 서비스를 제공 하는 방법에 대 한 내용은 [방법: 서비스 제공](../extensibility/how-to-provide-a-service.md)합니다.

## <a name="implementing-an-asynchronous-service"></a>비동기 서비스 구현

1. VSIX 프로젝트를 만듭니다 (**파일 / 새로 만들기 / 프로젝트 / Visual C# / 확장성 / VSIX 프로젝트**). 프로젝트 이름을 **TestAsync**합니다.

2. VSPackage 프로젝트에 추가 합니다. 프로젝트 노드를 선택 합니다 **솔루션 탐색기** 클릭 **추가 / 새 항목 / Visual C# 항목 / 확장성 / Visual Studio 패키지**합니다. 이 파일의 이름을 **TestAsyncPackage.cs**합니다.

3. TestAsyncPackage.cs, 패키지가 아닌 AsyncPackage에서 상속 하도록 패키지를 변경 합니다.

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. 서비스를 구현 하려면 세 가지 형식을 만들 필요 합니다.

    - 서비스를 설명 하는 인터페이스입니다. 이러한 인터페이스의 대부분은 빈, 즉, 이러한 방법이 없습니다.

    - 서비스 인터페이스를 설명 하는 인터페이스입니다. 이 인터페이스 메서드를 구현할 수를 포함 합니다.

    - 서비스와 서비스 인터페이스를 구현 하는 클래스입니다.

5. 다음 예제에서는 세 가지 형식의 매우 기본적인 구현을 보여 줍니다. 서비스 클래스의 생성자는 서비스 공급자를 설정 해야 합니다. 이 예제 패키지 코드 파일에 서비스를 추가 합니다.

6. 다음 추가 패키지 파일에 문을 사용 하 여:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. 비동기 서비스 구현은 다음과 같습니다. 참고 생성자에서 동기 서비스 공급자 보다는 비동기 서비스 공급자를 설정 해야 합니다.

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>서비스 등록
 서비스를 등록 하려면 추가 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 서비스를 제공 하는 패키지에 있습니다. 동기 서비스를 등록 하는 방법은 두 가지 차이가 있습니다.

- 자동 로드 하려는 경우 추가 해야 패키지를 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad 값 특성을 합니다. 자동 로드 Vspackage에 대 한 자세한 내용은 참조 하세요. [Vspackage 로드](../extensibility/loading-vspackages.md)합니다.

- 추가 해야 합니다 **AllowsBackgroundLoading = true** 필드를 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>합니다. PackageRegistrationAttribute에 대 한 자세한 내용은 참조 하세요. [등록 및 등록 취소 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)합니다.

  다음은 비동기 서비스 등록을 사용 하 여 AsyncPackage의 예::

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>서비스 추가

1. TestAsyncPackage.cs를 제거 합니다 `Initialize()` 메서드 및 재정의 `InitializeAsync()` 메서드. 서비스를 추가 하 고 서비스를 만드는 콜백 메서드를 추가 합니다. 서비스 추가 비동기 이니셜라이저의 예는 다음과 같습니다.

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll에 대 한 참조를 추가 합니다.

3. 콜백 메서드를 만들고 서비스를 반환 하는 비동기 메서드로 구현 합니다.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>서비스를 사용 하 여
 이제 서비스를 가져올 수 있으며 해당 메서드를 사용할 수 있습니다.

1. 이니셜라이저를에서이 보여 주지만 서비스를 사용 하려는 서비스 든 가져올 수 있습니다.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     변경할 것을 잊지 마세요  *\<userpath >* 파일 이름 및 컴퓨터에 적합 한 경로.

2. 빌드 및 코드를 실행 합니다. Visual Studio의 실험적 인스턴스가 표시 되 면 솔루션을 엽니다. 그러면 autoload AsyncPackage 됩니다. 이니셜라이저를 실행 하는 경우 지정한 위치에서 파일을 찾아야 합니다.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>명령 처리기에서 비동기 서비스를 사용 하 여
 비동기 서비스 메뉴 명령을 사용 하는 방법의 예는 다음과 같습니다. 다른 아닌 비동기 메서드에서 서비스를 사용 하려면 여기에 표시 된 절차를 사용할 수 있습니다.

1. 프로젝트에 메뉴 명령을 추가 합니다. (에 **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 선택 **추가 / 새 항목 / 확장성 사용자 지정 명령을**.) 명령 파일 이름을 **TestAsyncCommand.cs 합니다.**

2. 사용자 지정 명령 템플릿을 다시 추가 합니다 `Initialize()` 명령을 초기화 하기 위해 TestAsyncPackage.cs 파일로 메서드. Initialize () 메서드에서 명령을 초기화 하는 줄을 복사 합니다. 다음과 같이 표시됩니다.

    ```
    TestAsyncCommand.Initialize(this);
    ```

     이 줄을 이동 합니다 `InitializeAsync()` AsyncPackageForService.cs 파일입니다. 레지스트리를 사용 하 여 명령을 초기화 하기 전에 주 스레드를 전환 해야 합니다 이므로이 비동기 초기화에 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>입니다. 이제 다음과 같이 표시 됩니다.

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. 삭제 된 `Initialize()` 메서드.

4. TestAsyncCommand.cs 파일에서 찾기는 `MenuItemCallback()` 메서드. 메서드의 본문을 삭제 합니다.

5. using 문을 추가합니다.

    ```
    using System.IO;
    ```

6. 라는 비동기 메서드를 추가 `GetAsyncService()`, 서비스를 가져와 해당 메서드를 사용 하는:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. 이 메서드를 호출 합니다 `MenuItemCallback()` 메서드:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. 솔루션을 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 되 면 이동 합니다 **도구** 메뉴를 **TestAsyncCommand 호출** 메뉴 항목입니다. 여기를 클릭 하는 경우는 TextWriterService 지정한 파일에 씁니다. (필요가 없습니다 솔루션을 열고 로드할 패키지를 해도 명령을 호출 하기 때문에.)

## <a name="see-also"></a>참고 항목
 [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)
