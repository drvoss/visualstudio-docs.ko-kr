---
title: 시스템 요구 사항 검색 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a794391001934164e52bdd73d940cb73ff3b5f3b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500084"
---
# <a name="detect-system-requirements"></a>시스템 요구 사항 검색
VSPackage는 Visual Studio가 설치 되어 있지 않으면 작동 하지 않습니다. Microsoft Windows Installer를 사용 하 여 VSPackage의 설치를 관리할 때 Visual Studio가 설치 되어 있는지 여부를 검색 하려면 설치 관리자를 구성할 수 있습니다. 예를 들어 다른 요구 사항에 대 한 시스템을 확인 하 고, 특정 버전의 Windows 또는 특정 양의 RAM 구성할 수도 있습니다.  
  
## <a name="detect-visual-studio-editions"></a>Visual Studio 버전 검색  
 버전의 Visual Studio가 설치 되어 있는지 확인 하십시오는 값을 **설치** 레지스트리 키가 *(REG_DWORD) 1* 다음 표에 나열 된 적절 한 폴더에 합니다. Visual Studio 버전의 계층 구조는 참고 합니다.  
  
1.  엔터프라이즈  
  
2.  2차원 형식  
  
3.  커뮤니티  
      
최신 버전을 설치 하면 이전 버전의 경우 해당 버전에 대 한 레지스트리 키도 추가 됩니다. 즉 Enterprise edition에 설치 된 경우에 **설치** 키로 설정 됩니다 *1* Professional 및 Community 버전 뿐만 아니라 엔터프라이즈에 대 한 합니다. 따라서 해야 최신 버전에 대해서만 확인 해야 합니다.  
  
> [!NOTE]
>  레지스트리 편집기의 64 비트 버전에서는 32 비트 키 아래에 표시 됩니다 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**합니다. Visual Studio 키는 아래 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**합니다.  
  
|제품|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (통합 및 격리)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detect-when-visual-studio-is-running"></a>Visual Studio가 실행 하는 경우를 검색 합니다.  
 VSPackage를 설치할 때 Visual Studio가 실행 하는 경우 VSPackage는 올바르게 등록할 수 없습니다. 설치 관리자는 Visual Studio가 실행 하는 경우를 감지 하 고 프로그램을 설치 하려면 다음을 거부 해야 합니다. Windows Installer 이러한 검색을 사용 하도록 테이블 항목을 사용할 수 없습니다. 대신 만들어야 사용자 지정 작업을 다음과 같이: 사용 합니다 `EnumProcesses` 함수를 검색 하는 *devenv.exe* 처리 한 다음 시작 조건을 사용 되는 설치 관리자 속성을 설정 하거나 또는 조건에 따라 대화 상자를 표시 라는 Visual Studio를 닫을 수입니다.  
  
## <a name="see-also"></a>참고자료  
 [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)