---
title: '방법: 연결 문자열 저장 및 편집'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1f8300043f9a16c7d92d72c4dcb22e4cd0432a06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566975"
---
# <a name="how-to-save-and-edit-connection-strings"></a>방법: 연결 문자열 저장 및 편집
Visual Studio 응용 프로그램의 연결 문자열 (응용 프로그램 설정이 라고도 함) 응용 프로그램 구성 파일에 저장 또는 응용 프로그램에 직접 하드 코딩 됩니다. 애플리케이션 구성 파일에 연결 문자열을 저장하면 애플리케이션 유지 관리 작업을 간소화할 수 있습니다. 연결 문자열을 변경해야 하는 경우 소스 코드에서 문자열을 변경한 다음, 애플리케이션을 다시 컴파일하는 대신 애플리케이션 설정 파일에서 문자열을 업데이트할 수 있습니다.

암호와 같은 중요한 정보를 연결 문자열 내에 저장하면 애플리케이션 보안 문제가 발생할 수 있습니다. 애플리케이션 구성 파일에 저장된 연결 문자열은 암호화되거나 난독 처리되지 않으므로 다른 사람이 파일에 액세스하여 해당 내용을 볼 수 있습니다. 데이터베이스 액세스를 제어할 경우에는 Windows 통합 보안을 사용하는 방법이 더 안전합니다.

Windows 통합 보안을 사용하도록 선택하지 않았는데 데이터베이스에 사용자 이름과 암호가 필요한 경우 연결 문자열에서 사용자 이름과 암호를 생략할 수 있습니다. 그러나 데이터베이스에 정상적으로 연결하려면 애플리케이션이 이 정보를 제공해야 합니다. 예를 들어 이 정보를 입력하라는 메시지를 사용자에게 표시하고 런타임에 연결 문자열을 동적으로 작성하는 대화 상자를 만들 수 있습니다. 데이터베이스로 전송되는 와중에 정보를 가로챌 수 있는 경우에도 보안 문제가 발생할 수 있습니다.
자세한 내용은 [연결 정보 보호](/dotnet/framework/data/adonet/protecting-connection-information)를 참조하세요.

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>데이터 소스 구성 마법사 내에서 연결 문자열을 저장 하려면
에 **데이터 소스 구성 마법사**에서 연결을 저장 하는 옵션을 선택 합니다 **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지입니다.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>연결 문자열을 애플리케이션 설정에 직접 저장하려면
1. **솔루션 탐색기**에서 **내 프로젝트** 아이콘(Visual Basic) 또는 **속성** 아이콘(C#)을 두 번 클릭하여 **프로젝트 디자이너**를 엽니다.
1. **설정** 탭을 선택합니다.
1. 연결 문자열의 **이름**을 입력합니다. 코드에서 연결 문자열에 액세스할 때 이 이름을 참조합니다.
1. **형식**을 **연결 문자열**로 설정합니다.
1. **범위**는 **애플리케이션**으로 설정된 상태로 유지합니다.
1. 에 연결 문자열을 입력 합니다 **값** 필드를 누르거나를 **줄임표** (...) 단추를 **값** 열려는 필드는 **연결 속성** 대화 상자의 연결 문자열을 만듭니다.

## <a name="edit-connection-strings-stored-in-application-settings"></a>응용 프로그램 설정에 저장 된 연결 문자열 편집
**프로젝트 디자이너**를 사용하여 애플리케이션 설정에 저장된 연결 정보를 수정할 수 있습니다.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>애플리케이션 설정에 저장된 연결 문자열을 편집하려면
1. **솔루션 탐색기**에서 **내 프로젝트** 아이콘(Visual Basic) 또는 **속성** 아이콘(C#)을 두 번 클릭하여 **프로젝트 디자이너**를 엽니다.
1. **설정** 탭을 선택합니다.
1. 텍스트를 선택 하 고 편집 하려는 연결 찾습니다 합니다 **값** 필드입니다.
1. 연결 문자열을 편집할를 **값** 필드를 누르거나를 **줄임표** (...) 단추를 **값** 사용 하 여 연결을 편집 하려면 필드를 **연결 속성** 대화 상자.

## <a name="edit-connection-strings-for-datasets"></a>데이터 집합에 대 한 연결 문자열 편집
데이터 집합의 각 TableAdapter에 대 한 연결 정보를 수정할 수 있습니다.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>데이터 집합의 TableAdapter에 대 한 연결 문자열을 편집 하려면
1. **솔루션 탐색기**, 데이터 집합을 두 번 클릭 ( **.xsd** 파일)를 편집 하려면 연결 된입니다.
1. 선택 된 **TableAdapter** 또는 편집 하려면 연결 된 쿼리 합니다.
1. 에 **속성** 창에서 확장을 **연결 노드**.
1. 연결 문자열을 신속 하 게 수정 하려면 편집를 **ConnectionString** 속성을 하거나 아래쪽 화살표를 클릭 합니다 **연결** 속성 선택 **새 연결**.

## <a name="security"></a>보안
암호와 같은 중요한 정보를 연결 문자열 내에 저장하면 애플리케이션 보안 문제가 발생할 수 있습니다. 데이터베이스 액세스를 제어할 경우에는 Windows 통합 보안을 사용하는 방법이 더 안전합니다.
자세한 내용은 [연결 정보 보호](/dotnet/framework/data/adonet/protecting-connection-information)를 참조하세요.

## <a name="see-also"></a>참고자료

- [연결 추가](../data-tools/add-new-connections.md)