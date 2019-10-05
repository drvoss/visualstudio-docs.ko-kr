---
title: 대체 문자열을 사용 합니다. Pkgdef 및 합니다. Pkgundef 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160540"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>.Pkgdef 및 .Pkgundef 파일에 사용되는 대체 문자열
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.pkgdef에서 아래 나열 된 대체 문자열을 사용할 수 있습니다 하 고 Visual Studio에 대해 정의한.pkgundef 파일 격리 셸 응용 프로그램 키를 누릅니다.  
  
## <a name="substitution-strings"></a>대체 문자열  
  
|String|Description|  
|------------|-----------------|  
|$=*RegistryEntry*$|값을 *찾아* 항목입니다. 레지스트리 항목 문자열을 백슬래시로 끝나는 경우 (\\), 레지스트리 하위 키의 기본 값이 사용 됩니다. 예를 들어, 대체 문자열 $= HKEY_CURRENT_USER\Environment\TEMP $는 현재 사용자의 임시 폴더를 확장 합니다.|  
|$AppName$|AppEnv.dll 진입점에 전달 되는 응용 프로그램의 정규화 된 이름입니다. 정규화 된 이름을 응용 프로그램 이름, 밑줄 및 프로젝트.pkgdef 파일에서 ThisVersionDTECLSID 설정의 값으로도 기록 되는 응용 프로그램 자동화 개체의 클래스 식별자 (CLSID)으로 구성 됩니다.|  
|$AppDataLocalFolder|이 응용 프로그램에 대 한 % LOCALAPPDATA % 아래의 하위 폴더입니다.|  
|$BaseInstallDir $|Visual Studio가 설치 된 위치의 전체 경로입니다.|  
|$CommonFiles$|값 % CommonProgramFiles % 환경 변수입니다.|  
|$MyDocuments$|현재 사용자의 내 문서 폴더의 전체 경로입니다.|  
|$PackageFolder$|응용 프로그램에 대 한 패키지 어셈블리 파일이 있는 디렉터리의 전체 경로입니다.|  
|$ProgramFiles $|% ProgramFiles % 환경 변수 값입니다.|  
|$RootFolder$|응용 프로그램의 루트 디렉터리의 전체 경로입니다.|  
|$RootKey$|응용 프로그램에 대 한 루트 레지스트리 키입니다. 기본적으로 루트에 HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (경우 응용 프로그램이 실행 중인지, _Config이이 키에 추가 됩니다). RegistryRoot 값으로 설정 합니다 *SolutionName*.pkgdef 파일.<br /><br /> 응용 프로그램 하위 키에서 레지스트리 값을 검색 하려면 $RootKey$ 문자열을 사용할 수 있습니다. 예를 들어, 문자열 "$$ \AppIcon $RootKey =" 응용 프로그램 루트 하위 키 아래 AppIcon 엔트리의 값을 반환 합니다.<br /><br /> 파서는은.pkgdef 파일을 순차적으로 처리 하 고 해당 항목이 이전에 정의 된 경우에 응용 프로그램 하위 키 아래에 레지스트리 항목에 액세스할 수 있습니다.|  
|$ShellFolder$|Visual Studio가 설치 된 위치의 전체 경로입니다.|  
|$System $|Windows\system32 폴더입니다.|  
|$WINDIR $|Windows 폴더입니다.|  
  
 파서가 대체 문자열을 인식 하지 못합니다 경우 대체 문자열의 해당 부분에서 수행 되지 않는 다음 레지스트리 항목 또는 환경 변수 값을 확인할 수 없습니다.
