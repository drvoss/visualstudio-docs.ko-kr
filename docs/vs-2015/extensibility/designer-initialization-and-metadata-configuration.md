---
title: 디자이너 초기화 및 메타 데이터 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703065"
---
# <a name="designer-initialization-and-metadata-configuration"></a>디자이너 초기화 및 메타데이터 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램을 다른 처리 하는 도구 특정 디자이너에서 사용 되는 정의 대 한 메커니즘을 제공 하는 디자이너 또는 디자이너 구성 요소에 연결 된 필터 특성과 메타 데이터의 조작 <xref:System.Type> 개체 (예: 데이터 구조 클래스 또는 그래픽 엔터티) 경우 디자이너를 사용할 수 있고 디자이너를 지원 하도록 Visual Studio IDE를 구성 하는 방법 (인스턴스는 **도구 상자** 범주 또는 탭).  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] vspackage는 메타 데이터의 조작 및 디자이너나 디자이너 구성 요소의 초기화의 제어를 용이 하 게 여러 메커니즘을 제공 합니다.  
  
## <a name="initializing-metadata-and-configuration-information"></a>메타 데이터 및 구성 정보를 초기화합니다.  
 요청 시 로드 되므로 Vspackage 수 하지에 의해 로드 된는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디자이너의 인스턴스화 전에 환경입니다. Vspackage가 처리 하는 생성 시 디자이너 또는 디자이너 구성 요소를 구성 하는 데 표준 메커니즘을 사용할 수 없습니다는 따라서는 <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> 이벤트입니다. VSPackage의 인스턴스를 구현 하는 대신는 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 인터페이스를 디자인 화면 확장 이라고 하는 사용자 지정을 제공 하려면 자신을 등록 합니다.  
  
### <a name="customizing-initialization"></a>사용자 지정 초기화  
 디자이너, 구성 요소 또는 디자이너 화면에 사용자 지정 하는 작업에 포함 됩니다.  
  
1. 디자이너 메타 데이터를 수정 하 고 효과적으로 특정 방법 변경 <xref:System.Type> 액세스 되거나 변환 됩니다.  
  
     일반적으로 이렇게 합니다 <xref:System.Drawing.Design.UITypeEditor> 또는 <xref:System.ComponentModel.TypeConverter> 메커니즘입니다.  
  
     예를 들어 때 <xref:System.Windows.Forms>-기반된 디자이너는 초기화 되는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경 수정 합니다 <xref:System.Drawing.Design.UITypeEditor> 에 대 한 <xref:System.Web.UI.WebControls.Image> 디자이너를 사용 하 여 리소스 관리자를 사용 하 여 파일 시스템 보다는 비트맵을 가져오려고 하는 데 사용할 개체입니다.  
  
2. 이벤트 구독 또는 프로젝트 구성 정보를 가져오는 예를 들어, 환경에 통합 합니다. 프로젝트 구성 정보를 가져오고을 확보 하 여 이벤트를 구독할 수는 <xref:System.ComponentModel.Design.ITypeResolutionService> 인터페이스입니다.  
  
3. 적절 한를 활성화 하 여 사용자 환경의 수정 **도구 상자** 범주 또는 인스턴스에 적용 하 여 디자이너의 적용 가능성을 제한 하 여는 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 디자이너 클래스입니다.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Vspackage 디자이너 초기화  
 VSPackage 디자이너 초기화를 처리 해야 합니다.  
  
1. 구현 하는 개체 만들기는 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 클래스입니다.  
  
   > [!NOTE]
   > 합니다 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 클래스와 같은 개체에 구현 되지 해야는 <xref:Microsoft.VisualStudio.Shell.Package> 클래스입니다.  
  
2. 구현 하는 클래스를 등록 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 의 인스턴스를 적용 하 여 VSPackage의 디자이너 확장에 대 한 지원을 제공 하는 것 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>를 <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> 하 고 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage의 구현을 제공 하는 클래스에 <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   모든 디자이너 또는 디자이너 구성 요소를 만들 때마다는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경:  
  
3. 각 등록 된 디자인 화면 확장 공급자에 액세스합니다.  
  
4. 각 디자인 화면 확장 공급자의 인스턴스를 초기화를 인스턴스화하고 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 개체  
  
5. 각 디자인 화면 확장 공급자를 호출 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> 메서드 또는 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> 메서드 적절 하 게 합니다.  
  
   구현 하는 경우는 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 것을 알고 있어야 하는 VSPackage의 멤버인 개체:  
  
6. 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경 메타 데이터에 대 한 제어를 제공 하지 않습니다 또는 기타 구성 설정을 특정 `DesignSurfaceExtension` 공급자의 수정 합니다. 두 개 이상의 수 `DesignSurfaceExtension` 명확한 되 고 최종 수정 충돌 하는 방법으로 같은 디자이너 기능을 수정 하는 공급자입니다. 아닙니다 확정적이 지는 수정 마지막으로 적용 됩니다.  
  
7. 구현의 명시적으로 제한 하는 것이 불가능 합니다 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 개체의 인스턴스를 적용 하 여 특정 디자이너를 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 해당 구현에 합니다. 에 대 한 자세한 **도구 상자** 필터링 항목을 참조 합니다 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 및 <xref:System.ComponentModel.ToolboxItemFilterType>합니다.  
  
## <a name="additional-metadata-provisioning"></a>추가 메타 데이터를 프로 비전  
 VSPackage는 디자인 타임에 디자이너 또는 다른 디자이너 구성 요소 구성을 변경할 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 클래스를 프로그래밍 방식으로 사용할 수 있습니다 또는 디자이너를 제공 하는 VSPackage를 적용할 수 있습니다.  
  
 인스턴스는 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 클래스의 디자인 화면에서 만든 구성 요소 메타 데이터를 수정 하는 데 사용 됩니다. 예를 들어에서 사용 하는 기본 속성 브라우저를 바꿀 수 있습니다 하나 <xref:System.Windows.Forms.CommonDialog> 사용자 지정 속성 브라우저를 사용 하 여 개체입니다.  
  
 인스턴스에 제공 된 수정 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> VSPackage의 구현에 적용할 <xref:Microsoft.VisualStudio.Shell.Package> 두 범위 중 하나일 수 있습니다.  
  
- 지정 된 구성 요소의 모든 새 인스턴스에 대 한 전역-  
  
- 로컬 인스턴스의 현재 VSPackage가 제공 하는 디자인 화면에서 만든 구성 요소에만 관련 됩니다.  
  
  `IsGlobal` 의 속성을 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> VSPackage의 구현에 적용 되는 인스턴스 <xref:Microsoft.VisualStudio.Shell.Package> 이 범위를 결정 합니다.  
  
  구현에 특성을 적용 <xref:Microsoft.VisualStudio.Shell.Package> 사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> 의 속성을 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 개체가 설정 `true`, 전체 브라우저를 아래와 같이 변경 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  전역 플래그 설정한 경우 `false`, 현재 VSPackage에서 지 원하는 현재 디자이너에 로컬 메타 데이터 변경 됩니다.  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> 현 시점 디자인 화면을 만드는 구성 요소를 지원 하 고 따라서 구성 요소만 로컬 메타 데이터를 가질 수 합니다. 위의 예제에서와 같은 속성을 수정 하 려 했던 것을 `Color` 개체의 속성입니다. 하는 경우 `false` 전역 플래그에 대 한 전달 된 `CustomBrowser` 디자이너의 인스턴스를 실제로 만들어지기 때문에 표시 되지 않습니다 `Color`합니다. 전역 플래그 설정을 `false` 컨트롤, 타이머 및 대화 상자와 같은 구성 요소에 대해 유용 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [디자인 타임 지원 확장](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
