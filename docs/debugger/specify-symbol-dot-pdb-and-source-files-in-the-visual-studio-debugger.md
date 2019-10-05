---
title: 디버거에서 기호 (.pdb) 및 소스 파일 설정
ms.custom: seodec18
ms.date: 10/08/2018
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f2343d71d2ed0745f9c5a2a799c3018a2e64945
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746259"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio 디버거에서 기호 (.pdb) 및 원본 파일 지정 (C#, C++, Visual Basic의 경우 F#)

프로그램 데이터베이스 ( *.pdb*) 기호 파일이 라고도 하는 파일을이 식별자에 매핑하고 해당 식별자에 프로젝트의 소스 코드에서 문 및 지침에 컴파일된 앱.

디버그 빌드 구성 표준 Visual Studio IDE에서 프로젝트를 빌드할 때 컴파일러는 적절 한 기호 파일을 만듭니다. 할 수도 있습니다 [코드에서 기호 옵션을 설정할](#compiler-symbol-options)합니다.

합니다 *.pdb* 파일은 앱의 디버그 구성의 증분 링크를 허용 하는 디버깅 및 프로젝트 상태 정보를 포함 합니다. Visual Studio 디버거를 사용 하 여 *.pdb* 파일을 두 가지 중요 디버깅 하는 동안 정보를 확인 합니다.

* 소스 파일 이름과 줄 번호 Visual Studio IDE에서 표시 합니다.
* 중단점에 대 한 중지 하려면 앱의 위치입니다.

기호 파일에는 소스 파일 및 필요에 따라 서버에서 검색 하려면 위치 보여 줍니다.

디버거에서 로드 *.pdb* 정확 하 게 일치 하는 파일을 *.pdb* 앱을 빌드할 때 생성 된 파일 (즉, 원래 *.pdb* 파일이 나 복사본). 이 정확한 중복은 코드 자체가 변경 되지 않은 경우에 앱의 레이아웃 변경 될 수 있으므로 필요 합니다. 자세한 내용은 [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)를 참조하세요.

> [!TIP]
> Windows 코드 또는 제 3 자 코드 프로젝트 호출 같은 프로젝트 소스 코드를 사용 하 여 외부 코드를 디버그 하는 외부 코드의 위치를 지정 해야 *.pdb* 파일 (및 필요에 따라 소스 파일)는 정확히 일치 해야 합니다 앱의 빌드입니다.

## <a name="symbol-file-locations-and-loading-behavior"></a>기호 파일 위치 및 로드 동작

> [!NOTE]
> 모든 기호 파일 또는 로컬 컴퓨터의 위치에 배치 해야 원격 장치에서 관리 되는 코드를 디버깅할 때 [디버거 옵션에서 지정 된](#BKMK_Specify_symbol_locations_and_loading_behavior)합니다.

Visual Studio IDE에서 프로젝트를 디버깅할 때 디버거는 자동으로 프로젝트 폴더에 있는 기호 파일을 로드 합니다.

디버거가 기호 파일은 다음 위치에도 검색합니다.

1. DLL 또는 실행 파일 내의 지정 된 위치 ( *.exe*) 파일입니다.

   기본적으로 DLL을 만든 경우 또는 *.exe* 전체 경로 파일 이름을 연결 된 컴퓨터에 링커 파일 배치 *.pdb* DLL의 파일 또는 *.exe* 파일입니다. 디버거에서 기호 파일 위치에 존재 하는지 확인 합니다.

2. DLL 같은 폴더 또는 *.exe* 파일입니다.

3. 기호 파일에 대 한 디버거 옵션에서 지정 된 모든 위치입니다. 참조를 추가 및 기호 위치를 사용 하도록 설정 하려면 [기호 위치를 구성 하 고 로드 옵션](#BKMK_Specify_symbol_locations_and_loading_behavior)합니다.

   - 로컬 기호 캐시 폴더.

   - 선택한 경우 네트워크, 인터넷 또는 로컬 기호 서버 및 Microsoft 기호 서버 등의 위치를 지정 합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 구현 하는 기호 서버에서 디버깅 기호 파일을 다운로드할 수는 `symsrv` 프로토콜입니다. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) 하며 [도구에 대 한 Windows 디버깅](/windows-hardware/drivers/debugger/index) 기호 서버를 사용할 수 있는 도구가 두 가지 있습니다.

     기호 서버를 사용할 수는 다음과 같습니다.

     **공용 Microsoft 기호 서버**: 시스템 DLL 이나 타사 라이브러리를 호출 하는 동안 발생 하는 충돌을 디버깅 하려면 해야 시스템 *.pdb* 파일입니다. 시스템 *.pdb* Windows Dll에 대 한 기호를 포함 하는 파일 *.exe* 파일 및 장치 드라이버입니다. 공용 Microsoft 기호 서버에서 Windows 운영 체제, MDAC, IIS, ISA 및.NET Framework에 대 한 기호를 가져올 수 있습니다.

     **내부 네트워크 또는 로컬 머신의 기호 서버**: 팀이나 회사는 사용자 고유 제품에 사용하기 위해서나 외부 소스의 기호에 대한 캐시로 기호 서버를 만들 수 있습니다. 기호 서버가 사용자의 컴퓨터에 있을 수도 있습니다.

     **타사 기호 서버**: Windows 애플리케이션 및 라이브러리의 타사 공급자는 인터넷에 있는 기호 서버에 대한 액세스를 제공할 수 있습니다.

     > [!WARNING]
     > 공용 Microsoft 기호 서버 이외의 기호 서버를 사용 하는 경우 해당 경로 및 기호 서버를 신뢰할 수 있는지 확인 합니다. 기호 파일에서 임의의 실행 코드를 포함할 수 있으므로 보안 위협에 노출 될 수 있습니다.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>기호 위치 및 로드 옵션 구성

에 **도구** > **옵션** > **디버깅** > **기호** 페이지 할 수 있습니다.

- 지정 하 고 Microsoft, Windows, 또는 타사 구성 요소에 대 한 검색 경로 및 기호 서버를 선택 합니다.
- 디버거가 자동으로 기호를 로드 하지 않으려고 하거나 마십시오는 모듈을 지정 합니다.
- 적극적으로 디버깅 하는 동안 이러한 설정을 변경 합니다. 참조 [디버깅 하는 동안 기호 관리](#manage-symbols-while-debugging)합니다.

**기호 위치 및 로드 옵션을 지정 합니다.**

1. Visual Studio에서 엽니다 **도구가** > **옵션** > **디버깅** > **기호** (또는 **디버깅할** > **옵션** > **기호**).

   ![도구 &#45; 옵션 &#45; 디버깅 &#45; 기호 페이지](media/dbg-options-symbols.png "도구 &#45; 옵션 &#45; 디버그 &#45; 기호 페이지")

2. 아래 **기호 파일 (.pdb) 위치**,
   - 사용 하 여 **Microsoft 기호 서버**, 확인란을 선택 합니다.

   - 새 기호 서버 위치를 추가 하려면
     1. 선택 된 **+** 대체 합니다.
     1. 텍스트 필드에 기호 서버 또는 기호 위치 URL 또는 폴더 경로 입력 합니다. 문 완성 기능으로 올바른 형식을 찾을 수 있습니다.

     >[!NOTE]
     >지정된 된 폴더를 검색 합니다. 검색 하려는 하위 폴더에 대 한 항목을 추가 해야 합니다.

   - 새 VSTS 기호 서버 위치를 추가 하려면
     1. 선택 된 ![도구&#47; 옵션&#47; 디버깅&#47;기호 새 서버 아이콘](media/dbg_tools_options_foldersicon.png "도구 &#45; 옵션 &#45; 디버깅 &#45; 기호 새 서버 아이콘") 도구 모음에서 아이콘입니다.
     1. 에 **VSTS 기호 서버에 연결** 대화 상자에서 사용할 기호 서버 중 하나를 선택 하 고 선택 **Connect**합니다.

   - 기호 위치에 대 한 로드 순서를 변경 하려면 사용 하 여 **Ctrl**+**위로** 하 고 **Ctrl**+**아래로**, 또는 **등록** 하 고 **아래로** 화살표 아이콘입니다.
   - URL 또는 경로 편집 하려면 항목을 두 번 클릭 하거나 선택 하 고 키를 눌러 **F2**합니다.
   - 항목을 제거 하려면를 선택 하 고 다음을 선택 합니다 **-** 아이콘입니다.

3. (선택 사항) 아래에서 기호 로드 성능을 개선 하기 위해 **이 디렉터리의 기호 캐시**, 기호 서버에 복사할 수 있는 로컬 폴더 경로를 기호 형식입니다.

   > [!NOTE]
   > 로컬 기호 캐시 C:\Windows 또는 하위 폴더와 같은 보호 된 폴더에 배치 하지 마십시오. 대신 읽기/쓰기 폴더를 사용하십시오.

   > [!NOTE]
   > 에 대 한 C++ 프로젝트에 있는 경우는 `_NT_SYMBOL_PATH` 환경 변수 설정에서 설정 값을 재정의 합니다 **이 디렉터리의 기호 캐시**합니다.

4. 디버거에서 로드를 원하는 모듈을 지정 합니다 **기호 파일 (.pdb) 위치** 시작 되 면 합니다.

   - 선택 **제외 되지 않은 모두 모듈 로드** (기본값)에서 기호 파일 위치를 제외 하는 모듈을 제외 하 고 모든 모듈에 대 한 모든 기호를 로드 하려면. 특정 모듈을 제외 하려면 선택 **제외 된 모듈 지정**를 선택 합니다 **+** 아이콘을 선택 하 고 제외할 모듈의 이름을 입력 **확인**합니다.

   - 기호 파일 위치에서 지정 된 모듈만 로드를 선택 **지정 된 모듈만 로드**합니다. 선택 **포함 된 모듈 지정**를 선택 합니다 **+** 아이콘을 포함 하 여 선택한 모듈의 이름을 입력 **확인**합니다. 다른 모듈에 대 한 기호 파일이 로드 되지 않습니다.

5. **확인**을 선택합니다.

## <a name="other-symbol-options-for-debugging"></a>디버깅에 대 한 다른 기호 옵션

추가 기호 옵션에서 선택할 수 있습니다 **도구가** > **옵션** > **디버깅** > **일반** (또는 **디버깅할** > **옵션** > **일반**):

- **dll 내보내기 로드(네이티브 전용)**

  DLL 내보내기 테이블이 로드 c /C++입니다. 자세한 내용은 참조 하세요 [DLL 내보내기 테이블이](#use-dumpbin-exports)합니다. DLL 내보내기 정보를 읽으면 일부 오버를 헤드가, 기본적으로 해제 되어 내보내기 테이블을 로드 하도록 합니다. 사용할 수도 있습니다 `dumpbin /exports` c에서 /C++ 빌드 명령줄입니다.

- **주소 수준 디버깅 사용** 고 **소스를 사용할 수 없는 경우 디스어셈블리 표시**

  소스 또는 기호 파일을 찾을 수 없는 경우 항상 디스어셈블리를 표시 합니다.

  ![옵션 &#47; 디버깅 &#47; 일반 디스어셈블리 옵션](../debugger/media/dbg_options_general_disassembly_checkbox.png "옵션 &#47; 디버그 &#47; 일반 디스어셈블리 옵션")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **소스 서버 지원 사용**

  원본 서버를 사용 하 여 로컬 컴퓨터의 소스 코드가 없는 경우 앱을 디버깅 하는 데 또는 *.pdb* 파일이 소스 코드를 일치 하지 않습니다. 원본 서버는 파일에 대 한 요청을 사용 하 고 소스 제어에서 실제 파일을 반환 합니다. 원본 서버 라는 DLL을 사용 하 여 실행 *srcsrv.dll* 앱의 읽을 *.pdb* 파일입니다. 합니다 *.pdb* 파일은 소스 코드 리포지토리에 물론 리포지토리에서 소스 코드를 검색 하는 데 사용 되는 명령에 대 한 포인터를 포함 합니다.

  명령을 제한할 수 있는 *srcsrv.dll* 앱에서 실행할 수 있습니다 *.pdb* 라는 파일에 허용 되는 명령의 나열 하 여 파일 *srcsrv.ini*합니다. 위치는 *srcsrv.ini* 와 같은 폴더에 파일 *srcsrv.dll* 하 고 *devenv.exe*합니다.

  >[!IMPORTANT]
  >임의의 명령이 응용 프로그램에 포함할 수 있습니다 *.pdb* 파일을 실행 하려는 명령만 해야를 *srcsrv.ini* 파일입니다. *srcsvr.ini* 파일에 포함되지 않은 명령을 실행하려고 하면 확인 대화 상자가 나타납니다. 자세한 내용은 참조 하세요. [보안 경고: 디버거가 신뢰할 수 없는 명령을 실행해야 합니다](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >명령 매개 변수에 대해서는 유효성 검사를 수행하지 않으므로 신뢰되는 명령에 대해 주의를 기울여야 합니다. 예를 들어 사용자 나열 *cmd.exe* 에 사용자 *srcsrv.ini*, 악의적인 사용자에 매개 변수를 지정할 수 *cmd.exe* 는 위험 하 게 만드는 것입니다.

  이 항목 및 자식 항목을 선택 합니다. **부분 신뢰 어셈블리 (관리 전용)에 대해 소스 서버 허용** 하 고 **항상 묻지 않고 신뢰할 수 없는 소스 서버 명령 실행** 보안 위험을 증가 시킬 수 있습니다.

  ![원본 서버 옵션을 사용 하도록 설정](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>컴파일러 기호 옵션

표준 Visual Studio IDE에서 프로젝트를 빌드하면 **디버그** 빌드 구성에는 C++ 관리 되는 컴파일러 코드에 대 한 적절 한 기호 파일을 만듭니다. 또한 코드에서 컴파일러 옵션을 설정할 수 있습니다.

### <a name="cc-options"></a>C/C++ 옵션

- *VC\<x >.pdb* 하 고  *\<프로젝트 >.pdb* 파일

  A *.pdb* C에 대 한 파일 /C++ 사용 하 여 빌드할 때 만들어집니다 [/ZI 또는 /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)합니다. [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], [/Fd](/cpp/build/reference/fd-program-database-file-name) 이름 옵션은 *.pdb* 파일 컴파일러를 만듭니다. 프로젝트를 만들면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE를 사용 하 여는 **/Fd** create로 설정 된 옵션을 *.pdb* 라는 파일  *\<프로젝트 >.pdb*합니다.

  C 프로그램을 작성 하는 경우 /C++ 응용 프로그램을 사용 하는 메이크파일 지정할 **/ZI** 또는 **/Zi** 사용 하지 않고 **/Fd**, 컴파일러는 두 개 만듭니다 *.pdb* 파일:

  - *VC\<x>.pdb* 여기서 *\<x>* 는 Visual C++의 버전을 나타냅니다(예: *VC11.pdb*).

    합니다 *VC\<x >.pdb* 파일 개별 개체 파일에 대 한 모든 디버깅 정보를 저장 하 고, 프로젝트 메이크파일과 동일한 디렉터리에 상주 합니다. 때마다 C 개체 파일을 생성 /C++ 컴파일러에 디버그 정보를 병합 *VC\<x >.pdb*합니다. 와 같은 공통 헤더 파일은 모든 소스 파일에 포함 하는 경우에  *\<windows.h >* , 해당 헤더의 typedef는 모든 개체 파일 보다는 한 번만 저장 됩니다. 삽입되는 정보에는 유형 정보가 포함되지만 함수 정의와 같은 기호 정보는 포함되지 않습니다.

  - *\<project>.pdb*

    합니다  *\<프로젝트 >.pdb* 파일을 프로젝트에 대 한 모든 디버그 정보를 저장 *.exe* 파일과에 있는 합니다 *\debug* 하위 디렉터리입니다. *\<project>.pdb* 파일에는 *VC\<x>.pdb*에 있는 형식 정보뿐만 아니라 함수 프로토타입을 비롯한 전체 디버그 정보가 포함됩니다.

  모두를 *VC\<x >.pdb* 하 고  *\<프로젝트 >.pdb* 파일 증분 업데이트를 허용 합니다. 링커도에 대 한 경로 포함 합니다 *.pdb* 파일을 *.exe* 또는 *.dll* 생성 된 파일입니다.

- <a name="use-dumpbin-exports"></a>DLL 내보내기 테이블

  사용 하 여 `dumpbin /exports` DLL의 내보내기 테이블에서 사용할 수 있는 기호를 확인 합니다. DLL 내보내기 테이블에 대 한 기호화 된 정보는 Windows 메시지, Windows 프로시저 (WindowProcs), COM 개체, 마샬링 또는 기호가 없는 DLL을 사용 하 여 작업에 대 한 유용할 수 있습니다. 모든 32비트 시스템 DLL에 기호를 사용할 수 있습니다. 호출은 현재 함수(가장 안쪽에 중첩된)가 맨 위에 표시되어 호출한 순서로 나열됩니다.

  참조 하 여는 `dumpbin /exports` 출력 영숫자가 아닌 문자를 포함 하 고 정확한 함수 이름을 볼 수 있습니다. 함수 이름은 디버거에서 다른 곳에서 잘릴 수 있으므로 정확한 함수 이름을 표시 하는 것은 함수에 중단점을 설정 하는 것에 대 한 유용 합니다. 자세한 내용은 [dumpbin /exports](/cpp/build/reference/dash-exports)를 참조하십시오.

### <a name="net-framework-options"></a>.NET Framework 옵션

구축 **/debug** 만들려는 *.pdb* 파일입니다. **/debug:full** 또는 **/debug:pdbonly**를 사용하여 응용 프로그램을 빌드할 수 있습니다. **/debug:full** 을 사용하여 빌드하면 디버깅 가능한 코드가 생성됩니다. **/debug:pdbonly**를 사용하여 빌드하면 *.pdb* 파일이 생성되지만 디버그 정보를 사용할 수 있다는 사실을 JIT 컴파일러에 알리는 `DebuggableAttribute`는 생성되지 않습니다. 디버깅할 수 없도록 하려는 릴리스 빌드에 대해 *.pdb* 파일을 생성하려면 **/debug:pdbonly**를 사용합니다. 자세한 내용은 [/debug(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) 또는 [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug)를 참조하세요.

### <a name="web-applications"></a>웹 애플리케이션

설정 된 *web.config* 디버그 모드로 ASP.NET 응용 프로그램의 파일입니다. 디버그 모드에서는 동적으로 생성된 파일에 대한 기호가 ASP.NET에서 생성되며 디버거가 ASP.NET 애플리케이션에 연결될 수 있습니다. Visual Studio 설정이 자동으로 웹 프로젝트 템플릿에서 프로젝트를 만든 경우 디버깅을 시작 합니다.

## <a name="manage-symbols-while-debugging"></a>디버깅 하는 동안 기호 관리

사용할 수는 **모듈**, **호출 스택**를 **지역**를 **자동**, 또는 **조사식** 로드 창 기호 또는 디버깅 하는 동안 기호 옵션을 변경 합니다. 자세한 내용은 [더 디버거가 앱에 연결 하는 방법을 잘 알고 싶다면](../debugger/debugger-tips-and-tricks.md#modules_window)합니다.

### <a name="use-the-modules-window"></a>모듈 창 사용

디버그 하는 동안 합니다 **모듈** 창 디버거가 사용자 코드 또는 내 코드 및 상태를 로드 하는 기호 처리 하는 코드 모듈을 보여 줍니다. 또한 기호 로드 상태를 모니터링, 기호를 로드 하에서 기호 옵션을 변경 합니다 **모듈** 창입니다.

**모니터링 또는 디버깅 하는 동안 기호 위치 또는 옵션을 변경 합니다.**

1. 열려는 합니다 **모듈** 창에서 디버그 하는 동안 **디버그** > **Windows** > **모듈**합니다.
1. 에 **모듈** 창에서 마우스 오른쪽 단추로 클릭 합니다 **기호 상태** 또는 **기호 파일** 헤더 또는 모듈.
1. 상황에 맞는 메뉴에서 다음 옵션 중 하나를 선택 합니다.

|옵션|설명|
|------------|-----------------|
|**기호 로드**|건너뛴, 찾을 수 없음 또는 로드 되지 않았습니다 기호를 사용 하 여 모듈에 대 한 표시 됩니다. 에 지정 된 위치에서 기호를 로드 하려고 시도 합니다 **옵션** > **디버깅** > **기호** 페이지입니다. 기호 파일은 찾을 수 없거나 로드 되지 않은, 경우 시작 **파일 탐색기** 검색할 새 위치를 지정할 수 있습니다.|
|**기호 로드 정보**|로드 된 기호 파일의 위치 또는 디버거가 파일을 찾을 수 없는 경우 검색 된 위치를 보여 줍니다.|
|**기호 설정**|열립니다는 **옵션** > **디버깅** > **기호** 페이지를 편집 하 고 기호 위치를 추가할 수 있습니다.|
|**항상 자동으로 로드**|디버거에서 자동으로 로드 되는 파일 목록에 선택한 기호 파일을 추가 합니다.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Loaded/No 원본 로드 된 기호 없음 페이지를 사용 합니다.

디버거가 기호 또는 소스 파일 사용할 수 없는 코드를 중단 하는 방법은 여러 가지가 있습니다.

- 코드가 단계별로 실행 합니다.
- 중단점 또는 예외에서 코드를 나눕니다.
- 다른 스레드로 전환 합니다.
- 프레임을 두 번 클릭 하 여 스택 프레임을 변경 합니다 **호출 스택** 창입니다.

이 문제가 발생 하면 디버거 표시 합니다 **로드 된 기호 없음** 또는 **로드 된 소스 없음** 찾기 및 필요한 기호 또는 소스를 로드 하는 데는 페이지입니다.

 ![로드 된 기호 없음 페이지](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**에 누락 된 기호 찾기 및 로드 하는 데 로드 된 기호 없음 문서 페이지를 사용 합니다.**

- 검색 경로 변경 하려면 선택 되지 않은 경로 선택 하거나 선택 **새 경로** 하거나 **새 VSTS 경로** 고를 입력 하거나 새 경로 선택 합니다. 선택 **로드** 경로 다시 검색 하 고 있으면 기호 파일을 로드 합니다.
- 기호 옵션을 무시 하 고 검색 경로 다시 시도 선택 **찾아보기 \<실행 파일 이름 >** 합니다. 가 있을 경우 기호 파일이 로드 되 나 **파일 탐색기** 열리므로 기호 파일을 수동으로 선택할 수 있습니다.
- 열려는 합니다 **옵션** > **디버깅** > **기호** 페이지에서 선택 **기호 설정 변경**합니다.
- 한 번 새 창에서 디스어셈블리를 표시를 선택 **디스어셈블리 보기**를 선택 하거나 **옵션 대화 상자** 소스 또는 기호 파일을 찾을 수 없는 경우 항상 디스어셈블리를 표시 하는 옵션을 설정 하려면.
- 검색 위치 및 결과 표시 하려면 확장 **기호 로드 정보**합니다.

디버거가 발견 한 경우는 *.pdb* 파일 옵션 중 하나를 실행 하 고 정보에 따라 소스 파일을 검색할 수 있습니다 합니다 *.pdb* 파일 소스를 표시 합니다. 그렇지 않으면 표시를 **로드 된 소스 없음** 문제를 해결할 수 있는 작업에 대 한 링크를 사용 하 여 문제를 설명 하는 페이지입니다.

**솔루션에 소스 파일 검색 경로 추가 합니다.**

디버거에서 소스 파일을 검색할 위치를 지정 하 고 특정 파일을 검색에서 제외할 수 있습니다.

1. 솔루션을 선택 **솔루션 탐색기**를 선택한 후 합니다 **속성** 아이콘을 눌러 **Alt**+**Enter**, 또는 마우스 오른쪽 단추로 클릭 **속성**합니다.

1. 선택 **소스 파일 디버그**합니다.

1. 아래 **소스 코드를 포함 하는 디렉터리**입력 하거나 검색 하려면 소스 코드 위치를 선택 합니다. 사용 하 여는 **새 줄** 더 많은 위치를 추가 하려면 아이콘을 합니다 **등록** 및 **아래로** 하면 순서를 변경 하려면 화살표 아이콘 또는 **X** 삭제할 아이콘.

   >[!NOTE]
   >디버거는 지정된 된 디렉터리를 검색합니다. 검색하려는 하위 디렉터리에 대한 항목을 추가해야 합니다.

1. 아래 **다음 소스 파일을 찾지 않음**, 검색에서 제외할 소스 파일의 이름을 입력 합니다.

1. 선택 **확인** 하거나 **적용**합니다.

## <a name="see-also"></a>참고자료
- [기호 파일 및 Visual Studio 기호 설정 이해](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Visual Studio 2012 및 2013의 .NET 원격 기호 로드 변경 내용](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
