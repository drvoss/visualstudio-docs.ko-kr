---
title: 옵션 페이지 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d46055f14fdd1852e77ee78062548e5164140a3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340673"
---
# <a name="create-options-pages"></a>옵션 페이지 만들기
에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 관리 패키지 프레임 워크 클래스에서 파생 된 <xref:Microsoft.VisualStudio.Shell.DialogPage> 확장을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 추가 하 여 IDE **옵션** 아래 페이지를 **도구** 메뉴.

 구현 하는 개체를 지정 **도구 옵션** 페이지에서 특정 Vspackage와 사용 하 여 연결 된 된 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 개체입니다.

 환경 특정 구현 하는 개체를 인스턴스화하고 때문 **도구 옵션** 해당 특정 페이지 IDE에 의해 표시 되 면 페이지:

- A **도구 옵션** VSPackage를 구현 하는 개체 아닌 자체의 개체에 페이지를 구현 해야 합니다.

- 개체를 여러 개 구현할 수 없습니다 **도구 옵션** 페이지입니다.

## <a name="register-as-a-tools-options-page-provider"></a>도구 옵션 페이지 공급자로 등록
 통해 지 원하는 사용자 VSPackage 구성을 **도구 옵션** 페이지 제공 하는 이러한 개체를 나타냅니다 **도구 옵션** 의 인스턴스를 적용 하 여 페이지 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 합니다 적용할<xref:Microsoft.VisualStudio.Shell.Package>구현입니다.

 인스턴스가 하나 있어야 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 에 대 한 모든 <xref:Microsoft.VisualStudio.Shell.DialogPage>-파생 형식을 구현 하는 **도구 옵션** 페이지.

 인스턴스마다 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 구현 하는 형식을 사용 하는 **도구 옵션** 페이지 범주와 하위 범주를 식별 하는 데 포함 하는 문자열을 **도구 옵션** 페이지 및 리소스 제공 된 형식을 등록 하는 정보를 **도구 옵션** 페이지입니다.

## <a name="persist-tools-options-page-state"></a>도구 옵션 페이지 상태를 유지 합니다.
 경우는 **도구 옵션** 자동화 지원이 설정 된 페이지 구현을 등록 되 면 다른 모든 함께 페이지의 상태를 유지 하는 IDE **도구 옵션** 페이지입니다.

 VSPackage를 사용 하 여 자체 지 속성을 관리할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>합니다. 하나만 또는 지 속성의 다른 메서드를 사용 해야 합니다.

## <a name="implement-dialogpage-class"></a>DialogPage 클래스 구현
 VSPackage의 구현을 제공 하는 개체는 <xref:Microsoft.VisualStudio.Shell.DialogPage>-파생된 형식 상속 된 다음 기능을 활용을 걸릴 수 있습니다.

- 기본 사용자 인터페이스 창입니다.

- 기본 지 속성 메커니즘을 사용할 수 있는 경우 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 클래스에 적용 됩니다 또는 경우에는 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> 속성이로 설정 되어 `true` 에 대 한는 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 클래스에 적용 되는 합니다.

- 자동화 지원 합니다.

  구현 하는 개체에 대 한 최소 요구 사항을 **도구 옵션** 페이지를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.DialogPage> 추가 public 속성입니다.

  클래스도 올바르게 등록 하는 경우를 **도구 옵션** 공용 속성에 사용할 수 있는 공급자 페이지는 **옵션** 섹션을 **도구** 형식의 메뉴를 속성 표입니다.

  이러한 모든 기본 기능을 재정의할 수 있습니다. 예를 들어, 더 복잡 한 사용자를 만들려면 인터페이스를 사용 하려면의 기본 구현만 재정의 <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>합니다.

## <a name="example"></a>예제
 그 뒤에 나오는 옵션 페이지의 간단한 "Hello world" 구현입니다. Visual Studio 패키지 템플릿을 사용 하 여 만든 기본 프로젝트에 다음 코드를 추가 합니다 **메뉴 명령을** 옵션을 선택 옵션 페이지 기능을 보여 줍니다 적절 하 게 됩니다.

### <a name="description"></a>설명
 다음 클래스에는 최소한의 "Hello world" 옵션 페이지를 정의합니다. 공용 설정 하면 열리면 `HelloWorld` 속성 표에 속성입니다.

### <a name="code"></a>코드
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>설명
 패키지 클래스에 다음 특성을 적용 하면 페이지 옵션 사용할 패키지를 로드 하는 경우. 숫자는 범주 및 페이지에 대 한 임의의 리소스 Id 및 끝에 부울 값을 페이지 자동화를 지원 하는지 여부를 지정 합니다.

### <a name="code"></a>코드
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>설명
 다음 이벤트 처리기를 옵션 페이지에서 설정 된 속성의 값에 따라 결과를 표시 합니다. 사용 된 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 결과 사용 하 여 메서드를 명시적으로 페이지에 의해 노출 된 속성에 액세스 하려면 사용자 지정 옵션 페이지 형식으로 캐스팅 합니다.

 패키지 템플릿으로 생성 하는 프로젝트의 경우에서이 함수를 호출 합니다 `MenuItemCallback` 기본 명령에 연결 하는 함수에 추가 합니다 **도구** 메뉴.

### <a name="code"></a>코드
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>참고자료
- [사용자 설정 및 옵션 확장](../../extensibility/extending-user-settings-and-options.md)
- [Automation 옵션 페이지에 대 한 지원](../../extensibility/internals/automation-support-for-options-pages.md)