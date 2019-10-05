---
title: Side-by-side-배포에 대 한 파일 이름 확장명 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bdfb562ddfcce2584b8868c3c931c21f9dbc127
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334224"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Side-by-side-배포에 대 한 파일 이름 확장명 등록
Side-by-side-환경에 배포 하는 Vspackage, 파일의 올바른 버전을 사용 하 여 연결할 파일 이름 확장명을 등록 해야 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 버전별 파일 이름 확장명을 사용 하지 않으면 등록을 사용 하면 프로젝트를 열고 적절 한 버전의 항목 파일을 프로젝트에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]입니다.

## <a name="in-this-section"></a>단원 내용
- [파일 이름 확장명에 대 한](../extensibility/about-file-name-extensions.md) 파일 이름 확장명은 등록 하는 방법에 대해 설명 합니다.

- [파일 이름 확장명에 대 한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md) 열 수 있는 응용 프로그램, edit 및 등등으로 특정 파일 이름 확장명을 등록 하는 방법에 대 한 정보를 제공 합니다.

- [파일 이름 확장명에 대 한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md) 동사를 등록 하는 방법에 설명 합니다.

- [Side-by-side-파일 연결 관리](../extensibility/managing-side-by-side-file-associations.md) side-by-side-설치를 처리 하는 방법에 설명의 특정 버전 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 파일을 호출 해야 합니다.

## <a name="related-sections"></a>관련 단원
- [여러 버전의 Visual Studio 지원](../extensibility/supporting-multiple-versions-of-visual-studio.md) 의 여러 버전에 관련 된 문제에 설명 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 및 개발 및 최종 사용자에 게 배포 하는 동안 VSPackage입니다.