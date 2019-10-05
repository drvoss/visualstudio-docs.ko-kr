---
title: '방법: VSIX 패키지에 종속성을 추가 합니다. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee6ebeb776e6aa85d5fba200ac357a7375fa2b99
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341053"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>방법: VSIX 패키지에 종속성을 추가 합니다.

이미 대상 컴퓨터에 존재 하지 않는 모든 종속성을 설치 하는 VSIX 패키지 배포를 설정할 수 있습니다. 이를 위해 VSIX 종속성을 포함 합니다 *source.extension.vsixmanifest* 파일입니다.

## <a name="to-add-a-dependency"></a>종속성을 추가 하려면

1. 엽니다는 *source.extension.vsixmanifest* 파일을 **디자인** 보기. 로 이동 합니다 **종속성** 탭을 클릭 **새로 만들기**합니다.

2. 설치 된 확장을 추가 하:에 **새 종속성 추가** 대화 상자에서 **확장을 설치** 를 선택한 후는 **이름**, 목록에서 확장을 선택 합니다.

3. 설치 되지 않은 다른 VSIX를 추가 하려면:에 **새 종속성 추가** 대화 상자에서 **파일 시스템에 파일** 사용 하 여는 **찾아보기** VSIX를 선택 하려면 단추입니다.

## <a name="require-a-specific-visual-studio-release"></a>특정 Visual Studio 릴리스 필요

확장 프로그램에서 Visual Studio 2017의 특정 버전에 필요한 경우 예를 들어, 15.3에 릴리스된 기능에 따라, VSIX에 빌드 번호를 지정할 수 있습니다 **에서 InstallationTarget**합니다. 예를 들어, 15.3 릴리스 빌드 번호 '15.0.26730.3'는 있습니다. 릴리스 빌드 번호를 매핑을 볼 수 있습니다 [여기](../install/visual-studio-build-numbers-and-release-dates.md)합니다. 이때 릴리스를 사용 하 여 번호 '15.3' 제대로 작동 하지 것입니다.

확장 프로그램에 15.3 필요 하거나 선언 합니다 이상 합니다 **버전에서 InstallationTarget** 으로 [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller 이전 버전의 Visual Studio를 감지 하 고 이후의 업데이트는 필요한 사용자에 게 알립니다.

## <a name="see-also"></a>참고자료

- [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)
- [Windows Installer 배포에 대 한 확장 준비](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
