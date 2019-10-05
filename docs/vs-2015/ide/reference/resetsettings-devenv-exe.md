---
title: -ResetSettings(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b35026140b424da0f7fa71cb9e70b72c3dba243
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689652"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings(devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 기본 설정을 복원하고 자동으로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE를 시작합니다. 필요에 따라 설정을 지정한 .vssettings 파일로 다시 설정합니다.  
  
 기본 설정은 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]가 처음 시작될 때 선택된 프로필에 따라 결정됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>인수  
 `SettingsFile`  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에 적용할 .vssettings 파일의 전체 경로 및 이름.  
  
 일반 개발 설정 프로필을 복원하려면 `General`을 사용합니다.  
  
## <a name="remarks"></a>주의  
 `SettingsFile`이 지정되지 않은 경우에는 다음번에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 시작할 때 기본 설정 컬렉션을 선택할지 묻는 메시지가 표시됩니다.  
  
## <a name="example"></a>예제  
 다음 명령줄은 `MySettings.vssettings` 파일에 저장된 설정을 적용합니다.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
