---
title: '연습: Visual Studio 확장 기능 게시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86ed2455b19a3f7e56c92a37a9402b7d65bf70a3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337920"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>연습: Visual Studio 확장 게시

이 연습에서는 Visual Studio 확장 Visual Studio Marketplace에 게시 하는 방법을 보여 줍니다. 확장 프로그램을 Marketplace에 추가 하면 개발자가 사용할 수 **확장 및 업데이트** 새 확장과 업데이트 된 찾아볼 수 있습니다.

## <a name="prerequisites"></a>전제 조건

 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-visual-studio-extension"></a>Visual Studio 확장을 만들려면

이 문서에서는 기본 VSPackage 확장을 사용 하지만 단계는 모든 종류의 확장에 대 한 유효한 합니다.

1. C#에서 VSPackage를 만듭니다 `TestPublish` 메뉴 명령을 포함 합니다. 자세한 내용은 참조 하세요. [첫 번째 확장 만들기: Hello World](../extensibility/extensibility-hello-world.md)합니다.

## <a name="package-your-extension"></a>확장 패키지

1. 확장을 업데이트 *.vsixmanifest* 제품 이름, 만든이 및 버전에 대 한 올바른 정보로 합니다.

   ![확장 vsixmanifest 업데이트](media/update-extension-vsixmanifest.png)

2. 확장 프로그램을 빌드할 **릴리스** 모드입니다. 이제 확장 \bin\Release 폴더에는 VSIX로 패키지 됩니다.

3. VSIX 설치를 확인 하려면 두 번 클릭 수 있습니다.

## <a name="test-the-extension"></a>테스트 확장

 확장을 배포 하기 전에 빌드하고 테스트 하 여 Visual Studio의 실험적 인스턴스에서 올바르게 설치 되었는지 확인 합니다.

1. Visual Studio에서 Visual Studio의 실험적 인스턴스를 열려면 디버깅을 시작 합니다.

2. 실험적 인스턴스를 이동 합니다 **도구** 메뉴를 클릭 **확장 및 업데이트**합니다. TestPublish 확장 가운데 창에 표시 됩니다 하 고 사용 하도록 설정 합니다.

3. 에 **도구** 메뉴에서 테스트 명령 표시 되는지 확인 합니다.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>확장을 Visual Studio Marketplace에 게시

1. 확장 프로그램의 릴리스 버전 빌드 및 최신 상태 인지에 있는지 확인 합니다.

2. 웹 브라우저에서 엽니다는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 웹 사이트입니다.

3. 오른쪽 위 모퉁이에서 클릭 **로그인**합니다.

4. Microsoft 계정을 사용하여 로그인합니다. Microsoft 계정이 없는 경우이 시점에서 만들 수 있습니다.

5. 클릭 **확장을 게시할**합니다.  이 옵션 하는 모든 확장에 대 한 관리 페이지로 이동 합니다. 게시자 계정을 없다면이 이번에 만들라는 메시지가 표시 됩니다.

   ![Marketplace에 업로드](media/upload-to-marketplace.png)

6. 사용 하 여 확장을 업로드 하려면 게시자를 선택 합니다. 왼쪽에 나열 된 게시자 이름을 클릭 하 여 게시자를 변경할 수 있습니다. 클릭할 **새 확장명** 선택한 **Visual Studio**합니다.

7. **1: 확장 업로드**를 자신의 웹 사이트에 링크를 추가 하거나 Visual Studio Marketplace에 직접 VSIX 파일을 업로드 하도록 선택할 수 있습니다. 이 예제에서는 확장명 *TestPublish.vsix* 업로드 됩니다. 확장 끌어서 놓거나 사용 합니다 **클릭** 링크는 파일을 찾습니다. 프로젝트의 \bin\Release 폴더에서 확장을 프로그램을 찾습니다.  **Continue(계속)** 를 클릭합니다.

8. **2: 확장 세부 정보를 제공**, 일부 필드는에서 자동으로 채워집니다 합니다 *source.extension.vsixmanifest* 확장 프로그램에서 파일입니다. 아래 각에 대 한 자세한 세부 정보를 찾습니다.

    * **내부 이름** 확장의 세부 정보 페이지의 URL에 사용 됩니다. 예를 들어 게시자 이름 "myname"에서 확장을 게시 하 고 "my 확장" 하 고 내부 이름을 지정 결과의 URL에 "marketplace.visualstudio\.com/items?itemName=myname.myextension" 확장의 세부 정보 페이지입니다.

    * **표시 이름** 확장 합니다. 이 이름은에서 자동으로 채워진 합니다 *source.extension.vsixmanifest* 파일입니다.

    * **버전** 업로드 하는 확장의 번호입니다. 이 버전에서 자동으로 채워진은 *source.extension.vsixmanifest* 파일입니다.

    * **VSIX ID** 확장 프로그램에 대해 Visual Studio를 사용 하는 고유 식별자입니다. 에 확장명이 자동으로 업데이트 하려는 경우이 식별자가 필요 합니다. 이 식별자는에서 자동으로 채워진 합니다 *source.extension.vsixmanifest* 파일입니다.

    * **로고** 확장 프로그램에 사용 되는 합니다. 이 로고는에서 자동으로 채워진 합니다 *source.extension.vsixmanifest* 파일 제공 된 경우.

    * **간단한 설명** 확장을 수행 합니다. 이 설명에서 자동으로 채워진은 *source.extension.vsixmanifest* 파일입니다.

    * **개요** 스크린샷 및 확장 프로그램의 용도 대 한 자세한 정보를 포함 하는 것이 좋습니다.

    * **지원 되는 Visual Studio 버전** 어떤 버전의 Visual Studio 확장에 작동을 선택할 수 있습니다. 확장 프로그램은 해당 버전에만 설치 됩니다.

    * * * 지원 되는 Visual Studio 버전의 확장 프로그램에서 작동 하는 Visual Studio 버전을 선택할 수 있습니다. 확장 프로그램은 해당 버전에만 설치 됩니다.

    * **형식**. 확장의 가장 일반적인 유형이 **도구**합니다.

    * **범주**합니다. 적합 한 확장 된 최대 3 개를 선택 합니다.

    * **태그** 도움이 되는 키워드에 확장을 찾이 됩니다. 태그는 Marketplace의 확장 검색 관련성을 높일 수 있습니다.

    * **가격 책정 범주** 비용 확장 프로그램입니다.

    * **소스 코드 리포지토리에** 커뮤니티를 사용 하 여 소스 코드에 대 한 링크를 공유할 수 있습니다.

    * **확장 프로그램에 대 한 q&a 허용** 확장 항목 페이지에서 질문을 유지 하는 사용자가 수 있습니다.

9. 클릭 **저장 및 업로드**합니다. 게시자에 다시이 옵션은 페이지를 관리 합니다. 확장 프로그램에 아직 등록 되지 않았습니다. 확장 프로그램을 게시 하려면 마우스 오른쪽 단추로 클릭 선택한 서버 확장 **공개**합니다. 확장 프로그램 모양을 같은 Marketplace에서 선택 하 여 볼 수 있습니다 **확장 보기**합니다. 취득 숫자, 클릭 **보고서**합니다. 확장 프로그램을 변경 하려면 클릭 **편집**합니다.

   ![확장 항목 메뉴](media/extension-entry-menu.png)

10. 클릭 한 후 **공개**, 확장에 공개 되었습니다. 확장 프로그램에 대해 Visual Studio Marketplace를 검색 합니다.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>게시자 계정을 관리 하려면 추가 사용자를 추가 합니다.

Marketplace는 게시자 계정을 관리 하 고 액세스할 추가 사용자 권한 부여를 지원 합니다.

1. 추가 사용자를 추가 하려는 게시자 계정으로 이동 합니다.

2. 선택 **멤버** 를 클릭 **추가**합니다.

   ![추가 사용자를 추가 합니다.](media/add-users.png)

3. 추가 하 고 적절 한 수준의 액세스를 부여 하려는 사용자의 이메일 주소를 지정할 수 있습니다 **역할 선택**합니다.  다음 옵션 중에서 선택할 수 있습니다.

   * **작성자**: 사용자 확장을 게시할 수 있지만 볼 하거나 다른 사용자가 게시 된 확장을 관리 수 없습니다.

   * **판독기**: 사용자 확장을 볼 수 있지만 게시 하거나 확장을 관리할 수 없습니다.

   * **참가자**: 사용자 게시 및 확장을 관리 하지만 수 없습니다. 게시자 설정을 편집 하거나 관리할 수 액세스 합니다.

   * **소유자**: 사용자 수 게시 및 확장 관리, 게시자 설정을 편집 하 고 액세스 관리.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장을 설치 합니다.

확장을 게시 했으므로 Visual Studio에서 설치 하 고 테스트 합니다.

1. Visual Studio에서에 **도구** 메뉴에서 클릭 **확장 및 업데이트**합니다.

2. 클릭 **Online** 검색할 **TestPublish**합니다.

3. **다운로드**를 클릭합니다. 확장 설치에 대 한 다음 예약 됩니다.

4. 설치를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

컴퓨터에서 Visual Studio Marketplace에서 확장을 제거할 수 있습니다.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장을 제거 하려면

1. 엽니다는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 웹 사이트입니다.

2. 오른쪽 위 모퉁이에서 클릭 **게시** 확장 합니다. 게시자에 게시 하는 데 선택할 **TestPublish**합니다. 목록을 **TestPublish** 나타납니다.

3. 확장 항목을 마우스 오른쪽 단추로 클릭 하 고 클릭 **제거**합니다. 확장을 제거 하려는 경우 것인지 묻는 메시지가 나타납니다. **확인**을 클릭합니다.

### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거 하려면

1. Visual Studio에서에 **도구** 메뉴에서 클릭 **확장 및 업데이트**합니다.

2. 선택 **TestPublish** 을 클릭 한 다음 **제거**합니다. 확장 한 다음 제거 되도록 예약 됩니다.

3. 제거를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.
