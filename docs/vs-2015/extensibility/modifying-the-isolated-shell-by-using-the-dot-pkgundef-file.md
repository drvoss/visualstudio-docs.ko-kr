---
title: 사용 하 여 격리 셸 수정 합니다. Pkgundef 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538396"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>사용 하 여 격리 셸 수정 합니다. Pkgundef 파일
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

격리 셸 응용 프로그램에서 지정 된 레지스트리 항목을 제외.pkgundef 파일을 수정할 수 있습니다. 일반적으로 처음으로 컴퓨터에 응용 프로그램이 시작 되는 Visual Studio shell 복사 기존 Visual Studio 레지스트리 항목을 응용 프로그램에 대 한 루트 레지스트리 키입니다. 현재 설치 된 Vspackage에 대 한 참조가 포함 됩니다.  
  
 격리 셸 응용 프로그램에서 특정 레지스트리 항목을 제외할 항목 뒤에 키를 패키지 하는 응용 프로그램.pkgundef 파일에 추가 합니다. .Pkgdef 파일에서와 마찬가지로 키 및 항목은 표시 즉, [$RootKey $] 또는 [$RootKey$\\*하위 키*] 및 "*항목*" =*값*여기서 *하위 키* 하위 키에 영향을 줄은 *항목이* 제거할 항목이 및 *값* 은 `""` 또는 `dword:00000000`합니다.  
  
 레지스트리 키에서 여러 항목을 제외할 단지 나열 키를 한 번 뒤에 줄 제외할 각 항목에 대 한 합니다.  
  
 격리 셸 응용 프로그램에서 전체 레지스트리 키를 제외 하려면 응용 프로그램.pkgundef 파일에 키를 추가 하지만 해당 키에 대 한 레지스트리 항목을 지정 하지 마세요.  
  
 .Pkgundef 파일에 주석을 추가할 수 있습니다. 한 줄 주석을 처음 두 문자로 슬래시 두 개 있어야 합니다.  
  
 예를 들어, 제거 하는 **연결할 데이터베이스** 및 **r 서버에 연결** 명령을 **도구** 메뉴에서 줄의 주석 처리 제거:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 줄을 추가 합니다.  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 응용 프로그램의.pkgundef 파일입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 기능의 패키지 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [격리 셸 사용자 지정](../extensibility/customizing-the-isolated-shell.md)
