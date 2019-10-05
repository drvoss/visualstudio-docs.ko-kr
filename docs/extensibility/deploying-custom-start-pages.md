---
title: 사용자 지정 시작 페이지를 배포 합니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5a84ba2ff92463ebea177fc5c3b04810de7ae817
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348217"
---
# <a name="deploy-custom-start-pages"></a>사용자 지정 시작 페이지를 배포 합니다.

VSIX 배포를 사용 하 여 또는 대상 컴퓨터의 올바른 위치에 파일을 복사 하 여 사용자 지정 시작 페이지를 배포할 수 있습니다.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용 하 여 VSIX 배포

시작 페이지 프로젝트 템플릿을 사용 하 여 시작 페이지를 만들고 다음 프로젝트를 빌드합니다, Visual Studio 만듭니다는 *.vsix* 배포할 수 있는 파일입니다. 시작 페이지에서 패키지를 *.vsix* 파일 배포의 경우 사용자에 따라 다음 옵션을 제공 합니다.

- 넣을 수 있습니다 합니다 *.vsix* 공용 웹 사이트 또는 네트워크 공유에 파일입니다. 사용자가 파일을 시작 페이지를 자동으로 설치 됩니다.

- 업로드할 수 있습니다 합니다 *.vsix* 파일을 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트 사용자가 사용 하 여 설치할 수 있도록 **확장 관리자**합니다.

시작 페이지 프로젝트 템플릿 복사본을 수정 하 고 원래를 유지할 수 있도록 기본 Visual Studio 시작 페이지의 복사본을 만듭니다.

시작 페이지 프로젝트 템플릿을 사용 하 여 가져올 수 있습니다 **확장 관리자** 또는 웹 사이트에서 다운로드 하 여 합니다.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용 하지 않고 VSIX 배포
 성공적인 VSIX 배포는 확장을 VSIX 등록 프로세스에서 인식 되는 폴더에 설치 필요 **확장 관리자**합니다. 시작 페이지 프로젝트 템플릿을 이미 올바른 폴더를 지정 하기 때문에 VSIX 배포에 대 한 확장명 패키지 하려고 할 때마다 사용 하는 것이 좋습니다. 그러나 템플릿을 사용할 수 없습니다 하는 경우에 있는 경우 사용 하지 않고 VSIX 배포를 만들 수 있습니다.

 시작 페이지 프로젝트 템플릿을 사용 하지 않고 VSIX 배포를 만들려면, 먼저 만듭니다는 *.vsix* 이러한 두 가지 방법 중 하나로 시작 페이지에 대 한 파일:

- 사용자 지정 시작 페이지 파일 빈 VSIX 프로젝트에 추가 하 여 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)합니다.

- 수동으로 만들어를 *.vsix* 파일입니다. 만들려는 *.vsix* 수동으로 파일:

   1. 만들기는 *extension.vsixmanifest* 파일 및 *[Content_Types].xml* 새 폴더에는 파일입니다. 자세한 내용은 [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)합니다.

   2. Windows 탐색기에서 두 개의 XML 파일이 포함 된 폴더를 마우스 오른쪽 단추로 클릭 합니다 **보내기**, 한 다음 압축 (zip) 폴더를 클릭 합니다. 결과 이름 바꾸기 *.zip* 파일을 *Filename.vsix*여기서 Filename은 패키지를 설치 하는 재배포 가능 파일의 이름입니다.

For Visual Studio 시작 페이지를 인식 하는 `Content Element` 의 VSIX 매니페스트가 포함 되어야 합니다는 `CustomExtension Element` 있는 `Type` 특성이로 설정 `"StartPage"`합니다. VSIX 배포를 사용 하 여 설치 된 시작 페이지 확장에 표시 된 **시작 페이지 사용자 지정** 목록에서 **시작** 옵션으로 페이지 **[설치 된 확장]** *확장 이름*합니다.

시작 페이지 패키지 어셈블리에 포함 된 경우 Visual Studio를 시작할 때 사용할 수 있도록 바인딩 경로 등록을 추가 해야 합니다. 이렇게 하려면 패키지에 포함 되는지 확인 한 *.pkgdef* 다음 정보가 포함 된 파일입니다.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>모든 사용자에 대 한 VSIX 배포
 기본적으로 VSIX 패키지에 배포 하는 확장 현재 사용자에 대해서만 설치 합니다. 모든 사용자 배포를 만들어 대상 컴퓨터의 모든 사용자에 대 한 시작 페이지 설치를 만들 수 있습니다.

### <a name="to-create-an-all-users-deployment"></a>모든 사용자 배포를 만들려면

1. 엽니다는 *extension.vsixmanifest* 코드 보기에서 파일입니다.

2. 에 `Identifier` vsix 매니페스트의 요소 추가 `AllUsers` 의 값을 가진 요소가 `true`합니다.

    ```
    <AllUsers>true</AllUsers>
    ```

     이렇게 하면 관리자 권한을 묻는 메시지를 선택한 후 다음 파일을 vsix 설치 관리자 *\Common7\IDE\Extensions* 합니다.

3. 엽니다는 *.pkgdef* 파일입니다.

4. 수정 합니다 *.pkgdef* 다음을 추가 하 여 hklm 기본 시작 페이지를 설정 하려면 여기서 *MyStartPage.xaml* 의 이름입니다 합니다 *.xaml* 시작을 포함 하는 파일 페이지입니다.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     이렇게 하면 Visual Studio에서 새 시작 페이지 위치를 확인 합니다.

## <a name="file-copy-deployment"></a>파일 복사 배포
 만들 필요가 없습니다를 *.vsix* 사용자 지정 시작 페이지를 배포 하는 파일입니다. 대신, 태그 및 사용자를 직접 지원 파일을 복사할 수 있습니다 <em>\StartPages\* 폴더입니다. **시작 페이지 사용자 지정</em>*  목록에서 **시작** 옵션 목록 페이지 마다 *.xaml* 경로 함께 해당 폴더의 파일-예를 들어 *%USERPROFILE%\My Documents\Visual Studio {version} \StartPages\\{0} 파일 이름}.xaml*합니다. 시작 페이지에서 전용 어셈블리에 대 한 참조를 포함 하는 경우 복사 하며 붙여넣습니다는 * \PrivateAssemblies\* 폴더입니다.

 에 패키징하지 않고 만든 시작 페이지를 배포 하는 *.vsix* 파일 일괄 처리 스크립트 예를 들어, 기본 파일 복사 전략을 사용 하거나 좋습니다 수 있는 다른 배포 기술과의 파일을 배치 합니다 필요한 디렉터리입니다.

### <a name="to-manually-install-a-custom-start-page"></a>사용자 지정 시작 페이지를 수동으로 설치 하려면

1. 복사 합니다 *.xaml* 어셈블리 이외의 지원 파일과 함께 시작 페이지 태그를 포함 하는 사용자의 붙여넣을 파일 * \StartPages\* 폴더입니다.

2. 시작 페이지를 어셈블리에 필요한 경우 복사 하 고 붙여넣습니다 *... \\{Visual Studio 설치 폴더} \Common7\IDE\PrivateAssemblies\\* 합니다.

3. 에 **시작 페이지 사용자 지정** 목록에서 합니다 **시작** 옵션 페이지에서 새 시작 페이지를 선택 합니다. 자세한 내용은 [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료

- [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)
- [시작 페이지에 사용자 정의 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)