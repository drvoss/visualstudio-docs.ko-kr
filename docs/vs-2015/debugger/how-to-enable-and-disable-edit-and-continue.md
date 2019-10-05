---
title: '방법: 편집 하며 계속 하기 설정 / 해제 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689259"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>방법: 편집 하며 계속 하기 설정 / 해제
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 하지 않도록 설정 하거나 편집 하며 계속 하기를 사용 하도록 설정 합니다 **옵션** 디자인 타임에 대화 상자. 디버깅 중에는 이 설정을 변경할 수 없습니다.  
  
 편집하며 계속하기는 디버그 빌드에서만 작동합니다. 네이티브 C++의 경우 편집하며 계속하기를 실행하려면 /INCREMENTAL 옵션을 사용해야 합니다.  
  
## <a name="procedures"></a>절차  
  
#### <a name="to-enabledisable-edit-and-continue"></a>편집하며 계속하기를 사용하거나 사용하지 않도록 설정하려면  
  
1. 디버깅 옵션 페이지 열기 (**도구 / 옵션 / 디버깅**).  
  
2. 아래로 스크롤하여 **편집 하며 계속 하기** 범주입니다.  
  
3. 를 사용 하도록 설정 하려면 선택 합니다 **편집을 사용 하도록 설정 하 고 계속** 확인란 합니다. 이 기능을 사용하지 않도록 설정하려면 이 확인란의 선택을 취소합니다.  
  
   > [!NOTE]
   > IntelliTrace를 사용하도록 설정되어 있고 IntelliTrace 이벤트 및 호출 정보를 모두 수집하는 경우 편집하며 계속하기를 사용하지 않도록 설정됩니다. 자세한 내용은 [IntelliTrace 구성](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)합니다.  
  
4. **확인**을 클릭합니다.  
  
   이러한 옵션에 대 한 자세한 내용은 참조 하세요. [옵션 대화 상자, 디버깅, 일반](../debugger/general-debugging-options-dialog-box.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [편집하며 계속하기](../debugger/edit-and-continue.md)
