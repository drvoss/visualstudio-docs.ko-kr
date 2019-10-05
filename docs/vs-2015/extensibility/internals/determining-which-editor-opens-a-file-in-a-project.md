---
title: 프로젝트에서 파일을 엽니다는 편집기 결정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196767"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>프로젝트에서 파일을 여는 편집기 결정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자의 프로젝트에서 파일을 열면 환경 최종적으로 적절 한 편집기를 열거나 해당 파일에 대 한 디자이너는 폴링 프로세스를 진행 합니다. 환경에서 사용 되는 초기 절차 표준 및 사용자 지정 편집기에 대해 동일 합니다. 파일 열기를 사용 하는 편집기를 폴링할 때이 환경에서는 다양 한 조건 및 VSPackage이이 프로세스 중 환경과 조정 해야 합니다.  
  
 사용자 선택 하면 예를 들어 합니다 **열기** 명령을 **파일** 메뉴 후 선택 `filename`.rtf (또는 다른 파일 확장명이.rtf) 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 결과적으로 솔루션의 모든 프로젝트 인스턴스를 순환 하는 각 프로젝트에 대해 구현입니다. 프로젝트에는 우선 순위에 따라 문서에 대 한 클레임을 식별 하는 플래그 집합을 반환 합니다. 가장 높은 우선 순위를 사용 하 여, 환경이 적절 한 호출. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 메서드. 폴링 프로세스에 대 한 자세한 내용은 [추가 프로젝트 및 프로젝트 항목 템플릿](../../extensibility/internals/adding-project-and-project-item-templates.md)합니다.  
  
 기타 파일 프로젝트에는 모든 파일을 다른 프로젝트에서 요구 하지는 클레임입니다. 이 이렇게 하면 사용자 지정 편집기 문서를 열고 하 수 표준 편집기 열기 전에 합니다. 환경을 호출 하는 기타 파일 프로젝트 파일을 클레임 하는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드를 표준 편집기를 사용 하 여 파일을 엽니다. 환경에는.rtf 파일을 처리 하는 하나에 대해 등록 된 편집기의 내부 목록을 검사 합니다. 이 목록은 레지스트리에서 다음 키:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`>\Editors\\{<`editor factory guid`>}\Extensions]  
  
 또한 환경 HKEY_CLASSES_ROOT\CLSID 키 하위 키 DocObject 있는 모든 개체에 대 한 클래스 식별자를 확인 합니다. 파일 확장명을 찾을 수 없으면, Microsoft Word와 같은 응용 프로그램의 임베디드 버전이 Visual Studio에서 전체 만들어집니다. 이러한 문서 개체를 구현 하는 복합 파일 이어야 합니다는 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> 인터페이스 또는 개체를 구현 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 인터페이스입니다.  
  
 레지스트리에서.rtf 파일에 대 한 편집기 팩터리가 없습니다 경우를 HKEY_CLASSES_ROOT에서 환경을 찾습니다 \\.rtf 키 및 여기에 지정 된 편집기를 엽니다. 파일 확장명을 HKEY_CLASSES_ROOT에 없는 경우 환경을 사용 하 여 Visual Studio 핵심 텍스트 편집기 텍스트 파일인 경우 파일을 엽니다.  
  
 핵심 텍스트 편집기에 실패 하면 파일이 텍스트 파일로 없으면 다음 환경을 사용 하 여 해당 바이너리 편집기 파일에 대 한 발생 하는 합니다.  
  
 환경 해당 레지스트리에.rtf 확장에 대 한 편집기를 찾지, 경우에이 편집기 팩터리를 구현 하는 VSPackage 로드 합니다. 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 새 VSPackage 메서드. 호출 하 여 VSPackage `QueryService` 에 대 한 `SID_SVsRegistorEditor`를 사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 환경과 편집기 팩터리를 등록 하는 방법입니다.  
  
 환경 이제 다시 내부 목록을 검사 등록 편집기.rtf 파일에 대 한 새로 등록 된 편집기 팩터리를 찾으려고 합니다. 환경 구현의 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드를 만들려면 뷰 형식과 파일 이름을 전달 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
