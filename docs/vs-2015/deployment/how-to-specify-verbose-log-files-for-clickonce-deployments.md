---
title: '방법: ClickOnce 배포에 대 한 자세한 정보 표시 로그 파일을 지정 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441614"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>방법: ClickOnce 배포에 대한 자세한 로그 파일 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 모든 배포에 대 한 활동 로그를 유지 관리합니다. 이러한 로그는 설치, 초기화, 업데이트 및 제거와 관련 된 세부 정보 문서는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 합니다. 세부 사항이 증가 하는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 레지스트리 편집기를 사용 하 여 이러한 로그 파일에 쓰기 (**regedit.exe**) 세부 정보 표시 수준을 지정 하려면.  
  
> [!CAUTION]
> 레지스트리 편집기를 잘못 사용 하면 운영 체제를 다시 설치 해야 할 수 있는 심각한 문제가 발생할 수 있습니다. 레지스트리 편집기를 사용할 때는 주의하세요.  
  
 다음 절차에 대 한 세부 정보 표시 수준을 지정 하는 방법에 설명 합니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 현재 사용자에 대 한 파일을 기록 합니다. 자세한 정도 줄이려면이 레지스트리 값을 제거 합니다.  
  
### <a name="to-specify-verbose-log-files"></a>자세한 로그 파일을 지정 하려면  
  
1. 오픈 **Regedit.exe**합니다.  
  
2. 노드로 이동 `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`합니다.  
  
3. 필요한 경우 라는 새 문자열 값을 만듭니다. `LogVerbosityLevel`합니다.  
  
4. 설정 된 `LogVerbosityLevel` 값을 `1`입니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)
