---
title: 확장을 게시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201976"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>연습: Visual Studio 확장 게시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**참고**: Visual Studio Marketplace를 Visual Studio 갤러리 교체 되 고 있습니다. 자세한 내용은이 항목의 최신 버전을 참조 하세요.

이 연습에서는 Visual Studio 확장 Visual Studio 갤러리에 게시 하는 방법을 보여 줍니다. 갤러리로 확장 프로그램을 추가 하면 개발자가 사용할 수 **확장 및 업데이트** 을 검색할 수 있는 새롭고 업데이트 된 확장 합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.

## <a name="create-a-visual-studio-extension"></a>Visual Studio 확장을 만들려면
 이 경우에 기본 VSPackage 확장을 사용 합니다 되지만 동일한 단계를 모든 종류의 확장에 적합 합니다.

1. C#에서 VSPackage를 만듭니다 `TestPublishing` 메뉴 명령을 포함 합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.

## <a name="test-the-extension"></a>테스트 확장
 확장을 배포 하기 전에 빌드하고 테스트 하 여 Visual Studio의 실험적 인스턴스에서 올바르게 설치 되었는지 확인 합니다.

1. Visual Studio에서 디버깅을 시작 합니다. Visual Studio의 실험적 인스턴스를 엽니다.

2. 실험적 인스턴스를 이동 합니다 **도구가** 메뉴를 클릭 **확장 관리자**합니다. TestPublishing 확장 가운데 창에 표시 됩니다 하 고 사용 하도록 설정 합니다.

3. 에 **도구** 메뉴에서 테스트 명령 표시 되는지 확인 합니다.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Visual Studio 갤러리에 확장 게시
 이제 Visual Studio 갤러리에 확장을 게시할 수 있습니다.

1. 확장 프로그램의 릴리스 버전 빌드 및 최신 상태 인지에 있는지 확인 합니다.

2. 웹 브라우저에서 엽니다는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트입니다.

3. 오른쪽 위 모퉁이에서 클릭 **SIGN IN**합니다.

4. Microsoft 계정을 사용하여 로그인합니다. Microsoft 계정이 없는 경우이 시점에서 만들 수 있습니다.

5. **업로드**를 클릭합니다.

6. **1 단계: 확장 유형**을 선택 **도구** 을 클릭 한 다음 **다음**합니다.

7. **2 단계: 업로드**, Visual Studio 갤러리에 직접 업로드 하거나 자신의 웹 사이트에 링크를 추가 하도록 선택할 수 있습니다. 이 경우 선택 **도구를 업로드 하려는**합니다. 합니다 **컨트롤을 선택** 상자가 나타납니다. 클릭 **찾아보기** TestPublish.vsix 프로젝트의 \bin\Release 폴더에서를 선택 합니다. **다음**을 클릭합니다.

8. **3 단계: 기본 정보**에서 source.extension.vsixmanifest 파일에서 필드가 표시 됩니다. 적절 한 선택 **범주** 추가한 **태그** 에 확장을 찾을 수 있도록 합니다. 자세한 요약 및 설명 (적어도 280 자에 대 한 설명 이어야 함)을 추가 수 있습니다. 둡니다 **확장 유형이** 으로 **Microsoft 확장 되지** 및 **비용 범주** 으로 **평가판**합니다.

9. 페이지의 맨 아래에 기고 약관을 읽고 체크 **동의 함**합니다.

10. 클릭 **작성 글 만들기**합니다. 이 페이지가 아직 게시 되지 않은 메시지를 사용 하 여 Visual Studio 갤러리에서 확장 해야 하는 페이지가 표시 됩니다.

11. **게시**를 클릭합니다.

12. 확장 프로그램에 대해 Visual Studio 갤러리를 검색 합니다. TestPublish 확장에 대 한 목록이 표시 됩니다.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Visual Studio 갤러리에서 확장을 설치 합니다.
 확장을 게시 했으므로 Visual Studio에서 설치 하 고 테스트 합니다.

1. Visual Studio에서에 **도구** 메뉴에서 클릭 **확장 및 업데이트**합니다.

2. 클릭 **Online** 고 TestPublish를 검색 합니다. TestPublish 확장에 대 한 목록이 표시 됩니다.

3. **다운로드**를 클릭합니다. 확장을 다운로드한 후 **설치**를 클릭합니다.

4. 설치를 완료 하려면 Visual Studio를 다시 시작 합니다.

## <a name="removing-the-extension"></a>확장 제거
 컴퓨터에서 Visual Studio 갤러리에서 확장을 제거할 수 있습니다.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Visual Studio 갤러리에서 확장을 제거 하려면

1. 엽니다는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트입니다.

2. 오른쪽 위 모퉁이에서 클릭 **내 Extenions**합니다. TestPublish 목록을 표시 됩니다.

3. **삭제**를 클릭합니다.

#### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거 하려면

1. Visual Studio의 **도구** 메뉴에서 **확장 관리자**를 클릭합니다.

2. TestPublish를 선택한 다음 클릭 **제거**합니다.

3. 제거를 완료 하려면 Visual Studio를 다시 시작 합니다.
