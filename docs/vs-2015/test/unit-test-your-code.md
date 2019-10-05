---
title: 코드 단위 테스트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1e6f0dd19c9d5d3ea1ee28a267aa969aad638948
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695214"
---
# <a name="unit-test-your-code"></a>코드 단위 테스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개발자와 테스터는 단위 테스트를 통해 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] 및 [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)] 프로젝트에서 클래스의 메서드에 있는 논리 오류를 빠르게 찾을 수 있습니다.  
  
 단위 테스트 도구는 다음과 같습니다.  
  
1. **테스트 탐색기.** 테스트 탐색기에서는 단위 테스트를 실행하고 그 결과를 볼 수 있습니다. 테스트 탐색기에서는 타사 프레임워크를 비롯하여 탐색기용 어댑터가 있는 모든 단위 테스트 프레임워크를 사용할 수 있습니다.  
  
2. **관리 코드용 Microsoft 단위 테스트 프레임워크.** 관리 코드용 Microsoft 단위 테스트 프레임워크는 Visual Studio와 함께 설치되며 .NET 코드 테스트용 프레임워크를 제공합니다.  
  
3. **C++용 Microsoft 단위 테스트 프레임워크.** C++용 Microsoft 단위 테스트 프레임워크는 Visual Studio와 함께 설치되며 네이티브 코드 테스트용 프레임워크를 제공합니다.  
  
4. **코드 검사 도구.** 단위 테스트가 테스트 탐색기의 명령 하나에서 실행하는 제품 코드의 양을 결정할 수 있습니다.  
  
5. **Microsoft Fakes 격리 프레임워크.** Microsoft Fakes 격리 프레임워크는 테스트 중인 코드에서 종속성을 만드는 프로덕션 및 시스템 코드에 대한 대체 클래스 및 메서드를 만들 수 있습니다. 함수에 대한 모조 위임을 구현하여 종속성 개체의 동작과 출력을 제어할 수 있습니다.  
  
   [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md)를 사용하면 .NET 코드를 탐색하여 테스트 데이터 및 단위 테스트 도구 모음을 생성할 수도 있습니다. 코드의 모든 문에 대해 해당 문을 실행할 테스트 입력이 생성됩니다. 코드의 모든 조건부 분기에 대해 사례 분석이 수행됩니다.  
  
## <a name="key-tasks"></a>주요 작업  
 다음 항목은 단위 테스트를 이해하고 만드는 데 유용합니다.  
  
|작업|관련 항목|  
|-----------|-----------------------|  
|**빠른 시작 및 연습:** 다음 항목을 사용하여 코드 예제에서 Visual Studio의 단위 테스트에 대해 알아봅니다.|-   [연습: 관리 코드의 단위 테스트 만들기 및 실행](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).<br />-   [빠른 시작: 테스트 탐색기를 사용한 테스트 기반 개발](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [기존 C++ 애플리케이션에 단위 테스트 추가](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [테스트 탐색기를 사용하여 네이티브 코드 단위 테스트](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**테스트 탐색기를 사용한 단위 테스트:** 테스트 탐색기를 통해 보다 다 생산적이고 효율적인 단위 테스트를 만드는 방법에 대해 알아봅니다.|-   [단위 테스트 기본 사항](../test/unit-test-basics.md)<br />-   [단위 테스트 프로젝트 만들기](../test/create-a-unit-test-project.md)<br />-   [테스트 탐색기를 사용하여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)<br />-   [타사 단위 테스트 프레임워크 설치](../test/install-third-party-unit-test-frameworks.md)<br />-   [Visual Studio 2010에서 단위 테스트 업그레이드](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**관리 코드 단위 테스트:**|-   [관리 코드용 Microsoft 단위 테스트 프레임워크를 사용하여 .NET Framework용 단위 테스트 작성](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**C++ 코드 단위 테스트**|-   [C++용 Microsoft 단위 테스트 프레임워크를 사용하여 C/C++용 단위 테스트 작성](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**단위 테스트 격리**|-   [Microsoft Fakes를 사용하여 테스트 중인 코드 격리](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**단위 테스트를 사용 하 여 테스트 되는 프로젝트의 코드는 부분 식별을 사용 하 여 코드 검사:** 코드 검사 기능을 알아보려면 [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] 도구를 테스트 합니다.|-   [코드 검사를 사용하여 테스트할 코드 범위 결정](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**단위 테스트에 대 한 부하 테스트를 사용 하 여 스트레스 및 성능 분석을 수행 합니다.** 애플리케이션에서 성능 및 스트레스 문제를 격리하기 위해 부하 테스트를 만들고 여기에 단위 테스트를 추가할 수 있습니다. **참고:**  부하 테스트를 만들고 사용하려면 Visual Studio Enterprise가 필요합니다.|-   [부하 테스트 만들기 및 편집](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [방법: 부하 테스트 시나리오에 웹 성능 테스트 및 단위 테스트 추가](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [방법: 부하 테스트 시나리오에서 웹 성능 테스트 및 단위 테스트 제거](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**설정 하 고 품질 게이트를 적용 합니다.** 품질 게이트를 코드의 품질을 보장 하도록 코드를 체크 인하기 전에 테스트가 실행 되는 만들 수 있습니다.|-   [품질 게이트 설정 및 적용](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**단위 테스트 형식 확장:** 단위 테스트 프레임 워크에 없을 수도 있는 테스트에 기능을 추가할 수 있습니다. 예를 들어 테스트를 일반 사용자로 실행할지 여부를 지정하는 테스트 속성을 추가할 수 있습니다. 또는 프레임워크를 확장하여 메서드에 행 특성을 추가하고 테스트에서 이 행의 데이터를 사용할 수 있습니다.|단위 테스트 프레임워크를 확장하는 방법에 대한 예제 코드는 다음 [Microsoft 웹 사이트](http://go.microsoft.com/fwlink/?LinkId=185591)를 참조하세요.|  
|**테스트 옵션 설정:** 예를 들어 테스트 결과가 저장되는 위치를 지정할 수 있습니다.|[.runsettings 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>관련 작업  
 [Microsoft Test Manager에서 테스트 결과 검토](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 테스트 결과에 대해 설명하고, 테스트 결과 보기, 저장 및 삭제 방법을 비롯하여 테스트 결과의 사용 방법에 대해 설명합니다.  
  
 [Microsoft Visual Studio를 사용하여 시스템 테스트 실행](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130).  
  
 Visual Studio를 사용하여 자동화된 테스트를 실행하는 방법을 [!INCLUDE[TCMext](../includes/tcmext-md.md)]를 사용할 경우와 비교하여 설명하는 항목에 대한 링크를 제공합니다.  
  
## <a name="reference"></a>참조  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 유닛 테스트를 지원하는 특성, 예외, 어설션 및 기타 클래스를 제공하는 UnitTesting 네임스페이스에 대해 설명합니다.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 및 웹 서비스 단위 테스트를 지원하여 UnitTesting 네임스페이스를 확장하는 UnitTesting.Web 네임스페이스에 대해 설명합니다.  
  
## <a name="external-resources"></a>외부 리소스  
  
### <a name="videos"></a>비디오  
 [채널 9: XAML을 사용 하 여 빌드된 Windows 스토어 앱 유닛 테스트](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>포럼  
 [Visual Studio 단위 테스트](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>지침  
 [Visual Studio 2012 – Chapter 2를 사용한 연속 배달 테스트: 단위 테스트: 내부 테스트](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>참조  
 [단위 테스트에 대한 콘텐츠 인덱스](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>참고 항목  
 [코드 품질 향상](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [애플리케이션 테스트](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
