---
title: 시스템 요구 사항 검색 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445251"
---
# <a name="detecting-system-requirements"></a>시스템 요구 사항 검색
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage는 Visual Studio가 설치 되어 있지 않으면 작동 하지 않습니다. Microsoft Windows Installer를 사용 하 여 VSPackage의 설치를 관리할 때 Visual Studio가 설치 되어 있는지 여부를 검색 하려면 설치 관리자를 구성할 수 있습니다. 예를 들어 다른 요구 사항에 대 한 시스템을 확인 하 고, 특정 버전의 Windows 또는 특정 양의 RAM 구성할 수도 있습니다.  
  
## <a name="detecting-visual-studio-editions"></a>Visual Studio 버전 검색  
 버전의 Visual Studio가 설치 되어 있는지를 확인 하려면 설치 레지스트리 키의 값 (REG_DWORD) 1 적절 한 폴더에는 다음 표에 나열 된 대로 확인 합니다. Visual Studio 버전의 계층 구조는 참고 합니다.  
  
1. Enterprise  
  
2. Professional  
  
3. 커뮤니티  
  
   "상위" 버전을 설치할 때에 "lower" 버전의 경우 해당 버전에 대 한 레지스트리 키 추가 됩니다. 즉, Enterprise edition이 설치 되어 설치 키 Professional 및 Community 버전 뿐만 아니라 엔터프라이즈에 대 한 1로 설정 됩니다. 따라서 필요한 "최고" 버전에 대해서만 확인 해야 합니다.  
  
> [!NOTE]
> 레지스트리 편집기의 64 비트 버전에서는 32 비트 키 아래에 표시 됩니다 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\합니다. Visual Studio 키는 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing 아래\\합니다.  
  
|제품|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (통합 및 격리)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Visual Studio가 실행 하는 경우를 검색 합니다.  
 VSPackage를 설치할 때 Visual Studio가 실행 하는 경우 VSPackage는 올바르게 등록할 수 없습니다. 설치 관리자는 Visual Studio가 실행 하는 경우를 감지 하 고 프로그램을 설치 하려면 다음을 거부 해야 합니다. Windows Installer 이러한 검색을 사용 하도록 테이블 항목을 사용할 수 없습니다. 대신 다음과 같이 사용자 지정 작업을 만들어야 합니다. 사용 된 `EnumProcesses` Visual Studio를 닫을 수 있는 대화 상자를 표시 하는 devenv.exe 프로세스를 검색 하 고 다음 중 하나 또는 조건에 따라 시작 조건에서 사용 되는 설치 관리자 속성을 설정 하는 함수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Installer를 사용하여 VSPackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
