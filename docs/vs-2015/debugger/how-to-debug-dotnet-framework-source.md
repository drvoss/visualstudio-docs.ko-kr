---
title: '방법: .NET Framework 소스 디버그 | Microsoft Docs'
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
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205438"
---
# <a name="how-to-debug-net-framework-source"></a>방법: .NET Framework 소스 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

최신 버전의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에 대 한 새로운 기능을 제공 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 디버깅 합니다. 디버그 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 소스 코드에 대 한 기호 디버깅에 대 한 액세스 있어야 합니다. 한 단계씩 실행할 수 있도록 해야 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 원본입니다.  
  
 설정할 수 있습니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 단계별 실행 및 기호를 다운로드 합니다 **옵션** 대화 상자. 기호 다운로드를 설정할 때 기호를 즉시 다운로드할 수도 있고 나중에 다운로드하도록 옵션만 설정해 놓을 수도 있습니다. 기호를 즉시 다운로드하지 않으면 기호는 다음 번에 애플리케이션 디버깅을 시작할 때 다운로드됩니다. 수동으로 다운로드 하 여 수행할 수도 있습니다는 **모듈** 창 또는 **호출 스택** 창입니다.  
  
### <a name="to-enable-net-framework-source-debugging"></a>.NET Framework 소스 디버깅을 사용하려면  
  
1. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
2. 에 **옵션** 대화 상자에서 클릭 합니다 **디버깅** 범주입니다.  
  
3. 에 **일반적인** 상자에서 설정 **.NET Framework** 소스 단계별 실행 합니다.  
  
    1. 내 코드만을 사용하는 경우에는 내 코드만을 이제 사용하지 않는다는 경고 대화 상자가 표시됩니다. **확인**을 클릭합니다.  
  
    2. 기호 캐시 위치가 설정되어 있지 않으면 기본 기호 캐시 위치가 이제 설정된다는 또 다른 경고 대화 상자가 표시됩니다. **확인**을 클릭합니다.  
  
4. 아래는 **디버깅** 범주를 클릭 **기호**합니다.  
  
5. 기호 캐시 위치를 변경하려면:  
  
    1. 엽니다는 **디버깅** 왼쪽 상자에서 노드.  
  
    2. 아래는 **디버깅** 노드를 클릭 **기호**합니다.  
  
    3. 위치를 편집 **기호 서버에서이 디렉터리로 기호 캐시** 누르거나 **찾아보기** 위치를 선택 합니다.  
  
6. 기호를 즉시 다운로드 하려면 클릭 **기호 로드를 사용 하 여 위의 위치**합니다.  
  
     이 단추는 디자인 모드에서 사용할 수 없습니다.  
  
     지금 기호를 다운로드하도록 선택하지 않으면 다음 번 프로그램 디버깅을 시작할 때 기호가 자동으로 다운로드됩니다.  
  
7. **확인**을 클릭하여 **옵션** 대화 상자를 닫습니다.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>모듈 창을 사용하여 Framework 기호를 로드하려면  
  
1. 에 **모듈** 창에서 기호가 로드 되지 않은 모듈을 마우스 오른쪽 단추로 클릭 합니다. 기호가 로드 되 면 또는 확인 하 여 하지 할 수 있습니다 합니다 **기호 상태** 열입니다.  
  
2. 가리킨 **에서 기호 로드** 클릭 **Microsoft 기호 서버** Microsoft 공용 기호 서버에서 기호를 다운로드 하도록 또는 **기호 경로** 디렉터리에서 로드 하려면 이전에 저장 된 기호입니다.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>호출 스택 창을 사용하여 Framework 기호를 로드하려면  
  
1. 에 **호출 스택** 창에서 기호가 로드 되지 않은 프레임을 마우스 오른쪽 단추로 클릭 합니다. 프레임이 흐리게 표시됩니다.  
  
2. 가리킨 **에서 기호 로드** 클릭 **Microsoft 기호 서버** 하거나 **기호 경로**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) (관리 코드 디버그)  
 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
