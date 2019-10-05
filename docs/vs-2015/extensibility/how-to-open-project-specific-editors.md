---
title: '방법: 프로젝트별 편집기 열기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2439a07f63b8da854ca8dc331d26e30f49503257
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435935"
---
# <a name="how-to-open-project-specific-editors"></a>방법: 프로젝트별 편집기 열기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트에서 열려 있는 항목 파일을 기본적으로 해당 프로젝트에 대 한 특정 편집기에 바인딩되어 있으면 프로젝트 프로젝트별 편집기를 사용 하 여 파일을 열어야 합니다. 파일은 편집기를 선택 하는 IDE 메커니즘으로 위임할 수 없습니다. 예를 들어 표준 비트맵 편집기를 사용 하는 대신 프로젝트에 고유한 파일의 정보를 인식 하는 특정 비트맵 편집기를 지정 하려면이 프로젝트별 편집기 옵션을 사용할 수 있습니다.  
  
 IDE 호출 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 메서드 특정 프로젝트에서 파일을 열어야 한다는 결정 합니다. 자세한 내용은 [열린 파일 명령을 사용 하 여 표시 파일](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)합니다. 구현 하려면 다음 지침을 따르세요는 `OpenItem` 메서드를 사용 하려면 프로젝트 프로젝트별 편집기를 사용 하 여 파일을 엽니다.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>프로젝트별 편집기를 사용 하 여 OpenItem 메서드를 구현 합니다.  
  
1. 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 방법 (RDT_EditLock) 파일 (문서 데이터 개체)은 이미 열려 있는지 여부를 결정 합니다.  
  
    > [!NOTE]
    > 문서 데이터 및 문서 보기 개체에 대 한 자세한 내용은 참조 하세요. [문서 데이터 및 사용자 지정 편집기의 문서 뷰](../extensibility/document-data-and-document-view-in-custom-editors.md)합니다.  
  
2. 파일이 이미 열려 있으면 파일을 호출 하 여 resurface 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 메서드와 IDO_ActivateIfOpen에 대 한 값을 지정 합니다 `grfIDO` 매개 변수입니다.  
  
     열려 있는 파일을 호출 하는 프로젝트 이외의 프로젝트 문서가 소유 하는 경우 다른 프로젝트에서 열려 있는 편집기는 사용자에 게 경고가 표시 됩니다. 파일 창이 다음 표시 됩니다.  
  
3. 텍스트 버퍼 (문서 데이터 개체)가 이미 열려 있고 다른 보기에 연결 하려는 모르는 경우 해당 보기를 후크 하는 일을 담당 합니다. 프로젝트에서 뷰 (문서 뷰 개체)를 인스턴스화 하는 권장된 방법은 아래와 같습니다.  
  
    1. 호출 `QueryService` 에 <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> 에 대 한 포인터를 가져오기 위해 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> 인터페이스입니다.  
  
    2. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 문서 뷰 클래스의 인스턴스를 만드는 방법.  
  
4. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 메서드에 문서 뷰 개체를 지정 합니다.  
  
     이 메서드는 문서 창에 문서 뷰 개체를 사이트입니다.  
  
5. 에 대 한 적절 한 호출을 수행 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 메서드.  
  
     이 시점에서 뷰를 완전히 초기화 하 고 열려는 준비 해야 합니다.  
  
6. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 메서드를 표시 하 고 보기를 엽니다.  
  
## <a name="see-also"></a>참고 항목  
 [열기 및 프로젝트 항목 저장](../extensibility/internals/opening-and-saving-project-items.md)   
 [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)   
 [방법: 열린 문서의 편집기 열기](../extensibility/how-to-open-editors-for-open-documents.md)
