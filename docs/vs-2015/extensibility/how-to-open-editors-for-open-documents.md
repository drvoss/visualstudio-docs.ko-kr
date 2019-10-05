---
title: '방법: 열린 문서에 대 한 편집기 열기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6e565e026ca49825a7b00a82e4e5c62a2f6c3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204142"
---
# <a name="how-to-open-editors-for-open-documents"></a>방법: 열린 문서에 대한 편집기 열기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 문서 창이 열리기 전에 프로젝트 먼저 결정 해야 합니다 있는지 여부를 파일이 이미 열려 다른 편집기에 대 한 문서 창에서. 파일은 프로젝트 관련 편집기에 열거나 수 또는 표준 편집기 중 하나에 등록 된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
## <a name="opening-a-project-specific-editor"></a>프로젝트별 편집기 열기  
 이미 열려 있는 파일에 대 한 프로젝트별 편집기를 열려면 다음 절차를 따르십시오.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>열려 있는 파일에 대 한 프로젝트별 편집기를 열려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 메서드를 호출합니다.  
  
    이 호출은 해당 하는 경우 문서 계층, 계층 항목 및 창 프레임에 대 한 포인터를 반환 합니다.  
  
2. 문서를 연 경우 프로젝트 또는 있으면 문서 뷰 개체도 문서 데이터 개체만 볼 수 있는지를 확인 해야 합니다.  
  
   - 문서 뷰 개체를 이미 있는 경우이 뷰는 다른 계층 또는 계층 항목, 프로젝트 resurface 기존 창에 뷰의 창 프레임에 대 한 포인터를 사용 합니다.  
  
   - 문서 뷰 개체를 이미 있는 경우이 뷰는 동일한 계층 구조 및 계층 항목, 기본 문서 데이터 개체에 연결할 수 프로젝트 두 번째 보기를 열 수 있습니다. 그렇지 않으면 프로젝트 resurface 기존 창에 뷰의 창 프레임에 대 한 포인터를 사용 해야 합니다.  
  
   - 문서 데이터 개체가 하나만 있는 경우 프로젝트는 해당 보기에 대 한 문서 데이터 개체를 사용할 수 있는지 여부를 결정 해야 합니다. 문서 데이터 개체를 호환 되는 경우 전체 단계에서 설명한 [프로젝트별 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)합니다.  
  
     호환 되지 않는 문서 데이터 개체는 파일이 현재 사용에서 여부를 나타내는 사용자에 게 오류가 표시 됩니다. 이 오류에만 표시 되어야 일시적인 경우에는 사용자가 아닌 다른 편집기를 사용 하 여 파일을 엽니다 하려는 파일을 동시에 컴파일 중인 경우와 같이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 텍스트 편집기. 핵심 텍스트 편집기 컴파일러를 사용 하 여 문서 데이터 개체를 공유할 수 있습니다.  
  
3. 문서가 열려 있지 않으면 문서 뷰 개체 없거나 문서 데이터 개체 이므로의 단계를 완료 [프로젝트별 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)합니다.  
  
## <a name="opening-a-standard-editor"></a>표준 편집기 열기  
 이미 있는 파일에 대 한 표준 편집기를 열려면 다음 절차를 사용 하 여가 엽니다.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>열려 있는 파일에 대 한 표준 편집기를 열려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>를 호출합니다.  
  
     이 메서드는 문서가 아직 열려 있지 호출 하 여 먼저 확인 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>합니다. 문서가 이미 열려 있으면 해당 편집기 창 다시 표시 됩니다.  
  
2. 문서가 열려 있지 않으면 다음 단계에 따라 [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [열기 및 프로젝트 항목 저장](../extensibility/internals/opening-and-saving-project-items.md)   
 [방법: 프로젝트별 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)   
 [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)
