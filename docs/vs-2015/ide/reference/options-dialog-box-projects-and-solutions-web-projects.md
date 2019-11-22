---
title: 옵션 대화 상자, 프로젝트 및 솔루션, 웹 프로젝트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.WebProjects
ms.assetid: ea813046-1ae6-4c9f-9784-dc41494101b9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5456ef4935feb2ad6f08e2a0b7ff24ad58089e1f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297862"
---
# <a name="options-dialog-box-projects-and-solutions-web-projects"></a>옵션 대화 상자, 프로젝트 및 솔루션, 웹 프로젝트
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

웹 프로젝트가 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 내에서 개발에 사용할 웹 서버를 설정합니다. 이 대화 상자에 액세스하려면 **도구 옵션**을 클릭합니다. **프로젝트 및 솔루션**을 확장하고 **웹 프로젝트**를 클릭합니다.

 기본적으로 Visual Studio에서 웹 프로젝트를 실행하면(예: F5 또는 Ctrl+F5 사용) Visual Studio에서 Visual Studio 개발 서버를 사용합니다. 자세한 내용은 [Visual Studio의 ASP.NET 웹 프로젝트에 대한 웹 서버](https://msdn.microsoft.com/31d4f588-df59-4b7e-b9ea-e1f2dd204328)를 참조하세요.

> [!NOTE]
> 대화 상자에서 사용할 수 있는 옵션과 메뉴 명령의 이름 및 위치는 실제 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 이 도움말 페이지는 **웹 설정**에 따라 작성되었습니다. 설정을 보거나 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.

## <a name="settings"></a>설정
 **Use the 64-bit version of IIS Express for web sites and projects** Select this option to use IIS Express instead of the Visual Studio Development Server. 자세한 내용은 [Introducing IIS Express](https://weblogs.asp.net/scottgu/introducing-iis-express)(IIS Express 소개) 및 [IIS Express Overview](https://docs.microsoft.com/iis/extensions/introduction-to-iis-express/iis-express-overview)(IIS Express 개요)를 참조하세요. 이 옵션은 기본적으로 비활성화됩니다.

 **Warn before running web applications when there are errors in the error list** If this box is checked, you will be warned if you try to run your web application when it does not compile  without errors.
