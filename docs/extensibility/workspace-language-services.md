---
title: 작업 영역 및 Visual Studio에서 언어 서비스 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952707"
---
# <a name="workspaces-and-language-services"></a>작업 영역 및 언어 서비스

언어 서비스를 제공할 수 있습니다 [폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 사용자 같은 다양 한 언어 기능에 사용 되는 때 자신이 솔루션 및 프로젝트를 사용 하 여 작업 합니다. 언어 서비스 자체를 활성화할 수 있습니다이 "느슨한 파일" 언어 서비스는 구문 강조 표시를 제한 하지만 파일 확장명 또는 열린 문서의 콘텐츠를 기반 합니다. 소스 코드를 편집/검토할 때 보다 풍부한 환경을 제공 하는 추가 정보가 필요 합니다. 각 언어 서비스는 문서에 대 한 추가 컨텍스트이 데이터를 사용 하 여 초기화에 대 한 고유한 API. 이 일반적으로 언어 서비스와 빌드 시스템에 밀접 하 게 결합 되는 프로젝트 시스템으로 관리 됩니다.

## <a name="initialization"></a>초기화

에 [작업 영역](workspaces.md), 언어 서비스에 의해 초기화 됩니다는 <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 전문 언어 서비스에만 빌드 제작 중 아무 것도 인식 하는 확장 지점입니다. 따라서에서 언어 서비스 소유자를 단일 폴더 열기 (예를 들어 MSBuild, 메이크파일 등)을 빌드하는 동안 해당 컴파일러를 실행 하는 것에 대 한 파일과 폴더 내에 얼마나 많은 패턴에 관계 없이 확장 존재를 유지할 수 있습니다. 파일 컨텍스트 새로 고쳐집니다 디스크에서 파일 컨텍스트를 생성 된 파일이 변경 되 고 언어 서비스 공급자의 업데이트 된 파일 컨텍스트 집합 알립니다. 언어 서비스 공급자의 모델을 업데이트할 수 있습니다.

편집기에서 문서를 열면 Visual Studio만 고려할 것인지 언어 일치 하는 파일 컨텍스트 공급자를 찾을 수 있는 파일 상황에 맞는 형식이 필요로 하는 서비스 공급자입니다. 그런 다음 전달 파일 컨텍스트 일치 하는 공급자를 통해 선택한 언어 서비스 공급자에 `ILanguageServiceProvider.InitializeAsync`입니다. 파일 상황에 맞는 데이터는 언어 서비스 공급자의 세부 구현 이지만 예상 되는 사용자 환경에 대 한 다양 한 언어 서비스의 언어 서비스 공급자를가 사용 하 여 열 문서.

## <a name="using-ilanguageserviceprovider"></a>ILanguageServiceProvider를 사용 하 여

파일 컨텍스트를 사용 하 여 만들어집니다 경우 알림을 받을 언어 서비스는 `ContextType` 중 하 나와 일치 하는 `SupportedContextTypes` 언어 서버의 값 내보내기 특성입니다.

언어 서비스를 지원 하기 위해 확장 해야 합니다.

- 고유한 `Guid`합니다. 이 대 한 사용 됩니다 `SupportedContextTypes` 인수를 특성 및는 `FileContext` 개체입니다.
- 언어 파일 컨텍스트
  - 공급자 팩터리
    - `ExportFileContextProviderAttribute` 위의 특성을 고유 하 게 생성 `Guid` 에서 `SupportedContextTypes`
    - 구현 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 공급자 구현 `IFileContextProvider.GetContextsForFileAsync`
    - 새 생성 `FileContext` 사용 하 여는 `contextType` 고유 하 게 생성 된 생성자 인수 `Guid`
    - 사용 하 여는 `Context` 의 속성을 `FileContext` 추가 데이터를 제공 하는 `ILanguageServiceProvider`
- 언어 서비스
  - 공급자 팩터리
    - `ExportLanguageServiceProvider` 위의 특성을 고유 하 게 생성 `Guid` 에서 `SupportedContextTypes`
    - 구현 `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - 공급자
    - 구현 `ILanguageServiceProvider`
    - 사용 하 여 `ILanguageServiceProvider.InitializeAsync` 파일을 열 때 제공된 된 인수에 대 한 언어 서비스를 사용 하도록 설정 하려면
    - 사용 하 여 `ILanguageServiceProvider.UninitializeAsync` 파일로 닫힐 때 제공된 된 인수에 대 한 언어 서비스를 사용 하지 않도록 설정

>[!WARNING]
>`ILanguageServiceProvider` 주 스레드에서 작업 영역에서 메서드를 호출할 수 있습니다. UI가 지연 시 키 지 않도록 하는 다른 스레드에서 작업을 예약 하는 것이 좋습니다.

## <a name="language-server-protocol"></a>언어 서버 프로토콜

`Microsoft.VisualStudio.Workspace.*` Api 폴더 열기에서 언어 서비스를 사용 하도록 설정 하는 유일한 방법도 아닙니다. 언어 서버를 사용 하는 방법도 있습니다. 에 대 한 자세한 내용은 참조는 [언어 서버 프로토콜](language-server-protocol.md)합니다.

## <a name="related-interfaces"></a>관련된 인터페이스

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 일치 하는 파일 형식 파일로 열거나 편집을 위해 닫을 때 호출 됩니다.

## <a name="next-steps"></a>다음 단계

* [작업 영역 빌드](workspace-build.md) -폴더 열기에서 지 원하는 MSBuild 및 메이크파일와 같은 시스템을 구축 합니다.