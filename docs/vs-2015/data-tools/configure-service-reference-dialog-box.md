---
title: 서비스 참조 구성 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 883cdd8f3d150c894ecfbe7ccd2fbc2906c9e79b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705183"
---
# <a name="configure-service-reference-dialog-box"></a>서비스 참조 구성 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 **서비스 참조 구성** 대화 상자를 사용 하는 동작을 구성할 수 있습니다 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 서비스입니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
 **서비스 참조 구성** 대화 상자에 액세스하려면 **솔루션 탐색기**에서 서비스 참조를 마우스 오른쪽 단추로 클릭하고 **서비스 참조 구성**을 선택합니다. **서비스 참조 추가 대화 상자**에서 **고급** 단추를 클릭하여 대화 상자에 액세스할 수도 있습니다.  
  
## <a name="task-list"></a>작업 목록  
  
- WCF 서비스가 호스팅되는 주소를 변경하려면 **주소** 필드에 새 주소를 입력합니다.  
  
- WCF 클라이언트에서 클래스의 액세스 수준을 변경하려면 **생성된 클래스에 대한 액세스 수준** 목록에서 액세스 수준 키워드를 선택합니다.  
  
- WCF 서비스의 메서드를 비동기적으로 호출하려면 **비동기 작업 생성** 확인란을 선택합니다.  
  
- WCF 클라이언트에서 메시지 계약 형식을 생성하려면 **항상 메시지 계약 생성** 확인란을 선택합니다.  
  
- WCF 클라이언트에 대해 목록 또는 사전 컬렉션 형식을 지정하려면 **컬렉션 형식** 및 **사전 컬렉션 형식** 목록에서 형식을 선택합니다.  
  
- 형식 공유를 사용하지 않도록 설정하려면 **참조된 어셈블리의 형식 재사용** 확인란의 선택을 취소합니다. 일부 참조된 어셈블리에 대해 형식 공유를 사용하도록 설정하려면 **참조된 어셈블리의 형식 재사용** 확인란을 선택하고, **참조된 어셈블리 중 지정된 어셈블리의 형식 재사용**을 선택하고, **참조된 어셈블리 목록**에서 원하는 참조를 선택합니다.  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **Address**  
 서비스 참조가 서비스를 검색하는 웹 주소를 업데이트하는 데 사용됩니다. 예를 들어 개발 도중 서비스를 개발 서버에서 호스팅하다가 나중에 프로덕션 서버로 이동하여 주소를 변경해야 하는 경우가 이에 해당할 수 있습니다.  
  
> [!NOTE]
> Address 요소는 **서비스 참조 추가 대화 상자**에서 **서비스 참조 구성** 대화 상자가 표시된 경우에는 사용할 수 없습니다.  
  
 **생성된 클래스에 대한 액세스 수준**  
 WCF 클라이언트 클래스에 대한 코드 액세스 수준을 결정합니다.  
  
> [!NOTE]
> 웹 사이트 프로젝트의 경우 이 옵션은 항상 `Public`으로 설정되며 변경할 수 없습니다. 자세한 내용은 [서비스 참조 문제 해결](../data-tools/troubleshooting-service-references.md)합니다.  
  
 **동기 작업 생성**  
 WCF 서비스 메서드를 동기적으로(기본값) 호출할지 아니면 비동기적으로 호출할지를 결정합니다.  
  
 **작업 기반 작업 생성**  
 비동기 코드를 작성하는 경우 이 옵션을 사용하면 .Net 4에 도입된 TPL(작업 병렬 라이브러리)을 활용할 수 있습니다. 참조 [작업 병렬 라이브러리 (TPL)](https://msdn.microsoft.com/library/dd460717.aspx)합니다.  
  
 **항상 메시지 계약 생성**  
 WCF 클라이언트에 대해 메시지 계약 형식을 생성할지 여부를 결정합니다. 메시지 계약에 대 한 자세한 내용은 참조 하세요. [Using Message Contracts](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249)합니다.  
  
 **컬렉션 형식**  
 WCF 클라이언트에 대한 목록 컬렉션 형식을 지정합니다. 기본 형식은 <xref:System.Array>입니다.  
  
 **사전 컬렉션 형식**  
 WCF 클라이언트에 대한 사전 컬렉션 형식을 지정합니다. 기본 형식은 <xref:System.Collections.Generic.Dictionary%602>입니다.  
  
 **참조된 어셈블리의 형식 재사용**  
 서비스가 추가 또는 업데이트되면 WCF 클라이언트에서 새 형식을 생성하는 대신 참조된 어셈블리에 이미 있는 형식을 다시 사용하도록 할지 여부를 결정합니다. 기본적으로 이 옵션은 선택되어 있습니다.  
  
 **모든 참조된 어셈블리의 형식 재사용**  
 선택 하면 모든 형식에는 **참조 된 어셈블리 목록** 가능 하면 다시 사용 됩니다. 기본적으로 이 옵션이 선택됩니다.  
  
 **참조된 어셈블리 중 지정된 어셈블리의 형식 재사용**  
 선택한 형식만 선택 합니다 **참조 된 어셈블리 목록** 다시 사용 됩니다.  
  
 **참조된 어셈블리 목록**  
 프로젝트 또는 웹 사이트의 참조된 어셈블리 목록을 포함합니다. 때 **지정된 된 어셈블리의 형식 재사용** 을 선택 하면 개별 어셈블리를 선택 하거나 지울 수 있습니다.  
  
 **웹 참조 추가**  
 표시 된 [NIB: 웹 참조 추가 대화 상자](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)합니다.  
  
> [!NOTE]
> 이 옵션은 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 버전을 대상으로 하는 프로젝트에만 사용해야 합니다.  
  
> [!NOTE]
> **웹 참조 추가** 단추를 사용할 수 있는 경우에만 합니다 **서비스 참조 구성** 에서 대화 상자가 표시 됩니다는 **서비스 참조 추가 대화 상자**.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 추가, 업데이트 또는 서비스 참조를 제거 합니다.](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [방법: 웹 서비스에 대 한 참조를 추가 합니다.](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Windows Communication Foundation 서비스 및 WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
