---
title: 도구 상자, 구성 요소 탭 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98955b3f9428126775ca6a58f19a12de416833c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689499"
---
# <a name="toolbox-components-tab"></a>도구 상자, 구성 요소 탭
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 및 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 디자이너에 추가할 수 있는 구성 요소를 표시합니다. <xref:System.Messaging.MessageQueue> 및 <xref:System.Diagnostics.EventLog>와 같이 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에 함께 제공되는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 구성 요소 이외에 사용자 지정 또는 타사 구성 요소를 이 탭에 추가할 수 있습니다. 자세한 내용은 [방법: 도구 상자 탭 조작](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)을 참조하세요.  
  
 이 탭을 표시하려면 **보기** 메뉴에서 **도구 상자**를 선택합니다. **도구 상자**에서 **구성 요소** 탭을 선택합니다.  
  
 **BackgroundWorker**  
 작업을 별도의 전용 스레드에서 실행할 수 있는 `System.ComponentModel.BackgroundWorker` 구성 요소를 만듭니다.  
  
 **DirectoryEntry**  
 Active Directory 서비스 공급자를 조작하는 데 사용될 수 있고 Active Directory 계층 구조의 노드 또는 개체를 캡슐화하는 <xref:System.DirectoryServices.DirectoryEntry> 구성 요소 인스턴스를 만듭니다.  
  
 **DirectorySearcher**  
 Active Directory에 대해 쿼리를 실행하는 데 사용할 수 있는 <xref:System.DirectoryServices.DirectorySearcher> 구성 요소 인스턴스를 만듭니다.  
  
 **ErrorProvider**  
 최종 사용자에게 양식의 컨트롤에 관련 오류가 있음을 나타내는 `System.Windows.Forms.ErrorProvider` 구성 요소 인스턴스를 만듭니다.  
  
 **EventLog**  
 로그에 이벤트 쓰기 및 로그 데이터 읽기와 같이 시스템 및 사용자 지정 이벤트 로그를 조작하는 데 사용할 수 있는 <xref:System.Diagnostics.EventLog> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [EventLog 구성 요소 소개](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805)를 참조하세요.  
  
 **FileSystemWatcher**  
 액세스 권한을 가진 디렉터리 또는 파일이 변경되었는지 모니터링하는 데 사용할 수 있는 <xref:System.IO.FileSystemWatcher> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [방법: FileSystemWatcher 구성 요소 인스턴스 구성](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50)을 참조하세요.  
  
 **HelpProvider**  
 컨트롤에 대한 팝업 또는 온라인 도움말을 제공하는 `System.Windows.Forms.HelpProvider` 구성 요소 인스턴스를 만듭니다.  
  
 **ImageList**  
 `System.Drawing.Image` 개체 컬렉션을 관리하는 메서드를 제공하는 `System.Windows.Forms.ImageList` 구성 요소 인스턴스를 만듭니다.  
  
 **MessageQueue**  
 큐에서 메시지 읽기, 큐에 메시지 쓰기, 트랜잭션 처리, 큐 관리 작업 수행과 같이 메시지 큐를 조작하는 데 사용할 수 있는 <xref:System.Messaging.MessageQueue> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [메시지 구성 요소 사용](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7)을 참조하세요.  
  
 **PerformanceCounter**  
 새 범주 및 인스턴스 만들기, 카운터에서 값 읽기, 카운터 데이터에 대한 계산 수행과 같이 Windows 성능 카운터를 조작하는 데 사용할 수 있는 <xref:System.Diagnostics.PerformanceCounter> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [성능 임계값 모니터링](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91)을 참조하세요.  
  
 **Process**  
 시스템의 프로세스와 연결된 데이터를 중지, 시작, 조작하는 데 사용할 수 있는 <xref:System.Diagnostics.Process> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [Windows 프로세스 모니터링 및 관리](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e)를 참조하세요.  
  
 **SerialPort**  
 동기 및 이벤트 구동 I/O, 핀 및 중단 상태에 대한 액세스, 직렬 드라이버 속성에 대한 액세스를 제공하는 `System.IO.Ports.SerialPort` 구성 요소 인스턴스를 만듭니다.  
  
 **ServiceController**  
 서비스 시작 및 중지, 서비스에 명령 보내기와 같이 기존 서비스를 조작하는 데 사용할 수 있는 <xref:System.ServiceProcess.ServiceController> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [Windows 서비스 모니터링](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222)을 참조하세요.  
  
 **Timer**  
 Windows 기반 애플리케이션에 시간 기반 기능을 추가하는 데 사용할 수 있는 <xref:System.Windows.Forms.Timer> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [Timer 구성 요소](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7)를 참조하세요.  
  
> [!NOTE]
> **도구 상자**에 추가할 수 있는 시스템 기반 <xref:System.Timers.Timer>도 있습니다. 이 <xref:System.Timers.Timer>는 서버 애플리케이션에 최적화되어 있고 Windows Forms <xref:System.Windows.Forms.Timer>는 Windows Forms에 가장 적합합니다.  
  
## <a name="see-also"></a>참고 항목  
 [구성 요소를 사용한 프로그래밍](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [구성 요소 프로그래밍 연습](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [도구 상자](../../ide/reference/toolbox.md)   
 [도구 상자 항목 선택 대화 상자(Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
