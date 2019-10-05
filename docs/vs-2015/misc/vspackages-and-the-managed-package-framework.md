---
title: Vspackage 및 관리 패키지 프레임 워크 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 5b72b2c3bd6b03d1d3f3e50135c2ddf4758a4bd9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683053"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackage 및 관리 패키지 프레임워크
클래스를 만들어 VSPackage 관리 패키지 프레임 워크 (MPF) 대신 COM interop 클래스를 사용 하 여 개발 시간을 줄일 수 있습니다.  
  
 두 가지 방법으로 관리 되는 VSPackage를 만들려면:  
  
- 사용 된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 패키지 프로젝트 템플릿  
  
     자세한 내용은 [연습: Visual Studio 패키지 템플릿을 사용 하 여 메뉴 명령 만들기](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)합니다.  
  
- 없이 VSPackage를 빌드는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 패키지 프로젝트 템플릿  
  
     예를 들어 VSPackage 샘플을 복사 하 고 Guid 및 이름을 변경할 수 있습니다. VSX 부분에서 샘플을 찾을 수 있습니다 [코드 갤러리](http://code.msdn.microsoft.com/vsx/)합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [관리되는 패키지 프레임워크 클래스](../misc/managed-package-framework-classes.md)  
 에 대해 설명 하 고 MPF 클래스 네임 스페이스 및 DLL 파일을 나열 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [연습: Visual Studio 패키지 템플릿을 사용 하 여 메뉴 명령 만들기](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 관리 되는 VSPackage를 만드는 방법에 설명 합니다.  
  
 [관리되는 VSPackage](../misc/managed-vspackages.md)  
 관리 코드에 적용 되는 Vspackage의 측면을 소개 합니다.