---
title: 편집기 팩터리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197757"
---
# <a name="editor-factories"></a>편집기 팩터리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기 팩터리를 편집기 개체를 만들고 실제 뷰 라고 창 프레임에 넣습니다. 문서 데이터 및 편집기 및 디자이너를 만드는 데 필요한 문서 뷰 개체를 만듭니다. 편집기 팩터리를 Visual Studio 핵심 편집기 및 모든 표준 편집기를 만들 필요 합니다. 편집기 팩터리를 사용 하 여 사용자 지정 편집기를 만들 수도 있습니다.  
  
 편집기 팩터리를 구현 하 여 만든는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 인터페이스입니다. 다음 예제를 구현 하는 방법을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 편집기 팩터리를 만들려면:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 편집기를 열면 해당 편집기에서 처리 된 파일 형식을 처음으로 로드 됩니다. 특정 편집기 또는 기본 편집기를 열 수 있습니다. 기본 편집기를 선택 하면 통합된 개발 환경 (IDE)는 올바른 열 편집기를 결정 하 고 엽니다. 자세한 내용은 [프로젝트에서 파일을 엽니다는 편집기 결정](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)합니다.  
  
## <a name="registering-editor-factories"></a>편집기 팩터리를 등록합니다.  
 사용자가 만든 편집기를 사용 하려면 먼저에 대 한 정보를 처리할 수 있는 파일 확장명을 포함 하 여 먼저 등록 해야 합니다.  
  
 VSPackage, 관리 되는 코드로 작성 하는 경우 관리 패키지 프레임 워크 (MPF) 메서드를 사용할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> VSPackage를 로드 한 후 편집기 팩터리를 등록 합니다. VSPackage는 비관리 코드에서 작성 된 경우 사용자의 편집기 팩터리를 사용 하 여 등록 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> 서비스입니다.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>관리 되는 코드 편집기 팩터리를 사용 하 여 등록  
 편집기 팩터리의 VSPackage의 등록 해야 합니다는 `Initialize` 메서드. 먼저 호출 `base.Initialize`를 호출한 다음 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 각 편집기 팩터리의  
  
 관리 코드에서 있습니다 이므로 편집기 팩터리를 등록 취소 하지 않아도 VSPackage를 자동으로 처리 합니다. 또한 편집기 팩터리의 구현 하는 경우 <xref:System.IDisposable>, 등록 취소 되 면 자동 삭제 합니다.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>비관리 코드를 사용 하 여 편집기 팩터리를 등록  
 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 편집기 패키지를 사용 하 여 구현 합니다 `QueryService` 호출할 메서드를 `SVsRegisterEditors`합니다. 에 대 한 포인터를 반환 이렇게 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>합니다. 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 구현에 전달 하 여 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 인터페이스입니다. Mplement 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 별도 클래스에 있습니다.  
  
## <a name="the-editor-factory-registration-process"></a>편집기 팩터리 등록 프로세스  
 다음 프로세스에는 Visual Studio 편집기 팩터리를 사용 하 여 편집기를 로드할 때 발생 합니다.  
  
1. 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 시스템 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>합니다.  
  
2. 이 메서드는 편집기 팩터리를 반환합니다. 그러나 Visual Studio 지연 프로젝트 시스템 편집기에 실제로 필요한 때까지 편집기의 패키지를 로드 합니다.  
  
3. Visual Studio를 호출 하는 프로젝트 시스템에서 편집기를 필요한 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, 문서 보기 및 문서 데이터 개체를 반환 하는 특수 메서드입니다.  
  
4. 경우에 편집기 팩터리를 사용 하 여 Visual Studio에서 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 문서 데이터 개체 및 문서 뷰 개체를 반환 하 고 Visual Studio 다음 문서 창을 만듭니다, 문서 보기 개체에서 배치은 실행 중인 문서에 항목을 만듭니다 문서 데이터 개체에 대 한 테이블 (RDT).  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [문서 테이블 실행](../extensibility/internals/running-document-table.md)
