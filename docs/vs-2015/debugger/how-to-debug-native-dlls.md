---
title: '방법: 네이티브 Dll 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702674"
---
# <a name="how-to-debug-native-dlls"></a>방법: 네이티브 Dll 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
 DLL 디버깅은 다음 위치에서 시작할 수 있습니다.  
  
- DLL을 호출하는 실행 파일을 만드는 데 사용되는 프로젝트  
  
  \- 또는 -  
  
- DLL 자체를 만드는 데 사용되는 프로젝트  
  
  실행 파일을 만드는 데 사용되는 프로젝트가 있으면 그 프로젝트부터 디버깅을 시작합니다. 그런 다음 DLL의 소스 파일을 열고 그 파일에 중단점을 설정할 수 있습니다. 이는 이 소스 파일이 실행 파일을 만드는 데 사용되는 프로젝트에 포함되지 않은 경우에도 적용됩니다. 자세한 내용은 [중단점](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)을 참조하세요.  
  
  DLL을 만드는 데 사용되는 프로젝트에서 디버깅을 시작하는 경우 DLL을 디버깅하는 데 사용할 실행 파일을 지정해야 합니다.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>디버그 세션에 사용할 실행 파일을 지정하려면  
  
1. **솔루션 탐색기**, DLL을 만드는 프로젝트를 선택 합니다.  
  
2. **뷰** 메뉴 선택**속성 페이지**합니다.  
  
3. 에 **속성 페이지** 대화 상자를 엽니다는 **구성 속성** 폴더를 선택 합니다 **디버깅** 범주입니다.  
  
4. 에 **명령** 상자에서 컨테이너에 대 한 경로 이름을 지정 합니다. C:\Program Files\MyApplication\MYAPP.EXE와 같이 지정합니다.  
  
5. 에 **명령 인수** 상자에서 실행 파일에 필요한 인수를 지정 합니다.  
  
   실행 파일을 지정 하지 않는 경우는 _프로젝트_**속성 페이지** 대화 상자를 [디버깅 세션 대화 상자에 대 한 실행](../debugger/executable-for-debugging-session-dialog-box.md) 디버깅을 시작할 때 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)
