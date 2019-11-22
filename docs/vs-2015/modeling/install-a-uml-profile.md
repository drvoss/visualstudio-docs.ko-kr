---
title: Install a UML profile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14911cda4cfc2be5fece6005a879427c10529bbc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298909"
---
# <a name="install-a-uml-profile"></a>UML 프로필 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 프로필을 통해 Visual Studio를 확장할 수 있습니다. 프로필을 사용하면 UML 모델에서 만들 수 있는 요소에 스테레오타입 및 다른 속성을 추가할 수 있습니다. 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 프로필을 사용하여 만든 UML 모델을 받은 경우 동일한 프로필을 설치하지 않으면 일부 속성이 표시되지 않습니다.

 프로필은 Visual Studio 확장 내에 배포됩니다. 확장에 메뉴 명령과 같은 다른 기능이 포함될 수도 있습니다. For more information, see [Managing Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160728).

### <a name="to-install-a-uml-profile-on-your-computer"></a>컴퓨터에 UML 프로필을 설치하려면

1. 프로필이 Visual Studio 확장(`.vsix`) 파일 형식으로 제공되어야 합니다. 동일한 파일에 다른 기능이 있을 수도 있습니다.

     `.vsix` 파일을 컴퓨터의 편리한 위치로 이동합니다.

2. Windows 탐색기(또는 파일 탐색기)에서 `.vsix` 파일을 두 번 클릭하거나 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 내에서 엽니다.

3. Click **Install** in the dialog box that appears.

4. To uninstall or temporarily disable the extension, open **Extension Manager** from the **Tools** menu.

### <a name="to-uninstall-or-disable-a-profile-extension"></a>프로필 확장을 제거하거나 사용하지 않도록 설정하려면

1. On the Visual Studio **Tools** menu, click **Extension Manager**.

2. Click the extension that you want to remove, and then click **Disable** or **Uninstall**.

## <a name="see-also"></a>관련 항목:
 [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md)
