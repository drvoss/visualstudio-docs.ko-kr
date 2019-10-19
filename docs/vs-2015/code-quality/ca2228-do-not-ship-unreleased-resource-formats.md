---
title: 'CA2228: 릴리스되지 않은 리소스 형식을 제공 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9297ea0bb24eed54d0134a5f3c0fce87e6757adb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662880"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: 릴리스되지 않은 리소스 형식을 제공하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 리소스 파일이 현재 지원 되지 않는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 사용 하 여 빌드 되었습니다.

## <a name="rule-description"></a>규칙 설명
 @No__t_0 시험판 버전을 사용 하 여 작성 된 리소스 파일은 지원 되는 버전의 .NET Framework에서 사용할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 지원 되는 버전의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k을 사용 하 여 리소스를 빌드합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.
