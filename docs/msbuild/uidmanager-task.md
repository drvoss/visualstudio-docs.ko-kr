---
title: UidManager 작업 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59bcb413ab391f74f9d2713fe87b4384e30cc0c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844564"
---
# <a name="uidmanager-task"></a>UidManager 작업
<xref:Microsoft.Build.Tasks.Windows.UidManager> 작업은 소스 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 포함된 모든 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 요소를 지역화하기 위해 UID(고유 식별자)를 확인, 업데이트 또는 제거합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
  
| 매개 변수 | 설명 |
|-------------------------| - |
| `IntermediateDirectory` | 선택적 **문자열** 매개 변수입니다.<br /><br /> **MarkupFiles** 매개 변수로 지정된 소스 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일을 백업하는 데 사용되는 디렉터리를 지정합니다. |
| `MarkupFiles` | 필수 **ITaskItem[]** 매개 변수입니다.<br /><br /> UID 확인, 업데이트 또는 제거를 포함할 소스 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일을 지정합니다. |
| `Task` | 필수 **String** 매개 변수입니다.<br /><br /> 수행하려는 UID 관리 작업을 지정합니다. 유효한 옵션은 **Check**, **Update** 또는 **Remove**입니다. |
  
## <a name="example"></a>예  
 다음 예제에서는 <xref:Microsoft.Build.Tasks.Windows.UidManager> 작업을 사용하여 지정된 소스 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 해당 UID를 갖는 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 요소가 포함되어 있는지를 확인합니다.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
 [WPF MSBuild 참조](../msbuild/wpf-msbuild-reference.md)   
 [작업 참조](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [WPF 응용 프로그램 빌드(WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [방법: 응용 프로그램 지역화](/dotnet/framework/wpf/advanced/how-to-localize-an-application)