---
title: '방법: 오류 표식 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435963"
---
# <a name="how-to-implement-error-markers"></a>방법: 오류 마커를 구현 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

오류 표식 (또는 빨간색 물결 무늬 밑줄)은 가장 어려운 구현 하려면 텍스트 편집기 사용자 지정 합니다. 그러나 VSPackage의 사용자에 게 혜택을 제공 하는 데 비용이 훨씬 보다 클 수 있습니다. 약간 오류 표식에 언어 파서 하다 구불구불한 또는 물결 모양의 빨간색 선으로 잘못 된 고 판단 되는 텍스트를 표시 합니다. 잘못 된 코드를 시각적으로 표시 하 여 프로그래머에 게 도움이 됩니다.  
  
 텍스트 마커를 사용 하 여 빨간색 물결 무늬 밑줄을 구현 합니다. 일반적으로 언어 서비스 추가 빨간색 물결 무늬 밑줄 텍스트 버퍼에 백그라운드 통과로 유휴 시간에 또는 백그라운드 스레드에서 합니다.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>빨간색 물결선 밑줄이 기능을 구현 하려면  
  
1. 빨간색 물결선 밑줄이 배치 하려는 텍스트를 선택 합니다.  
  
2. 형식의 마커 만들려면 `MARKER_CODESENSE_ERROR`합니다. 자세한 내용은 [방법: 표준 텍스트 마커 추가](../extensibility/how-to-add-standard-text-markers.md)합니다.  
  
3. 그 후에 전달 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스 포인터입니다.  
  
   이 프로세스를 사용 하면 지정된 표식을 통해 팁 텍스트 또는 특수 한 상황에 맞는 메뉴를 만들 수 있습니다. 자세한 내용은 [방법: 표준 텍스트 마커 추가](../extensibility/how-to-add-standard-text-markers.md)합니다.  
  
   오류 표식 표시 되기에 다음 개체가 필요 합니다.  
  
- 파서입니다.  
  
- 작업 공급자 (즉, 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) 줄 정보에서는 변경 레코드를 다시 구문 분석할 줄을 식별 하기 위해 유지 관리 합니다.  
  
- 캐럿을 캡처하는 텍스트 뷰 필터 변경 이벤트를 사용 하 여 보기를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) 메서드.  
  
  파서, 작업 공급자 및 필터 오류 마커를 가능 하 게 하는 데 필요한 인프라를 제공 합니다. 다음 단계를 오류 마커를 표시 하기 위한 프로세스를 제공 합니다.  
  
1. 필터링 된 뷰 필터는 해당 보기의 데이터와 관련 된 작업 공급자에 대 한 포인터를 가져옵니다.  
  
    > [!NOTE]
    > 메서드 팁, 문 완성, 오류 표식, 등에 대 한 동일한 명령 필터를 사용할 수 있습니다.  
  
2. 필터를 다른 줄으로 이동 했음을 나타내는 이벤트를 수신 하는 경우 오류를 확인 하는 작업이 만들어집니다.  
  
3. 작업 처리기 줄 변경 되었는지 확인 합니다. 그렇다면 오류에 대 한 줄 구문 분석 합니다.  
  
4. 오류가 발견 되 면 작업 공급자는 작업 항목 인스턴스를 만듭니다. 이 이런은 환경을 텍스트 보기에는 오류 표식으로 사용 하는 텍스트 마커를 만듭니다.  
  
## <a name="see-also"></a>참고 항목  
 [텍스트 마커를 사용 하 여 레거시 API를 사용 하 여](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 표준 텍스트 마커를 추가 합니다.](../extensibility/how-to-add-standard-text-markers.md)   
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)   
 [방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)
