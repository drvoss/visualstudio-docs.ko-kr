---
title: 여러 문서 보기 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9377fc12db8cedba65a418fd32b82a1421bd9b43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160508"
---
# <a name="supporting-multiple-document-views"></a>여러 문서 보기 지원
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기에 대 한 별도 문서 데이터 및 문서 보기 개체를 만들어 문서 둘 이상의 뷰를 제공할 수 있습니다. 추가 문서 보기를는 유용할 수 있는 경우에 따라 다음과 같습니다.  
  
- 새 창 지원 합니다. 편집기에서 엽니다 기간이 이미 사용자를 선택 하 여 새 창을 열 수 있도록 원하는 편집기는 동일한 형식의 두 개 이상의 보기를 제공 하는 **새 창** 명령을 합니다 **창** 메뉴.  
  
- 폼과 코드 보기 지원: 편집기를 다양 한 종류의 보기를 제공 해야 합니다. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]예를 들어 폼 보기와 코드 보기를 제공 합니다.  
  
  이 대 한 자세한 내용은 Visual Studio 패키지 템플릿을 만든 사용자 지정 편집기 프로젝트 EditorFactory.cs 파일에서 CreateEditorInstance 절차를 참조 합니다. 이 프로젝트에 대 한 자세한 내용은 참조 하세요. [연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)합니다.  
  
## <a name="synchronizing-views"></a>뷰를 동기화합니다.  
 여러 뷰를 구현 하는 경우 문서 데이터 개체는 데이터와 동기화 하는 모든 보기를 유지 하는 일을 담당 합니다. 인터페이스에서 처리 하는 이벤트를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 여러 뷰 데이터와 동기화 합니다.  
  
 사용 하지 않는 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 문서 데이터 개체에 대 한 변경 내용을 처리 하도록 사용자 고유의 이벤트 시스템을 구현 해야 하는 다음 여러 뷰를 동기화 하는 개체입니다. 여러 뷰를 최신 상태로 유지 하려면 다양 한 수준의 세분성을 사용할 수 있습니다. 최대 단위는 설정 된 하나의 보기에 입력할 때 다른 뷰를 즉시 업데이트 됩니다. 최소 세분성을 사용 하 여 다른 보기의 정품 인증 될 때까지 업데이트 되지 않습니다.  
  
## <a name="determining-whether-document-data-is-already-open"></a>이미 열려 있는지 여부를 문서 데이터를 결정  
 통합된 개발 환경 (IDE)에서 실행 중인 문서 테이블 (RDT)는 다음 다이어그램에 나와 있는 것 처럼 문서에 대 한 데이터가 이미 열려 있는지 여부를 추적 하는 데 도움이 됩니다.  
  
 ![DocDataView 그래픽](../extensibility/media/docdataview.gif "Docdataview")  
다중 뷰  
  
 기본적으로 각 보기가 (문서 뷰 개체)는 자체 창 프레임에 포함 된 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). 그러나 이미 설명한 대로 문서 데이터를 표시할 여러 뷰에서 합니다. 이 작업이 가능 하도록 Visual Studio는 해당 문서 편집기에 열려 이미 있는지 여부를 결정할 RDT를 확인 합니다. IDE를 호출 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 편집기를 만들려면 NULL이 아닌 값을 반환 합니다 `punkDocDataExisting` 매개 변수는 다른 편집기에에서 열려 있는 문서 이미 나타냅니다. RDT 함수를 참조 하는 방법에 대 한 자세한 내용은 [문서 테이블 실행](../extensibility/internals/running-document-table.md)합니다.  
  
 사용자 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 구현에서 반환 하는 문서 데이터 개체를 검사 `punkDocDataExisting` 문서 데이터를 편집기에 대 한 적합 한지 여부를 확인 하려면. (예를 들어 HTML 데이터만 표시 되어서는 HTML 편집기에서.) 적절 한 이기 편집기 팩터리의 데이터에 대 한 두 번째 뷰를 제공 해야 합니다. 경우는 `punkDocDataExisting` 매개 변수가 아닙니다 `NULL`, 불가능 하거나 문서 데이터 개체는 다른 편집기에서 열고, 가능성이, 같은 편집기를 사용 하 여 다른 보기에서 열린 문서 데이터가 이미 있습니다. 문서 데이터 편집기 팩터리의 지원 하지 않는 다른 편집기에에서 열려 있는 경우 Visual Studio 편집기 팩터리의 열려는 실패 합니다. 자세한 내용은 [방법: 문서 데이터에 보기 연결](../extensibility/how-to-attach-views-to-document-data.md)합니다.
