---
title: 프로젝트 디자이너, 디버그 페이지 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 039b6722ca064c64c0e0b7f7757070852e908395
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703909"
---
# <a name="debug-page-project-designer"></a>프로젝트 디자이너, 디버그 페이지
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> 이 항목은 Windows 스토어 응용 프로그램에 적용되지 않습니다. Windows 개발자 센터에서 [디버그 세션 시작(VB, C#, C++ 및 XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)을 참조하세요.  
  
 **프로젝트 디자이너**의 **디버그** 페이지를 사용하여 Visual Basic 또는 C# 프로젝트에서 디버깅 동작의 속성을 설정합니다.  
  
 **디버그** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택합니다. **프로젝트** 메뉴에서 _ProjectName_**속성**을 클릭합니다. **프로젝트 디자이너**가 나타나면 **디버그** 탭을 클릭합니다.  
  
## <a name="configuration-and-platform"></a>구성 및 플랫폼  
 다음 옵션을 사용하면 표시하거나 수정할 구성 및 플랫폼을 선택할 수 있습니다.  
  
 **구성**  
 표시하거나 수정할 구성 설정을 지정합니다. 설정에는 **디버그**(기본값), **릴리스** 또는 **모든 구성**이 포함됩니다. 자세한 내용은 [디버그 및 릴리스 프로젝트 구성](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)을 참조하세요.  
  
 **플랫폼**  
 표시하거나 수정할 플랫폼 설정을 지정합니다. 선택 항목에는 **CPU**(기본값), **x64** 및 **x86**이 포함됩니다. 자세한 내용은 [디버그 및 릴리스 프로젝트 구성](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)을 참조하세요.  
  
## <a name="start-action"></a>시작 작업  
 **시작 작업**은. 프로젝트, 사용자 지정 프로그램, URL 등 응용 프로그램을 디버깅할 때 시작할 항목을 나타냅니다. 기본적으로 이 옵션은 **프로젝트 시작**으로 설정되어 있습니다. **디버그** 페이지의 **시작 작업** 설정은 `StartAction` 속성의 값을 결정합니다.  
  
 **시작 프로젝트**  
 이 옵션을 선택하여 애플리케이션을 디버깅할 때 실행 파일(Windows 애플리케이션 및 콘솔 애플리케이션 프로젝트의 경우)이 시작되도록 지정합니다. 이 옵션은 기본적으로 선택됩니다.  
  
 **시작 외부 프로그램**  
 이 옵션을 선택하여 애플리케이션을 디버깅할 때 특정 프로그램을 시작하도록 지정합니다.  
  
 **URL로 브라우저 시작**  
 이 옵션을 선택하여 애플리케이션을 디버깅할 때 특정 URL에 액세스하도록 지정합니다.  
  
## <a name="start-options"></a>시작 옵션  
 **명령줄 인수**  
 이 텍스트 상자에 디버깅에 사용할 명령줄 인수를 입력합니다.  
  
 **작업 디렉터리**  
 이 텍스트 상자에 프로젝트를 시작할 디렉터리를 입력합니다. 또는 찾아보기 단추(**...**)를 클릭하여 디렉터리를 선택합니다.  
  
 **원격 컴퓨터 사용**  
 원격 컴퓨터에서 애플리케이션을 디버깅하려면 이 확인란을 선택하고 텍스트 상자에 원격 컴퓨터에 대한 경로를 입력합니다.  
  
## <a name="enable-debuggers"></a>디버거 사용  
 **비관리 코드 디버깅 사용**  
 이 옵션은 네이티브 코드의 디버깅이 지원되는지를 지정합니다. COM 개체를 호출하는 경우 또는 프로젝트를 호출하는 네이티브 코드로 작성된 사용자 지정 프로그램을 시작하고 네이티브 코드를 디버깅해야 하는 경우 이 확인란을 선택합니다. 이 확인란의 선택을 취소하여 비관리 코드의 디버깅을 비활성화합니다. 이 확인란은 기본적으로 선택되어 있지 않습니다.  
  
 **SQL Server 디버깅 사용**  
 Visual Basic 애플리케이션에서 SQL 프로시저의 디버깅을 사용하거나 사용하지 않도록 설정하려면 이 확인란을 선택하거나 선택을 취소합니다. 이 확인란은 기본적으로 선택되어 있지 않습니다.  
  
 **Visual Studio 호스팅 프로세스 사용**  
 이 확인란을 선택하여 Visual Studio 호스팅 프로세스를 사용합니다. 이 확인란은 기본적으로 선택되어 있습니다. 자세한 내용은 [호스팅 프로세스(vshost.exe)](../../ide/hosting-process-vshost-exe.md)를 참조하세요.  
  
 보안 영역을 디버그하려면 [고급 보안 설정 대화 상자](../../ide/reference/advanced-security-settings-dialog-box.md)에서 이 옵션 및 **선택한 사용 권한 집합으로 이 애플리케이션 디버깅**을 사용해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio의 디버깅](../../debugger/debugging-in-visual-studio.md)   
 [C# 디버그 구성을 위한 프로젝트 설정](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 디버그 구성을 위한 프로젝트 설정](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [디버깅 속성 관리](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [방법: 제한 된 권한으로 ClickOnce 응용 프로그램 디버그](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [방법: 구성 만들기 및 편집](../../ide/how-to-create-and-edit-configurations.md)
