---
title: '방법: 모듈 창 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696121"
---
# <a name="how-to-use-the-modules-window"></a>방법: 모듈 창 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> SQL 또는 스크립트 디버깅에는 이 기능을 사용할 수 없습니다.  
  
 합니다 **모듈** 창 각각에 대 한 관련 정보를 표시 및 프로그램에서 사용 되는 Dll와 EXE가 나열 됩니다.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>중단 모드 또는 실행 모드에서 모듈 창을 표시하려면  
  
- 에 **디버그** 메뉴 선택 **Windows**를 클릭 하 고 **모듈**합니다.  
  
     기본적으로 **모듈** 창에서는 모듈이 로드 순서대로 정렬됩니다. 그러나 열을 기준으로 정렬할 수도 있습니다.  
  
### <a name="to-sort-by-any-column"></a>열별로 정렬하려면  
  
- 정렬 기준이 될 열 맨 위에 있는 단추를 클릭합니다.  
  
     기호를 로드 하거나 기호 경로 지정 합니다 **모듈** 바로 가기 메뉴를 사용 하 여 창입니다.  
  
## <a name="loading-symbols"></a>기호 로드  
 에 **모듈** 창 디버깅 기호가 로드 된 모듈을 볼 수 있습니다. 이 정보에 표시 된 **기호 상태** 열입니다. 상태 표시 되 면 **건너뜀 loadingCannot 찾거나 PDB 파일을 엽니다**, 또는 **포함/제외 설정으로 로드가 비활성화 되었습니다**, Microsoft 공용 기호에서 기호를 다운로드 하도록 디버거에 지시할 수 있습니다 서버 컴퓨터의 기호 경로에서 기호를 로드 합니다. 자세한 내용은 참조 하세요. [지정 기호 (.pdb) 및 소스 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>기호를 수동으로 로드하려면  
  
1. 에 **모듈** 창에서 기호가 로드 되지 않은 모듈을 마우스 오른쪽 단추로 클릭 합니다.  
  
2. 가리킨 **에서 기호 로드** 클릭 하 고 **Microsoft 기호 서버** 하거나 **기호 경로**합니다.  
  
#### <a name="to-change-symbol-load-settings"></a>기호 로드 설정을 변경하려면  
  
1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.  
  
2. 클릭 **기호 설정**합니다.  
  
     에 설명 된 대로 이제 기호 로드 설정의 변경할 수 있습니다 [기호 위치를 지정 하 고 로드 동작](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)합니다. 디버깅 세션을 다시 시작할 때까지 변경 내용이 적용되지 않습니다.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>특정 모듈에 대한 기호 로드 동작을 변경하려면  
  
1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.  
  
2. 가리킨 **자동 기호 로드 설정을** 클릭 하 고 **항상 수동으로 로드** 하거나 **기본**입니다. 디버깅 세션을 다시 시작할 때까지 변경 내용이 적용되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [실행 중단](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)   
 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
