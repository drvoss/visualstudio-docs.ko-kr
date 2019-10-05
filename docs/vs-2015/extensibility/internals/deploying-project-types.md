---
title: 프로젝트 형식 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196873"
---
# <a name="deploying-project-types"></a>프로젝트 형식 배포
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 새 프로젝트 형식 aggregator (ProjectAggregator2.dll) 및 재배포 (ProjectAggregator2.msi)에 대 한 Windows Installer 패키지를 설치합니다. 관리 코드 프로젝트 형식에 대해 새 집계가 사용 해야 합니다. ProjectAggregator2 작동 방법 제한 된 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aggregator 관리 코드 프로젝트 형식을 올바르게 작동 하지 못하도록 하는 프로젝트입니다. 다음 단계를 새 집계를 사용 하 여 VSPackage를 변경 하는 방법에 설명 합니다.  
  
1. 솔루션에서 NativeHierarchyWrapper 프로젝트를 제거 합니다.  
  
2. 설치 프로그램에서 NativeHierarchyWrapper 이진 파일을 제거 합니다.  
  
3. ProjectAggregator2.msi 설치에 추가 합니다.
