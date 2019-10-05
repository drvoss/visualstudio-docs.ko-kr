---
title: -Command (devenv.exe) | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a87be2f0b60b02588b5ba73e5837caca1b4bd8ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685839"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE(통합 개발 환경)를 시작한 후 지정된 명령을 실행합니다.  
  
## <a name="syntax"></a>구문  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>인수  
 `CommandName`  
 필수 요소. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 명령 또는 해당 별칭의 전체 이름으로, 큰따옴표로 묶습니다. 명령 및 별칭 구문에 대한 자세한 내용은 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)을 참조하세요.  
  
## <a name="remarks"></a>주의  
 시작이 완료된 후 IDE는 명명된 명령을 실행합니다. 이 스위치를 사용하면 IDE는 시작 시 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 시작 페이지를 표시하지 않습니다.  
  
 추가 기능이 명령을 표시할 경우에는 이 스위치를 사용하여 명령줄에서 추가 기능을 시작할 수 있습니다. 자세한 내용은 [방법: 추가 기능 관리자를 사용하여 추가 기능 제어](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb)를 참조하세요.  
  
## <a name="example"></a>예제  
 이 예제에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 시작하고 Open Favorite Files(즐겨찾기 파일 열기) 매크로를 자동으로 실행합니다.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>참고 항목  
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
