---
title: VSPackage 파일 위치를 VS Shell 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0662bfe22b4c78bb754bbac2fbfdd281a4a7bce
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408509"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VSPackage 파일 위치를 VS Shell에 지정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage를 로드 하는 DLL 어셈블리를 찾을 수 있어야 합니다. 다음 표에 설명 된 대로 다양 한 방법으로를 찾을 수 있습니다.  
  
|메서드|설명|  
|------------|-----------------|  
|코드 베이스 레지스트리 키를 사용 합니다.|코드 베이스 키를 사용할 수 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 모든 정규화 된 파일 경로에서 VSPackage 어셈블리를 로드 합니다. 키의 값에는 dll 파일 경로 여야 합니다. 이 가장 좋은 방법은 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 패키지 어셈블리를 로드 합니다. 이 기술은 때때로 "코드 베이스/개인 설치 디렉터리 기술입니다." 이라고 등록 하는 동안 값의 코드 베이스의 전달 등록 특성 클래스의 인스턴스를 통해 여 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> 형식입니다.|  
|DLL에 배치 합니다 **PrivateAssemblies** 디렉터리입니다.|어셈블리를 배치 합니다 **PrivateAssemblies** 의 하위 디렉터리를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디렉터리입니다. 어셈블리에 배치 **PrivateAssemblies** 는 자동으로 검색 하지만 표시 되지 합니다 **참조 추가** 대화 상자. 차이점 **PrivateAssemblies** 하 고 **PublicAssemblies** 어셈블리는에 **PublicAssemblies** 에 열거 되어를 **참조 추가**  대화 상자. "코드 베이스/개인 설치 디렉터리" 기법을 사용 하지 않도록 선택한 경우에 설치 해야 합니다 **PrivateAssemblies** 디렉터리입니다.|  
|강력한 이름의 어셈블리와 어셈블리 레지스트리 키를 사용 합니다.|어셈블리 키를 명시적으로 보내기 위해 사용할 수 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 라는 VSPackage 어셈블리를 강력한 로드 합니다. 키의 값에는 어셈블리의 강력한 이름 이어야 합니다.|  
|DLL에 배치 합니다 **PublicAssemblies** 디렉터리입니다.|마지막으로, 어셈블리도 배치 될 수 있습니다 합니다 **PublicAssemblies** 하위 디렉터리입니다. 어셈블리에 배치 **PublicAssemblies** 는 자동으로 검색 및에 나타납니다 합니다 **참조 추가** 대화 상자 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.<br /><br /> VSPackage 어셈블리에만 배치 해야 합니다 **PublicAssemblies** 디렉터리가 있을 경우 다른 VSPackage 개발자가 다시 사용할 수 있는 구성 요소를 관리 합니다. 대부분의 어셈블리에는이 조건을 충족 하지 않습니다.|  
  
> [!NOTE]
> 모든 종속 어셈블리에 대 한 강력한 이름의 서명 된 어셈블리를 사용 합니다. 이러한 어셈블리는 또한 고유한 디렉터리나 전역 어셈블리 캐시 (GAC)에 설치 되어야 합니다. 이 약한 이름 바인딩을 이라고 하는 동일한 기본 파일 이름이 있는 어셈블리와 충돌 방지 됩니다.
