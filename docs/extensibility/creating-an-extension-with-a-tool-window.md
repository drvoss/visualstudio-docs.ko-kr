---
title: Creating an Extension with 도구 창 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5a38c9912be87c94c79076675b5db25663fb5f0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345440"
---
# <a name="create-an-extension-with-a-tool-window"></a>도구 창으로 확장 프로그램을 만들려면

이 절차에 알아봅니다 VSIX 프로젝트 템플릿을 사용 하는 방법 및 **사용자 지정 도구 창을** 도구 창을 사용 하 여 확장 프로그램을 만들려면 항목 템플릿.

## <a name="prerequisites"></a>전제 조건

 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

### <a name="create-a-tool-window"></a>도구 창을 만들려면

1. 라는 VSIX 프로젝트를 만듭니다 **FirstWindow**합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** "vsix"를 검색 하 여 대화 상자.

2. 프로젝트를 열면 라는 도구 창 항목 템플릿을 추가 **MyWindow**합니다. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 에 **새 항목 추가** 대화 상자에서로 이동 **Visual C#**  > **확장성** 선택한 **사용자 지정 도구 창을**합니다. 에 **이름을** 창의 맨 아래에 있는 필드에 도구 창 파일 이름을 *MyWindow.cs*합니다.

3. 프로젝트를 빌드하고 디버깅을 시작합니다.

   Visual Studio의 실험적 인스턴스가 표시 됩니다. 실험적 인스턴스에 대 한 자세한 내용은 참조 하세요. [실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다.

4. 실험적 인스턴스에서로 이동 **뷰** > **기타 Windows**합니다.

   에 대 한 메뉴 항목 표시 **MyWindow**합니다. 클릭 합니다.

   제목의 도구 창 표시 **MyWindow** 한 단추 **Click Me!.**