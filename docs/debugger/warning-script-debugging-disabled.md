---
title: '경고: 스크립트 디버깅 사용 안 함 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50fe457e2b66a4c1ddafc9fc24658f58f6f753d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901025"
---
# <a name="warning-script-debugging-disabled"></a>경고: 스크립트 디버깅 사용 안 함
Internet Explorer에서는 현재 스크립트 디버깅을 사용하지 않습니다.

 이 경고는 Internet Explorer에서 스크립트 디버깅을 사용할 수 없는 상태에서 스크립트를 디버깅할 때 발생합니다. 보안상의 이유로 Internet Explorer에서는 스크립트 디버깅을 기본적으로 사용하지 않습니다.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Internet Explorer에서 스크립트 디버깅을 사용하려면

1. Internet Explorer의 **도구** 메뉴에서 **인터넷 옵션**을 선택합니다.

2. **인터넷 옵션** 대화 상자에서 **고급** 탭을 클릭합니다.

3. **고급** 탭의 **설정** 상자에서 **탐색** 범주를 찾습니다.

4. **스크립트 디버깅 사용 안 함(Internet Explorer)** 의 선택을 취소합니다.

5. **확인**을 클릭합니다.

6. Internet Explorer를 종료하고 다시 시작합니다.

     그러면 새 설정이 적용됩니다.

## <a name="see-also"></a>참고 항목
- [방법: 스크립트에 연결](../debugger/how-to-attach-to-script.md)