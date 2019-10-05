---
title: 간단한 포함 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8e1ac2fa17409ac3228f87eb71c99ce9e725521
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447194"
---
# <a name="simplified-embedding"></a>간단한 포함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

해당 문서 뷰 개체 (즉, 자식 수) 부모가 되는 경우 편집기에서 활성화 되어 단순화 포함 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스 해당 창 명령을 처리 하기 위해 구현 됩니다. 간단한 포함 편집기 활성 컨트롤을 호스팅할 수 없습니다. 간단한 포함 편집기를 만드는 데 개체는 다음 그림에 표시 됩니다.  
  
 ![간단한 포함 편집기 그래픽](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
간단한 포함 편집기  
  
> [!NOTE]
> 만이 그림의 개체는 `CYourEditorFactory` 표준 파일 기반 편집기를 만드는 데 필요한 개체입니다. 사용자 지정 편집기를 만드는 경우는 필요가 없으며 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>편집기에는 자체 전용 지 속성 메커니즘이 있을 때문입니다. 그러나 사용자 지정이 아닌 편집기에 대해 해야 합니다.  
  
 에 포함 된 간단한 포함 편집기를 만들기 위해 구현 하는 모든 인터페이스는 `CYourEditorDocument` 개체입니다. 그러나 문서 데이터의 여러 보기를 지원 하기 위해 분할 별도 데이터와 뷰 개체 인터페이스는 다음 표에 표시 된 대로.  
  
|인터페이스|인터페이스의 위치|사용|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|보기|부모 창에 대 한 연결을 제공합니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|보기|명령을 처리합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|보기|상태 표시줄 업데이트를 사용하도록 설정합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|보기|사용 하도록 설정 **도구 상자** 항목입니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|데이터|파일 변경 되 면 알림을 보냅니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|데이터|파일 형식으로 저장 기능을 사용 하도록 설정 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|데이터|문서에 대해 지속성을 사용하도록 설정합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|데이터|다시 로드 트리거 같은 파일 변경 이벤트의 제거를 허용합니다.|
