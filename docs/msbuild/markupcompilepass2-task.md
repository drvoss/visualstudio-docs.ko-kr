---
title: MarkupCompilePass2 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d929abc6581bf77dfd6ff5cf8b23d450a78a6f6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817351"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 작업

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 작업은 같은 프로젝트의 형식을 참조하는 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 파일에 대해 두 번째 패스 태그 컴파일을 수행합니다.

## <a name="task-parameters"></a>작업 매개 변수

| 매개 변수 | 설명 |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | 선택적 **Boolean** 매개 변수입니다.<br /><br /> 별도의 <xref:System.AppDomain>에서 작업을 실행할지 여부를 지정합니다. 이 매개 변수가 **false**를 반환하는 경우 작업은 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]와 동일한 <xref:System.AppDomain>에서 더 빠르게 실행됩니다. 이 매개 변수가 **true**를 반환하는 경우 작업은 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)]에서 분리된 또 다른 <xref:System.AppDomain>에서 실행되며 더 느리게 실행됩니다. |
| `AssembliesGeneratedDuringBuild` | 선택적 **String[]** 매개 변수입니다.<br /><br /> 빌드 프로세스 중에 변경되는 어셈블리에 대한 참조를 지정합니다. 예를 들어 Visual Studio 솔루션에는 다른 프로젝트의 컴파일된 출력을 참조하는 하나의 프로젝트가 포함될 수 있습니다. 이 경우 두 번째 프로젝트의 컴파일된 출력을 **AssembliesGeneratedDuringBuild**에 추가할 수 있습니다.<br /><br /> 참고: **AssembliesGeneratedDuringBuild**는 빌드 솔루션에 의해 생성되는 어셈블리의 전체 세트에 대한 참조를 포함해야 합니다. |
| `AssemblyName` | 필수 **String** 매개 변수입니다.<br /><br /> 프로젝트에 대해 생성되는 어셈블리의 약식 이름을 지정합니다. 예를 들어 프로젝트가 이름이 *WinExeAssembly.exe*인 [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] 실행 파일을 생성하는 경우 **AssemblyName** 매개 변수는 **WinExeAssembly** 값을 갖습니다. |
| `GeneratedBaml` | 선택적 **ITaskItem** 출력 매개 변수입니다.<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 이진 형식으로 생성된 파일 목록을 포함합니다. |
| `KnownReferencePaths` | 선택적 **String[]** 매개 변수입니다.<br /><br /> 빌드 프로세스 중에 절대 변경되지 않는 어셈블리에 대한 참조를 지정합니다. [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] 설치 디렉터리 등에 있는 어셈블리를 포함합니다. |
| `Language` | 필수 **String** 매개 변수입니다.<br /><br /> 컴파일러가 지원하는 관리되는 언어를 지정합니다. 유효한 옵션은 **C#**, **VB**, **JScript** 및 **C++** 입니다. |
| `LocalizationDirectivesToLocFile` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 각 소스 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 대한 지역화 정보를 생성하는 방법을 지정입니다. 유효한 옵션은 **None**, **CommentsOnly** 및 **All**입니다. |
| `OutputPath` | 필수 **String** 매개 변수입니다.<br /><br /> 생성된 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 이진 형식 파일이 생성되는 디렉터리를 지정합니다. |
| `OutputType` | 필수 **String** 매개 변수입니다.<br /><br /> 프로젝트에서 생성되는 어셈블리의 형식을 지정합니다. 유효한 옵션은 **winexe**, **exe**, **library** 및 **netmodule**입니다. |
| `References` | 선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에서 사용되는 형식을 포함하는 어셈블리에 대한 파일의 참조 목록을 지정합니다. 한 가지 참조는 <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> 작업에 의해 생성된 어셈블리에 대한 것입니다. 이 작업은 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 작업 전에 실행되어야 합니다. |
| `RootNamespace` | 선택적 **문자열** 매개 변수입니다.<br /><br /> 프로젝트 내에 있는 클래스에 대한 루트 네임스페이스를 지정합니다. **RootNamespace**는 해당 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 `x:Class` 특성이 포함되어 있지 않을 때 생성된 관리 코드 파일의 기본 네임스페이스로도 사용됩니다. |
| `XAMLDebuggingInformation` | 선택적 **Boolean** 매개 변수입니다.<br /><br /> **true**이면 디버깅에 도움을 주기 위해 진단 정보가 생성되고 컴파일된 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]에 포함됩니다. |

## <a name="remarks"></a>주의

**MarkupCompilePass2**를 실행하기 전에 해당 마크업 컴파일 패스가 지연된 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에서 사용되는 형식을 포함하는 임시 어셈블리를 생성해야 합니다. **GenerateTemporaryTargetAssembly** 작업을 실행하여 임시 어셈블리를 생성합니다.

생성된 임시 어셈블리에 대한 참조가 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 작업이 실행될 때 제공되어 첫 번째 태그 컴파일 패스에서 컴파일이 지연되었던 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일이 이진 형식으로 컴파일되도록 합니다.

## <a name="example"></a>예제

다음 예제에서는 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 작업을 사용하여 두 번째 패스 컴파일을 수행하는 방법을 보여 줍니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>참고 항목

- [WPF MSBuild 참조](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild 작업 참조](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [MSBuild 작업 참조](../msbuild/msbuild-task-reference.md)
- [WPF 애플리케이션 빌드(WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 브라우저 애플리케이션 개요](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)