---
title: 코드 분석 정책 오류 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b61d7d9718e9557ef153474718542f889ad7629
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576743"
---
# <a name="code-analysis-policy-errors"></a>코드 분석 정책 오류
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

체크 인할 때 코드 분석 정책이 충족 되지 않으면 다음과 같은 오류가 발생 합니다.  
  
 **하나 이상의 프로젝트에 대 한 코드 분석 설정이 코드 분석 정책과 호환 되지 않습니다.**  
  
 코드 분석의 팀 프로젝트 소스 제어에 대한 체크 인 요구 사항이 하나 이상의 코드 프로젝트에서 충족되지 않았습니다. 이 오류는 다음과 같은 하나 이상의 조건에 의해 발생할 수 있습니다.  
  
1. 솔루션에 있는 모든 프로젝트에 대해 코드 분석이 빌드 시에 설정되지 않았습니다.  
  
2. 로컬 규칙 집합에 Visual Studio에서 프로젝트를 덜 제한적인 **동작** 팀 프로젝트 규칙 집합으로 설정 된 규칙을 예를 들어 외 설정 **동작**=**오류**  서버에 해당 **작업** 로 설정 **경고** 하거나 **None** Visual Studio에서 실행 되 고 설정 규칙에).  
  
3. Visual Studio에 지정된 규칙 집합은 팀 프로젝트에 대한 코드 분석 체크 인 정책에 지정된 규칙 집합에 지정된 모든 규칙이 포함되지 않습니다.  
  
   **코드 분석 정책이 실패 했습니다. 프로젝트에 오류가 있는 {0} 빌드가 최신 상태입니다. 또는 합니다.**  
  
   빌드에 오류 오류 수정 되었지만 문제를 해결 한 후 코드 분석을 수행 하지 않았습니다.  
  
   **확인에 실패 했습니다. 코드 분석 정책에 따라 체크 인하는 Visual Studio를 통해 열려 있는 솔루션에 필요 합니다.**  
  
   코드 분석 정책에 따라 모든 파일을 체크 인하는 현재 열려 있는 솔루션에 있어야 필요 합니다. 이 오류를 해결 하려면 체크 인할 파일을 포함 하는 솔루션을 엽니다.  
  
   **모든 보류 중인 체크 인에 파일이 현재 열려 있는 솔루션입니다.**  
  
   코드 분석 정책에 따라 모든 파일을 체크 인하는 현재 열려 있는 솔루션에 있어야 필요 합니다. 이 오류는 열린 솔루션 이지만 "보류 중인 체크 인" 보기에서 일부 파일이 현재 열려 있는 솔루션의 일부가 아닌 경우에 발생 합니다. 이 오류를 해결 하려면 체크 인할 파일을 포함 하는 솔루션을 엽니다.  
  
   **버전의 '{0}' 올바르지 않습니다. 강력한-정책에 지정 된 이름은 '{1}'.**  
  
   이 오류는.NET 프로젝트에 적용 됩니다. 로컬 컴퓨터의 코드 분석 정책에 필요한 규칙.dll이 있지만 버전/공개 키가 일치 하지 않습니다. 이 오류를 해결 하려면 정책 작성자의 업데이트 해야 합니다 *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  자신의 컴퓨터에서 디렉터리입니다.  
  
   **'{0}' 정책에 지정 된 어셈블리가 존재 하지 않습니다.**  
  
   이 오류는.NET 프로젝트에 적용 됩니다. 코드 분석 정책에 필요한 규칙에는 클라이언트 컴퓨터에 설치 하는 해당 dll이 없습니다. 이 오류를 해결 하려면 정책 작성자에서 dll을 업데이트 해야 합니다 *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  자신의 컴퓨터에서 디렉터리입니다.  
  
   **프로젝트 {0} 규칙 설정이 코드 분석 정책 따르지에서 않습니다.**  
  
   이 오류는.NET 프로젝트에 적용 됩니다. 관리 코드 규칙 설정은 정책에 필요한 만큼 엄격한입니다. 이 오류를 해결 하려면 클라이언트 설정이 동일 해야 하거나 서버에 정책 요구 사항을 보다 엄격 합니다.  
  
   **활성 구성에서 코드 분석 사용 되지 않습니다. 구성으로 전환 {0} 프로젝트를 빌드하고 {1} 체크 인하기 전에 합니다.**  
  
   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 활성 구성에서 코드 분석을 사용 하도록 설정 되지 않은 이지만 하나 이상의 코드 분석을 사용 합니다.  
  
   **프로젝트에서 관리 되는 이진에 대 한 코드 분석을 사용 해야 {0} 속성과 체크 인하기 전에 빌드입니다.**  
  
   이 오류에 적용 됩니다 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] .NET 응용 프로그램입니다. 정책 관리 코드 분석을 수행할 수 하는데 클라이언트에서 현재 프로젝트에서 사용 되지 않습니다.  
  
   **프로젝트에서 코드 분석을 사용 해야 {0} 속성과 체크 인하기 전에 빌드입니다.**  
  
   이 오류는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 및 웹 프로젝트입니다. 정책 관리 코드 분석을 수행할 수 하는데 클라이언트에서 현재 프로젝트에서 사용 되지 않습니다.  
  
   **C를 사용 하도록 설정 해야 /C++ 프로젝트에서 코드 분석 {0} 속성과 체크 인하기 전에 빌드입니다.**  
  
   이 오류는 관리 되지 않는 프로젝트에 적용 됩니다. 코드 분석 정책에 따라 C에 대 한 코드 분석 필요 /C++, 하지만 클라이언트에서 현재 프로젝트에서 사용 되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [코드 분석 애플리케이션 오류](../code-quality/code-analysis-application-errors.md)
