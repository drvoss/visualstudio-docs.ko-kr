---
title: 레거시 언어 서비스의 자동 서식 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157264"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>레거시 언어 서비스의 자동 서식
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

자동 서식 지정 된 언어 서비스를 자동으로 삽입 코드 조각과 사용자 알려진된 코드 구문을 입력을 시작 하는 경우.  
  
## <a name="automatic-formatting-behavior"></a>자동 서식 지정 동작  
 입력 하면 예를 들어 `if`, 언어 서비스는 자동으로 일치 하는 중괄호 삽입 또는 ENTER 키를 누를 경우 언어 서비스에 강제로 적용 삽입 지점이 새 줄 인지에 따라 적절 한 들여쓰기 수준으로 이전 새 범위를 줄이 열립니다.  
  
 자동 서식 지정에 대 한 언어 서비스의 나머지 부분에 사용 되는 명령 필터를 사용할 수도 있습니다. 호출 하 여는 중괄호를 강조 표시도 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
