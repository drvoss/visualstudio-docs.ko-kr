---
title: 사용자 지정 문서 저장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d41b075111797a12d68b4aa30c23e3cbacd8058a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432107"
---
# <a name="saving-a-custom-document"></a>사용자 지정 문서 저장
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

환경 핸들을 **저장**를 **다른 이름으로 저장**, 및 **모두 저장** 명령입니다. 사용자가 클릭 하면 **저장**, **다른 이름으로 저장**, **또는 모두 저장** 에 **파일** 메뉴 Save All, 다음에 솔루션을 닫습니다 프로세스가 발생합니다.  
  
 ![고객 편집기 저장](../../extensibility/internals/media/private.gif "개인")  
다른 이름으로 저장 하 고 모두 저장 명령 사용자 지정 편집기에 대 한 처리에 저장  
  
 다음 단계에서는이 프로세스를 자세히 설명 합니다.  
  
1. 에 대 한는 **저장** 및 **다른 이름으로 저장** 명령을 사용 하 여 환경을 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 활성 문서 창이 확인 하려면 서비스와 따라서 항목 저장 해야 합니다. 활성 문서 창이 확인 되 면 환경을 문서 테이블 실행에서 문서에 대 한 계층 포인터 및 항목 식별자 (itemID)를 찾습니다. 자세한 내용은 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)합니다.  
  
     모두 저장 명령에 대 환경을 실행 중인 문서 테이블의 정보를 저장 하려면 모든 항목 목록이 컴파일하는 데 사용 합니다.  
  
2. 솔루션 받으면를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 호출을 반복 하는 선택한 항목 집합 (의해 노출 되는, 여러 선택 항목을 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 서비스).  
  
3. 계층 포인터를 호출 하는 솔루션 선택 영역에 있는 각 항목에 사용 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 저장 메뉴 명령을 활성화 해야 하는지 여부를 결정 하는 방법입니다. 하나 이상의 항목이 더티 인 경우에 Save 명령 사용 됩니다. 계층에서 표준 편집기를 사용 하는 경우 다음에 대 한 쿼리 계층 구조 대리자 더티 상태 편집기를 호출 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 메서드.  
  
4. 변경 된 각 선택 항목을 솔루션 계층 포인터가 호출을 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 적절 한 계층 메서드.  
  
     사용자 지정 편집기의 경우 문서 데이터 개체 및 프로젝트 간의 통신 비공개입니다. 따라서 이러한 두 개체 간의 특별 한 지 속성 관련 된 고민을 처리 됩니다.  
  
    > [!NOTE]
    > 고유한 지 속성을 구현 하는 경우 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 시간을 절약 하는 방법입니다. 이 메서드는 파일을 저장 해도 안전 하다 되도록 확인 (예를 들어, 파일 읽기 전용이 아닌지).  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
