---
title: Windows Communication Foundation 서비스 및 WCF Data Services
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 68f2b400cc92673131dea2fc281b830df86019f7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704378"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Windows Communication Foundation 서비스 및 Visual Studio의 WCF.NET 데이터 서비스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio는 Windows Communication Foundation (WCF)를 사용 하 여 작업에 대 한 도구를 제공 하 고 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], 분산 응용 프로그램을 만들기 위한 Microsoft 기술입니다. 이 항목에서 서비스에 대해 소개를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 관점입니다. 전체 설명서를 참조 하세요 [WCF Data Services 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)합니다.

## <a name="what-is-wcf"></a>새로운 WCF 기능
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 보안, 신뢰할 수 있는, 트랜잭션 및 상호 운용 가능한 분산된 응용 프로그램을 만들기 위한 통합 된 프레임 워크입니다. ASMX 웹 서비스,.NET Remoting, Enterprise Services (DCOM) 및 MSMQ와 같은 이전 프로세스 간 통신 기술을 대체합니다. WCF 통합된 프로그래밍 모델에서 이러한 모든 기술의 기능을 결합 합니다. 이 분산된 응용 프로그램 개발 환경을 간소화 합니다.

#### <a name="what-are-wcf-data-services"></a>WCF Data Services 란
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 표준 OData (개방형 데이터) 프로토콜의 구현입니다.  WCF Data Services와 같은 표준 HTTP 동사를 사용 하 여 데이터 가져오기, POST, PUT 또는 DELETE 키를 반환할 수 있도록 하는 REST Api의 집합으로 테이블 형식 데이터를 노출할 수 있습니다. 서버 쪽에서 WCF Data Services에 의해 대체 되 [ASP.NET Web API](http://www.asp.net/web-api) 새 OData 서비스 만들기에 대 한 합니다. WCF Data Services 클라이언트 라이브러리를 계속 적합 한 Visual Studio에서.NET 응용 프로그램에서 OData 서비스를 이용할 수 있습니다 (**프로젝트 &#124; 서비스 참조 추가**). 자세한 내용은 [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952)를 참조하세요.

### <a name="wcf-programming-model"></a>WCF 프로그래밍 모델
 WCF 프로그래밍 모델을 기반으로 두 엔터티 간의 통신: WCF 서비스와 WCF 클라이언트입니다. 프로그래밍 모델에 캡슐화 되어는 <xref:System.ServiceModel> 네임 스페이스는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]합니다.

#### <a name="wcf-service"></a>WCF 서비스
 WCF 서비스는 서비스와 클라이언트 간의 계약을 정의 하는 인터페이스를 기반으로 합니다. 로 표시 되는 <xref:System.ServiceModel.ServiceContractAttribute> 특성을 다음 코드 에서처럼:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 함수 또는 표시 하 여 WCF 서비스에 의해 노출 되는 메서드가 정의 하는 <xref:System.ServiceModel.OperationContractAttribute> 특성입니다. 또한 사용 하 여 복합 형식을 표시 하 여 serialize 된 데이터를 노출할 수 있습니다는 <xref:System.Runtime.Serialization.DataContractAttribute> 특성입니다. 이 클라이언트에서 데이터 바인딩을 활성화합니다.

 인터페이스 및 해당 메서드를 정의한 후 인터페이스를 구현 하는 클래스에 캡슐화 됩니다. 단일 WCF 서비스 클래스는 여러 서비스 계약을 구현할 수 있습니다.

 WCF 서비스를 통해 소비 라고에 대 한 노출 되는 *끝점*합니다. 끝점 제공 서비스와 통신 하는 유일한 방법은 다른 클래스와 마찬가지로 직접 참조를 통해 서비스를 액세스할 수 없습니다.

 끝점 주소, 바인딩 및 계약으로 구성 됩니다. 서비스가 위치한; 주소 정의 URL, FTP 주소를 네트워크 또는 로컬 경로는 일 수 있습니다. 바인딩은은 서비스와 통신 하는 방식을 정의 합니다. HTTP 또는 FTP와 Windows 인증 또는 사용자 이름 및 암호와 같은 보안 메커니즘을와 같은 프로토콜을 지정 하기 위한 다양 한 모델을 제공 하는 WCF 바인딩 등입니다. 계약에는 WCF 서비스 클래스에 의해 노출 되는 작업이 포함 됩니다.

 하나의 WCF 서비스에 대 한 여러 끝점을 노출할 수 있습니다. 따라서 다른 클라이언트가 다양 한 방법으로 동일한 서비스와 통신할 수 있습니다. 예를 들어 뱅킹 서비스 수 하나의 끝점에 대 한 제공 직원 및 다른 외부 고객에 게 각각 다른 주소, 바인딩를 사용 하 여 및/또는 계약입니다.

#### <a name="wcf-client"></a>WCF 클라이언트
 WCF 클라이언트 구성 된 *프록시* 수 있도록 하는 WCF 서비스와 통신 하는 응용 프로그램 및 서비스에 대해 정의 된 끝점과 일치 하는 끝점입니다. 프록시는 app.config 파일에서 클라이언트 쪽에서 생성 되 고 형식 및 서비스에 의해 노출 되는 방법에 대 한 정보가 포함 되어 있습니다. 여러 끝점을 노출 하는 서비스에 대 한 클라이언트에는 HTTP를 통해 통신 하 고 Windows 인증을 사용 하려면 예를 들어, 해당 요구에 가장 잘 맞는 하나를 선택할 수 있습니다.

 WCF 클라이언트를 만든 후 서비스에서에서 참조 코드는 다른 개체와 마찬가지로 합니다. 예를 들어, 호출 하 여 `GetData` 다음과 유사한 코드를 작성 하는 이전에 표시 된 메서드:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio의 WCF 도구
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF 서비스와 WCF 클라이언트를 만들 수 있도록 도구를 제공 합니다. 도구를 보여 주는 연습을 참조 하세요. [연습: Windows Forms에서 간단한 WCF 서비스 만들기](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)합니다.

### <a name="creating-and-testing-wcf-services"></a>만들기 및 WCF 서비스 테스트
 WCF를 사용할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 템플릿을 기반으로 신속 하 게 직접 서비스를 만듭니다. 그런 다음 디버그 및 테스트 서비스를 WCF 서비스 자동 호스트 및 WCF 테스트 클라이언트를 사용할 수 있습니다. 이러한 도구는 함께 빠르고 편리 하 게 디버그 및 테스트 주기를 제공 하 고 초기 단계에서 호스팅 모델에 대 한 커밋 요구 사항을 제거 합니다.

#### <a name="wcf-templates"></a>WCF 템플릿
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 템플릿은 서비스 개발을 위한 기본 클래스 구조를 제공 합니다. 몇 가지 WCF 템플릿을 사용할 수는 **새 프로젝트 추가** 대화 상자. 여기에 WCF 서비스 라이브러리 프로젝트, WCF 서비스 웹 사이트 및 WCF 서비스 항목 템플릿 포함 됩니다.

 서식 파일을 선택 하면 서비스 계약, 서비스 구현 및 서비스 구성 파일이 추가 됩니다. 모든 필요한 특성이 이미 추가 되 면 서비스의 간단한 "Hello World" 형식 만들기 및 않은 코드를 작성할 필요가 없습니다. 물론, 함수 및 실제 서비스의 메서드를 제공 하는 코드를 추가 하려면 싶지만 템플릿을 기본 기초를 제공 합니다.

 WCF 템플릿에 대 한 자세한 내용은 참조 하세요 [WCF Visual Studio 템플릿](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f)합니다.

#### <a name="wcf-service-host"></a>WCF 서비스 호스트
 시작 하는 경우는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF 서비스 프로젝트를 로컬로 서비스를 호스팅할 도구를 자동으로 시작 WCF 서비스 호스트에 대 한 디버거 (F5를 눌러). WCF 서비스 호스트는 WCF 서비스 프로젝트에서 서비스를 열거 하 고, 프로젝트의 구성을 로드, 발견 되는 각 서비스에 대 한 호스트를 인스턴스화합니다.

 WCF 서비스 호스트를 사용 하 여 추가 코드를 작성 하거나 개발 하는 동안 특정 호스트를 커밋하지 않고 WCF 서비스를 테스트할 수 있습니다.

 WCF 서비스 호스트에 대 한 자세한 내용은 참조 하세요 [WCF 서비스 호스트 (WcfSvcHost.exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e)합니다.

#### <a name="wcf-test-client"></a>WCF 테스트 클라이언트
 WCF 테스트 클라이언트 도구 테스트 매개 변수 입력, 제출 하는 WCF 서비스에 입력 수 있으며 서비스를 다시 보내는 응답을 봅니다. WCF 서비스 호스트를 사용 하 여 결합 하는 경우 환경 테스트 서비스를 편리 하 게 제공 합니다. 이 도구는 c: 드라이브에 설치 된 Visual Studio 2015 용는 \Common7\IDE 폴더에서 찾을 수 있습니다. **C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\\** .

 WCF 서비스 프로젝트를 디버그 하려면 f5 키를 누르면 WCF 테스트 클라이언트 열리고 구성 파일에 정의 된 서비스 끝점의 목록을 표시 합니다. 매개 변수를 테스트 하 고 및 서비스를 시작 하 고, 지속적으로 테스트 하 고 서비스의 유효성을 검사 하는이 프로세스를 반복 수 합니다.

 WCF 테스트 클라이언트에 대 한 자세한 내용은 참조 하세요 [WCF 테스트 클라이언트 (WcfTestClient.exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7)합니다.

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio에서 WCF 서비스에 액세스
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF 클라이언트를 자동으로 생성 되는 프록시 및 서비스를 사용 하 여 추가 대 한 끝점을 만드는 작업을 간소화 합니다 **서비스 참조 추가** 대화 상자. 모든 필요한 구성 정보는 app.config 파일에 추가 됩니다. 대부분의 경우 사용 하기 위해 서비스를 인스턴스화하는 수행 해야 하는 모든.

 합니다 **서비스 참조 추가** 대화 상자를 사용 하면 서비스에 대 한 주소를 입력 하거나, 솔루션에 정의 된 서비스를 검색 합니다. 대화 상자에는 서비스 및 해당 서비스에서 제공 하는 작업의 목록을 반환 합니다. 또한 네임 스페이스는 코드에서 서비스 참조는 정의할 수 있습니다.

 합니다 **서비스 참조 구성** 대화 상자를 사용 하는 서비스에 대 한 구성을 사용자 지정할 수 있습니다. 서비스에 대 한 주소를 변경 하 고, 액세스 수준, 비동기 동작 및 메시지 계약 형식을 지정 하 고, 형식 재사용을 구성할 수 있습니다.

## <a name="how-to-select-a-service-endpoint"></a>방법: 서비스 끝점을 선택 합니다.
 일부 Windows Communication Foundation (WCF) 서비스는 클라이언트가 서비스와 통신할 수 있습니다 하는 여러 끝점을 노출 합니다. 서비스는 HTTP 바인딩 및 사용자 이름을 사용 하는 하나의 끝점을 노출할 수 예를 들어 / 암호 보안 및 FTP 및 Windows 인증을 사용 하는 두 번째 끝점입니다. 두 번째는 인트라넷에서 사용할 수 있지만 방화벽 외부에서 서비스에 액세스 하는 응용 프로그램에서 첫 번째 끝점을 사용할 수 있습니다.

 이러한 경우에 지정할 수 있습니다는 `endpointConfigurationName` 서비스 참조에 대 한 생성자 매개 변수로 합니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>서비스 끝점을 선택 합니다.

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 선택 하 여 WCF 서비스에 대 한 참조를 추가 **서비스 참조 추가**

2. 코드 편집기에서 서비스 참조에 대 한 생성자를 추가 합니다.

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > 바꿉니다 *ServiceReference* 바꾸고 서비스 참조에 대 한 네임 스페이스를 사용 하 여 *Service1Client* 서비스의 이름입니다.

3. 생성자의 오버 로드를 사용 하 여 IntelliSense 목록이 표시 됩니다. 선택 된 `endpointConfigurationName As String` 오버 로드 합니다.

4. 입력 한 다음 오버 로드 `=` *ConfigurationName*여기서 *ConfigurationName* 사용 하려는 끝점의 이름입니다.

    > [!NOTE]
    > 사용 가능한 끝점의 이름을 모르는 경우에 app.config 파일에서 찾을 수 있습니다.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>WCF 서비스에 대 한 사용 가능한 끝점을 찾으려면

1. **솔루션 탐색기**서비스 참조를 포함 하는 프로젝트의 app.config 파일을 마우스 오른쪽 단추로 클릭 하 고 클릭 **오픈**합니다. 파일 코드 편집기에 표시 됩니다.

2. 검색 된 `<Client>` 파일에 태그 합니다.

3. 아래에 있는 검색 된 `<Client>` 로 시작 하는 태그에 대 한 태그 `<Endpoint>`합니다.

     서비스 참조를 여러 끝점을 제공 하는 경우 있습니다 됩니다 두 개 이상의 `<Endpoint` 태그입니다.

4. 내 합니다 `<EndPoint>` 태그를 찾을 수 있습니다를 `name="` *SomeService* `"` 매개 변수 (여기서 *SomeService* 끝점 이름을 나타냅니다). 에 전달 될 수 있는 끝점에 대 한 이름를 `endpointConfigurationName As String` 서비스 참조에 대 한 생성자의 오버 로드 합니다.

## <a name="how-to-call-a-service-method-asynchronously"></a>방법: 서비스 메서드를 비동기적으로 호출
 Windows Communication Foundation (WCF) 서비스에서 대부분의 메서드는 동기적 또는 비동기적으로 호출할 수 있습니다. 메서드를 비동기적으로 호출 응용을 프로그램을 저속 연결을 통해 작동 하는 경우 메서드가 호출 되는 동안 작업을 계속할 수 있습니다.

 기본적으로 서비스 참조를 프로젝트에 추가 되 면 메서드를 동기적으로 호출 하 여 구성 됩니다. 설정을 변경 하 여 메서드를 비동기적으로 호출 하려면 동작을 변경할 수는 **서비스 참조 구성** 대화 상자.

> [!NOTE]
> 이 옵션은 서비스별 단위로 설정 됩니다. 서비스에 대 한 하나의 메서드를 비동기적으로 호출 하는 경우 모든 메서드를 비동기적으로 호출 되어야 합니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>서비스 메서드를 비동기적으로 호출 하려면

1. **솔루션 탐색기**, 서비스 참조를 선택 합니다.

2. 에 **프로젝트** 메뉴에서 클릭 **서비스 참조 구성**합니다.

3. 에 **서비스 참조 구성** 대화 상자를 선택 합니다 **비동기 작업 생성** 확인란.

## <a name="how-to-bind-data-returned-by-a-service"></a>방법: 서비스에서 반환 된 데이터 바인딩
 다른 데이터 소스 컨트롤에 바인딩할 수 있습니다 하는 것 처럼 컨트롤에 Windows Communication Foundation (WCF) 서비스에서 반환 되는 데이터를 바인딩할 수 있습니다. 서비스에 데이터를 반환 하는 복합 형식이 포함 된 경우 WCF 서비스에 대 한 참조를 추가 하면 이러한는에 자동으로 추가 합니다 **데이터 원본** 창입니다.

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>WCF 서비스에서 반환 하는 단일 데이터 필드에 컨트롤을 바인딩하려면

1. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다. 합니다 **데이터 원본** 창이 표시 됩니다.

2. 에 **데이터 원본** 창에서 서비스 참조 노드를 확장 합니다. 서비스에서 반환 하는 모든 복합 형식이 표시 됩니다.

3. 형식에 대 한 노드를 확장 합니다. 해당 유형에 대 한 데이터 필드가 표시 됩니다.

4. 필드를 선택 하 고 데이터 형식에 사용할 수 있는 컨트롤의 목록을 표시 하려면 드롭다운 화살표를 클릭 합니다.

5. 에 바인딩할 컨트롤의 유형을 클릭 합니다.

6. 필드를 폼으로 끌어 옵니다. 와 함께 폼에 추가할 컨트롤을 <xref:System.Windows.Forms.BindingSource> 구성 요소 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소입니다.

7. 4 단계를 반복 하 여 다른 6 있는 필드가 있지만 바인딩하려 합니다.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>WCF 서비스에서 반환 하는 복합 형식으로 컨트롤을 바인딩하려면

1. 에 **데이터** 메뉴에서 **데이터 소스 표시**합니다. 합니다 **데이터 원본** 창이 표시 됩니다.

2. 에 **데이터 원본** 창에서 서비스 참조 노드를 확장 합니다. 서비스에서 반환 하는 모든 복합 형식이 표시 됩니다.

3. 형식에 대 한 노드를 선택 하 고 사용 가능한 옵션 목록을 표시 하려면 드롭다운 화살표를 클릭 합니다.

4. 중 하나를 클릭 **DataGridView** 표에 데이터를 표시할 또는 **세부 정보** 개별 컨트롤에 데이터를 표시 합니다.

5. 노드를 폼으로 끌어 옵니다. 와 함께 폼에 추가할 컨트롤을 <xref:System.Windows.Forms.BindingSource> 구성 요소 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소입니다.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>방법: 기존 형식 다시 사용 하려면 서비스 구성
 서비스 참조를 프로젝트에 추가 되 면 서비스에 정의 된 모든 형식은 로컬 프로젝트에서 생성 됩니다. 대부분의 경우이 중복 된 형식이 만들어집니다 서비스를 사용 하는 경우 일반적인 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식 또는 형식 공유 라이브러리에 정의 된 경우.

 이 문제를 방지 하려면 참조 된 어셈블리의 형식에에서는 기본적으로 공유 됩니다. 하나 이상의 어셈블리에 대해 형식 공유를 사용 하지 않도록 설정 하려는 경우 가능 하므로 합니다 **서비스 참조 구성** 대화 상자.

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>단일 어셈블리의 형식 공유를 사용 하지 않도록 설정

1. **솔루션 탐색기**, 서비스 참조를 선택 합니다.

2. 에 **프로젝트** 메뉴에서 클릭 **서비스 참조 구성**합니다.

3. 에 **서비스 참조 구성** 대화 상자에서 **지정된 된 어셈블리의 형식 재사용**합니다.

4. 형식 공유를 사용 하도록 설정 하려는 각 어셈블리에 대 한 확인란을 선택 합니다. 어셈블리에 대해 형식 공유를 사용 하지 않으려면 확인란의 선택을 취소를 둡니다.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>모든 어셈블리의 형식 공유를 사용 하지 않도록 설정

1. **솔루션 탐색기**, 서비스 참조를 선택 합니다.

2. 에 **프로젝트** 메뉴에서 클릭 **서비스 참조 구성**합니다.

3. 에 **서비스 참조 구성** 대화 상자, 일반 합니다 **참조 된 어셈블리의 형식 재사용** 확인란 합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연습: Windows Forms에서 간단한 WCF 서비스 만들기](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|WCF 서비스 만들기 및 사용 단계별 데모를 제시 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.|
|[연습: WPF 및 Entity Framework를 사용하여 WCF 데이터 서비스 만들기](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|만들기 및 사용 하는 방법의 단계별 데모를 제시 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.|
|[WCF 개발 도구 사용](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|만들 WCF 서비스를 테스트 하는 방법을 설명 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.|
|[방법: 추가, 업데이트 또는 서비스 참조를 제거 합니다.](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|추가, 업데이트 또는 프로젝트에서 WCF 서비스를 제거 하는 방법을 설명 합니다.|
|[방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|참조 하 고 사용 하는 방법을 설명 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.|
|[서비스 참조 문제 해결](../data-tools/troubleshooting-service-references.md)|서비스 참조 및 방지 하는 방법을 사용 하 여 발생할 수 있는 몇 가지 일반적인 오류를 표시 합니다.|
|[WCF 서비스 디버그](../debugger/debugging-wcf-services.md)|일반적인 디버깅 문제와 WCF 서비스를 디버깅할 때 발생할 수 있는 기술에 설명 합니다.|
|[Windows Communication Foundation 인증 서비스 개요](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|WCF를 사용 하 여 웹 사이트에 대 한 역할 서비스를 제공 하는 방법에 설명 합니다.|
|[연습: N 계층 데이터 애플리케이션 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|형식화된 데이터 세트을 만들고 TableAdapter 및 데이터 세트 코드를 여러 프로젝트로 분리하는 단계별 지침을 제공합니다.|
|[서비스 참조 구성 대화 상자](../data-tools/configure-service-reference-dialog-box.md)|사용자 인터페이스 요소에 설명 합니다 **서비스 참조 구성** 대화 상자.|

## <a name="reference"></a>참조
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>참고 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
