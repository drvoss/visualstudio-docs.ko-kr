---
title: '연습: 레거시 언어 서비스 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56323447d1d4134939c8fd7550778d2c946bfe19
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144405"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>연습: 레거시 언어 서비스 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

언어 서비스를 구현 하는 관리 되는 패키지 프레임 워크 (MPF) 언어 클래스를 사용 하 여 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 간단 합니다. 언어 서비스, 자체 언어 서비스 및 언어에 대 한 파서를 호스트 하기 위해 VSPackage 해야 합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 패키지 프로젝트 템플릿의 위치  
 Visual Studio 패키지 프로젝트 템플릿은 세 가지 다른 템플릿 위치에서 찾을 수 있습니다 합니다 **새 프로젝트** 대화 상자:  
  
1. Visual Basic 확장성에 위치한 템플릿 프로젝트의 기본 언어는 Visual Basic입니다.  
  
2. C# 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C#입니다.  
  
3. 다른 프로젝트 형식 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C++입니다.  
  
### <a name="create-a-vspackage"></a>VSPackage를 만듭니다  
  
1. Visual Studio 패키지 프로젝트 템플릿을 사용 하 여 새 VSPackage를 만듭니다.  
  
     언어 서비스는 기존 vspackage를 추가 하는 경우 다음 단계를 건너뛰고 "언어 서비스 클래스 만들기" 절차로 바로 이동 합니다.  
  
2. MyLanguagePackage 프로젝트의 이름을 입력 하 고 클릭 **확인**합니다.  
  
     원하는 어떤 이름을 사용할 수 있습니다. 여기에서 자세히 설명 하는 이러한 프로시저는 이름으로 MyLanguagePackage를 가정 합니다.  
  
3. 선택 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 언어와 새 키 파일을 생성 하는 옵션입니다. **다음**을 클릭합니다.  
  
4. 적절 한 회사 및 패키지 정보를 입력 합니다. **다음**을 클릭합니다.  
  
5. 선택 **메뉴 명령을**합니다. **다음**을 클릭합니다.  
  
     코드 조각 지원 하지 않을 경우 방금 마침을 클릭를 다음 단계를 무시 합니다.  
  
6. 입력 **코드 조각 삽입** 으로 **명령 이름** 및 `cmdidInsertSnippet` 에 대 한 합니다 **명령 ID**합니다. **마침**을 클릭합니다.  
  
     합니다 **명령 이름** 하 고 **명령 ID** 원하는 대로 지정할 수 있으며, 다음은 예제 일 뿐입니다.  
  
### <a name="create-the-language-service-class"></a>언어 서비스 클래스 만들기  
  
1. **솔루션 탐색기**MyLanguagePackage 프로젝트를 마우스 오른쪽 단추로 선택 **추가**를 **참조**를 선택한 후는 **새 참조 추가** 단추입니다.  
  
2. 에 **참조 추가** 대화 상자에서 **Microsoft.VisualStudio.Package.LanguageService** 에 **.NET** 탭을 클릭 **확인**합니다.  
  
     언어 패키지 프로젝트에 대 한 한 번만 수행 해야 합니다.  
  
3. **솔루션 탐색기**VSPackage 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **추가**하십시오 **클래스**.  
  
4. 했는지 **클래스** 템플릿 목록에서 선택 합니다.  
  
5. 입력 **MyLanguageService.cs** 고 클래스 파일의 이름을 **추가**합니다.  
  
     원하는 어떤 이름을 사용할 수 있습니다. 여기에서 자세히 설명 하는 이러한 절차를 가정 `MyLanguageService` 이름으로 합니다.  
  
6. MyLanguageService.cs 파일에 다음 추가 `using` 문입니다.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#1)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#1)]  
  
7. 수정 된 `MyLanguageService` 에서 파생 된 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#2)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#2)]  
  
8. "LanguageService"에 커서를 **편집**를 **IntelliSense** 메뉴에서 **추상 클래스 구현**합니다. 이 언어 서비스 클래스를 구현 하는 데 필요한 최소 메서드를 추가 합니다.  
  
9. 에 설명 된 대로 추상 메서드를 구현 [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)합니다.  
  
### <a name="register-the-language-service"></a>언어 서비스 등록  
  
1. MyLanguagePackagePackage.cs 파일을 열고 다음을 추가 `using` 문:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs#3)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb#3)]  
  
2. 에 설명 된 대로 언어 서비스 클래스를 등록 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)합니다. ProvideXX 특성 및 "언어 서비스 Proffering" 섹션을 포함 합니다. 이 항목에서는 TestLanguageService를 사용 하는 위치 MyLanguageService를 사용 합니다.  
  
### <a name="the-parser-and-scanner"></a>파서 및 검사기  
  
1. 에 설명 된 대로 파서 및 언어에는 스캐너를 구현 [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)합니다.  
  
     프로그램 파서 및 검사기를 구현 하는 방법을 전적으로 사용자 이며이 항목의 범위를 벗어납니다.  
  
## <a name="language-service-features"></a>언어 서비스 기능  
 언어 서비스의 각 기능을 구현 하려면 일반적으로 적절 한 MPF 언어 서비스 클래스에서 클래스를 파생, 필요에 따라 모든 추상 메서드를 구현 및 적절 한 메서드를 재정의 합니다. 지원 하려는 어떤 클래스를 만들고에서 파생 되는 기능에 따라 달라 집니다. 이러한 기능에 대 한 자세한 설명은 [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)합니다. 다음 절차는 일반적인 방법은 MPF 클래스에서 클래스를 파생 하는 것을 방법은입니다.  
  
#### <a name="deriving-from-an-mpf-class"></a>MPF 클래스에서 파생  
  
1. **솔루션 탐색기**VSPackage 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **추가**하십시오 **클래스**.  
  
2. 했는지 **클래스** 템플릿 목록에서 선택 합니다.  
  
     클래스 파일에 대 한 적절 한 이름을 입력 하 고 클릭 **추가**합니다.  
  
3. 새 클래스 파일에서 다음을 추가 `using` 문입니다.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#4)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#4)]  
  
4. 원하는 MPF 클래스에서 파생 되도록 클래스를 수정 합니다.  
  
5. 적어도 기본 클래스의 생성자와 동일한 매개 변수를 사용 하는 클래스 생성자를 추가 하 고 기본 클래스 생성자에 생성자 매개 변수를 전달 합니다.  
  
     예를 들어에서 파생 된 클래스의 생성자를 <xref:Microsoft.VisualStudio.Package.Source> 클래스는 다음과 같습니다.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#5)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#5)]  
  
6. **편집**를 **IntelliSense** 메뉴에서 **추상 클래스 구현** 기본 클래스에 구현 해야 하는 모든 추상 메서드.  
  
7. 그렇지 않은 경우 클래스 내에서 캐럿을 배치 하 고 메서드를 재정의할 수를 입력 합니다.  
  
     예를 들어 입력 `public override` 해당 클래스에서 재정의 될 수 있는 모든 메서드의 목록을 보려면.  
  
## <a name="see-also"></a>관련 항목  
 [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
