---
title: 데이터의 사용자 지정 시각화 도우미 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434905"
---
# <a name="create-custom-visualizers-of-data"></a>데이터의 사용자 지정 시각화 도우미 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

시각화 도우미는 구성 요소는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 디버거 사용자 인터페이스입니다. A *시각화 도우미* 대화 상자 또는 해당 데이터 형식에 적합 한 방식으로 변수나 개체를 표시할 다른 인터페이스를 만듭니다. 예를 들어 HTML 시각화 도우미는 HTML 문자열을 해석하고 브라우저 창에서와 마찬가지로 그 결과를 표시합니다. 비트맵 시각화 도우미는 비트맵 구조를 해석하고 그 구조가 표현하는 그래픽을 표시합니다. 일부 시각화 도우미에서는 데이터를 볼 수 있을 뿐만 아니라 수정할 수도 있습니다.  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 디버거에는 6가지 표준 시각화 도우미가 포함되어 있습니다. 텍스트, HTML, XML 및 JSON 시각화 도우미, 문자열 개체에서 사용 되는 WPF 개체 시각적 트리의; 속성을 표시 하는 것에 대 한 WPF 트리 시각화 도우미 및 DataSet, DataView 및 DataTable 개체에 대해 작동 하는 데이터 집합 시각화 도우미입니다. 향후 Microsoft Corporation의 추가 시각화 도우미를 다운로드할 수 있으며 타사와 커뮤니티의 시각화 도우미도 사용 가능합니다. 또한 자신만의 시각화 도우미를 직접 작성하여 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 디버거에 설치할 수 있습니다.  
  
> [!NOTE]
> **Store** 앱에만 표준 텍스트, HTML, XML 및 JSON 시각화 도우미는 지원 합니다. 사용자가 만든 사용자 지정 시각화 도우미는 지원되지 않습니다.  
  
 시각화 도우미는 디버거에 돋보기 모양의 아이콘으로 표시됩니다. 에 돋보기 모양 아이콘이 표시 되 면을 **DataTip**, 디버거 변수 창에서 또는 합니다 **간략 한 조사식** 대화 상자를 클릭할 수 데이터 형식에 적합 한 시각화 도우미를 선택 하려면 돋보기 효과 만들기 해당 개체입니다.  
  
 Compact Framework에서는 시각화 도우미가 지원되지 않습니다.  
  
> [!NOTE]
> 디버거 시각화 도우미에는 부분 신뢰 애플리케이션에 허용되는 것보다 많은 권한이 필요합니다. 따라서 부분 신뢰 코드에서 중지하면 시각화 도우미가 로드되지 않습니다. 시각화 도우미를 사용하여 디버깅하려면 완전 신뢰 코드를 실행해야 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [방법: 시각화 도우미 작성](../debugger/how-to-write-a-visualizer.md)  
  
 [연습: C#에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [방법: 시각화 도우미 설치](../debugger/how-to-install-a-visualizer.md)  
  
 [방법: 시각화 도우미 테스트 및 디버그](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [시각화 도우미 API 참조](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>관련 단원  
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
