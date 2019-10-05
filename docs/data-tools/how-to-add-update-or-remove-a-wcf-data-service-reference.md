---
title: '방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da8555d4246d2177b3d97eeef8d24c7b4a22b31d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925630"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거
*서비스 참조* 를 사용 하면 프로젝트에서 하나 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]이상의에 액세스할 수 있습니다. **서비스 참조 추가** 대화 상자를 사용 하 여 로컬 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 영역 네트워크 또는 인터넷에서 현재 솔루션의를 검색할 수 있습니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>서비스 참조 추가

### <a name="to-add-a-reference-to-an-external-service"></a>외부 서비스에 대 한 참조를 추가 하려면

1. **솔루션 탐색기**에서 서비스를 추가 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 한 다음 **서비스 참조 추가**를 클릭 합니다.

     **서비스 참조 추가** 대화 상자가 나타납니다.

2. **주소** 상자에 서비스에 대 한 URL을 입력 하 고 **이동** 을 클릭 하 여 서비스를 검색 합니다. 서비스에서 사용자 이름 및 암호 보안을 구현 하는 경우 사용자 이름 및 암호를 입력 하 라는 메시지가 표시 될 수 있습니다.

    > [!NOTE]
    > 신뢰할 수 있는 원본의 서비스만 참조해야 합니다. 신뢰할 수 없는 원본에서 참조를 추가하면 보안이 손상될 수 있습니다.

     또한 올바른 서비스 메타 데이터를 찾은 이전 15 개 Url을 저장 하는 **주소** 목록에서 URL을 선택할 수 있습니다.

     검색을 수행 하는 동안 진행률 표시줄이 표시 됩니다. **중지**를 클릭 하 여 언제 든 지 검색을 중지할 수 있습니다.

3. **서비스** 목록에서 사용 하려는 서비스에 대 한 노드를 확장 하 고 엔터티 집합을 선택 합니다.

4. **네임 스페이스** 상자에 참조에 사용할 네임 스페이스를 입력 합니다.

5. **확인** 을 클릭 하 여 프로젝트에 참조를 추가 합니다.

     서비스 클라이언트 (프록시)가 생성 되 고 서비스를 설명 하는 메타 데이터가 *app.config* 파일에 추가 됩니다.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>현재 솔루션의 서비스에 대 한 참조를 추가 하려면

1. **솔루션 탐색기**에서 서비스를 추가 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 한 다음 **서비스 참조 추가**를 클릭 합니다.

    **서비스 참조 추가** 대화 상자가 나타납니다.

2. **검색**을 클릭 합니다.

    현재 솔루션의 모든 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 서비스 (및 WCF 서비스)가 **서비스** 목록에 추가 됩니다.

3. **서비스** 목록에서 사용 하려는 서비스에 대 한 노드를 확장 하 고 엔터티 집합을 선택 합니다.

4. **네임 스페이스** 상자에 참조에 사용할 네임 스페이스를 입력 합니다.

5. **확인** 을 클릭 하 여 프로젝트에 참조를 추가 합니다.

    서비스 클라이언트 (프록시)가를 생성 하 고, 서비스를 설명 하는 메타 데이터가 *app.config* 파일에 추가 됩니다.

## <a name="update-a-service-reference"></a>서비스 참조 업데이트
엔터티 데이터 모델는 경우에 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 따라 변경 됩니다. 이 경우 서비스 참조를 업데이트 해야 합니다.

### <a name="to-update-a-service-reference"></a>서비스 참조를 업데이트 하려면

- **솔루션 탐색기**에서 서비스 참조를 마우스 오른쪽 단추로 클릭 한 다음 **서비스 참조 업데이트**를 클릭 합니다.

     원본 위치에서 참조를 업데이트 하는 동안 진행률 대화 상자가 표시 되 고 메타 데이터의 변경 내용을 반영 하도록 서비스 클라이언트가 다시 생성 됩니다.

## <a name="remove-a-service-reference"></a>서비스 참조 제거
서비스 참조가 더 이상 사용 되지 않는 경우 솔루션에서 제거할 수 있습니다.

### <a name="to-remove-a-service-reference"></a>서비스 참조를 제거 하려면

- **솔루션 탐색기**에서 서비스 참조를 마우스 오른쪽 단추로 클릭 한 다음 **삭제**를 클릭 합니다.

     서비스 클라이언트는 솔루션에서 제거 되 고, 서비스를 설명 하는 메타 데이터는 *app.config* 파일에서 제거 됩니다.

    > [!NOTE]
    > 서비스 참조를 참조 하는 모든 코드는 수동으로 제거 해야 합니다.

## <a name="see-also"></a>참고자료

- [Windows Communication Foundation 서비스 및 Visual Studio의 WCF 데이터 서비스](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)