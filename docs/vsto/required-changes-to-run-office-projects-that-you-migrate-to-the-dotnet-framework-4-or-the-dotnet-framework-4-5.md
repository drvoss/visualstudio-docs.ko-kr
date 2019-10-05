---
title: Office 프로젝트에 필요한 변경 내용이.NET Framework 4, 4.5로 마이그레이션
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82ae3f8a43b65e6ff617192dc38149691d229455
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836068"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 또는.NET Framework 4.5로 마이그레이션하는 Office 프로젝트를 실행 하는 필요한 변경
  Office 프로젝트의 대상 프레임 워크를 변경 된 경우는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 나중에.NET Framework의 이전 버전에서 수행 해야 솔루션을 개발 컴퓨터에 최종 사용자 컴퓨터에서 실행할 수 있도록 다음 작업을 합니다.

- Visual Studio 2008에서 업그레이드한 경우 프로젝트에서 <xref:System.Security.SecurityTransparentAttribute>를 제거합니다.

- 수행 된 **정리** 실행 하거나 개발 컴퓨터에서 프로젝트를 디버깅할 수 있으려면 Visual Studio에서 명령을 합니다.

- 프로젝트에 대한 .NET Framework 필수 조건을 업데이트합니다.

- 또한 대상 프레임워크를 변경하기 전에 ClickOnce를 사용하여 이전에 배포한 경우 최종 사용자가 솔루션을 다시 설치해야 합니다.

  이러한 각 작업에 대한 자세한 내용은 아래 해당 섹션을 참조하세요.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Visual Studio 2008에서 업그레이드 하는 프로젝트에서 SecurityTransparent 특성 제거
 Visual Studio 2008에서 Office 프로젝트를 업그레이드하고 프로젝트의 대상 프레임워크가 이후에 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경되는 경우 프로젝트에서 <xref:System.Security.SecurityTransparentAttribute>를 제거해야 합니다. Visual Studio에서 자동으로 이 특성을 제거하지 않습니다. 이 특성을 제거하지 않으면 프로젝트를 컴파일할 때 오류 메시지가 수신됩니다.

 Visual Studio는 업그레이드 된 프로젝트의 대상 프레임 워크를 변경할 수는 조건에 대 한 자세한 내용은 합니다 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]를 참조 하세요 [업그레이드 Office 솔루션 마이그레이션 및](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>SecurityTransparentAttribute를 제거하려면

1. Visual Studio에서 프로젝트를 열고 **솔루션 탐색기**를 엽니다.

2. **속성** 노드(C#의 경우) 또는 **My Project** 노드(Visual Basic의 경우) 아래에서 AssemblyInfo 코드 파일을 두 번 클릭하여 코드 편집기에서 엽니다.

    > [!NOTE]
    > Visual Basic 프로젝트에서 AssemblyInfo 코드 파일을 보려면 **솔루션 탐색기** 에서 **모든 파일 표시** 단추를 클릭해야 합니다.

3. <xref:System.Security.SecurityTransparentAttribute>를 찾아 파일에서 제거하거나 주석으로 처리합니다.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>개발 컴퓨터에서 프로젝트를 실행 하거나 디버그 정리 명령을 수행합니다
 Office 프로젝트를 프로젝트의 대상 프레임 워크를 변경 하기 전에 작성 된 경우는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 나중에 수행 해야 하는 또는 **정리** 명령 및 대상 프레임 워크를 변경한 후 프로젝트를 다시 빌드합니다. 하는 경우 수행 하지 않습니다는 **정리** 명령을 받을 수는 <xref:System.Runtime.InteropServices.COMException> 디버그 또는 대상이 변경 된 프로젝트를 실행 하려는 경우.

 에 대 한 자세한 내용은 합니다 **정리** 명령을 참조 하십시오 [빌드 Office 솔루션](../vsto/building-office-solutions.md)합니다.

## <a name="update-the-prerequisites-for-deployment"></a>배포에 대 한 필수 구성 요소를 업데이트 합니다.
 Office 프로젝트 대상을 다시 지정 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 나중에 해당.NET Framework를 필수 구성 요소 에서도 업데이트 해야 합니다 **필수 구성 요소** 대화 상자. 그렇지 않으면 ClickOnce 배포 또는 InstallShield Limited Edition 프로젝트가 이전 버전의 .NET Framework를 검사하고 설치합니다.

 최종 사용자 컴퓨터에 배포에 대 한 필수 구성 요소를 업데이트 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: Office 솔루션을 실행 하려면 최종 사용자 컴퓨터에 필수 구성 요소 설치](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)합니다.

## <a name="reinstall-solutions-on-end-user-computers"></a>최종 사용자 컴퓨터에서 솔루션을 다시 설치
 ClickOnce를 사용하여 .NET Framework 3.5를 대상으로 하는 Office 솔루션을 배포한 다음 프로젝트 대상을 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경하는 경우 다시 게시한 후 최종 사용자가 솔루션을 제거하고 다시 설치해야 합니다. 최종 사용자를 받을 대상이 변경 된 솔루션을 다시 게시 하는 경우 최종 사용자 컴퓨터에서 솔루션이 업데이트 되는 <xref:System.Runtime.InteropServices.COMException> 업데이트 된 솔루션을 실행할 때.

## <a name="see-also"></a>참고자료
- [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
