---
title: Analyze .NET Framework memory issues | Microsoft Docs
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
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295890"
---
# <a name="analyze-net-framework-memory-issues"></a>.NET Framework 메모리 문제 분석
관리되는 Visual Studio 메모리 분석기를 사용하여 .NET Framework 코드에서 메모리 누수 및 비효율적인 메모리 사용을 찾습니다. 대상 코드의 최소 .NET Framework 버전은 .NET Framework 4.5입니다.  
  
 The memory analysis tool analyzes information in *dump files with heap data* that a copy of the objects in an app's memory. Visual Studio IDE에서 또는 다른 시스템 도구를 사용해 덤프(.dmp) 파일을 수집할 수 있습니다.  
  
- 단일 스냅샷을 분석하여 메모리 사용에 대한 개체 형식의 상대적 영향을 파악하고 앱에서 메모리를 비효율적으로 사용하는 코드를 찾을 수 있습니다.  
  
- You can also compare (*diff*) two snapshots of an app to find areas in your code that cause the memory use to increase over time.  
  
  For a walkthrough of the managed memory analyzer, see [Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) on the Visual Studio ALM + Team Foundation Server blog .  
  
## <a name="BKMK_Contents"></a> 목차  
 [Memory use in .NET Framework apps](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identify a memory issue in an app](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Collect memory snapshots](#BKMK_Collect_memory_snapshots)  
  
 [Analyze memory use](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Memory use in .NET Framework apps  
 .NET Framework는 가비지 수집 런타임이므로 대부분의 앱에서 메모리 사용은 문제가 되지 않습니다. 그러나 오래 실행되는 애플리케이션(예: 웹 서비스 및 애플리케이션)과 메모리의 양이 제한된 디바이스에서 메모리에 개체가 누적되면 앱이 실행되는 디바이스와 앱의 성능에 영향을 미칠 수 있습니다. 가비지 수집기가 너무 자주 실행되거나 운영 체제에서 강제로 RAM과 디스크 간에 메모리를 이동하는 경우 과도한 메모리 사용은 애플리케이션과 컴퓨터에 리소스 부족을 일으킬 수 있습니다. 최악의 경우 앱에서 "메모리 부족" 예외가 발생할 수 있습니다.  
  
 The .NET *managed heap* is a region of virtual memory where reference objects created by an app are stored. 개체의 수명은 GC(가비지 수집기)가 관리합니다. 가비지 수집기에서는 참조를 사용하여 메모리 블록을 차지하는 개체를 추적합니다. 개체를 만들어 변수에 할당하면 참조가 생성됩니다. 단일 개체에는 참조가 여러 개 있을 수 있습니다. 예를 들어 개체를 클래스, 컬렉션 또는 기타 데이터 구조에 추가하거나 개체를 두 번째 변수에 할당하여 개체에 대한 추가 참조를 만들 수 있습니다. 참조를 만드는 덜 확실한 방법은 개체 하나가 다른 개체의 이벤트에 처리기를 추가하도록 하는 것입니다. 이 경우 처리기가 명시적으로 제거되거나 두 번째 개체가 제거될 때까지 두 번째 개체에는 첫 번째 개체에 대한 참조가 들어 있습니다.  
  
 각 애플리케이션의 경우 GC는 애플리케이션에서 참조하는 개체를 추적하는 참조 트리를 유지 관리합니다. The *reference tree* has a set of roots, which includes global and static objects, as well as associated thread stacks and dynamically instantiated objects. 개체에 자신에 대한 참조가 있는 부모 개체가 하나 이상 있는 경우 해당 개체는 루트로 지정됩니다. GC는 애플리케이션에 있는 다른 개체 또는 변수가 해당 개체를 참조하지 않는 경우에만 해당 개체의 메모리를 회수할 수 있습니다.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identify a memory issue in an app  
 메모리 문제의 가장 눈에 띄는 증상은 앱의 성능으로 특히 시간에 따라 성능이 저하되는 경우입니다. 앱 실행 중 다른 앱의 성능 저하 역시 메모리 문제를 나타낼 수 있습니다. If you suspect a memory issue, use a tool like Task Manager or [Windows Performance Monitor](https://technet.microsoft.com/library/cc749249.aspx) to investigate further. 예를 들어 메모리 누수의 가능한 원인으로 설명할 수 없는 메모리의 총 크기 증가를 찾습니다.  
  
 ![Consistent memory growth in Resource Monitor](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 또한 코드에 대한 지식으로 제안할 수 있는 것보다 더 큰 메모리 스파이크를 알아챌 수도 있습니다. 이는 프로시저에서 비효율적인 메모리 사용을 나타낼 수 있습니다.  
  
 ![Memory spikes in Resource Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Collect memory snapshots  
 The memory analysis tool analyzes information in *dump files* that contain heap information. You can create dump files in Visual Studio, or you can use a tool like [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) from [Windows Sysinternals](https://technet.microsoft.com/sysinternals). See [What is a dump, and how do I create one?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) on the Visual Studio Debugger Team blog.  
  
> [!NOTE]
> 대부분의 도구는 전체 힙 메모리 데이터가 포함되거나 포함되지 않은 덤프 정보를 수집할 수 있습니다. Visual Studio 메모리 분석기는 전체 힙 정보가 필요합니다.  
  
 **To collect a dump from Visual Studio**  
  
1. Visual Studio 프로젝트에서 시작한 프로세스에 대한 덤프 파일을 생성하거나 디버거를 실행 중인 프로세스에 연결할 수 있습니다. See [Attach to Running Processes](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. 실행을 중지합니다. The debugger stops when you choose **Break All** on the **Debug** menu, or at an exception or at a breakpoint  
  
3. On the **Debug** menu, choose **Save Dump As**. In the **Save Dump As** dialog box, specify a location and make sure that **Minidump with Heap** (the default) is selected in the **Save as type** list.  
  
   **To compare two memory snapshots**  
  
   앱의 메모리 사용 증가를 분석하려면 앱의 단일 인스턴스에서 덤프 파일 두 개를 수집합니다.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analyze memory use  
 [Filter the list of objects](#BKMK_Filter_the_list_of_objects) **&#124;** [Analyze memory data in from a single snapshot](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [Compare two memory snapshots](#BKMK_Compare_two_memory_snapshots)  
  
 메모리 사용 문제에 대한 덤프 파일을 분석하려면:  
  
1. In Visual Studio, choose **File**, **Open** and specify the dump file.  
  
2. On the **Minidump File Summary** page, choose **Debug Managed Memory**.  
  
    ![Dump file summary page](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   메모리 분석기에서는 디버그 세션을 시작하여 파일을 분석하고 힙 보기 페이지에 결과를 표시합니다.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filter the list of objects  
 기본적으로 메모리 분석기는 메모리 스냅샷에서 개체 목록을 필터링하여 사용자 코드인 형식 및 인스턴스만 표시하고 총 포함 크기가 총 힙 크기의 임계값 비율을 초과하는 형식만 표시합니다. You can change these options in the **View Settings** list:  
  
|||  
|-|-|  
|**[내 코드만] 기능 사용**|내 코드만은 대부분의 공통 시스템 개체를 숨기므로 사용자가 만든 형식만 목록에 표시됩니다.<br /><br /> You can also set the Just My Code option in the Visual Studio **Options** dialog box. **디버그** 메뉴에서 **옵션 및 설정**을 선택합니다. In the **Debugging**/**General** tab, choose or clear **Just My Code**.|  
|**Collapse Small Objects**|**Collapse Small Objects** hides all types whose total inclusive size is less than 0.5 percent of the total heap size.|  
  
 You can also filter the type list by entering a string in the **Search** box. 목록에는 이름에 문자열이 포함된 형식만 표시됩니다.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analyze memory data in from a single snapshot  
 Visual Studio는 새 디버깅 세션을 시작하여 파일을 분석하고 힙 보기 창에 메모리 데이터를 표시합니다.  
  
 ![The Object Type list](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>개체 형식 테이블  
 상단 테이블에는 메모리에 저장된 개체 형식이 나열됩니다.  
  
- **Count** shows the number of instances of the type in the snapshot.  
  
- **Size (Bytes)** is the size of the all instances of the type, excluding the size of objects it holds references to. Component  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  You can choose the instances icon (![The instance icon in the Object Type column](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) in the **Object Type** column to view a list of the instances of the type.  
  
#### <a name="instance-table"></a>인스턴스 테이블  
 ![Instances table](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** is the memory location of the object that serves as the object identifier of the object  
  
- **Value** shows the actual value of value types. 참조 형식의 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
   ![Instance values in a data tip](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Size (Bytes)** is the size of the object, excluding the size of objects it holds references to. Component  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  By default, types and instances are sorted by **Inclusive Size (Bytes)** . 정렬 순서를 변경하려면 목록에서 열 머리글을 선택합니다.  
  
#### <a name="paths-to-root"></a>루트 경로  
  
- For a type selected from the **Object Type** table, the **Paths to Root** table shows the unique type hierarchies that lead to root objects for all objects of the type, along with the number of references to the type that is above it in the hierarchy.  
  
- For an object selected from the instance of a type, **Paths to Root** shows a graph of the actual objects that hold a reference to the instance. 개체의 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
#### <a name="referenced-types--referenced-objects"></a>참조된 형식/참조된 개체  
  
- For a type selected from the **Object Type** table, the **Referenced Types** tab shows the size and number of referenced types held by all objects of the selected type.  
  
- For a selected instance of a type, **Referenced Objects** shows the objects that are held by the selected instance. 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
  **Circular references**  
  
  개체는 첫 번째 개체를 직접적 또는 간접적으로 참조하는 두 번째 개체를 참조할 수 있습니다. When the memory analyzer encounters this situation, it stops expanding the reference path and adds a **[Cycle Detected]** annotation to the listing of the first object and stops.  
  
  **Root types**  
  
  메모리 분석기에서는 보유 중인 참조의 종류를 설명하는 루트 개체에 다음과 같은 주석을 추가합니다.  
  
|주석|설명|  
|----------------|-----------------|  
|**Static variable** `VariableName`|정적 변수. `VariableName`은 변수의 이름입니다.|  
|**Finalization Handle**|종료자 큐의 참조입니다.|  
|**Local Variable**|A local variable.|  
|**Strong Handle**|개체 참조 테이블의 강력한 참조에 대한 핸들입니다.|  
|**Async. Pinned Handle**|개체 핸들 테이블의 비동기 고정된 개체입니다.|  
|**Dependent Handle**|개체 핸들 테이블의 종속 개체입니다.|  
|**Pinned Handle**|개체 핸들 테이블의 고정된 강력한 참조입니다.|  
|**RefCount Handle**|개체 핸들 테이블의 참조 횟수가 계산되는 개체입니다.|  
|**SizedRef Handle**|가비지 컬렉션 시 모든 개체 및 개체 루트의 집합 클로저의 대략적인 크기를 유지하는 강력한 핸들입니다.|  
|**Pinned local variable**|고정된 지역 변수입니다.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Compare two memory snapshots  
 프로세서의 덤프 파일 두 개를 비교하여 메모리 누수의 원인이 될 수 있는 개체를 찾을 수 있습니다. 첫 번째(이전) 및 두 번째(이후) 파일 컬렉션 간의 간격은 누수된 개체 수 증가를 명백하게 확인하기에 충분할 정도로 커야 합니다. 두 파일을 비교하려면 다음 단계를 수행하세요.  
  
1. Open the second dump file, and then choose **Debug Managed Memory** on the **Minidump File Summary** page.  
  
2. On the memory analysis report page, open the **Select baseline** list, and then choose **Browse** to specify the first dump file.  
  
   The analyzer adds columns to the top pane of the report that display the difference between the **Count**, **Size**, and **Inclusive Size** of the types to those values in the earlier snapshot.  
  
   ![Diff columns in the type list](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **Reference Count Diff** column is also added to the **Paths to Root** table.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>관련 항목:  
 [VS ALM TFS Blog: Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio TV &#124; Managed Memory Analysis](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio Toolbox &#124; Managed Memory Analysis in Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)