---
title: 사용자 지정 시작 페이지를 배포 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1cdd172c2960024da8b12735764161d36498c4e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162098"
---
# <a name="deploying-custom-start-pages"></a>사용자 지정 시작 페이지 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 배포를 사용 하 여 또는 대상 컴퓨터의 올바른 위치에 파일을 복사 하 여 사용자 지정 시작 페이지를 배포할 수 있습니다.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용 하 여 VSIX 배포  
 시작 페이지 프로젝트 템플릿을 사용 하 여 시작 페이지를 만들고 다음 프로젝트를 빌드합니다, Visual Studio는 배포할 수 있는.vsix 파일을 만듭니다. 패키지는.vsix 파일의 시작 페이지를 사용 하면 배포의 경우 사용자에 따라 다음 옵션:  
  
- 공용 웹 사이트 또는 네트워크 공유에서.vsix 파일을 넣을 수 있습니다. 사용자가 파일을 시작 페이지를 자동으로 설치 됩니다.  
  
- .Vsix 파일을 업로드할 수 있습니다 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트 사용자가 사용 하 여 설치할 수 있도록 **확장 관리자**합니다.  
  
  시작 페이지 프로젝트 템플릿 복사본을 수정 하 고 원래를 유지할 수 있도록 기본 Visual Studio 시작 페이지의 복사본을 만듭니다.  
  
  시작 페이지 프로젝트 템플릿을 사용 하 여 가져올 수 있습니다 **확장 관리자** 또는 웹 사이트에서 다운로드 하 여 합니다.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용 하지 않고 VSIX 배포  
 성공적인 VSIX 배포는 확장을 VSIX 등록 프로세스에서 인식 되는 폴더에 설치 필요 **확장 관리자**합니다. 시작 페이지 프로젝트 템플릿을 이미 올바른 폴더를 지정 하기 때문에 VSIX 배포에 대 한 확장명 패키지 하려고 할 때마다 사용 하는 것이 좋습니다. 그러나 템플릿을 사용할 수 없습니다 하는 경우에 있는 경우 사용 하지 않고 VSIX 배포를 만들 수 있습니다.  
  
 시작 페이지 프로젝트 템플릿을 사용 하지 않고 VSIX 배포를 만들려면 먼저이 두 가지 방법 중 하나로 시작 페이지에 대 한.vsix 파일을 만듭니다.  
  
- 사용자 지정 시작 페이지 파일 빈 VSIX 프로젝트에 추가 하 여 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)합니다.  
  
- .Vsix 파일을 수동으로 만듭니다. 자세한 내용은 [방법: 수동으로 확장명 패키지 (VSIX 배포)](../misc/how-to-manually-package-an-extension-vsix-deployment.md)합니다.  
  
  For Visual Studio 시작 페이지를 인식 하는 `Content Element` 의 VSIX 매니페스트가 포함 되어야 합니다는 `CustomExtension Element` 있는 `Type` 특성이로 설정 `"StartPage"`합니다. VSIX 배포를 사용 하 여 설치 된 시작 페이지 확장에 표시 된 **시작 페이지 사용자 지정** 목록에서 **시작** 옵션으로 페이지 **[설치 된 확장]** *확장 이름*합니다.  
  
  시작 페이지 패키지 어셈블리에 포함 된 경우 Visual Studio를 시작할 때 사용할 수 있도록 바인딩 경로 등록을 추가 해야 합니다. 이렇게 하려면 패키지에 다음 정보가 포함 된.pkgdef 파일을 포함 해야 합니다.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>모든 사용자에 대 한 VSIX 배포  
 기본적으로 VSIX 패키지에 배포 하는 확장 현재 사용자에 대해서만 설치 합니다. 모든 사용자 배포를 만들어 대상 컴퓨터의 모든 사용자에 대 한 시작 페이지 설치를 만들 수 있습니다.  
  
##### <a name="to-create-an-all-users-deployment"></a>모든 사용자 배포를 만들려면  
  
1. 코드 뷰에서 extension.vsixmanifest 파일을 엽니다.  
  
2. 에 `Identifier` vsix 매니페스트의 요소 추가 `AllUsers` 의 값을 가진 요소가 `true`합니다.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     이렇게 하면 vsix 설치 관리자를 묻는 메시지를 관리자 권한 및 \Common7\IDE\Extensions에 파일을 설치 합니다.  
  
3. .Pkgdef 파일을 엽니다.  
  
4. 다음을 추가 하 여 hklm 기본 시작 페이지를 설정 하려면.pkgdef를 수정 합니다. 여기서 *MyStartPage.xaml* 시작 페이지를 포함 하는.xaml 파일의 이름입니다.  
  
     [$RootKey$\StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     이 새 시작 페이지 위치에 검색할 Visual 했음을 나타냅니다.  
  
## <a name="file-copy-deployment"></a>파일 복사 배포  
 사용자 지정 시작 페이지를 배포 하기 위한.vsix 파일을 만들 필요가 없습니다. 대신, 사용자의 \StartPages\ 폴더에 직접 마크업 및 지원 파일을 복사할 수 있습니다. **시작 페이지 사용자 지정** 목록에서 **시작** 경로 함께 해당 폴더에 있는 모든.xaml 파일을 나열 하는 옵션 페이지-예를 들어 %USERPROFILE%\My Documents\Visual Studio  *버전*\StartPages\\*파일 이름*.xaml입니다. 시작 페이지에서 전용 어셈블리에 대 한 참조를 포함 하는 경우 복사 하며 \PrivateAssemblies\ 폴더에 붙여 넣습니다.  
  
 패키징 없이 만든 시작 페이지를 배포 하는.vsix 파일에 것이 좋습니다는 기본 파일 복사 전략을 사용 하면, 예를 들어 일괄 처리 스크립트 또는 수 있는 다른 배포 기술과의 파일을 배치 필요한 디렉터리.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>사용자 지정 시작 페이지를 수동으로 설치 하려면  
  
1. 시작 페이지 태그 어셈블리 이외의 지원 파일과 함께 포함 된.xaml 파일을 복사 하 고 사용자의 \StartPages\ 폴더에 붙여 넣습니다.  
  
2. 시작 페이지를 어셈블리에 필요한 경우 복사 하 고 붙여넣습니다. \\ *Visual Studio 설치 폴더*\Common7\IDE\PrivateAssemblies\\합니다.  
  
3. 에 **시작 페이지 사용자 지정** 목록에서 합니다 **시작** 옵션 페이지에서 새 시작 페이지를 선택 합니다. 자세한 내용은 [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)   
 [시작 페이지에 사용자 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)
