---
title: 암호화 경고 | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c573d461b477bbcdc7e988ea66f03d5a7cc0fdb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201440"
---
# <a name="cryptography-warnings"></a>암호화 경고
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

암호화를 올바르게 사용하여 더 안전한 라이브러리 및 애플리케이션을 지원하는 암호화 경고입니다. 이들 경고는 프로그램의 보안 결함을 방지하는 데 도움이 됩니다. 이들 경고를 비활성화하는 경우 코드에 그 이유를 명확하게 표시하고 개발 프로젝트의 지정된 보안 담당자에게 이 사실을 알려야 합니다.  
  
|규칙|Description|  
|----------|-----------------|  
|[CA5350: 약한 암호화 알고리즘 사용 안 함](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|오늘날 여러 가지 이유로 약한 암호화 알고리즘 및 해시 함수가 사용되지만 데이터의 무결성과 기밀성을 보장하기 위해서는 이 방법을 사용하지 않아야 합니다.        이 규칙은 코드에 TripleDES, SHA1 또는 RIPEMD160 알고리즘이 있을 때 발생합니다.|  
|[CA5351 끊어진 암호화 알고리즘을 사용하지 마십시오.](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|끊어진 암호화 알고리즘은 안전하지 않은 것으로 간주되므로 사용해서는 안 됩니다. 이 규칙은 코드에 MD5 해시 알고리즘 또는 DES나 RC2 암호화 알고리즘이 있을 때 트리거됩니다.|
