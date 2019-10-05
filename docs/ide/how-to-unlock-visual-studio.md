---
title: '방법: Visual Studio 잠금 해제'
titleSuffix: ''
ms.date: 03/30/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: fe0aa86be242e9a7e7ed8d877944c66247718167
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926298"
---
# <a name="how-to-unlock-visual-studio"></a>방법: Visual Studio 잠금 해제

최대 30일 동안 무료로 Visual Studio 평가판을 사용할 수 있습니다. IDE에 로그인하면 평가판 사용 기간이 90일로 연장됩니다. Visual Studio를 계속 사용하려면 다음과 같은 방법으로 IDE를 잠금 해제합니다.

- 온라인 구독 사용

- 제품 키 입력

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>온라인 구독을 사용하여 Visual Studio의 잠금을 해제하려면

Microsoft 계정이나 회사 또는 학교 계정과 연결된 Visual Studio 구독 또는 Azure DevOps 조직을 사용하여 Visual Studio를 잠금 해제하려면:

1. IDE의 오른쪽 위에 있는 **로그인** 단추를 선택하거나 **파일** > **계정 설정**을 선택하여 **계정 설정** 대화 상자를 열고 **로그인** 단추를 선택합니다.

1. Microsoft 계정이나 회사 또는 학교 계정에 대한 자격 증명을 입력합니다. Visual Studio에서 해당 계정과 연결된 Visual Studio 구독 또는 Azure DevOps 조직을 찾습니다.

> [!IMPORTANT]
> **팀 탐색기** 도구 창에서 Azure DevOps 조직에 연결하면 Visual Studio에서 연결된 온라인 구독을 자동으로 찾습니다. Azure DevOps 조직에 연결하면 Microsoft 계정 및 회사 또는 학교 계정을 사용하여 로그인할 수 있습니다. 해당 사용자 계정에 대한 온라인 구독이 있으면 Visual Studio에서 IDE를 자동으로 잠금 해제합니다.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>제품 키를 사용하여 Visual Studio의 잠금을 해제하려면

1. **파일** > **계정 설정**을 선택하여 **계정 설정** 대화 상자를 열고 **제품 키가 있는 라이선스** 링크를 선택합니다.

1. 제공된 입력란에 제품 키를 입력합니다.

> [!TIP]
> 시험판 버전의 Visual Studio에는 제품 키가 없습니다. 시험판 버전을 사용하려면 IDE에 로그인해야 합니다.

## <a name="address-license-problem-states"></a>라이선스 문제 해결 상태

### <a name="update-stale-licenses"></a>부실 라이선스 업데이트

Visual Studio에서 라이선스가 부실하게 된다는 다음 메시지를 본 적이 있을 수 있습니다. “라이선스가 만료되어 업데이트해야 합니다.”

![Visual Studio 부실 라이선스 메시지](../ide/media/vs2017_stale-license.png)

이 메시지는 구독이 여전히 유효할 수 있지만 Visual Studio에서 구독을 최신으로 유지하는 데 사용하는 라이선스 토큰이 새로 고쳐지지 않았으므로 다음 이유 중 하나로 인해 부실해졌음을 나타냅니다.

- Visual Studio를 사용한 적이 없거나 오랫동안 인터넷에 연결하지 않았습니다.
- Visual Studio에서 로그아웃했습니다.

라이선스 토큰이 부실해지기 전에 Visual Studio에서 먼저 자격 증명을 다시 입력하라는 경고 메시지가 표시됩니다.

자격 증명을 다시 입력하지 않으면 토큰이 부실해지고 **계정 설정** 대화 상자에 토큰이 완전히 만료되기까지 남은 기간이 표시됩니다. 토큰이 만료된 후에는 계정의 자격 증명을 다시 입력해야 Visual Studio를 계속 사용할 수 있습니다.

> [!Important]
> 인터넷 연결이 제한되거나 인터넷에 연결되지 않은 환경에서 오랫동안 Visual Studio를 사용하는 경우 작업이 중단되지 않도록 제품 키를 사용하여 Visual Studio의 잠금을 해제해야 합니다.

### <a name="update-expired-licenses"></a>만료된 라이선스 업데이트

구독이 완전히 만료되어 Visual Studio 액세스 권한이 더 이상 없으면 사용자 구독을 갱신하거나 구독이 있는 다른 계정을 추가해야 합니다. 사용 중인 라이선스에 대한 자세한 정보를 보려면 **파일** > **계정 설정**으로 이동하고 대화 상자의 오른쪽에 있는 라이선스 정보를 살펴봅니다. 다른 계정에 연결된 다른 구독이 있는 경우 **계정 추가** 링크를 선택하여 대화 상자의 왼쪽에 있는 **모든 계정** 목록에 해당 계정을 추가합니다.

## <a name="see-also"></a>참고 항목

* [Visual Studio에 로그인](../ide/signing-in-to-visual-studio.md)
