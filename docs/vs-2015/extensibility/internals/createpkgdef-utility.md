---
title: CreatePkgDef 유틸리티 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441485"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 유틸리티
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

매개 변수로 Visual Studio 확장명.dll 파일을 사용 하 고.dll 함께.pkgdef 파일을 만듭니다. 그렇지 않으면 작성 될 수 있는 시스템 레지스트리에 확장을 설치할 때 모든 정보를 포함 하는.pkgdef 파일.  
  
> [!NOTE]
> 자동으로 Visual Studio SDK에 포함 된 프로젝트 템플릿 중 대부분은 빌드 프로세스의 일부로.pkgdef 파일을 만듭니다. 이 문서는 패키지를 수동으로 만들거나.pkgdef 배포를 사용 하도록 기존 패키지를 변환 하려면 사용자에 게 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>인수  
 /out=`FileName`  
 필수 요소. .Pkgdef 출력 파일의 이름을 설정`FileName`합니다.  
  
 /codebase  
 선택 사항입니다. 코드 베이스 유틸리티를 사용 하 여 강제로 등록 합니다.  
  
 /assembly  
 어셈블리 유틸리티를 사용 하 여 강제로 등록 합니다.  
  
 `AssemblyPath`  
 생성 된.pkgdef 하려는.dll 파일의 경로입니다.  
  
## <a name="remarks"></a>설명  
 .Pkgdef 파일을 사용 하 여 확장 배포에는 이전 버전의 Visual Studio의 레지스트리 요구 사항을 대체 합니다.  
  
 다음 위치 중 하나에서.pkgdef 파일을 설치 해야 합니다: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ 또는 %vsinstalldir%\Common7\IDE\Extensions\\합니다. 설치 폴더는 %localappdata%\Microsoft\Visual Studio\14.0\Extensions 경우\\, 확장이 Visual Studio에서 인식할 수는 있지만 기본적으로 비활성화 됩니다. 사용자를 사용 하 여 확장을 설정할 수 있습니다 **확장 및 업데이트**합니다. 설치 폴더는 %vsinstalldir%\Common7\IDE\Extensions 경우\\, 확장은 기본적으로 사용 됩니다.  
  
> [!NOTE]
> 합니다 **확장 및 업데이트** VSIX 패키지의 일부로 설치 되어 있지 않으면 확장에 액세스 하는 도구를 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [CreateExpInstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)
