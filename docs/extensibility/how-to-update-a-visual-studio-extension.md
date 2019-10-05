---
title: '방법: Visual Studio 확장 기능 업데이트 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 237a1139a7a314cf99b5edbd8993abefe04592c8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324865"
---
# <a name="how-to-update-a-visual-studio-extension"></a>방법: Visual Studio 확장 기능 업데이트
사용 하 여 시스템에서 Visual Studio 확장을 업데이트할 수 있습니다 **확장 및 업데이트** 업데이트 된 버전을 설치 합니다. 확장의 업데이트 된 버전을 만들면 VSIX 매니페스트의 버전 번호를 증가 시켜 업데이트 되었음을 표시할 수 있습니다.

 들어오는 확장의 VSIX 매니페스트가 동일한 업데이트가 설치 됩니다 `ID` 하나씩 설치 및 더 높은 `Version` 수입니다. 경우는 `Version` 번호는 동일 하거나 낮은, 패키지를 설치할 수 없습니다. 경우는 `ID` 값 일치 하지 않는 경우 아직 설치 되지 않은 패키지를 별도 확장으로 인식 됩니다.

 개발 하는 동안 충돌을 방지 하려면는 진행에서 확장의 이전 버전을 제거 하 고 또한 제거 또는 기타 잠재적으로 충돌 하는 확장을 사용 하지 않도록 설정는 것이 좋습니다.

## <a name="to-update-an-extension-on-your-system"></a>시스템에서 확장을 업데이트 하려면

1. **도구** 메뉴에서 **확장 및 업데이트**를 클릭합니다.

2. 왼쪽된 창에서 클릭 **업데이트**합니다.

3. 가운데 창에서 업데이트를 설치 하려면 클릭 합니다.

     업데이트 된 확장의 버전 번호는 다른 정보와 함께 오른쪽 창에 표시 됩니다.

4. 오른쪽 창의 맨 아래에서 클릭 **업데이트**합니다.

## <a name="to-publish-an-update-of-an-extension"></a>확장의 업데이트를 게시 하려면

1. Visual Studio에서 업데이트 하려는 확장에 대 한 솔루션을 엽니다. 변경 내용을 확인 합니다.

    > [!IMPORTANT]
    > 부호 없는 모든 사용자 확장 자동으로 업데이트 되지 않습니다. 확장 프로그램에 항상 서명 해야 합니다.

2. **솔루션 탐색기**오픈 *source.extension.manifest*합니다.

3. 매니페스트 디자이너에서 숫자 값을 증가 합니다 **버전** 필드입니다.

4. 솔루션을 저장 하 고 빌드하십시오.

5. 새 업로드 *.vsix* 파일 (에 * \bin\Debug\* 프로젝트의 폴더)에 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 웹 사이트입니다.

     확장의 이전 버전을 가진 사용자가 열리면 **확장 및 업데이트**를 새 버전에 표시 됩니다는 **업데이트** 도구를 자동으로 업데이트를 찾도록 설정 되어 있는 목록입니다.

     아래쪽의 업데이트 자동 확인을 사용 하지 않도록 설정 하거나 설정할 수 있습니다 합니다 **업데이트** 창 (**사용 가능한 업데이트의 자동 검색 설정/해제**), 변경 내용을 **확인 업데이트가** 에서 설정 **도구** > **옵션** > **환경**  >  **확장 및 업데이트**합니다.

    > [!NOTE]
    > Visual Studio 2015 업데이트 2에서부터 지정할 수 있습니다 (에 **도구가** > **옵션** > **환경**  >  **확장 및 업데이트**) 업데이트를 사용할지 자동 사용자별 확장, 모든 사용자 확장 또는 둘 다 (기본 설정).

## <a name="see-also"></a>참고자료
- [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)
- [찾기 및 Visual Studio 확장을 사용 하 여](../ide/finding-and-using-visual-studio-extensions.md)