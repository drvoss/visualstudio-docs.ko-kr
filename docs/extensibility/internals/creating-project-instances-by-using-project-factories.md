---
title: 프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b6f6dee7850610b222cf26964dd4811fcf79b5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329388"
---
# <a name="create-project-instances-by-using-project-factories"></a>프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기
프로젝트 형식에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용을 *프로젝트 팩터리* 프로젝트 개체의 인스턴스를 만듭니다. 프로젝트 팩터리 cocreatable COM 개체에 대 한 표준 클래스 팩터리와 비슷합니다. 그러나 프로젝트 개체 않습니다 cocreatable; 프로젝트 팩터리를 사용 하 여 만들 수만 있습니다.

 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기존 프로젝트를 로드 하거나에서 새 프로젝트를 만듭니다 때 VSPackage의 구현 프로젝트 팩터리를 호출 하는 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 새 프로젝트 개체를 채우는 데 충분 한 정보를 사용 하 여 IDE를 제공 **솔루션 탐색기**합니다. 새 프로젝트 개체는 또한 IDE에서 시작 하는 모든 관련 UI 작업을 지원 하기 위한 필수 인터페이스를 제공 합니다.

 구현할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 프로젝트에서 클래스에 인터페이스입니다. 일반적으로 자체 모듈에 상주합니다.

 소유자에 의해 집계 되 고 지 원하는 프로젝트에는 해당 프로젝트 파일의 소유자 키를 유지 해야 합니다. 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 메서드는 프로젝트 소유자 키로, 소유 프로젝트 변환 해당 소유자 키 GUID를 호출 하는 프로젝트 팩터리는 `CreateProject` 이 프로젝트 팩터리에서 실제 생성 작업을 수행 하는 메서드.

## <a name="create-an-owned-project"></a>소유 프로젝트 만들기
 소유자는 두 단계로 소유 프로젝트를 만듭니다.

1. 호출 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> 메서드. 소유 프로젝트 입력 제어에 따라 집계 된 프로젝트 개체를 만들 수 있는 기회를 이렇게 `IUnknown`합니다. 소유 프로젝트 내부 전달 `IUnknown` 및 소유자 프로젝트에 다시 집계 된 개체입니다. 소유 프로젝트 내부에 저장할 수 있는 기회를 이렇게 `IUnknown`합니다.

2. 호출 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> 메서드. 호출 하는 대신이 메서드가 호출 될 때 소유 프로젝트에 모든 인스턴스화하지 않습니다 `IVsProjectFactory::CreateProject` 처럼 소유 하지 않는 프로젝트에 대 한 사례입니다. 입력 `VSOWNEDPROJECTOBJECT` 열거형은 일반적으로 집계 된 소유 프로젝트입니다. 소유 프로젝트가이 변수를 사용 하 여 해당 프로젝트 개체가 이미 생성 되었는지 여부를 결정할 수 있습니다 (쿠키 NULL를 동일 하지 않음) 또는 (쿠키 같음 NULL)를 만들어야 합니다.

   프로젝트 형식 GUID cocreatable COM 개체의 CLSID 비슷합니다는 고유한 프로젝트도 식별 됩니다. 일반적으로 한 프로젝트 팩터리를 가질 수 있지만 단일 프로젝트 형식의 인스턴스를 만드는 프로젝트 팩터리 핸들 둘 이상의 프로젝트 형식 GUID를 처리 합니다.

   프로젝트 형식은 특정 파일 이름 확장명을 사용 하 여 연결 됩니다. 사용자를 기존 프로젝트 파일을 열려고 시도 또는 템플릿을 복제 하 여 새 프로젝트를 만들려고 시도 하는 경우 IDE 확장 파일에 사용할지 해당 프로젝트 GUID를 확인할 수 있습니다.

   IDE는 정보를 사용 하 여 시스템 레지스트리에서 IDE 여부를 결정 하기 해야 새 프로젝트를 만들 특정 형식의 기존 프로젝트를 엽니다, 즉시 **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]**  을 확인 하려면 VSPackage 필요한 프로젝트 팩터리 구현입니다. IDE는이 VSPackage를 로드합니다. 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage 메서드를 호출 하 여 IDE를 사용 하 여 해당 프로젝트 팩터리를 등록 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> 메서드.

   기본 메서드를 `IVsProjectFactory` 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, 두 가지 시나리오를 처리 해야 하는: 기존 프로젝트를 열고 새 프로젝트 만들기. 대부분의 프로젝트는 프로젝트 파일에서 해당 프로젝트 상태를 저장합니다. 템플릿 파일의 복사본이 전달 활용 하 여 새 프로젝트를 만들 일반적으로 `CreateProject` 메서드와 여는 복사본입니다. 에 전달 된 프로젝트 파일을 열고 직접 기존 프로젝트에서 인스턴스화된 `CreateProject` 메서드. `CreateProject` 메서드는 필요에 따라 사용자에 게 추가 UI 기능을 표시할 수 있습니다.

   프로젝트 수 없는 파일을 사용할 수도 대신, 데이터베이스 또는 웹 서버를 같은 파일 시스템 이외의 저장소 메커니즘에는 프로젝트 상태를 저장 합니다. 파일 이름 매개 변수를 전달 하는 경우는 `CreateProject` 메서드는 파일 시스템 경로 실제로 아니라 고유한 문자열-URL-프로젝트 데이터를 확인 합니다. 에 전달 되는 템플릿 파일을 복사할 필요가 없습니다 `CreateProject` 실행할 적절 한 생성 시퀀스를 트리거할 수 있습니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)