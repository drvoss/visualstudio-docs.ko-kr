---
title: '방법: 추가, 업데이트 또는 WCF 데이터 서비스 참조를 제거 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 970f3828319e2e9c016baa66bb1e5fc2032b81ce
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387034"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *서비스 참조* 액세스 하나 이상의 프로젝트를 사용 하면 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]합니다. 사용 합니다 **서비스 참조 추가** 대화 상자를 검색할 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 로컬 영역 네트워크에 로컬에서 또는 인터넷에 현재 솔루션에서.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>서비스 참조 추가  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>외부 서비스에 대 한 참조를 추가 하려면  
  
1. **솔루션 탐색기**, 서비스를 추가 하 고 클릭 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 **서비스 참조 추가**합니다.  
  
     합니다 **서비스 참조 추가** 대화 상자가 나타납니다.  
  
2. 에 **주소** 상자, 서비스에 대 한 URL을 입력 한 다음 클릭 **이동** 는 서비스를 검색 합니다. 서비스 사용자 이름 및 암호 보안을 구현 하는 경우에 사용자 이름과 암호를 묻는 메시지가 될 수 있습니다.  
  
    > [!NOTE]
    > 신뢰할 수 있는 원본의 서비스만 참조해야 합니다. 신뢰할 수 없는 원본에서 참조를 추가하면 보안이 손상될 수 있습니다.  
  
     URL을 선택할 수도 있습니다는 **주소** 유효한 서비스 메타 데이터를 찾을 수는 15 이전 Url을 저장 하는 목록입니다.  
  
     검색을 수행할 때 진행률 표시줄이 표시 됩니다. 클릭 하 여 언제 든 지 검색을 중지할 수 있습니다 **중지**합니다.  
  
3. 에 **Services** 목록에서 사용 하 고 엔터티 집합을 선택 하려는 서비스에 대 한 노드를 확장 합니다.  
  
4. 에 **Namespace** 상자, 참조에 사용 하려는 네임 스페이스를 입력 합니다.  
  
5. 클릭 **확인** 프로젝트에 대 한 참조를 추가 합니다.  
  
     서비스 클라이언트 (프록시)가 생성 되 고 서비스를 설명 하는 메타 데이터가 app.config 파일에 추가 됩니다.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>현재 솔루션에는 서비스에 대 한 참조를 추가 하려면  
  
1. **솔루션 탐색기**, 서비스를 추가 하 고 클릭 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 **서비스 참조 추가**합니다.  
  
     합니다 **서비스 참조 추가** 대화 상자가 나타납니다.  
  
2. 클릭 **검색**합니다.  
  
     모든 서비스 (둘 다 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 및 WCF 서비스) 현재 솔루션에 추가 합니다 **Services** 목록입니다.  
  
3. 에 **Services** 목록에서 사용 하 고 엔터티 집합을 선택 하려는 서비스에 대 한 노드를 확장 합니다.  
  
4. 에 **Namespace** 상자, 참조에 사용 하려는 네임 스페이스를 입력 합니다.  
  
5. 클릭 **확인** 프로젝트에 대 한 참조를 추가 합니다.  
  
     서비스 클라이언트 (프록시)가 생성 되 고 서비스를 설명 하는 메타 데이터가 app.config 파일에 추가 됩니다.  
  
## <a name="updating-a-service-reference"></a>서비스 참조 업데이트  
 엔터티 데이터 모델을 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 경우에 따라 변경 됩니다. 이 경우 서비스 참조를 업데이트 해야 합니다.  
  
#### <a name="to-update-a-service-reference"></a>서비스 참조를 업데이트 하려면  
  
- **솔루션 탐색기**서비스 참조를 마우스 오른쪽 단추로 클릭 한 다음 클릭 **서비스 참조 업데이트**합니다.  
  
     원래 위치에서 참조를 업데이트 및 서비스 클라이언트는 메타 데이터의 변경 내용을 반영 하도록 다시 생성 하는 동안 진행률 대화 상자가 표시 됩니다.  
  
## <a name="removing-a-service-reference"></a>서비스 참조를 제거합니다.  
 서비스 참조를 더 이상 사용 중인 경우에 솔루션에서 제거할 수 없습니다.  
  
#### <a name="to-remove-a-service-reference"></a>서비스 참조를 제거 하려면  
  
- **솔루션 탐색기**서비스 참조를 마우스 오른쪽 단추로 클릭 한 다음 클릭 **삭제**합니다.  
  
     서비스 클라이언트 솔루션에서 제거한 메타 데이터 서비스를 설명 하는 app.config 파일에서 제거 됩니다.  
  
    > [!NOTE]
    > 서비스 참조를 참조 하는 코드를 수동으로 제거 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Communication Foundation 서비스 및 Visual Studio의 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
