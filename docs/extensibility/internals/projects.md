---
title: 프로젝트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f8fbd19eca1a6aab770718628bbd36a49902074
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327363"
---
# <a name="projects"></a>프로젝트
Visual Studio에서 프로젝트는 개발자가 소스 코드 파일 및에 표시 되는 기타 리소스를 구성 하는 데 사용할 컨테이너 **솔루션 탐색기**합니다. 일반적으로 프로젝트는 소스 코드 파일 및 비트맵 파일 같은 리소스에 대 한 참조를 저장 하는 파일 (예를 들어 C# 프로젝트의.csproj 파일)입니다. 구성, 빌드, 디버그 및 소스 코드를 배포할 수 있습니다. 프로젝트, 웹 서비스 및 데이터베이스 및 기타 리소스에 대 한 참조입니다. Vspackage는 세 가지 주요 방법으로 Visual Studio 프로젝트 시스템을 확장할 수 있습니다: *프로젝트 형식*, *프로젝트 하위 형식*, 및 *사용자 지정 도구*합니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 형식](../../extensibility/internals/project-types.md)

 *프로젝트 형식* 프로그래밍 언어와 같은 프로젝트의 새 종류에 대 한 지원을 추가 합니다. 예를 들어, Visual Studio에서 지 원하는 각 언어에는 고유한 프로젝트 형식이 및 IronPython 통합 샘플 IronPython 언어에 대 한 프로젝트 형식을 포함 합니다. C# 또는 Visual Basic 방법 항목은 작성, 디버깅, 배포 및 표시 사용자 지정 하려면 이외의 언어에 대 한 프로젝트 유형을 만들어야 **솔루션 탐색기**합니다. 자세한 내용은 [프로젝트 형식](../../extensibility/internals/project-types.md)합니다.

- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

 *프로젝트 하위 형식* 프로젝트 형식을 기반으로 하 고 프로젝트 빌드, 디버깅 및 배포 하는 방식을 사용자 지정할 수 있습니다. Visual Studio 스마트 장치 프로젝트를 사용 하 여 프로젝트 하위 형식 사용 이러한 새로 빌드된 프로그램을 개발 컴퓨터에서 대상 장치에 복사 하 여 배포를 사용자 지정 합니다. C# 프로젝트 하위 형식;에 대 한 기준으로 사용할 수 있습니다 Visual Basic 프로젝트 형식 C++ 프로젝트 형식 수 없습니다. 사용자 고유의 프로젝트 형식은 기반으로 프로젝트 하위 형식에 대 한 사용할 수도 수 있습니다. 자세한 내용은 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)합니다.

- [웹 프로젝트](../../extensibility/internals/web-projects.md)

 웹 응용 프로그램 만들고 웹 프로젝트에 설명 합니다.

- [새 프로젝트 생성: 내부적으로 1 부](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 고 [새 프로젝트 생성: 내부 살펴보기, 2부](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 새 프로젝트를 만들 때 실제로 발생에 대해 설명 합니다.

- [VSSDK 샘플](https://aka.ms/vs2015sdksamples) 프로젝트 및 솔루션을 사용 하 여 처리 하는 VSSDK에 대 한 샘플이 포함 되어 있습니다.

## <a name="related-sections"></a>관련 단원
- [Visual Studio SDK 기본 사항](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Visual Studio 확장성의 다양 한 측면을 설명 합니다.