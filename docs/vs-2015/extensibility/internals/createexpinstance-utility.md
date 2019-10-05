---
title: CreateExpInstance 유틸리티 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d778f0f31a7651412915a898bff9e4bdfe6c55f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196985"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 유틸리티
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

CreateExpInstance 유틸리티를 만드는 데, 다시 설정 하거나 Visual Studio의 실험적 인스턴스를 삭제 합니다. 디버그 하 고 내부 제품을 변경 하지 않고 Visual Studio 확장을 테스트 하는 실험적 인스턴스를 사용할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>매개 변수  
 / 만들기  
 실험적 인스턴스를 만듭니다.  
  
 / 재설정  
 실험적 인스턴스를 삭제 하 고 새 리소스를 만듭니다.  
  
 /Clean  
 실험적 인스턴스를 삭제합니다.  
  
 / VSInstance  
 복사할 기본 Visual Studio 인스턴스를 포함 하는 디렉터리의 이름입니다.  
  
 /RootSuffix  
 실험적 인스턴스 디렉터리의 이름에 추가할 접미사입니다.  
  
## <a name="remarks"></a>설명  
 Visual Studio 확장에서 작업 하는 경우 기본 실험적 인스턴스를 열고 현재 확장을 설치 하려면 F5를 눌러 수 있습니다. 실험적 인스턴스를 사용할 수 있는 경우 Visual Studio는 기본 설정을 포함 하는 것을 만듭니다.  
  
 실험적 인스턴스에서의 기본 위치는 Visual Studio 버전 번호에 따라 달라 집니다. 예를 들어, Visual Studio 2015에 대 한 위치가 %localappdata%\Microsoft\VisualStudio\14.0Exp\ 디렉터리 위치에 있는 모든 파일에는 해당 인스턴스의 일부로 간주 됩니다. 추가 실험적 인스턴스를 기본 위치는 디렉터리 이름을 변경 하지 않으면 Visual Studio에서 로드 되지 않습니다.  
  
 Visual Studio 실험적 인스턴스를 열었을 때 시스템 레지스트리를 액세스 하지 않습니다. 이 레지스트리 하이브의 실험적 버전을 사용 하는 Visual Studio의 이전 버전에서 서로 다릅니다.  
  
 CreateExpInstance 유틸리티 VsRegEx 유틸리티가 대체합니다.  
  
 다음 예제에서는 Visual Studio의 기본 실험적 인스턴스 다시 설정합니다.  
  
 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**  
  
## <a name="see-also"></a>관련 항목  
 [제품 릴리스](../../misc/releasing-a-visual-studio-integration-product.md)
