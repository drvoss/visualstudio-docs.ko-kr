---
title: 서비스 참조 문제 해결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f1c5886d4ac3efcb906a27f73af6a79fad95a5af
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700230"
---
# <a name="troubleshooting-service-references"></a>서비스 참조 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
이 항목에서는 사용 하 여 작업할 때 발생할 수 있는 일반적인 문제 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 나 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 참조 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.

## <a name="error-returning-data-from-a-service"></a>서비스에서 데이터를 반환 하는 오류
 반환 하는 `DataSet` 또는 `DataTable` 서비스에서 "들어오는 메시지의 최대 크기 할당량 초과 했습니다." 예외가 표시 될 수 있습니다. 기본적으로 `MaxReceivedMessageSize` 일부 바인딩에 대 한 속성은 상대적으로 작은 값으로 서비스 거부 공격에 대 한 노출을 제한 합니다. 예외를 방지 하기 위해이 값을 늘릴 수 있습니다.

 이 오류를 해결하려면

1. **솔루션 탐색기**를 열려는 app.config 파일을 두 번 클릭 합니다.

2. 찾을 `MaxReceivedMessageSize` 속성 보다 큰 값으로 변경 합니다.

## <a name="cannot-find-a-service-in-my-solution"></a>필자의 솔루션에는 서비스를 찾을 수 없습니다.
 클릭할 때 합니다 **Discover** 단추를 **서비스 참조 추가** 대화 상자에서 솔루션의 WCF 서비스 라이브러리 프로젝트를 하나 이상의 서비스 목록에 나타나지 않습니다. 서비스 라이브러리를 솔루션에 추가 되었지만 아직 컴파일되지 않은 경우 발생할 수 있습니다.

 이 오류를 해결하려면

- **솔루션 탐색기**WCF 서비스 라이브러리 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 클릭 **빌드**합니다.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>원격 데스크톱을 통해 서비스에 액세스 하는 오류
 사용자가 액세스 한 원격 데스크톱 연결을 통해 웹에서 호스팅되는 WCF 서비스에 관리 권한이 없는 경우 NTLM 인증이 사용 됩니다. 사용자 관리 권한이 없으면 사용자의 다음과 같은 오류 메시지가 나타날 수 있습니다. "HTTP 요청이 클라이언트 인증 구성표 '익명' 권한이 부여 되지 않습니다. 합니다. 서버에서 수신한 인증 헤더가 되었습니다 'NTLM'. "

 이 오류를 해결하려면

1. 웹 사이트 프로젝트에서 엽니다는 **속성** 페이지입니다.

2. 에 **시작 옵션** 탭을 선택 취소 합니다 **NTLM 인증** 확인란 합니다.

    > [!NOTE]
    > 단독으로 WCF 서비스를 포함 하는 웹 사이트에 대해서만 NTLM 인증을 해제 해야 합니다. WCF 서비스에 대 한 보안은 web.config 파일에서 구성을 통해 관리 됩니다. 이렇게 하면 NTLM 인증이 불필요 한 합니다.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>생성 된 클래스에 대 한 액세스 수준 설정의 영향 없음
 설정 합니다 **액세스 수준 생성 된 클래스에 대 한** 옵션을 **서비스 참조 구성** 대화 상자 **내부** 또는 **Friend** 효과가 없는 경우가 있습니다. 액세스 수준 옵션 대화 상자에서 설정할 표시 되 면, 결과 지원 클래스를 생성할 `Public`합니다.

 사용 하 여 serialize 하는 것과 같은 특정 형식의 알려진 제한 사항는 <xref:System.Xml.Serialization.XmlSerializer>합니다.

## <a name="error-debugging-service-code"></a>서비스 코드를 디버깅 하는 오류
 클라이언트 코드에서 WCF 서비스에 대 한 코드를 한 단계씩 실행할 때 기호가 누락 관련 오류가 표시 될 수 있습니다. 이 솔루션의 일부 였던 서비스 이동 또는 솔루션에서 제거 되었을 때 발생할 수 있습니다.

 현재 솔루션에 포함 된 WCF 서비스에 대 한 참조를 처음 추가할 때 명시적 빌드 종속성 서비스 프로젝트 및 서비스 클라이언트 프로젝트 간에 추가 됩니다. 이렇게 하면는 클라이언트가 항상 액세스 하는 최신 서비스 바이너리, 클라이언트 코드에서 서비스 코드를 한 단계씩 실행 하는 등의 시나리오를 디버깅을 위해 특히 중요 합니다.

 서비스 프로젝트를 솔루션에서 제거 되 면 명시적 빌드 종속성이 무효화 됩니다. Visual Studio 더 이상 보장할 수 서비스 프로젝트가 다시 빌드됩니다는 필요에 따라 합니다.

 이 오류를 해결 하려면 수동으로 서비스 프로젝트를 다시 작성 해야 합니다.

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. 에 **옵션** 대화 상자에서 **프로젝트 및 솔루션**를 선택한 후 **일반**합니다.

3. 있는지 확인 합니다 **고급 빌드 구성 표시** 확인란을 선택한 다음 클릭 **확인**합니다.

4. WCF 서비스 프로젝트를 로드 합니다. 자세한 내용은 참조 하세요. [NIB 방법: 다중 프로젝트 솔루션 만들기](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)합니다.

5. 에 **Configuration Manager** 대화 상자에서를 **활성 솔루션 구성** 하 **디버그**합니다. 자세한 내용은 [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)을 참조하세요.

6. **솔루션 탐색기**, WCF 서비스 프로젝트를 선택 합니다.

7. 에 **빌드** 메뉴에서 클릭 **다시** WCF 서비스 프로젝트를 다시 빌드해야 합니다.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF 데이터 서비스가 브라우저에 표시 되지 않음
 데이터의 XML 표현을 확인 하려고 할 때를 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], Internet Explorer에서 RSS 피드로 데이터를 잘못 해석할 수 있습니다. RSS 피드를 표시하는 옵션은 반드시 비활성화되어 있어야 합니다.

 이 오류를 해결 하려면 RSS 피드를 사용 하지 않도록 설정 합니다.

1. Internet Explorer의 **도구** 메뉴에서 **인터넷 옵션**을 클릭합니다.

2. 에 **콘텐츠** 탭의 **피드** 섹션에서 **설정**.

3. 에 **피드 설정** 대화 상자, 일반 합니다 **피드 읽기용 보기를 켜려면** 확인란을 선택한 다음 클릭 **확인**.

4. **확인**을 클릭하여 **인터넷 옵션** 대화 상자를 닫습니다.

## <a name="see-also"></a>참고자료

- [Windows Communication Foundation 서비스 및 Visual Studio의 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)