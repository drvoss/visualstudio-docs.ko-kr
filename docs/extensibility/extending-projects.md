---
title: 프로젝트 확장 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0333e09aee207e10657999dda4b5b1d59e181cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341102"
---
# <a name="extend-projects"></a>프로젝트를 확장 합니다.
프로젝트 및 솔루션은 Visual Studio 코드 및 리소스 파일을 컴파일 및 배포 단위로 구성 하는 방법입니다. 프로젝트에 대 한 자세한 정보를 찾을 수 있습니다 [프로젝트 (Visual Studio SDK)](../extensibility/extending-projects.md)합니다.

 Visual Studio SDK 및 프로젝트의 경우에서 다운로드할 수 있는 관리 되는 패키지 프레임 워크는 사용 하 여 사용자 고유의 프로젝트 형식을 만들 수 있습니다 [프로젝트에 대 한 관리 되는 패키지 프레임 워크](https://github.com/tunnelvisionlabs/MPFProj10)합니다. 이해를 사용자 지정 프로젝트, 구현 참조 [새 프로젝트 생성: 내부적으로 1 부](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 고 [새 프로젝트 생성: 내부적으로 2 부](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)합니다.

 이 섹션의에서 항목에서는 사용자 지정 프로젝트를 만드는 방법 및 다양 한 Visual Studio 솔루션을 관리 하는 방법을 설명 합니다.

## <a name="in-this-section"></a>단원 내용
- [1 부 기본 프로젝트 시스템을 만들려면](../extensibility/creating-a-basic-project-system-part-1.md) 사용자 지정 프로젝트 시스템을 만드는 방법에 설명 합니다.

- [2 부 기본 프로젝트 시스템을 만들려면](../extensibility/creating-a-basic-project-system-part-2.md) 사용자 지정 프로젝트 시스템을 만드는 방법에 설명 합니다.

- [프로젝트 파일에 데이터를 저장할](../extensibility/saving-data-in-project-files.md) Explains 프로젝트에 추가 방법 (<em>.</em> proj *) 파일입니다.

- [런타임에 프로젝트의 하위 형식 확인](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) 런타임에 프로젝트의 하위 형식을 확인 하는 방법에 설명 합니다.

- [속성 페이지 추가 하거나 제거할](../extensibility/adding-and-removing-property-pages.md) 사용자 지정 프로젝트에 대 한 속성 페이지를 사용자 지정 하는 방법에 설명 합니다.

- [프로젝트 항목에 특성 추가](../extensibility/adding-an-attribute-to-a-project-item.md) 특성 사용자 지정 프로젝트 항목을 추가 하는 방법에 설명 합니다.

- [프로젝트 항목의 속성 유지](../extensibility/persisting-the-property-of-a-project-item.md) 사용자 지정 프로젝트 항목의 속성을 유지 하는 방법에 설명 합니다.

- [유니버설 Windows 프로젝트 관리](../extensibility/managing-universal-windows-projects.md) 유니버설 프로젝트를 관리 하는 방법에 설명 합니다.