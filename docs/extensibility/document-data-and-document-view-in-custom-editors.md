---
title: 사용자 지정 편집기의 문서 데이터 및 문서 보기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7574fad343e2966ab9a8782d472a0491bd29767b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348083"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>문서 데이터 및 사용자 지정 편집기의 문서 뷰
사용자 지정 편집기를 두 부분으로 구성 됩니다: 문서 데이터 개체 및 문서 뷰 개체입니다. 이름으로 문서 데이터 개체에 표시할 텍스트 데이터를 나타냅니다. 마찬가지로, 문서 뷰 개체 (또는 "보기")에서 문서 데이터 개체를 표시 하는 하나 이상의 windows를 나타냅니다.

## <a name="document-data-object"></a>문서 데이터 개체
 문서 데이터 개체에는 텍스트 버퍼의 텍스트 데이터 표현입니다. 문서 텍스트 및 기타 정보를 저장 하는 COM 개체입니다. 문서 데이터 개체는 또한 문서 지 속성을 처리 하 고 해당 데이터의 여러 보기를 사용 하도록 설정 합니다. 자세한 내용은 다음 항목을 참조하세요.

 <xref:EnvDTE80.Window2.DocumentData%2A> 및 [Windows 문서](../extensibility/internals/document-windows.md)합니다.

 사용자 지정 편집기 및 디자이너를 사용 하도록 선택할 수는 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 개체 또는 고유한 사용자 지정 버퍼입니다. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 표준 편집기에 대 한 간소화 된 포함 모델을 따릅니다, 그리고 여러 뷰를 지원 하 고 여러 뷰를 관리 하는 데 사용 되는 이벤트 인터페이스를 제공 합니다.

## <a name="document-view-object"></a>문서 뷰 개체
 코드 및 기타 텍스트를 표시 하는 창을 문서 라고 보기 또는 보기입니다. 편집기를 만든 경우 중 하나를 단일 뷰에서 하나의 창에 표시 되는 텍스트를 선택할 수 있습니다. 또는 텍스트 둘 이상의 창에 표시 되는 여러 뷰를 선택할 수 있습니다. 선택한 응용 프로그램에 따라 달라 집니다. 예를 들어 편집 side-by-side-필요한 경우 여러 보기를 선택 합니다. 각 보기 항목 통합된 개발 환경 (IDE) document 테이블 (RDT) 실행에 연결 됩니다. 프로젝트에 속하는 보기 창 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 개체입니다.

 편집기에서 문서 데이터 개체의 여러 뷰를 지 원하는 경우 다음 문서 데이터 및 문서 보기 개체 구분 되어야 합니다. 그렇지 않으면 해당 그룹화 될 수 있습니다. 자세한 내용은 [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)합니다.

 IDE는 실행 중인 문서 테이블의 각 항목에 대 한 항목 식별자 (ItemID)를 비교 하 여 (예: 문서를 포함 하는 솔루션을 닫으면) 이벤트에 대 한 뷰를 알립니다. 이 대 한 자세한 내용은 참조 하세요. [문서 테이블 실행](../extensibility/internals/running-document-table.md)합니다.

 사용자 지정 편집기에 대 한 뷰를 만드는 두 가지 옵션이 있습니다. 하나는 뷰에서 ActiveX 컨트롤 또는 문서 데이터 개체를 사용 하 여 창에서 호스트 되는 내부 활성화 모델입니다. 두 번째는 보기에서 호스트 되는 간단한 포함 모델 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 창 명령을 처리 하기 위해 구현 됩니다. 바로 활성화 모델에 대 한 자세한 내용은 [내부 활성화](../extensibility/in-place-activation.md)합니다. 간단한 포함 모델에 대 한 자세한 내용은 참조 하세요. [간단한 포함](../extensibility/simplified-embedding.md)합니다.

## <a name="see-also"></a>참고자료
- [여러 문서 보기를 지원 합니다.](../extensibility/supporting-multiple-document-views.md)
- [간단한 포함](../extensibility/simplified-embedding.md)
- [방법: 문서 데이터에 보기 연결](../extensibility/how-to-attach-views-to-document-data.md)
- [문서 잠금 소유자 관리](../extensibility/document-lock-holder-management.md)
- [단일 및 다중 탭 보기](../extensibility/single-and-multi-tab-views.md)
- [표준 문서 저장](../extensibility/internals/saving-a-standard-document.md)
- [지 속성 및 문서 테이블 실행](../extensibility/internals/persistence-and-the-running-document-table.md)
- [프로젝트에서 파일을 엽니다는 편집기 결정](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
- [편집기 팩터리](../extensibility/editor-factories.md)