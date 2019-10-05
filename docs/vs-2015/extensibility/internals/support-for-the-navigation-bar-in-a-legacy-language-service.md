---
title: 레거시 언어 서비스의 탐색 모음에 대 한 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cef18951a6ac5494f74c150c4251bafd9597686
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154100"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>레거시 언어 서비스의 탐색 모음 지원
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

편집기 보기의 맨 위에 있는 탐색 모음에서 파일 형식 및 멤버를 표시합니다. 왼쪽된 드롭다운 목록에 표시 됩니다 및 멤버 드롭다운 오른쪽에 표시 됩니다. 사용자가 유형을 선택 하면 형식의 첫 번째 줄에 캐럿 배치 됩니다. 사용자가 멤버를 선택 하면 멤버의 정의에 캐럿 배치 됩니다. 드롭다운 목록 상자 캐럿의 현재 위치를 반영 하도록 업데이트 됩니다.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>표시 및 탐색 모음 업데이트  
 탐색 모음을 지원 하려면 클래스에서 파생 해야 합니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 클래스 및 구현를 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드. 언어 서비스는 코드 창, 기본을 지정 된 경우 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스를 인스턴스화하는 <xref:Microsoft.VisualStudio.Package.CodeWindowManager>를 포함 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 코드 창을 나타내는 개체입니다. 합니다 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 개체는 새 권한을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 개체입니다. 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 개체입니다. 인스턴스를 반환 하는 경우에 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 클래스를 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 호출에 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 나열 하 고 전달 하는 메서드 내부를 채우는 데에 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 개체를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] manager 표시줄 드롭다운 합니다. 드롭다운 표시줄 관리자를 호출 하는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> 메서드를 프로그램 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 설정 하는 개체를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> 두 개의 드롭다운 막대를 보유 하는 개체입니다.  
  
 캐럿 움직이면 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> 메서드 호출을 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 메서드. 기본 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 메서드 호출을 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 에서 메서드 프로그램 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 탐색 표시줄의 상태를 업데이트 하는 클래스입니다. 집합을 전달 하면 <xref:Microsoft.VisualStudio.Package.DropDownMember> 이 메서드는 개체입니다. 각 개체 드롭다운 목록에서 항목을 나타냅니다.  
  
## <a name="the-contents-of-the-navigation-bar"></a>탐색 모음의 내용  
 탐색 모음 일반적으로 형식의 목록 및 멤버의 목록을 포함 합니다. 형식 목록 현재 소스 파일에서 사용할 수 있는 모든 형식을 포함합니다. 전체 네임 스페이스 정보를 포함 하는 형식 이름입니다. 다음은 두 가지 종류를 사용 하 여 C# 코드 예제입니다.  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 형식 목록에 표시 됩니다 `TestLanguagePackage.TestLanguageService` 고 `TestLanguagePackage.TestLanguageService.Tokens`입니다.  
  
 멤버 목록에는 형식 목록에서 선택한 형식의 사용 가능한 멤버가 표시 됩니다. 경우에 위의 코드 예제를 사용 하 여 `TestLanguagePackage.TestLanguageService` 을 선택 하는 형식은 멤버 목록에는 private 멤버 포함 됩니다 `tokens` 및 `serviceName`합니다. 내부 구조 `Token` 표시 되지 않습니다.  
  
 멤버 목록을 그 안에 캐럿 배치 되는 경우 멤버의 이름이 굵게 표시 하려면를 구현할 수 있습니다. 멤버도 표시할 수 있습니다에 회색으로 표시 텍스트를 나타내는 캐럿 현재 위치한 범위 내에서 되지 않은.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>탐색 모음에 대 한 지원을 사용 하도록 설정  
 탐색 모음에 대 한 지원을 사용 하려면 설정 해야 합니다 `ShowDropdownBarOption` 의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 특성을 `true`입니다. 이 매개 변수는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 속성을 설정합니다. 탐색 모음을 지원 하려면 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 개체를 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스.  
  
 구현에서는 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 메서드를 경우는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 속성이로 설정 되어 `true`를 반환할 수 있습니다를 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 개체입니다. 개체를 반환 하지 않는 경우 탐색 모음 표시 되지 않습니다.  
  
 이 컨트롤 편집기 뷰를 열려 있는 상태로 다시 설정할 수 있도록 사용자가 탐색 모음을 표시 하는 옵션을 설정할 수 있습니다. 사용자를 닫고 변경 수행 되기 전에 편집기 창을 다시 열려면 해야 합니다.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>탐색 모음에 대 한 지원 구현  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드는 두 개의 목록 (각 드롭다운에 대해 하나) 및 각 목록에서 현재 선택 영역을 나타내는 두 값을 사용 합니다. 목록과 선택 값을 업데이트할 수 있는 경우에 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드를 반환 해야 `true` 목록 변경 된 것을 나타내려면.  
  
 선택 유형 드롭다운 목록에서에서 변경 되 면 멤버 목록 새 유형을 반영 하도록 업데이트 되어야 합니다. 멤버 목록에 표시 된 항목 일 수 있습니다.  
  
- 현재 형식에 대 한 멤버의 목록입니다.  
  
- 원본에서 사용할 수 있는 모든 멤버 파일에 있지만 현재 형식에 없는 모든 멤버가 포함 된 회색 텍스트로 표시 합니다. 빠른 탐색을 위해 사용할 수 있지만 색은 없음을 나타냅니다 현재 선택 된 형식의 일부로 회색 멤버를 여전히 선택할 수 있습니다.  
  
  구현 된 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드는 일반적으로 다음 단계를 수행 합니다.  
  
1. 소스 파일에 대 한 현재 선언의 목록을 가져옵니다.  
  
     목록을 채우는 방법의 여러 가지가 있습니다. 버전에는 사용자 지정 메서드를 만드는 한 가지 방법은 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService> 를 호출 하는 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 모든 선언의 목록을 반환 하는 사용자 지정 구문 분석 이유를 사용 하 여 메서드. 또 다른 방법은 호출할 수 있습니다는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 에서 직접 메서드는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드를 사용자 지정 구문 분석 합니다. 세 번째 접근법의 선언에 캐시할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 의 마지막 전체 구문 분석 작업에서 반환 하는 클래스를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스는 검색 및는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드.  
  
2. 채우거 나 형식의 목록을 업데이트 합니다.  
  
     형식 목록의 콘텐츠는 소스가 변경 된 경우 또는 현재 캐럿 위치에 따라 형식의 텍스트 스타일을 변경 하려면 선택한 경우 업데이트할 수 있습니다. 이 위치에 전달 되는 참고를 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드.  
  
3. 현재 캐럿 위치에 따라 형식 목록에서 선택 유형을 결정 합니다.  
  
     현재 캐럿 위치를 포함 하는 형식을 찾기 위해 1 단계에서 얻은 선언의 검색 하 고 형식 목록에 해당 항목이 있는 인덱스를 확인 하려면 해당 형식에 대 한 형식 목록을 검색 합니다.  
  
4. 채우거 나 선택한 형식을 기반으로 멤버의 목록을 업데이트 합니다.  
  
     멤버 목록에 현재 표시 되는 항목을 반영 합니다 **멤버** 드롭 다운 합니다. 멤버 목록의 콘텐츠는 소스가 변경 된 경우 선택한 형식의 멤버만 표시 하는 경우 선택한 형식 변경 된 경우 업데이트 해야 합니다. 소스 파일의 모든 멤버를 표시 하려는 경우 목록의 각 멤버의 텍스트 스타일을 현재 선택한 형식의 변경 된 경우 업데이트 해야 합니다.  
  
5. 현재 캐럿 위치에 따라 구성원 목록에서 선택한 멤버를 결정 합니다.  
  
     현재 캐럿 위치를 포함 하는 멤버에 대해 1 단계에서 얻은 선언을 검색 한 다음 멤버 목록에 해당 항목이 있는 인덱스를 확인 하려면 해당 멤버에 대 한 멤버 목록을 검색 합니다.  
  
6. 반환 `true` 목록 또는 목록 중 하나를 선택 영역에 변경 내용을 적용 된 경우.
