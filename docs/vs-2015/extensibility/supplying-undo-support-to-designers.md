---
title: 실행 취소 디자이너 지원을 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675334"
---
# <a name="supplying-undo-support-to-designers"></a>디자이너에 실행 취소 지원 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일반적으로 디자이너, 편집기와 같은 코드 요소를 수정 하는 경우 사용자가 최근 변경 내용이 되돌릴 수 있도록 실행 취소 작업을 지원 해야 합니다.  
  
 Visual Studio에서 구현 하는 대부분의 디자이너는 실행 취소 지원 환경에서 자동으로 제공 합니다.  
  
 실행 취소 기능에 대 한 지원을 제공 해야 하는 디자이너 구현 합니다.  
  
- 추상 기본 클래스를 구현 하 여 실행 취소 관리를 제공 합니다. <xref:System.ComponentModel.Design.UndoEngine>  
  
- 구현 하 여 제공 지 속성 및 CodeDOM을 지원 합니다 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> 및 <xref:System.ComponentModel.Design.IComponentChangeService> 클래스입니다.  
  
  디자이너를 사용 하 여 작성 하는 방법은 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]를 참조 하세요 [디자인 타임 지원 확장](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)합니다.  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 에서 기본 실행 취소 인프라를 제공 합니다.  
  
- 실행 취소를 통해 관리 구현이 제공 하는 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 고 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> 클래스입니다.  
  
- 지 속성 및 기본 통해 CodeDOM 지원 제공 <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 고 <xref:System.ComponentModel.Design.IComponentChangeService> 구현 합니다.  
  
## <a name="obtaining-undo-support-automatically"></a>실행 취소 기능을 자동으로 가져오기  
 만든 모든 디자이너 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 자동 및 전체 실행 취소 지원 경우 디자이너:  
  
- 사용을 <xref:System.Windows.Forms.Control> 사용자 인터페이스에 대 한 클래스를 기반으로 합니다.  
  
- 코드 생성 및 지 속성에 대 한 표준 CodeDOM 기반 코드 생성 및 구문 분석 시스템을 사용합니다.  
  
     Visual Studio CodeDOM 지원 사용 하 여 작업에 대 한 자세한 내용은 참조 하세요. [동적 소스 코드 생성 및 컴파일](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>명시적 디자이너 실행 취소 기능을 사용 하는 경우  
 디자이너 뷰 어댑터를 제공한 것 이외의 라고 그래픽 사용자 인터페이스를 사용 하는 경우 자체 실행 취소 관리를 제공 해야 <xref:System.Windows.Forms.Control>합니다.  
  
 이 예가 있습니다 수 제품을 만드는 그래픽 디자인 웹 기반 인터페이스를 사용 하 여 대신 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 그래픽 인터페이스를 기반으로 합니다.  
  
 이러한 경우 하나는 등록 해야 사용 하 여이 뷰 어댑터 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>, 명시적 실행 취소 관리를 제공 합니다.  
  
 디자이너를 사용 하지 않는 경우 CodeDOM 및 지 속성 지원을 제공 해야 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 제공 하는 코드 생성 모델을 <xref:System.CodeDom> 네임 스페이스.  
  
## <a name="undo-support-features-of-the-designer"></a>디자이너 지원 기능을 실행 취소  
 환경 SDK 작업 취소 되지를 사용 하 여 디자이너에서 사용할 수 있는 지원을 제공 하는 데 필요한 인터페이스의 기본 구현을 제공 <xref:System.Windows.Forms.Control> 해당 사용자 인터페이스 또는 표준 CodeDOM 및 지 속성 모델에 대 한 클래스를 기반으로 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 클래스에서 파생 되는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> 클래스의 구현을 사용 하는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 실행 취소 작업을 관리 하는 클래스입니다.  
  
 Visual Studio 디자이너 실행 취소 하는 다음 기능을 제공합니다.  
  
- 여러 디자이너에서 연결 된 실행 취소 기능입니다.  
  
- 구현한 디자이너 내에서 자식 단위 부모와 상호 작용할 수 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> 하 고 <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> 에서 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>합니다.  
  
  제공 하 여 CodeDOM 및 지 속성 지원을 제공 하는 환경 SDK:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 구현으로는 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  A <xref:System.ComponentModel.Design.IComponentChangeService> 제공한는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' 디자인 호스트 합니다.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>환경 SDK 기능을 사용 하 여 작업 취소 지원 제공  
 실행 취소 기능을 가져오려면 다음과 같은 디자이너를 구현 하는 개체 같아야 합니다.  
  
- 인스턴스화 및 인스턴스를 초기화 합니다 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 유효한를 사용 하 여 클래스 <xref:System.IServiceProvider> 구현 합니다.  
  
- 이 <xref:System.IServiceProvider> 클래스는 다음 서비스를 제공 해야 합니다.  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       디자이너를 사용 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CodeDOM serialization 사용 하도록 선택할 수 있습니다 <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 와 함께 제공 되는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 의 구현으로는 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>합니다.  
  
       이 경우에 <xref:System.IServiceProvider> 를 제공 하는 클래스를 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 생성자의 구현으로이 개체를 반환 해야는 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> 클래스입니다.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       기본값을 사용 하 여 디자이너 <xref:System.ComponentModel.Design.DesignSurface> 제공한 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디자인 호스트의 기본 구현을 포함 하도록 보장 합니다 <xref:System.ComponentModel.Design.IComponentChangeService> 클래스.  
  
  구현 하는 디자이너는 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 경우 자동으로 따라 실행 취소 메커니즘 변경 내용을 추적 합니다.  
  
- 통해 속성이 변경 되는 <xref:System.ComponentModel.TypeDescriptor> 개체입니다.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> 이벤트는 실행 취소할 수 있는 변경이 커밋된 경우에 수동으로 생성 됩니다.  
  
- 컨텍스트 내에서 생성 된 디자이너에서 수정 된 <xref:System.ComponentModel.Design.DesignerTransaction>합니다.  
  
- 디자이너의 구현에 의해 제공 된 표준 실행 취소 단위를 사용 하 여 실행 취소 단위를 명시적으로 만들 하기로 <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> 또는 Visual Studio 관련 구현이 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>에서 파생 되는 <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> 제공는 둘 다 구현의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> 고 <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>입니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [디자인 타임 지원 확장](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
