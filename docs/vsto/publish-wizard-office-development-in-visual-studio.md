---
title: 게시 마법사 (Visual Studio에서 Office 개발)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7879ad7cf18c3d09fddbab3923296e0896688af9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447062"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>게시 마법사 (Visual Studio에서 Office 개발)
  사용 된 **게시 마법사** 솔루션 파일에 지정된 된 위치를 복사 하려면 매니페스트 파일을 만들고 설치 프로그램을 만듭니다.

 이 마법사에 액세스 하려면 합니다 **빌드할** 메뉴에서 선택 **게시** *SolutionName*합니다. 액세스할 수도 있습니다는 **게시 마법사** 에서 **솔루션 탐색기**합니다. 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 선택한 **게시**합니다.

 아래의 각 섹션에서는 마법사의 페이지를 설명합니다.

## <a name="where-do-you-want-to-publish-the-application"></a>여기서 응용 프로그램을 게시 하 시겠습니까?
 **이 응용 프로그램을 게시할 위치를 지정** 필요 합니다. 게시 위치는 디렉터리 위치를 **게시 마법사** 빌드에서 매니페스트, 어셈블리, 임시 인증서 및 기타 파일과 같은 솔루션 파일을 복사 합니다. 이 디렉터리에 쓰기 권한이 있어야 합니다.

 부모 디스크 경로, 파일 공유, FTP 사이트 또는 웹 사이트 URL 위치를 입력 하거나 클릭 하는 **찾아보기** 단추 위치를 찾습니다. 이러한 형식의 경로일 수 있습니다.

- 표준에서 상대 또는 절대 경로 Windows 형식으로 *C:\Deploy\MyApplication* 하거나 *\MyApplication*합니다.

- 범용 명명 규칙 (UNC) 경로 같은  *\\\ServerName\MyApplication\\* 합니다.

- URL의 웹 사이트와 같은 http://www.microsoft.com/MyApplication합니다.

  게시 위치는 기본적으로 *http://localhost/projectname/* IIS가 설치 되어 있는 경우 또는 않은 경우 publish\ 디렉터리 IIS가 설치 되지 합니다.

> [!NOTE]
> 대상 컴퓨터는 Windows Vista를 실행 하는 경우 더 많은 고려 사항이 있습니다. 로컬 게시 옵션을 사용 하려면 Windows Vista 컴퓨터의 관리자 여야 합니다. 또한 기본 위치는 항상을 *게시\\*  IIS가 설치 되어 있는지 여부에 관계 없이 디렉터리입니다.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>최종 사용자 컴퓨터의 기본 설치 경로 무엇입니까?
 설치 경로 선택 사항입니다. 원하는 경우 나중에 설치 경로 설정할 수 있습니다. 자세한 내용은 [방법: Office 솔루션의 설치 경로 변경](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)합니다.

 설치 경로는 최종 사용자가 사용자 지정을 설치 하는 데는 디렉터리입니다. 또한 솔루션에서 업데이트를 확인하는 데 사용하는 경로이기도 합니다. 합니다 **게시 마법사** 경로에 입력 한 것과 동일한 경우이 위치에 솔루션을 배포 하지 않습니다는 **이 응용 프로그램을 게시할 위치를 지정** 이전 페이지에서 상자입니다.

 **웹 사이트에서** 최종 사용자에 게 솔루션을 설치 하기 위해 수행 하는 URL을 지정 합니다.

 **UNC 경로 또는 파일 공유에서** 최종 사용자에 게 솔루션을 설치 하기 위해 수행 된 UNC 경로 지정 합니다.

 **CD-ROM 또는 DVD-ROM에서** 이 옵션의 설치 경로 필요가 없습니다.

 CD 또는 DVD에는 visual Studio 진행 되지 않습니다. 출력을 CD 또는 DVD에 수동으로 복사 해야 합니다.

## <a name="see-also"></a>참고자료
- [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [게시 페이지, 프로젝트 디자이너 &#40;Visual Studio에서 Office 개발&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
