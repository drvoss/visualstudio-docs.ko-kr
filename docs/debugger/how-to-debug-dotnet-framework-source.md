---
title: '방법: .NET Framework 소스 디버그 | Microsoft Docs'
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 25f40b0528b794863aabdb13ed9785d2b0c551b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894276"
---
# <a name="how-to-debug-net-framework-source"></a>방법: .NET Framework 소스 디버그

.NET Framework 소스를 디버깅 하려면 다음을 수행 해야 합니다.

- .NET Framework 소스 단계별 실행을 사용 하도록 설정 합니다.

- 디버깅 코드에 대 한 기호에 액세스할 수 있으며

  디버깅 기호를 즉시 다운로드 하거나 나중에 다운로드 하는 것에 대 한 옵션을 설정 하도록 선택할 수 있습니다. 기호를 즉시 다운로드 하지 않으면, 다음에 응용 프로그램을 디버깅을 시작할 때를 다운로드 됩니다. 디버깅 하는 동안 사용할 수도 있습니다는 **모듈** 또는 **호출 스택** windows를 다운로드 하 여 기호를 로드 합니다.

### <a name="to-enable-stepping-into-net-framework-source"></a>.NET Framework 소스 단계별 실행을 사용 하도록 설정 하려면

1. 아래 **도구가** (또는 **디버그**) > **옵션** > **디버깅** > **일반**을 선택 **.NET Framework 소스 단계별 실행**합니다.

   - 내 코드만을 사용하는 경우에는 내 코드만을 이제 사용하지 않는다는 경고 대화 상자가 표시됩니다. **확인**을 선택합니다.

   - 로컬 기호 캐시에 없는 경우 경고 대화 상자가 기본 기호 캐시가 설정 되어 있는지 알려 줍니다. **확인**을 선택합니다.

1. 선택 **확인** 닫으려면 합니다 **옵션** 대화 합니다.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>설정 하거나 기호 원본 위치 및 로드 동작을 변경 하려면

1. 선택 된 **기호** 에서 범주 **도구** (또는 **디버그**) > **옵션** > **디버깅**.

1. 에 **기호** 페이지의 **기호 파일 (.pdb) 위치**를 선택 **Microsoft 기호 서버** 공용 Microsoft 기호 서버에서 액세스 기호입니다. 기타 기호 위치를 추가 하 고 로드 순서를 변경 하려면 도구 모음 단추를 선택 합니다.

1. 로컬 기호 캐시를 변경 하려면 편집 하거나에서 다른 위치로 이동 **이 디렉터리의 기호 캐시**합니다.

1. 기호를 즉시 다운로드 하려면 **모든 기호 로드**합니다. 이 단추는 디버깅 하는 동안에 사용할 수 있습니다.

   지금 기호를 다운로드 하지는 디버깅을 시작 하면 다음에 다운로드 됩니다.

1. 선택 **확인** 닫으려면 합니다 **옵션** 대화 합니다.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>모듈 또는 호출 스택에서 기호를 로드 하려면 windows

1. 디버그 하는 동안 창을 선택 하 여 **디버깅할** > **Windows** > **모듈** (누르거나 **Ctrl + Alt + U**) 또는 **디버깅할** > **Windows** > **호출 스택** (**Ctrl + Alt + C**).

1. 기호가 로드 되지 모듈을 마우스 오른쪽 단추로 클릭 합니다. 에 **모듈** 에서 창 상태를 로드 하는 기호를 합니다 **기호 상태** 열입니다. 에 **호출 스택** 창에서 상태가 합니다 **프레임 상태** 열 및 프레임이 흐리게 표시 됩니다.

   - 선택 **기호 로드** 를 찾아 컴퓨터 폴더에서 기호 파일을 로드 합니다.

   - 선택 **기호 로드 정보** 디버거가 기호를 검색할 위치를 표시 하도록 합니다.

   - 선택 **기호 설정** 열려는 합니다 **기호** 페이지입니다. 에 **기호** 페이지의 **기호 파일 (.pdb) 위치**를 선택 **Microsoft 기호 서버** 공용 Microsoft 기호 서버에서 액세스 기호입니다. 기타 기호 위치를 추가 하 고 로드 순서를 변경 하려면 도구 모음 단추를 선택 합니다. 선택 **확인** 는 대화 상자를 닫습니다.

### <a name="see-also"></a>참고자료
- [관리 코드 디버깅](../debugger/debugging-managed-code.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)