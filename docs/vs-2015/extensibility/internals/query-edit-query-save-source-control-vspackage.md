---
title: 쿼리 편집, 쿼리 저장 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad0cf7c3e1d3269dbe7ebee051cc32e2e8531ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148896"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>쿼리 편집, 쿼리 저장(소스 제어 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 편집기 쿼리 편집 쿼리 저장 (QEQS) 이벤트를 브로드캐스트할 수 있습니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 원본 제어 스텁 QEQS 이벤트 수신자 되도록 QEQS 서비스를 구현 합니다. 그런 다음 이러한 이벤트는 현재 소스 제어 VSPackage에 위임 됩니다. 현재 소스 제어 VSPackage 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 및 해당 메서드. 메서드는 `IVsQueryEditQuerySave2` 인터페이스는 일반적으로 문서를 처음으로 및 문서가 저장 될 직전 편집할 직전 호출 됩니다.  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave 이벤트  
 소스 제어 VSPackage를 구현 하 여 QEQS 이벤트를 처리 해야 합니다는 `IVsQueryEditQuerySave2` 인터페이스와 필요한 메서드. 아래 최소한 VSPackage 구현 해야 하는 두 가지 방법의 간략 한 설명이입니다. 소스 제어 모델의 논리에 따라 실제 구현 해야 합니다.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles 메서드  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 프로젝트 또는 편집기에서 파일을 수정 하려고 할 때 호출 됩니다. 이 메서드를 호출 하는 것이 좋습니다 *하기 전에* 파일이 수정 되 고은 파일을 저장 하는 경우. 호출 하는 경우는 `IVsQueryEditQuerySave2::QueryEditFiles` 메서드 여부를 지정 된 파일이 소스 제어, 체크아웃할 수 해야 하는지 여부 및 로드 하는지 여부를 확인 합니다. 상황 파일을 편집할 수 없도록 방지 하는 경우는 `IVsQueryEditQuerySave2::QueryEditFiles` 메서드 편집을 취소 호출 프로그램에 알려 줍니다. 호출 모드를 지정 하려면 호출자가 것도 가능 합니다. "자동" 모드에서는이 메서드는 모든 UI 표시 되지는지 않습니다 하는 경우에 작업을 수행 합니다. UI를 피할 수 없는 경우 문제를 나타내기 위해 플래그를 반환 합니다.  
  
 트랜잭션 방식으로;에서 메서드 동작 즉, 단일 파일에서 편집이 취소 되는 경우 모든 파일에 대 한 편집 취소 되었습니다. 반대로, 편집이 허용 되 면 모든 파일에 대 한 허용 됩니다. 이 메서드는 지정 된 파일 집합에 대해 한 번 편집을 허용 하는 경우 파일의 동일한 집합에 대 한 후속 호출에서 편집 허용 항상 해야 합니다. 편집 허용 루프가 파일, 저장, 닫히고;를 다시 로드 될 때까지 계속 됩니다. 해당 특성 (속성)이 변경 될 때까지 또는 소스 제어 패키지 변경 될 때까지 합니다. 구현에서 고려 하는 경우는 `IVsQueryEditQuerySave2::QueryEditFiles` 메서드 여러 파일을 특수 한 파일, 사용자 및 메모리 내 편집에서 취소 합니다.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles 메서드  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 프로젝트 또는 편집기 파일 집합을 저장 해야 할 때 호출 됩니다. 호출 되 면를 `IVsQueryEditQuerySave2::QuerySaveFiles` 메서드 지정 된 파일은 읽기 전용와 소스 제어 되는지 확인 합니다. 파일을 체크 아웃 해야 하는 경우 호출 소스 제어 패키지에 위임 됩니다. 환경 파일을 저장 되지 못하도록 하는 경우는 `IVsQueryEditQuerySave2::QuerySaveFiles` 메서드 파일을 저장 하려면 편집기에서 지정 해야 합니다. 와 마찬가지로 `IVsQueryEditQuerySave2::QueryEditFiles` 호출 모드를 지정 하려면 호출자가 불가능 메서드. "자동" 모드에서는이 메서드는 모든 UI 표시 되지는지 않습니다 하는 경우에 작업을 수행 합니다. UI를 피할 수 없는 경우 문제를 나타내기 위해 플래그를 반환 합니다.  
  
 이 메서드에; 트랜잭션 방식으로 작동 해야 합니다. 즉, 단일 파일에 저장이 취소 되는 경우 모든 파일에 대 한 저장 취소 되었습니다. 반대로, 저장이 허용 되 면 모든 파일에 대 한 허용 되어야 합니다. 와 마찬가지로 합니다 `IVsQueryEditQuerySave2::QueryEditFiles` 메서드를 구현 하는 것이 좋습니다에 사례를 `IVsQueryEditQuerySave2::QuerySaveFiles` 메서드 여러 파일을 특수 한 파일, 사용자 및 메모리 내 편집에서 취소 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
