---
title: 배포를 다른 사용자에 대 한 ClickOnce 응용 프로그램 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff76fe46f07ef713cb3c0e529e8029730450f2a6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675596"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>다른 사용자가 배포할 수 있는 ClickOnce 애플리케이션 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 배포를 만든 모든 개발자가 응용 프로그램 자체를 배포 하려고 합니다. 이들 중 다 수만 ClickOnce를 사용 하 여 해당 응용 프로그램을 패키지 및 같은 규모가 큰 기업 고객에 게 파일을 전달 합니다. 고객이 네트워크에서 응용 프로그램을 호스트 하는 일을 담당 합니다. 이 항목에서는.NET framework 버전 3.5 이전 버전에서 이러한 배포의 문제 중 일부를 설명합니다. .NET Framework 3.5의 새로운 "트러스트에 대 한 매니페스트를 사용" 기능을 사용 하 여 제공 하는 새 솔루션에 설명 합니다. 마지막으로, 이전 버전의.NET Framework를 여전히 사용 하는 고객에 대 한 ClickOnce 배포를 만들기 위한 권장 되는 전략을 사용 하 여 완료 합니다.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>고객에 대 한 배포 만들기와 관련 된 문제  
 몇 가지 문제는 배포를 고객에 게 제공 하려는 경우 발생 합니다. 첫 번째 문제는 코드 서명 관련이 있습니다. 네트워크를 통해 배포 하기 위해 배포 매니페스트와 응용 프로그램 매니페스트는 ClickOnce 배포 둘 다 서명 되어야 합니다는 디지털 인증서를 사용 하 여. 이 매니페스트를 서명할 때 개발자 인증서 또는 고객의 인증서를 사용할 것인지에 대 한 문제를 발생 시킵니다.  
  
 ClickOnce 응용 프로그램의 id는 배포 매니페스트의 디지털 서명을 기준으로 인증서를 사용 하 여 질문은 매우 중요 합니다. 배포 매니페스트에 서명 하는 개발자, 고객은 큰 회사 및 회사의 여러 부서 응용 프로그램의 사용자 지정된 버전을 배포 하는 경우 충돌이 발생할 수 있습니다.  
  
 예를 들어 Adventure Works 재무 부서 및 인적 자원 부서에 가정해 보겠습니다. 두 부서에는 SQL 데이터베이스에 저장 된 데이터에서 보고서를 생성 하는 Microsoft Corporation에서 ClickOnce 응용 프로그램을 라이선스. Microsoft는 해당 데이터에 대 한 사용자 지정 된 응용 프로그램의 버전을 사용 하 여 각 부서를 제공 합니다. 동일한 Authenticode 인증서를 사용 하 여 응용 프로그램은 서명 하는 경우 응용 프로그램을 모두 사용 하려고 하는 사용자 ClickOnce는 첫 번째와 동일한 것으로 두 번째 응용 프로그램을 인식 하는 것 처럼 오류가 발생 합니다. 이 경우 고객이 예기치 않은 결과가 응용 프로그램에서 로컬로 저장 된 데이터가 손실 되는 발생할 수 있습니다.  
  
 또 다른 문제는 관련 코드 서명 하는 `deploymentProvider` 배포 매니페스트에서 ClickOnce 응용 프로그램 업데이트를 검색할 수 있는 위치를 지시 하는 요소입니다. 이 요소를 서명 하기 전에 배포 매니페스트에 추가 해야 합니다. 이 요소는 나중에 추가 되 면 배포 매니페스트에 다시 서명 해야 합니다.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>배포 매니페스트에 서명 하는 고객 요구  
 고유 하지 않은 배포의이 문제를 해결 하려면 개발자 로그인 응용 프로그램 매니페스트는 및 고객 배포 매니페스트에 서명 합니다. 이 방법은 작동 하는 동안 다른 문제 소개 합니다. Authenticode 인증서를 보호 된 자산을 유지 해야 하므로 고객 배포에 서명 하려면 개발자에 게 인증서를 바로 제공할 수 없습니다. 고객 수 배포 매니페스트에 서명 자체는.NET Framework SDK를 사용 하 여 자유롭게 사용할 수 있는 도구를 사용 하 여는 동안이 고객을 제공할 수 또는 부재를 보다 기술적 지식이 해야 합니다. 이러한 경우 개발자는 응용 프로그램, 웹 사이트 또는 고객 수 서명 응용 프로그램의 해당 버전을 제출 하는 데는 다른 메커니즘에 일반적으로 만듭니다.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>ClickOnce 응용 프로그램 보안에 서명 하는 고객의 영향  
 개발자와 고객이 고객 응용 프로그램 매니페스트를 서명 해야 동의 하는 경우에이 신뢰할 수 있는 응용 프로그램 배포에 적용 될 때에 특히 응용 프로그램의 id를 둘러싸고 있는 다른 문제가 발생 합니다. (이 기능에 대 한 자세한 내용은 참조 하세요. [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) 예를 들어 Adventure Works는 Microsoft Corporation에서 제공 하는 모든 응용 프로그램 완전 신뢰로 실행 되도록 클라이언트 컴퓨터를 구성 하려고 합니다. 배포 매니페스트에 서명 하는 Adventure Works, ClickOnce 응용 프로그램의 신뢰 수준을 확인 하려면 Adventure Work 보안 시그니처를 사용 합니다.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>트러스트에 대 한 응용 프로그램 매니페스트를 사용 하 여 고객 배포를 만들기  
 .NET Framework 3.5에서 ClickOnce 매니페스트에 서명 하는 방법의 시나리오에 개발자와 고객이 새 솔루션을 제공 하는 새로운 기능을 포함 합니다. ClickOnce 응용 프로그램 매니페스트 라는 새 요소를 지 원하는 `<useManifestForTrust>` 개발자의 응용 프로그램 매니페스트 디지털 서명을 신뢰 결정에 사용 해야 임을 나타낼 수 있도록 합니다. ClickOnce 패키징 도구를 사용 하는 개발자-Visual Studio, Mage.exe 및 MageUI.exe, 등-응용 프로그램 매니페스트에서이 요소를 포함할 뿐만 아니라 매니페스트에서 해당 게시자 이름과 응용 프로그램의 이름을 포함 합니다.  
  
 사용 하는 경우 `<useManifestForTrust>`, 배포 매니페스트는 인증 기관에서 발급 된 Authenticode 인증서로 서명할 필요가 없습니다. 대신 사용 하 여 자체 서명 된 인증서로 서명할 수 있습니다. 자체 서명 된 인증서는 표준.NET Framework SDK 도구를 사용 하 여 고객 또는 개발자에서 생성 되 고 그런 다음 표준 ClickOnce 배포 도구를 사용 하 여 배포 매니페스트를 적용할 합니다. 자세한 내용은 [Makecert.exe (인증서 작성 도구)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)합니다.  
  
 자체 서명 된 인증서를 사용 하 여 배포 매니페스트에 대 한 여러 가지 이점을 제공 합니다. 자신의 Authenticode 인증서를 만들거나 가져와야 고객에 대 한 필요를 없애 `<useManifestForTrust>` 개발자가 응용 프로그램의 고유한 브랜드 id를 유지 하면서 고객에 대 한 배포를 간소화 합니다. 결과 더 안전 하 고 고유한 응용 프로그램 id는 서명 된 배포의 집합. 여러 고객에 게 동일한 응용 프로그램 배포에서 발생할 수 있는 잠재적인 충돌을 제거 합니다.  
  
 ClickOnce 배포를 만드는 방법에 대 한 단계별 정보에 대 한 `<useManifestForTrust>` 참조 설정 [연습: 다시 서명 하는 필요가 없고 브랜드 정보가 유지 되는 ClickOnce 응용 프로그램 수동 배포](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)합니다.  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>런타임 시 트러스트 작동에 대 한 응용 프로그램 매니페스트  
 런타임 시 응용 프로그램 매니페스트를 사용 하 여 신뢰의 작동 방식을 더 잘 이해를 가져오려면 다음 예제를 살펴보겠습니다. .NET Framework 3.5를 대상으로 하는 ClickOnce 응용 프로그램은 Microsoft에서 생성 됩니다. 사용 하 여 응용 프로그램 매니페스트는 `<useManifestForTrust>` 요소 Microsoft에서 서명 됩니다. Adventure Works는 자체 서명 된 인증서를 사용 하 여 배포 매니페스트를 서명 합니다. Adventure Works 클라이언트는 Microsoft에서 서명 하는 모든 응용 프로그램을 신뢰 하도록 구성 됩니다.  
  
 사용자가 배포 매니페스트에 대 한 링크를 클릭 하면 ClickOnce 응용 프로그램 사용자의 컴퓨터에 설치 합니다. 인증서 및 배포 정보를 고유 하 게 클라이언트 컴퓨터의 ClickOnce 응용 프로그램을 식별 합니다. 사용자를 다른 위치에서 동일한 응용 프로그램을 다시 설치 하려고 ClickOnce이이 id를 사용 하 여 클라이언트에 응용 프로그램이 이미 존재 하는지 결정할 수 있습니다.  
  
 다음으로, ClickOnce ClickOnce는 권한을 부여 하는 신뢰 수준을 결정 하는 응용 프로그램 매니페스트에 서명 하는 데 사용 되는 Authenticode 인증서를 검사 합니다. Adventure Works가 Microsoft에서 서명 하는 모든 응용 프로그램을 신뢰 하도록 클라이언트를 구성한 후이 ClickOnce 응용 프로그램에 완전 신뢰가 부여 됩니다. 자세한 내용은 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)을 참조하십시오.  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>이전 버전에 대 한 고객 배포 만들기  
 그렇다면 개발자 이전 버전의.NET Framework를 사용 하는 고객에 게 ClickOnce 응용 프로그램 구축는 무엇입니까? 다음 섹션에서는 몇 가지 권장 되는 솔루션을 함께 각각의 장단점 요약 되어 있습니다.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>고객을 대신 하 여 배포에 서명  
 가능한 배포 전략 중 하나는 고객의 개인 키를 사용 하 여 고객을 대신 하 여 배포를 서명 하는 메커니즘을 만드는 개발자입니다. 이렇게 하면 개발자 개인 키 또는 여러 개의 배포 패키지를 관리 하지 않아도 됩니다. 개발자는 각 고객에 게 동일한 배포만 제공합니다. 서명 서비스를 사용 하 여 해당 환경에 맞게 고객 책임 이라는 것입니다.  
  
 이 방법 한 가지 단점은 시간 및 구현 하는 데 필요한 비용입니다. 이러한 서비스는.NET Framework SDK에서 제공 하는 도구를 사용 하 여 빌드할 수 있지만 제품 수명 주기를 더 많은 개발 시간이 추가 됩니다.  
  
 이 항목의 앞부분에서 설명 했 듯이 또 다른 단점은 각 고객의 응용 프로그램 버전 충돌이 발생할 수 있는 동일한 응용 프로그램 id를 되어입니다. 중요 한 경우 개발자는 각 응용 프로그램에 고유한 이름을 배포 매니페스트를 생성할 때 사용 되는 이름 필드를 변경할 수입니다. 응용 프로그램의 각 버전에 대 한 별도 id를 만들 되 고 id가 충돌할 가능성이 제거 됩니다. 이 필드에 해당 하는 `-Name` Mage.exe 및 인수를 **이름** 필드에 **이름** MageUI.exe에서 탭 합니다.  
  
 예를 들어, 개발자 Application1 라는 응용 프로그램을 만들었음을 가정해 보겠습니다. Application1로 이름 필드를 사용 하 여 단일 배포를 만드는 대신 개발자는 고객별 변형 Application1-CustomerA에 Application1-CustomerB 등이 이름을 사용 하 여 여러 배포를 만들 수 있으며 등.  
  
### <a name="deploy-using-a-setup-package"></a>설치 패키지를 사용 하 여 배포  
 두 번째 가능한 배포 전략을 ClickOnce 응용 프로그램의 초기 배포를 수행 하는 Microsoft 설치 프로젝트를 생성 하는 것입니다. 여러 가지 형식 중 하나에서 값이 제공 될 수 있습니다: 설치 실행 파일을 MSI 배포 형태로 (합니다. EXE) 또는 일괄 처리 스크립트를 함께 캐비닛 (.cab) 파일로.  
  
 이 방법을 사용할 경우 개발자는 제공 고객 응용 프로그램 파일, 응용 프로그램 매니페스트 및 템플릿으로 사용 되는 배포 매니페스트를 포함 하는 배포 합니다. 고객은 메시지가 표시 하는 배포 URL (서버 또는 파일 공유 사용자는 ClickOnce 응용 프로그램을 설치 하는 위치)에 대 한 디지털 인증서 설치 프로그램을 실행 합니다. 설치 응용 프로그램 업데이트 확인 간격 같은 추가 ClickOnce 구성 옵션을 묻는 수도 있습니다. 이 정보를 수집 되 면 설치 프로그램은 실제 배포 매니페스트를 생성, 서명 하 고, 및 ClickOnce 응용 프로그램을 지정 된 서버 위치에 게시  
  
 세 가지 방법으로 고객이이 상황에서 배포 매니페스트를 서명할 수 있습니다.  
  
1. 고객 인증 기관 (CA)에서 발급 한 올바른 인증서를 사용할 수 있습니다.  
  
2. 이 접근 방식에 대 한 변형, 고객이 자체 서명 된 인증서를 사용 하 여 해당 배포 매니페스트에 서명 하도록 선택할 수 있습니다. 이 단점은 사용자는 것인지 묻는 메시지가 나타나면 설치 하는 경우 "알 수 없는 게시자" 단어를 표시 하려면 응용 프로그램을 하면 된다는입니다. 그러나 혜택을 작은 고객을 인증 기관에서 발급 한 인증서에 필요한 비용을 들이지 않아도 하지.  
  
3. 마지막으로, 개발자가 설치 패키지에 자신의 자체 서명 된 인증서를 포함할 수 있습니다. 이 항목의 앞부분에서 설명한 응용 프로그램 id 사용 하 여 문제가 도입 되었습니다.  
  
   설치 배포 프로젝트 메서드에 단점은 시간이 나 사용자 지정 배포 응용 프로그램을 빌드하는 데 필요한 비용입니다.  
  
### <a name="have-customer-generate-deployment-manifest"></a>고객 배포 매니페스트를 생성 포함  
 세 번째 가능한 배포 전략을 전달 하는 데 응용 프로그램 파일 및 응용 프로그램 매니페스트 해제 되어 고객에 게 있습니다. 이 시나리오에서 고객은.NET Framework SDK를 사용 하 여 생성 및 배포 매니페스트에 서명 하는 일을 담당 합니다.  
  
 이 방법의 단점은 고객은.NET Framework SDK tools를 설치 하 고 개발자 또는 시스템 관리자 사용에 능숙 할 필요 하다는 것입니다. 일부 고객은 솔루션에서 기술 작업이 거의 또는 전혀 필요을 요구할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [테스트에 대 한 ClickOnce 응용 프로그램을 배포 하 고 다시 서명 하지 않고 프로덕션 서버](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [연습: 다시 서명할 필요가 없고 브랜드 정보가 유지되는 ClickOnce 애플리케이션 수동 배포](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)
