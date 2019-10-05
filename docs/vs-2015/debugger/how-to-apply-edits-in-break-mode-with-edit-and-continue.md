---
title: '방법: 편집을 사용 하 여 중단 모드에서 편집을 적용 하 고 계속 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c04dc0ae6e5272d2544ad7436fa7ca516c9a022
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437354"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>방법: 편집을 사용 하 여 중단 모드에서 편집을 적용 하 고 계속
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집하며 계속하기를 사용하면 실행을 중지한 후에 다시 시작하지 않고도 중단 모드에서 코드를 편집한 다음 계속 진행할 수 있습니다.  
  
 다음과 같은 디버깅 시나리오에서는 편집하며 계속하기를 사용할 수 없습니다.  
  
- 혼합 모드(네이티브/관리) 디버깅  
  
- SQL 디버깅  
  
- Dr. Watson 덤프 디버깅  
  
- **처리되지 않은 예외에 대한 호출 스택 해제** 옵션을 선택하지 않은 상태에서 처리되지 않은 예외가 발생한 후 코드 편집  
  
- 포함된 런타임 애플리케이션 디버깅  
  
- 응용 프로그램을 디버깅할 **연결할** 사용 하 여 응용 프로그램을 실행 하는 대신 **시작** 에서 합니다 **디버그** 메뉴.  
  
- 최적화된 코드 디버깅  
  
- 대상이 64비트 애플리케이션인 경우 관리 코드 디버깅. 편집하며 계속하기를 사용하려면 대상을 x86으로 설정해야 합니다. (_프로젝트_**속성**합니다 **컴파일** 탭 **고급 컴파일러** 설정 합니다.).  
  
- 빌드 오류가 발생하여 새 버전을 빌드하는데 실패한 후에 이전 버전의 코드 디버깅  
  
### <a name="to-edit-code-in-break-mode"></a>중단 모드에서 코드를 편집하려면  
  
1. 다음 중 한 가지 방법으로 중단 모드를 시작합니다.  
  
    - 코드에 중단점을 설정한 다음, **디버그** 메뉴에서 **디버깅 시작**을 선택하고 애플리케이션이 중단점에 도달할 때까지 기다립니다.  
  
         – 또는 –  
  
    - 디버깅을 시작한 다음, **디버그** 메뉴에서 **모두 중단**을 선택합니다.  
  
         – 또는 –  
  
    - 예외가 발생 하는 경우 선택할 **편집 사용** 에**예외 도우미**합니다.  
  
2. 코드에 필요한 내용을 올바르게 변경합니다.  
  
     자세한 내용은 [Visual Basic 편집 하며 계속 하기에서 지원 되지 않는 편집](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)합니다.  
  
    > [!NOTE]
    > 편집하며 계속하기에서 허용되지 않는 코드 변경 작업을 수행하면 자주색 물결선이 편집 내용 아래에 밑줄로 표시되고 해당 작업이 작업 목록에 나타납니다. 잘못된 코드 변경 내용을 취소하지 않으면 코드 실행을 계속 진행할 수 없습니다.  
  
3. **디버그** 메뉴에서 **계속**을 클릭하여 실행을 다시 시작합니다.  
  
     적용한 편집 내용이 프로젝트에 통합된 상태로 코드가 실행됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Basic에서 지원 되지 않는 편집 편집 하며 계속 하기](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [편집하며 계속하기(Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
