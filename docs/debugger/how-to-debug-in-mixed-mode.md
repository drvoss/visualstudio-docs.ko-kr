---
title: '방법: 혼합된 모드에서 디버그 | Microsoft Docs'
ms.custom: ''
ms.date: 11/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ef87a1f9fd90395a9a1f5c99ad6e8090b13304e
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295477"
---
# <a name="how-to-debug-in-mixed-mode"></a>방법: 혼합된 모드에서 디버깅
다음 절차에서는 관리 및 네이티브 코드 함께, 혼합 모드 라고도 디버깅에 대 한 디버깅을 사용 하는 방법에 설명 합니다. 두 가지 혼합 모드 디버깅 시나리오가 있습니다.  
  
- 네이티브 코드에서 DLL을 호출 하는 앱이 작성 및 DLL 관리 됩니다. 
  
- 관리 코드에서 DLL을 호출 하는 앱이 작성 되며 DLL에서 네이티브 코드. 이 시나리오를 자세히 설명 하는 자습서를 참조 하세요. [관리 및 네이티브 코드 디버그](../debugger/how-to-debug-managed-and-native-code.md)합니다.
   
호출 앱 프로젝트의 관리 및 네이티브 디버거를 설정할 수 있습니다 **속성** 페이지입니다. 네이티브 및 관리 앱 간에 다를 설정 합니다. 

호출 하는 앱의 프로젝트에 액세스할 수 없으면 DLL 프로젝트에서 DLL을 디버깅할 수 있습니다. DLL 프로젝트만을 디버깅 하려면 혼합된 모드가 필요는 없습니다. 자세한 내용은 [방법: DLL 프로젝트에서 디버그](../debugger/how-to-debug-from-a-dll-project.md)합니다. 

> [!NOTE]
> 대화 상자 및 명령 표시에서 가장이 문서에서는 Visual Studio 설정이 나 버전에 따라 달라질 수 있습니다. 설정을 변경 하려면 **도구가** > **설정 가져오기 및 내보내기**합니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>네이티브 호출 앱에 대 한 혼합 모드 디버깅 사용  
  
1. c + + 프로젝트를 선택 **솔루션 탐색기** 을 클릭 합니다 **속성** 아이콘을 눌러 **Alt**+**Enter**, 또는 마우스 오른쪽 단추로 **속성**합니다.
   
1. 에  **\<프로젝트 > 속성 페이지** 대화 상자에서 **구성 속성**를 선택한 후 **디버깅**합니다.  
   
1. 설정 **디버거 형식** 하 **혼합** 하거나 **자동**합니다.
   
1. **확인**을 선택합니다.
   
   ![혼합된 모드 디버깅을 사용 하도록 설정](../debugger/media/dbg-mixed-mode-from-native.png "혼합된 모드 디버깅 사용")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>관리 되는 호출 앱에 대 한 혼합 모드 디버깅 사용  
  
1. C# 또는 Visual Basic 프로젝트를 선택 **솔루션 탐색기** 선택 합니다 **속성** 아이콘을 눌러 **Alt**+**Enter**를 마우스 오른쪽 단추로 클릭 하 고 선택 하거나 **속성**합니다.
   
1. 선택 된 **디버그** 탭을 선택한 후 **네이티브 코드 디버깅 사용**합니다.
   
1. 변경 내용을 저장할 속성 페이지를 닫습니다.

   ![네이티브 코드 디버깅 사용](../debugger/media/dbg-mixed-mode-from-csharp.png "네이티브 코드 디버깅 사용")
  
>[!NOTE]
>대부분의 Visual Studio 2017 버전을 사용 해야 하는 *launchSettings.json* .NET Core 앱에서 네이티브 코드에 대 한 혼합 모드 디버깅을 사용 하려면 프로젝트 속성 대신 파일입니다. 자세한 내용은 참조 하세요 [관리 및 네이티브 코드 디버그](../debugger/how-to-debug-managed-and-native-code.md)합니다.

## <a name="see-also"></a>참고자료  
 [방법: DLL 프로젝트에서 디버그](../debugger/how-to-debug-from-a-dll-project.md)