---
title: 확장 팩 항목 템플릿을 사용 하 여 확장 팩을 만드는 | Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: madskristensen
ms.author: madsk
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 66a1c42340a88f0756d4fcc1f323433ab2640127
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322802"
---
# <a name="walkthrough-create-an-extension-pack"></a>연습: 확장 팩 만들기

확장 팩을 함께 설치할 수 있는 확장 집합이 있습니다. 확장 팩을 사용 하면 손쉽게 즐겨 찾는 확장을 다른 사용자와 공유 하거나, 특정 시나리오에 함께 확장 집합이 번들 수 있습니다.

## <a name="prerequisites"></a>전제 조건

Visual Studio 2015부터 Visual Studio SDK는 Visual Studio 설치에서 선택적 기능으로 포함 합니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

확장 팩이 기능은 Visual Studio 15.8 Preview 2부터 사용할 수 있습니다.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>확장 팩 항목 템플릿을 사용 하 여 확장 만들기

확장 팩 항목 템플릿을 함께 설치할 수 있는 확장 집합과 확장 팩을 만듭니다.

1. 에 **새 프로젝트** 대화 상자에서 선택한 "vsix" 검색 **VSIX 프로젝트**합니다. 에 대 한 **프로젝트 이름**, "테스트 확장 팩"을 입력 합니다. **만들기**를 선택합니다.

2. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 이동 하 여 Visual C# **확장성** 노드와 선택 **확장 팩**합니다. 기본 파일 이름 (ExtensionPack1.cs)을 그대로 둡니다.

3. 다음 코드를 포함 하는 ExtensionPack1.vsext 파일이 추가 됩니다.

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. 확장 팩에 포함 된 확장의 vsixid 복지부 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)합니다. 포함 하 고 클릭 하려는 확장을 찾을 **복사 ID**합니다. 기존 업데이트할 수 있습니다 **vsixId** 위의 파일 또는 목록에 다른 확장을 추가 합니다.

    ![Marketplace에서 VsixId 복사](media/vsixid-marketplace.png)

5. 프로젝트를 빌드하고 Marketplace에 확장을 업로드 합니다. 참조 [Visual Studio 확장 기능 게시](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)합니다.

> [!NOTE]
> 확장 팩에서 사용할 수 있는 확장만 설치할 수는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 또는 [전용 갤러리](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)합니다.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장 팩을 설치 합니다.

확장을 게시 했으므로 Visual Studio에서 설치 하 고 테스트 합니다.

::: moniker range="vs-2017"

1. Visual Studio에서에 **도구** 메뉴에서 클릭 **확장 및 업데이트**합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio에서에 **확장** 메뉴에서 클릭 **Managed Extensions**합니다.

::: moniker-end

2. 클릭 **Online** 고 "테스트 확장 팩"을 검색 합니다.

3. **다운로드**를 클릭합니다. 설치에 대 한 확장 및 확장 팩에 포함 된 확장 목록을 다음 예약 됩니다.

4. 다음은 샘플 확장 팩 다운로드 보기는 **확장 관리** 대화 합니다. 확장 팩에 포함 된 확장의 일부만 설치 하려는 경우에 확장 목록에서 수정할 수 있습니다 **설치에 대 한 예약**합니다.

    ![Marketplace에서 확장 팩을 다운로드 합니다.](media/vside-extensionpack.png)

5. 설치를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

컴퓨터에서 확장 제거:

::: moniker range="vs-2017"

1. Visual Studio에서에 **도구** 메뉴에서 클릭 **확장 및 업데이트**합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio에서에 **확장** 메뉴에서 클릭 **Managed Extensions**합니다.

::: moniker-end

2. 선택 **테스트 확장 팩** 을 클릭 한 다음 **제거**합니다. 그런 다음 확장 및 확장 팩에 포함 된 확장 목록을 제거에 대 한 예약 됩니다.

3. 제거를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.
