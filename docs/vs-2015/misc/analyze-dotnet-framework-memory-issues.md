---
title: .NET Framework 메모리 문제 분석 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 885f96a4e1e43fe422c6fd9cfaa414fe5871bce1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688569"
---
# <a name="analyze-net-framework-memory-issues"></a>.NET Framework 메모리 문제 분석
관리되는 Visual Studio 메모리 분석기를 사용하여 .NET Framework 코드에서 메모리 누수 및 비효율적인 메모리 사용을 찾습니다. 대상 코드의 최소 .NET Framework 버전은 .NET Framework 4.5입니다.  
  
 정보를 분석 하는 메모리 분석 도구 *힙 데이터를 사용 하 여 파일을 덤프* 는 앱의 메모리에 개체의 복사본입니다. Visual Studio IDE에서 또는 다른 시스템 도구를 사용해 덤프(.dmp) 파일을 수집할 수 있습니다.  
  
- 단일 스냅샷을 분석하여 메모리 사용에 대한 개체 형식의 상대적 영향을 파악하고 앱에서 메모리를 비효율적으로 사용하는 코드를 찾을 수 있습니다.  
  
- 비교할 수도 있습니다 (*diff*) 메모리를 일으키는 코드에서 영역을 찾으려면 앱의 스냅숏 두 개 사용 하 여 시간이 지남에 따라 증가 합니다.  
  
  관리 되는 메모리 분석기의 연습을 참조 하세요 [프로덕션 환경의.NET 메모리 문제 진단에 사용 하 여 Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) Visual Studio ALM + Team Foundation Server 블로그.  
  
## <a name="BKMK_Contents"></a> 목차  
 [.NET Framework 앱에서 메모리 사용](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [앱의 메모리 문제 식별](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [메모리 스냅숏 수집](#BKMK_Collect_memory_snapshots)  
  
 [메모리 사용 분석](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> .NET Framework 앱에서 메모리 사용  
 .NET Framework는 가비지 수집 런타임이므로 대부분의 앱에서 메모리 사용은 문제가 되지 않습니다. 그러나 오래 실행되는 애플리케이션(예: 웹 서비스 및 애플리케이션)과 메모리의 양이 제한된 디바이스에서 메모리에 개체가 누적되면 앱이 실행되는 디바이스와 앱의 성능에 영향을 미칠 수 있습니다. 가비지 수집기가 너무 자주 실행되거나 운영 체제에서 강제로 RAM과 디스크 간에 메모리를 이동하는 경우 과도한 메모리 사용은 애플리케이션과 컴퓨터에 리소스 부족을 일으킬 수 있습니다. 최악의 경우 앱에서 "메모리 부족" 예외가 발생할 수 있습니다.  
  
 .NET *관리 되는 힙* 앱에서 만든 참조 개체가 저장 된 가상 메모리 영역입니다. 개체의 수명은 GC(가비지 수집기)가 관리합니다. 가비지 수집기에서는 참조를 사용하여 메모리 블록을 차지하는 개체를 추적합니다. 개체를 만들어 변수에 할당하면 참조가 생성됩니다. 단일 개체에는 참조가 여러 개 있을 수 있습니다. 예를 들어 개체를 클래스, 컬렉션 또는 기타 데이터 구조에 추가하거나 개체를 두 번째 변수에 할당하여 개체에 대한 추가 참조를 만들 수 있습니다. 참조를 만드는 덜 확실한 방법은 개체 하나가 다른 개체의 이벤트에 처리기를 추가하도록 하는 것입니다. 이 경우 처리기가 명시적으로 제거되거나 두 번째 개체가 제거될 때까지 두 번째 개체에는 첫 번째 개체에 대한 참조가 들어 있습니다.  
  
 각 애플리케이션의 경우 GC는 애플리케이션에서 참조하는 개체를 추적하는 참조 트리를 유지 관리합니다. 합니다 *참조 트리* 이 관련된 스레드 스택와 동적으로 전역 및 정적 개체를 포함 하는 한 루트 집합 개체를 인스턴스화입니다. 개체에 자신에 대한 참조가 있는 부모 개체가 하나 이상 있는 경우 해당 개체는 루트로 지정됩니다. GC는 애플리케이션에 있는 다른 개체 또는 변수가 해당 개체를 참조하지 않는 경우에만 해당 개체의 메모리를 회수할 수 있습니다.  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> 앱의 메모리 문제 식별  
 메모리 문제의 가장 눈에 띄는 증상은 앱의 성능으로 특히 시간에 따라 성능이 저하되는 경우입니다. 앱 실행 중 다른 앱의 성능 저하 역시 메모리 문제를 나타낼 수 있습니다. 메모리 문제를 생각 하는 경우 작업 관리자와 같은 도구를 사용 하거나 [Windows 성능 모니터](https://technet.microsoft.com/library/cc749249.aspx) 추가로 조사 합니다. 예를 들어 메모리 누수의 가능한 원인으로 설명할 수 없는 메모리의 총 크기 증가를 찾습니다.  
  
 ![리소스 모니터의 지속적인 메모리 증가](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 또한 코드에 대한 지식으로 제안할 수 있는 것보다 더 큰 메모리 스파이크를 알아챌 수도 있습니다. 이는 프로시저에서 비효율적인 메모리 사용을 나타낼 수 있습니다.  
  
 ![리소스 관리자의 메모리 스파이크](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> 메모리 스냅숏 수집  
 정보를 분석 하는 메모리 분석 도구 *덤프 파일* 힙 정보가 포함 된 합니다. Visual Studio에서 덤프 파일을 만들 수 있습니다 또는 같은 도구를 사용할 수 있습니다 [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) 에서 [Windows Sysinternals](https://technet.microsoft.com/sysinternals)합니다. 참조 [덤프는 이란 무엇 이며 어떻게 만드나요?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) Visual Studio 디버거 팀 블로그.  
  
> [!NOTE]
> 대부분의 도구는 전체 힙 메모리 데이터가 포함되거나 포함되지 않은 덤프 정보를 수집할 수 있습니다. Visual Studio 메모리 분석기는 전체 힙 정보가 필요합니다.  
  
 **Visual Studio에서 덤프를 수집 하려면**  
  
1. Visual Studio 프로젝트에서 시작한 프로세스에 대한 덤프 파일을 생성하거나 디버거를 실행 중인 프로세스에 연결할 수 있습니다. 참조 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)합니다.  
  
2. 실행을 중지합니다. 선택 하면 디버거가 중지 **모두 중단** 에 **디버그** 메뉴, 예외 시 또는 중단점에서  
  
3. 에 **디버그** 메뉴 선택 **다른 이름으로 덤프 저장**합니다. 에 **다른 이름으로 덤프 저장** 대화 상자 위치를 지정 하 고 있는지 **힙 사용 미니 덤프** (기본값)에서 선택한를 **형식으로 저장** 목록.  
  
   **두 메모리 스냅숏을 비교 하려면**  
  
   앱의 메모리 사용 증가를 분석하려면 앱의 단일 인스턴스에서 덤프 파일 두 개를 수집합니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> 메모리 사용 분석  
 [개체 목록을 필터링](#BKMK_Filter_the_list_of_objects) **&#124;** [단일 스냅숏에서 메모리 데이터 분석](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [두 메모리 비교 스냅숏](#BKMK_Compare_two_memory_snapshots)  
  
 메모리 사용 문제에 대한 덤프 파일을 분석하려면:  
  
1. Visual Studio에서 선택 **파일**를 **오픈** 덤프 파일을 지정 합니다.  
  
2. 에 **미니 덤프 파일 요약** 페이지에서 **관리 되는 메모리 디버깅**합니다.  
  
    ![덤프 파일 요약 페이지](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   메모리 분석기에서는 디버그 세션을 시작하여 파일을 분석하고 힙 보기 페이지에 결과를 표시합니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> 개체 목록 필터링  
 기본적으로 메모리 분석기는 메모리 스냅샷에서 개체 목록을 필터링하여 사용자 코드인 형식 및 인스턴스만 표시하고 총 포함 크기가 총 힙 크기의 임계값 비율을 초과하는 형식만 표시합니다. 이러한 옵션을 변경할 수 있습니다 합니다 **설정 보기** 목록:  
  
|||  
|-|-|  
|**[내 코드만] 기능 사용**|내 코드만은 대부분의 공통 시스템 개체를 숨기므로 사용자가 만든 형식만 목록에 표시됩니다.<br /><br /> Visual Studio에서 내 코드만 옵션을 설정할 수도 있습니다 **옵션** 대화 상자. **디버그** 메뉴에서 **옵션 및 설정**을 선택합니다. 에 **디버깅**/**일반** 탭을 선택 하거나 선택을 취소 **Just My Code**합니다.|  
|**작은 개체 축소**|**작은 개체 축소** 총 포함 크기가 총 힙 크기의 0.5% 보다 작은 모든 형식을 숨깁니다.|  
  
 문자열을 입력 하 여 형식 목록을 필터링 할 수도 있습니다는 **검색** 상자입니다. 목록에는 이름에 문자열이 포함된 형식만 표시됩니다.  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> 단일 스냅숏에서 메모리 데이터 분석  
 Visual Studio는 새 디버깅 세션을 시작하여 파일을 분석하고 힙 보기 창에 메모리 데이터를 표시합니다.  
  
 ![개체 형식 목록을](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>개체 형식 테이블  
 상단 테이블에는 메모리에 저장된 개체 형식이 나열됩니다.  
  
- **개수** 스냅숏에 있는 형식의 인스턴스 수를 보여 줍니다.  
  
- **크기 (바이트)** 에 대 한 참조를 포함 하는 개체의 크기를 제외한 형식의 모든 인스턴스 크기입니다. Component  
  
- **포함 크기 (바이트)** 참조 된 개체의 크기를 포함 합니다.  
  
  인스턴스 아이콘을 선택할 수 있습니다 (![개체 형식 열의 인스턴스 아이콘](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon"))에 **개체 유형** 인스턴스의 목록을 보려면 열을 형식입니다.  
  
#### <a name="instance-table"></a>인스턴스 테이블  
 ![인스턴스 테이블](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **인스턴스** 개체의 개체 식별자로 사용 되는 개체의 메모리 위치  
  
- **값** 값 형식의 실제 값을 보여 줍니다. 참조 형식의 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
   ![데이터 팁에서 값을 인스턴스](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **크기 (바이트)** 를 참조 하는 개체의 크기를 제외한 개체의 크기입니다. Component  
  
- **포함 크기 (바이트)** 참조 된 개체의 크기를 포함 합니다.  
  
  기본적으로 형식 및 인스턴스 기준으로 정렬 됩니다 **포함 크기 (바이트)** 합니다. 정렬 순서를 변경하려면 목록에서 열 머리글을 선택합니다.  
  
#### <a name="paths-to-root"></a>루트 경로  
  
- 선택한 유형에 대 한는 **개체 유형** 테이블의 **루트 경로** 테이블에 대 한 참조의 수와 함께 유형의 모든 개체에 대 한 루트 개체로 이어지는 고유한 형식 계층 구조를 표시는 계층 구조에서 위에 있는 형식입니다.  
  
- 형식의 인스턴스에서 선택한 개체에 대 한 **루트 경로** 인스턴스에 대 한 참조를 포함 하는 실제 개체의 그래프를 보여 줍니다. 개체의 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
#### <a name="referenced-types--referenced-objects"></a>참조된 형식/참조된 개체  
  
- 선택한 유형에 대 한는 **개체 유형** 테이블의 **참조 된 형식** 탭 크기와 선택한 유형의 모든 개체를 소유 하는 참조 형식의 수를 보여 줍니다.  
  
- 형식의 선택한 인스턴스에 대 한 **참조 된 개체** 선택한 인스턴스가 보유 하 고 있는 개체를 보여 줍니다. 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
  **순환 참조**  
  
  개체는 첫 번째 개체를 직접적 또는 간접적으로 참조하는 두 번째 개체를 참조할 수 있습니다. 참조 경로 확장을 중지 하 고 추가 하는 경우 메모리 분석기에서 이러한 상황이 발생 합니다는 **[순환 발견]** 중지에 고 첫 번째 개체의 주석 목록입니다.  
  
  **루트 형식**  
  
  메모리 분석기에서는 보유 중인 참조의 종류를 설명하는 루트 개체에 다음과 같은 주석을 추가합니다.  
  
|주석|설명|  
|----------------|-----------------|  
|**정적 변수** `VariableName`|정적 변수. `VariableName`은 변수의 이름입니다.|  
|**종료 핸들**|종료자 큐의 참조입니다.|  
|**지역 변수**|지역 변수입니다.|  
|**강력한 핸들**|개체 참조 테이블의 강력한 참조에 대한 핸들입니다.|  
|**비동기입니다. 고정 된 핸들**|개체 핸들 테이블의 비동기 고정된 개체입니다.|  
|**종속 핸들**|개체 핸들 테이블의 종속 개체입니다.|  
|**고정 된 핸들**|개체 핸들 테이블의 고정된 강력한 참조입니다.|  
|**RefCount Handle**|개체 핸들 테이블의 참조 횟수가 계산되는 개체입니다.|  
|**SizedRef Handle**|가비지 컬렉션 시 모든 개체 및 개체 루트의 집합 클로저의 대략적인 크기를 유지하는 강력한 핸들입니다.|  
|**고정 된 지역 변수**|고정된 지역 변수입니다.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> 두 메모리 스냅숏 비교  
 프로세서의 덤프 파일 두 개를 비교하여 메모리 누수의 원인이 될 수 있는 개체를 찾을 수 있습니다. 첫 번째(이전) 및 두 번째(이후) 파일 컬렉션 간의 간격은 누수된 개체 수 증가를 명백하게 확인하기에 충분할 정도로 커야 합니다. 두 파일을 비교하려면 다음 단계를 수행하세요.  
  
1. 두 번째 덤프 파일을 열고 선택한 **관리 되는 메모리 디버깅** 에 **미니 덤프 파일 요약** 페이지입니다.  
  
2. 메모리 분석 보고서 페이지에서 엽니다는 **선택 기준** 목록 및 선택한 **찾아보기** 첫 번째 덤프 파일을 지정 합니다.  
  
   분석기 간의 차이 표시 하는 보고서의 위쪽 창에 열을 추가 합니다 **개수**, **크기**, 및 **포함 크기** 에서 해당 값 형식의 이전 스냅숏입니다.  
  
   ![형식 목록의 Diff 열](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **참조 개수 차이** 열에도 추가 됩니다 합니다 **루트 경로** 테이블입니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="see-also"></a>참고 항목  
 [VS ALM TFS 블로그: Visual Studio 2013을 사용 하 여 프로덕션에서.NET 메모리 문제 진단](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV &#124; 관리 되는 메모리 분석](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio 도구 상자 &#124; 관리 되는 Visual Studio 2013의 메모리 분석](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)