---
title: MSSCCPRJ.SCC File | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 983c6aa0a418ec87d521852bd4b0d781c5c90cfa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344016"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC file
Visual Studio 솔루션 또는 IDE를 사용 하 여 소스 제어 프로젝트에 배치 하는 경우 IDE는 두 가지 중요 정보를 받습니다. 문자열의 형태로 플러그 인 소스 제어에서 정보를 가져옵니다. 이러한 문자열에 "AuxPath" 및 "ProjName" IDE에 불투명 되지만 하는 데 플러그 인에서 버전 제어에서 솔루션 또는 프로젝트를 찾습니다. IDE 일반적으로 이러한 문자열 처음으로 호출 하 여 가져옵니다 합니다 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), 다음에 대 한 이후 호출에 대 한 솔루션 또는 프로젝트 파일에 저장 하는 [SccOpenProject](../extensibility/sccopenproject-function.md)합니다. 솔루션 및 프로젝트 파일에 포함 하는 경우 "AuxPath" 및 "ProjName" 문자열은 자동으로 업데이트 되지 사용자 분기를 포크를 만들거나 버전 제어 중인 솔루션 및 프로젝트 파일을 복사 합니다. 솔루션 및 프로젝트 파일을 버전 제어에서의 올바른 위치를 가리키는지 확인 하려면 사용자가 문자열을 수동으로 업데이트 해야 합니다. 불투명 문자열 되며, 때문에 해당 하지 않을 지우기 업데이트 하는 방법.

 소스 제어 플러그 인 이라는 특수 파일에 "AuxPath" 및 "ProjName" 문자열을 저장 하 여이 문제를 방지할 수는 *MSSCCPRJ.SCC* 파일입니다. 가 소유 하 고 플러그 인에서 유지 관리 하는 로컬, 클라이언트 쪽 파일입니다. 이 파일 소스 제어 두지 않습니다 하지만 원본 제어 파일을 포함 하는 모든 디렉터리에 대 한 플러그 인에서 생성 됩니다. 파일은 Visual Studio 솔루션 및 프로젝트 파일을 확인 하려면 소스 제어 플러그 인을 표준 또는 사용자가 제공한 목록을 파일 확장명을 비교할 수 있습니다. IDE는 검색 되 면 플러그 인을 지원 합니다 *MSSCCPRJ.SCC* 솔루션 및 프로젝트 파일에 "AuxPath" 및 "ProjName" 문자열을 포함 하는 더 이상 파일과 해당 문자열에서 읽는 *MSSCCPRJ.SCC*파일을 대신 합니다.

 하는 소스 제어 플러그 인을 지 원하는 합니다 *MSSCCPRJ.SCC* 파일은 다음 지침을 따라야 합니다.

- 하나만 있을 수 있습니다 하나 *MSSCCPRJ.SCC* 디렉터리 당 파일입니다.

- *MSSCCPRJ.SCC* 파일에 지정된 된 디렉터리 내에서 소스 제어 아래에 있는 여러 파일에 대 한 "AuxPath" 및 "ProjName"을 포함할 수 있습니다.

- "AuxPath" 문자열을 그 안에 따옴표를 사용할 수 없습니다. 구분 기호로 주위에 따옴표를 할 수 (예를 들어, 큰따옴표 쌍 수를 나타내는 빈 문자열)입니다. 읽을 때 IDE에서는 "AuxPath" 문자열에서 모든 따옴표를 제거 합니다 *MSSCCPRJ.SCC* 파일입니다.

- "ProjName" 문자열을 *MSSCCPRJ 합니다. SCC 파일* 에서 반환 된 문자열과 정확히 일치 해야 합니다 `SccGetProjPath` 함수입니다. 함수에서 반환한 문자열 주위에 따옴표를 문자열에 있으면 합니다 *MSSCCPRJ.SCC* 파일 따옴표 있어야 합니다. 주위에 그 반대로 가능 합니다.

- *MSSCCPRJ.SCC* 파일을 만들거나 파일을 소스 제어 아래에 배치 됩니다 될 때마다 업데이트 됩니다.

- 경우는 *MSSCCPRJ.SCC* 파일 삭제, 공급자를 다시 생성 해야 그 다음에 해당 디렉터리와 관련 된 소스 제어 작업을 수행 합니다.

- *MSSCCPRJ.SCC* 파일에서 정의 된 형식을 엄격 하 게 따라야 합니다.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ 보여 줍니다. SCC 파일 형식
 다음은 샘플은 *MSSCCPRJ.SCC* 파일 형식 (줄 번호를 가이드로만 제공 됩니다 및 파일 본문에 포함 되지 않아야):

- [Line 1] `SCC = This is a Source Code Control file`

- [Line 2]

- [Line 3] `[TestApp.sln]`

- [Line 4] `SCC_Aux_Path = "\\server\vss\"`

- [Line 5] `SCC_Project_Name = "$/TestApp"`

- [Line 6]

- [Line 7] `[TestApp.csproj]`

- [Line 8] `SCC_Aux_Path = "\\server\vss\"`

- [Line 9] `SCC_Project_Name = "$/TestApp"`

 첫 번째 줄은 파일의 용도 설명 하 고이 형식의 모든 파일에 대 한 서명으로 제공 합니다. 이 줄이 모두 똑같이 표시 됩니다 *MSSCCPRJ.SCC* 파일:

 `SCC = This is a Source Code Control file`

 다음 섹션에는 대괄호 안에 있는 파일 이름으로 표시 된 각 파일에 대 한 설정을 자세히 설명 합니다. 이 섹션에서는 추적 중인 각 파일에 대해 반복 됩니다. 즉,이 줄은 파일 이름, 샘플 `[TestApp.csproj]`합니다. IDE에는 다음 두 줄은 필요합니다. 스타일 정의 된 값을 단, 정의 되지 않습니다. 변수가 `SCC_Aux_Path` 고 `SCC_Project_Name`입니다.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 이 섹션 끝 구분 문자가 있습니다. 파일에 나타나는 모든 리터럴 뿐만 아니라 파일의 이름은 scc.h 헤더 파일에 정의 됩니다. 자세한 내용은 [소스 제어 플러그 인을 찾기 위한 키로 사용 되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)합니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [소스 제어 플러그 인을 찾기 위한 키로 사용 되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)