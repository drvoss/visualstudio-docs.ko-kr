---
title: Dia2dump 샘플 | Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c8b92ae2f607ae449b7b4392fc3638fcdcb6a80
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715348"
---
# <a name="dia2dump-sample"></a>Dia2dump 샘플

Dia2dump 샘플 Microsoft 디버그 인터페이스 액세스 소프트웨어 개발 키트 (DIA SDK)를 사용 하 여 정보에 대 한 PDB 파일을 쿼리 하는 방법을 보여 줍니다.

Dia2dump 샘플 Visual Studio와 함께 설치 되 고 솔루션 및 원본 파일이 포함 되어 있습니다. 명령줄에서 컴파일된 실행 파일 실행 됩니다. 전체 프로그램 데이터베이스 (.pdb) 파일의 내용을 표시할 수 있습니다 또는 섹션만 관심이 있습니다.

## <a name="install-the-sample"></a>샘플 설치

샘플 선택 하면 설치 되는 **를 사용한 데스크톱 개발 C++**  Visual Studio 설치 관리자에서 워크 로드. Visual Studio를 설치 하 고 특정 워크 로드 및 개별 구성 요소를 선택 하는 방법에 대 한 정보를 참조 하세요 [Visual Studio 설치](../../install/install-visual-studio.md)합니다.

설치 \DIA SDK\Samples\DIA2Dump 라는 하위 디렉터리에서 Visual Studio 설치 디렉터리에는 샘플입니다.

## <a name="build-the-sample"></a>샘플 빌드

기본적으로 설치 디렉터리는 보호 된 디렉터리를 사용 합니다. 즉, 빌드하고이 위치에서 샘플 솔루션을 편집 하려면 개발자 명령 프롬프트 또는 Visual Studio의 인스턴스를 사용 해야 합니다. 빌드를 간소화 하려면 먼저 문서 폴더에 있는 폴더와 같이 다른 디렉터리에 샘플 디렉터리에서 파일을 복사 하 고 샘플 빌드는 것이 좋습니다.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Visual Studio에서 Dia2Dump 샘플을 빌드합니다.

1. Visual Studio에서 DIA2Dump.sln 파일을 엽니다. 다른 디렉터리로 솔루션을 복사 하지 않은 경우 관리자 권한으로 Visual Studio를 다시 시작 하 라는 메시지가 표시 될 수 있습니다.

1. **솔루션 탐색기**, Dia2Dump 프로젝트 (솔루션 아님)를 선택 합니다.

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](/cpp/build/working-with-project-properties)을 참조하세요.

1. 엽니다는 **구성 속성** > **C /C++**  > **일반** 속성 페이지.

1. 에 **Additional Include Directories** 속성을 dropdown 컨트롤을 선택 하 고 선택 **편집**합니다.

1. 에 **Additional Include Directories** 대화 상자에서 편집 필드에 입력을 `$(VSInstallDir)DIA SDK\include` 디렉터리입니다. 컴파일러 dia2.h 파일을 찾을 수 있도록 보장 하기 위해이 디렉터리를 추가 합니다. **확인**을 선택하여 변경 내용을 저장합니다.

1. 선택할 **확인** 프로젝트 속성에 변경 내용을 저장 합니다.

1. 에 **빌드할** 메뉴에서 선택 **솔루션 다시 빌드**합니다. 기본적으로 Visual Studio 디버그 디렉터리의 하위 디렉터리를 솔루션에에서 있는 샘플의 디버그 버전을 빌드합니다.

1. Visual Studio를 닫습니다.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>명령줄에서 Dia2Dump 샘플을 빌드합니다.

1. 개발자 명령 프롬프트 창에서 샘플 파일을 복사한 디렉터리로 변경 합니다. 관리자 권한 (관리자 권한으로 실행)를 사용 해야 샘플을 다른 디렉터리로 복사 하지 않은 개발자 명령 프롬프트 창입니다.

1. 명령을 입력 `nmake makefile` dia2dump.exe의 기본 디버그 구성을 빌드할 수 있습니다.

## <a name="run-the-dia2dump-sample"></a>Dia2Dump 샘플 실행

Dia2Dump.exe는 msdia 의존*버전*.dll COM 서버를 해당 서비스를 제공 합니다. Visual Studio 2015부터 버전이 msdia140.dll을 합니다. 경우는 msdia*버전*.dll COM 서버 초기화 되지, dia2dump.exe 사용할 수 있도록 등록 해야 합니다. DIA SDK 디렉터리에는 x86을 포함 하는 bin 하위 디렉터리에 DLL의 버전입니다. 버전 x64 아키텍처 컴퓨터 bin\amd64, 이며 ARM에 대 한 버전 bin\arm에서. Dll을 등록 하려면 상승 된 개발자 명령 프롬프트 창을 열고 컴퓨터 아키텍처에 대 한 버전이 포함 된 디렉터리로 변경 합니다. 명령을 입력 `regsvr32 msdia140.dll` COM 서버를 등록 합니다.

### <a name="to-run-the-sample"></a>이 샘플을 실행하려면

1. 명령 프롬프트를 열고 dia2dump.exe 작성 하는 포함 된 디렉터리로 변경 합니다.

1. 명령을 입력 합니다 `dia2dump filename` 여기서 *filename* 검사할 PDB 파일의 이름입니다. PDB 파일을 다른 디렉터리에 있으면 전체 경로와 파일에 사용 *filename*합니다. 이 명령은 PDB 파일의 모든 데이터를 나열합니다.

1. Dia2Dump에 선택한 정보만 표시 하기 위해 다른 옵션이 있습니다. 사용 된 `dia2dump -?` 모든 사용 가능한 옵션을 나열 하는 명령입니다.

## <a name="see-also"></a>참고자료

- [Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
