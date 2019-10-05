---
title: Clang 링커 속성(Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 16dcb7ff5925f341fc78b57f1d9a4f011a27d576
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815779"
---
# <a name="clang-linker-properties-android-c"></a>Clang 링커 속성(Android C++)

속성 | 설명 | 선택 항목
--- | ---| ---
출력 파일 | 이 옵션은 링커가 만드는 프로그램의 기본 이름 및 위치를 재정의합니다. (-o)
진행률 표시 | 링커 진행 메시지를 출력합니다.
버전 | -version 옵션을 사용하면 실행 파일의 헤더에 버전 번호를 삽입하도록 링커에 지시할 수 있습니다.
자세한 출력 사용 | -verbose 옵션을 사용하면 디버깅에 대한 자세한 메시지를 출력하도록 링커에 지시할 수 있습니다.
증분 링크 사용 | 이 옵션을 사용하면 증분 링크를 사용하도록 링커에 지시할 수 있습니다.
공유 라이브러리 검색 경로 | 사용자가 공유 라이브러리 검색 경로를 채울 수 있도록 허용합니다.
추가 라이브러리 디렉터리 | 사용자가 환경의 라이브러리 경로를 재정의할 수 있습니다. (-L folder).
확인되지 않은 기호 참조 보고 | 이 옵션을 사용하도록 설정하면 확인되지 않은 기호 참조가 보고됩니다.
메모리 사용량 최적화 | 필요할 경우 기호 테이블을 다시 읽어서 메모리 사용량을 최적화합니다.
특정 기본 라이브러리 무시 | 무시할 하나 이상의 기본 라이브러리 이름을 지정합니다.
강제 기호 참조 | 기호를 출력 파일에 정의되지 않은 기호로 강제 입력합니다.
디버거 기호 정보 | 출력 파일의 디버거 기호 정보입니다. | **모두 포함**<br>**재배치 중에 필요 없는 기호 생략**<br>**디버거 기호 정보만 생략**<br>**모든 기호 정보 생략**<br>
패키지 디버거 기호 정보 | 패키지하기 전에 디버거 기호 정보를 제거합니다.  원래 바이너리의 복사본이 디버깅에 사용됩니다.
맵 파일 이름 | [맵] 옵션을 사용하면 사용자가 지정한 이름으로 맵 파일을 만들도록 링커에 지시할 수 있습니다.
재배치 후 변수를 ReadOnly로 표시 | 이 옵션을 사용하면 재배치 후 변수가 ReadOnly로 표시됩니다.
직접 함수 바인딩 사용 | 이 옵션을 사용하면 직접 함수 바인딩에 대한 개체가 표시됩니다.
실행 가능한 스택 필요 | 이 옵션을 사용하면 실행 가능한 스택 필요 없음으로 출력이 표시됩니다.
전체 보관 파일 | 전체 보관 파일이 소스와 추가 종속성의 모든 코드를 사용합니다.
추가 옵션 | 추가 옵션입니다.
추가 종속성 | 링크 명령줄에 추가할 추가 항목을 지정합니다.
라이브러리 종속성 | 이 옵션을 사용하면 링커 명령줄에 추가할 추가 라이브러리를 지정할 수 있습니다. 추가 라이브러리는 링커 명령줄의 끝에 추가되며, *lib*로 시작하고 *.a* 또는 *.so* 확장명으로 끝납니다.  (-lFILE)
