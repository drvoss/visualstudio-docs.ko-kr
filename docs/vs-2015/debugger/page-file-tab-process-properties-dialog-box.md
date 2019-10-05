---
title: 프로세스 속성 대화 상자, 페이지 파일 탭 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192722"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>프로세스 속성 대화 상자, 페이지 파일 탭
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 된 **페이지 파일** 프로세스의 페이징 파일을 검사 하려면 탭 합니다. 표시할 합니다 [프로세스 속성 대화 상자](../debugger/process-properties-dialog-box.md), 포커스를 이동 하는 [프로세스 뷰에](../debugger/processes-view.md) 창입니다. 선택한 프로세스 노드 트리에서 선택 **속성** 에서 합니다 **보기** 메뉴.  
  
 다음 설정을 사용할 합니다 **페이지 파일** 탭:  
  
|입력|설명|  
|-----------|-----------------|  
|**페이지 파일 바이트**|이 프로세스에서 페이징 파일에 사용 하는 페이지의 현재 수입니다. 페이징 파일의 프로세스에서 사용 되지만 다른 파일에 포함 되어 있지 데이터 페이지를 저장 합니다. 페이징 파일은 모든 프로세스에서 사용 하 고 다른 프로세스에서 실행 되는 동안 페이징 파일의 공간 부족 오류가 발생할 수 있습니다.|  
|**최고 페이지 파일 바이트**|페이징 파일에이 프로세스는 페이지의 최대 수입니다.|  
|**페이지 폴트**|이 프로세스의 실행 스레드에서 페이지 폴트 수입니다. 페이지 폴트는 스레드가 주 메모리의 작업 집합에 없는 가상 메모리 페이지를 참조 하는 경우에 발생 합니다. 따라서 페이지 검색 되지 것입니다 디스크에서 대기 목록에 있으면 되므로 주 메모리에 이미 사용 하 여 페이지를 공유 하거나 다른 사용 되는 경우 처리 합니다.|
