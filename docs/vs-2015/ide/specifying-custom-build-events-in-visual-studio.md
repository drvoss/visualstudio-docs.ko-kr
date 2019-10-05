---
title: 사용자 지정 빌드 이벤트 지정
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d00c520f75869e6cf886074c482575f1170e923a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679523"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Visual Studio에서 사용자 지정 빌드 이벤트 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 빌드 이벤트를 지정하여 빌드가 시작되기 전이나 완료된 후에 명령을 자동으로 실행할 수 있습니다. 예를 들어 빌드가 시작되기 전에 .bat 파일을 실행하거나 빌드가 완료된 후에 새 파일을 폴더로 복사할 수 있습니다. 빌드가 빌드 프로세스의 해당 지점에 성공적으로 도달하는 경우에만 빌드 이벤트가 실행됩니다.

 사용 중인 프로그래밍 언어에 대한 자세한 내용은 다음 항목을 참조하세요.

- Visual Basic--[방법: 빌드 이벤트 지정(Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)을 참조하세요.

- Visual C# 및 F#-[방법: 빌드 이벤트 지정 (C#)](../ide/how-to-specify-build-events-csharp.md)합니다.

- Visual C++--[빌드 이벤트 지정](https://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc)

## <a name="syntax"></a>구문
 빌드 이벤트는 DOS 명령과 동일한 구문을 따르지만 매크로를 사용하여 빌드 이벤트를 보다 쉽게 만들 수 있습니다. 사용 가능한 매크로 목록은 [빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)를 참조하세요.

 최상의 결과를 얻으려면 다음 서식 지정 팁을 따릅니다.

- .bat 파일을 실행하는 모든 빌드 이벤트 앞에 `call` 문을 추가합니다.

     예: `call C:\MyFile.bat`

     예: `call C:\MyFile.bat call C:\MyFile2.bat`

- 파일 경로를 따옴표로 묶습니다.

     예([!INCLUDE[win8](../includes/win8-md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- 줄 바꿈을 사용하여 여러 명령을 구분합니다.

- 필요에 따라 와일드카드를 포함합니다.

     예: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`

    > [!NOTE]
    > 위 코드의 `%I`는 배치 스크립트에서 `%%I`여야 합니다.

## <a name="see-also"></a>참고 항목
 [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md) [빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [MSBuild 특수 문자](../msbuild/msbuild-special-characters.md) [연습: 애플리케이션 빌드](../ide/walkthrough-building-an-application.md)
