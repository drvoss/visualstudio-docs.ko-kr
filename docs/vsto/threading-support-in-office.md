---
title: Office의 스레딩 지원
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3218a12add86739c76cd50f82fdda5d845e2b069
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978769"
---
# <a name="threading-support-in-office"></a>Office의 스레딩 지원
  이 문서에서는 Microsoft Office 개체 모델의 스레딩 지원 되는 방법에 대 한 정보를 제공 합니다. Office 개체 모델은 하지 스레드로부터 안전한 지, 이지만 Office 솔루션에서 여러 스레드를 사용 하 여 작업할 수 있습니다. Office 응용 프로그램은 구성 요소 개체 모델 (COM) 서버. COM 클라이언트가 임의 스레드에서 COM 서버를 호출할 수 있습니다. 스레드로부터 안전 하지 않은 COM 서버에 대 한 COM 하나만 논리 스레드가 언제 든 지 서버에서 실행 되도록 동시 호출을 serialize 하는 메커니즘을 제공 합니다. 이 메커니즘 (STA) 단일 스레드 아파트 모델 이라고 합니다. 호출이 serialize 되므로 서버 사용량이 또는 백그라운드 스레드에서 다른 호출을 처리 하는 동안 호출자 기간 동안 차단 될 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>여러 스레드를 사용 하는 경우 필요한 지식
 여러 스레드를 사용 하려면의 다음 양상에 대 한 최소 기본 지식이 있어야 다중 스레딩:

- Windows Api

- COM 다중 스레드 개념

- 동시성

- 동기화

- 마샬링

  일반 정보에 대 한 다중 스레딩에 대 한 참조 [관리 되는 스레딩](/dotnet/standard/threading/)합니다.

  Office 주 STA에서 실행 됩니다. 이 의미를 이해 Office를 사용 하 여 여러 스레드를 사용 하는 방법을 이해할 수 있습니다.

## <a name="basic-multithreading-scenario"></a>다중 스레딩 기본 시나리오
 Office 솔루션에서 코드는 항상 주 UI 스레드에서 실행 됩니다. 백그라운드 스레드에서 별도 작업을 실행 하 여 응용 프로그램 성능을 개선할 수도 있습니다. 작업을 완료 하 두 겉보기 한 번에 하나의 태스크 뒤에 다른 원활 하 게 실행 (다중 스레드를 사용 하는 주된 이유)을 유발 하는 대신 목표가입니다. 예를 들어, 기본 Excel UI 스레드에서 이벤트 코드를 사용 해야 하 고 백그라운드 스레드에서 서버에서 데이터를 수집 하 고 서버에서 데이터를 사용 하 여 Excel UI에서 셀을 업데이트 하는 작업을 실행할 수 있습니다.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Office 개체 모델을 호출 하는 백그라운드 스레드
 Office 응용 프로그램에 호출 하는 백그라운드 스레드를 STA 경계를 넘어 호출을 자동으로 마샬링됩니다. 그러나 보장이 없습니다 Office 응용 프로그램에서 해당 호출 시 백그라운드 스레드를 처리할 수 있도록 합니다. 일부의 가능성이 있습니다.

1. Office 응용 프로그램에는 입력 수에 대 한 호출에 대 한 메시지 펌프 해야 합니다. 수행 하는 경우이 생성 하지 않고 처리 하는 많은 시간이 걸릴 수 있습니다.

2. 다른 논리 스레드 아파트에 이미 있으면 새 스레드를 입력할 수 없습니다. 논리 스레드 Office 응용 프로그램을 입력 하 고 호출자의 아파트 돌아가기 재진입 호출 하는 경우에 자주 발생 합니다. 응용 프로그램은 해당 호출이 반환 되기를 기다리는 차단 됩니다.

3. Excel는 들어오는 호출을 즉시 처리할 수 없는 상태의 수 있습니다. 예를 들어 Office 응용 프로그램 모달 대화 상자를 표시할 수 있습니다.

   COM 가능성 2와 3에 대 한 제공 된 [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) 인터페이스입니다. 모든 호출을 통해 입력 서버를 구현 하는 경우는 [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) 메서드. 2 가능성에 대 한 호출은 자동으로 거부 됩니다. 세 번째 서버는 상황에 따라 호출을 거부할 수 있습니다. 호출이 거부 되 면 호출자가 수행할 작업을 결정 해야 합니다. 일반적으로 호출자에 게 구현 [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), 이때가 거부 알림을 받을 것은 [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) 메서드.

   그러나 Visual Studio에서 Office 개발 도구를 사용 하 여 만든 솔루션의 경우 COM interop에서는 변환에 대 한 모든 거부 된 호출을 <xref:System.Runtime.InteropServices.COMException> ("메시지 필터가 표시 응용 프로그램이 사용 중인"). 개체 모델을 호출할 때마다 할 백그라운드 스레드에서이 예외를 처리 하도록 준비 여야 합니다. 일반적으로 특정 시간 동안 다시 시도 하 고 다음 대화 상자를 표시 합니다. 그러나 백그라운드 스레드를 STA로 만들 수도 및 다음이 경우를 처리 하도록 해당 스레드에 대 한 메시지 필터를 등록할 수 있습니다.

## <a name="start-the-thread-correctly"></a>스레드를 제대로 시작
 새 STA 스레드를 만들 때에 스레드를 시작 하기 전에 아파트 상태를 STA로 설정 합니다. 다음 코드 예제에서는 이 작업을 수행하는 방법을 보여 줍니다.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 자세한 내용은 [관리 되는 모범 사례 스레딩](/dotnet/standard/threading/managed-threading-best-practices)합니다.

## <a name="modeless-forms"></a>모덜리스 폼
 모덜리스 폼 양식이 표시 되는 동안 일부 유형의 응용 프로그램과 상호 작용을 수 있습니다. 양식을 닫지 않고 응용 프로그램 상호 작용 하 고 폼을 사용 하 여 사용자 상호 작용. Office 개체 모델을 관리 되는 모덜리스 폼; 지원 그러나 백그라운드 스레드에서 사용 하지 않아야 합니다.

## <a name="see-also"></a>참고자료
- [스레딩(C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [스레딩(Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [사용 하 여 스레드 및 스레딩](/dotnet/standard/threading/using-threads-and-threading)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
