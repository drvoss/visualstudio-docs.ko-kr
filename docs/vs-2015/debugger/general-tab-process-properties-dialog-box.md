---
title: 프로세스 속성 대화 상자, 일반 탭 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9256ca4141e9e4ec9e5ae218f1e5a11bf2fa5362
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182289"
---
# <a name="general-tab-process-properties-dialog-box"></a>프로세스 속성 대화 상자, 일반 탭
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 된 **일반** 특정 프로세스에 대 한 자세한 내용을 알아보려면 탭 합니다. 표시할 합니다 [프로세스 속성 대화 상자](../debugger/process-properties-dialog-box.md), 포커스를 이동 하는 [프로세스 뷰에](../debugger/processes-view.md) 창입니다. 선택한 프로세스 노드 트리에서 선택 **속성** 에서 합니다 **보기** 메뉴.  
  
 다음 설정을 사용할 합니다 **일반** 탭:  
  
|입력|Description|  
|-----------|-----------------|  
|**모듈 이름**|모듈의 이름입니다.|  
|**프로세스 ID**|이 프로세스의 고유 ID입니다. 프로세스 ID 번호는 다시 사용 되므로 해당 프로세스의 기간에만 프로세스를 식별 합니다. 프로세스 개체 유형은 프로그램이 실행 될 때 생성 됩니다. 프로세스의 모든 스레드는 동일한 주소 공간을 공유 하 고 동일한 데이터에 액세스할 수 있습니다.|  
|**기본 우선 순위**|이 프로세스의 현재 기본 우선 순위입니다. 스레드는 프로세스 내에서 발생 하 고 프로세스의 기본 우선 순위를 기준으로 자신의 기본 우선 순위를 낮출 수 있습니다.|  
|**스레드**|이 프로세스에서 현재 활성 상태인 스레드 수입니다.|  
|**CPU 시간**|이 프로세스와 해당 스레드에서 소요 된 총 CPU 시간입니다. 사용자 시간 및 특권을과 같습니다.|  
|**사용자 시간**|이 프로세스의이 스레드가 사용자 모드에서 실행 중인 코드 비 유휴 스레드에서 소비한는 누적 경과 된 시간입니다. 응용 프로그램 창 관리자 그래픽 엔진 등 하위 시스템 사용자 모드에서 실행 됩니다.|  
|**권한 있는 시간**|총 경과 시간에이 프로세스가 되었습니다 실행 특권 모드에서 비 유휴 스레드에서입니다. 서비스 계층, 실행 루틴 및 커널 특권 모드에서 실행 됩니다. 장치 드라이버 그래픽 어댑터와 프린터 이외의 다른 대부분의 장치에 대 한 특권 모드에서 실행할 수도 있습니다. Windows 응용 프로그램에 대해 수행 하는 일부 작업은 특권 외에도 기타 하위 시스템 프로세스에서 나타날 수 있습니다.|  
|**경과 시간**|이 프로세스가 실행 된 총 경과 된 시간입니다.|
