---
title: VLSC에 표시된 개인 전자 메일
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Visual Studio 구독 - 구독자의 Hotmail 또는 Gmail 주소가 보이는 이유는 무엇인가요?
ms.openlocfilehash: 8418a177e793f0b4fe9a5019d2cf62fa724312ff
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605760"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio 구독 - 구독자의 Hotmail 또는 Gmail 주소가 보이는 이유는 무엇인가요?
기업이 VLSC(볼륨 라이선스 서비스 센터)에서 새 Visual Studio [구독 관리 포털](https://manage.visualstudio.com)로 마이그레이션한 후 관리자는 일부 구독자의 “로그인 전자 메일 주소”에 Hotmail, Gmail 또는 Yahoo와 같은 타사 전자 메일 주소가 표시되는 것을 발견했습니다.  자세한 내용은 [이 비디오](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6)를 참조하세요.

## <a name="cause"></a>원인
이 시나리오는 레거시 MSDN 구독자 환경에 연결된 로그인 프로세스로 인해 발생합니다. 사용자가 수정 과정 없이 VLSC(볼륨 라이선스 서비스 센터)에서 Visual Studio 구독 관리 포털로 마이그레이션되었습니다. 관리자는 사용자가 개인 계정을 사용하여 구독 혜택에 액세스했음을 알지 못했을 수 있습니다. 2016년에 완료된 Visual Studio 구독자 마이그레이션 전에는 Visual Studio 구독을 성공적으로 사용하는 데 필요한 두 가지 작업이 있었습니다.
1. 관리자가 해당 회사 또는 학교 전자 메일 주소를 사용하여 개별 구독자에게 구독을 “할당”했습니다.
2. 구독자가 구독을 “활성화”했습니다.

구독자 활성화 프로세스 중에: 로그인하려면 Microsoft 계정(MSA)이 필요했습니다. 구독자가 해당 회사 또는 학교 계정(예: tasha@contoso.com)을 MSA로 설정하지 않은 경우 새 MSA를 만들거나 기존 MSA를 활용할 수 있었습니다. 이로 인해 “로그인 전자 메일 주소”가 “할당 대상 전자 메일 주소”와 달라졌습니다.

> [!NOTE]
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)의 새로운 구독자 환경은 회사/학교 및 Microsoft 계정(MAA) ID 유형을 둘 다 지원합니다.

마지막으로, 관리자 마이그레이션은 구독자의 “로그인 전자 메일 주소”에 대한 VLSC의 데이터를 가져와서 새 구독자 관리 환경을 채웠으므로, 이 정보가 더 잘 보이는 사용자 인터페이스 변경으로 인해 최근에 마이그레이션된 관리자는 이전에는 보이지 않았던 이러한 개인 계정을 볼 수 있습니다.

## <a name="solution"></a>솔루션
문제를 해결하려면 구독자 정보를 편집하여 로그인 전자 메일 주소를 업데이트해야 합니다.  개별 구독자를 편집하거나 일괄적으로 편집할 수 있습니다. 자세한 내용은 [구독 편집](edit-license.md)을 참조하세요.

##  <a name="next-steps"></a>다음 단계
- 구독자 전자 메일 주소를 업데이트한 후 로그인 정보가 변경되었음을 구독자에게 알려야 할 수 있습니다.  또한 업데이트된 정보가 포함된 전자 메일을 받게 됩니다.
- 변경이 필요할 수 있는 로그인 전자 메일 주소를 찾기 위해 조직의 [구독자 목록을 필터링](search-license.md)하는 것이 유용할 수 있습니다.  

