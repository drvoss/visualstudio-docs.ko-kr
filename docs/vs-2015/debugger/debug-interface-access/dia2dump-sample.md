---
title: Dia2dump 샘플 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197595"
---
# <a name="dia2dump-sample"></a>Dia2dump 샘플
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dia2dump 샘플 Visual Studio와 함께 설치 되 고 Dia2dump.cpp 소스 파일을 포함 합니다. 명령줄에서 실행 하 고 전체 프로그램 데이터베이스 (.pdb) 파일의 내용을 표시 하는 컴파일된 실행 파일입니다.  
  
### <a name="to-install-the-sample"></a>샘플을 설치 하려면  
  
1. 시스템에 Visual Studio 설치 프로그램 시작 페이지에서 설명 하는 모든 설치 요구 사항을 충족 하는지 확인 합니다.  
  
2. Visual Studio를 설치 하 고 포함 된 샘플의 모든 설정 및 설치 지침을 따르세요.  
  
#### <a name="to-build-the-sample"></a>이 샘플을 빌드하려면  
  
1. Visual Studio에서 Dia2dump.sln 파일을 엽니다. (필요한 경우 Visual Studio는 먼저 도움이 Dia2dump 프로젝트를 업그레이드 합니다.)  
  
2. 프로젝트 속성 페이지에서에 **C /C++**  &#124; **일반** &#124; **Additional Include Directories** 속성을 지정 합니다 `..\DIA SDK\include` 디렉터리입니다. 이 컴파일러 dia2.h 파일을 찾을 수 있도록 보장 합니다.  
  
3. **빌드** 메뉴에서 **솔루션 다시 빌드**를 클릭합니다.  
  
4. Visual Studio를 닫습니다.  
  
#### <a name="to-run-the-sample"></a>이 샘플을 실행하려면  
  
1. 명령 프롬프트를 열고 다음을 입력 합니다.  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [Dia2dump.cpp 소스 파일](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [방법: 실패한 Visual Studio 프로젝트 업그레이드 문제 해결](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
