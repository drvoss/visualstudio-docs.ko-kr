---
title: 사용자에 게 피드백 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7773c611733ccec525fc25264311e72c1dfe36e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537682"
---
# <a name="feedback-to-the-user"></a>사용자에 대한 피드백
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE) 시각적 피드백을 사용할 수 있는 기능에 관한 사용자의 현재 선택 영역 및 전역 선택 컨텍스트를 기반으로 합니다. 다음 표에서 다른 선택 컨텍스트에서 사용할 수 있는 기능을 보여 줍니다.  
  
|선택 항목 컨텍스트|사용할 수 있는 기능|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|현재 제품 설정|특정 제품|  
|활성 계층 구조|계층 구조 형식 관련|  
|활성 계층 구조 항목|계층 항목 형식별|  
|활성 문서|문서 형식 특정|  
|창 맨 위에 있는 다중 문서 인터페이스 MDI)|창 형식별|  
|현재 선택 항목 컨텍스트|특정 선택 항목 컨텍스트|  
  
 만 사용자가 필요 하 고 지속적으로 일관 된 선택 및 환경 상황에 맞는 피드백을 제공 하는 기능을 노출, IDE의 복잡성을 줄어듭니다. 다음 규칙에는 IDE에서 창으로 열릴 때마다 적용 됩니다.  
  
- 창이 해당 선택 항목 컨텍스트를 변경, 선택 피드백 창에서 명확 하 게 표시 됩니다 고 동적 도움말 창에서 표시 하는 경우 업데이트 됩니다 현재 컨텍스트를 반영 하도록 합니다.  
  
- 전역 선택 컨텍스트를 변경 하는 창, 모든 상황에 맞는 메뉴, 활성 계층 구조 창 및 응용 프로그램 제목 표시줄 현재 컨텍스트를 반영 하도록 업데이트 됩니다.  
  
- 창에서 현재 선택 영역에 대 한 속성을 노출 해야 합니다 **속성** 창 및 필요에 따라 표시 하는 경우를 **속성 페이지** 대화 상자.  
  
- 창의 속성을 노출 하지 않거나 전역 선택 컨텍스트를 변경, 선택 피드백이 IDE의 활성 창에 더 이상 없습니다 창에서 유지 되어야 합니다.  
  
- 모든 문서 관련 도구 창에서 활성 문서를 반영 지속적으로 해야 합니다.  
  
- 메뉴, 도구 모음 및 응용 프로그램 제목 표시줄 클라이언트 창 맨 위에 있는 다중 문서 인터페이스 MDI ()를 반영 해야 합니다.  
  
  예를 들어, Visual Basic 웹 응용 프로그램 프로젝트 내에서 Web Form의 HTML 뷰가 열려 시간과 사용자가 선택 된 `<td>` 태그를 다음과 같이 하면 피드백이 제공 됩니다.  
  
- 활성 창에 표시 된 선택 이며에 반영 합니다 **속성** 창입니다.  
  
- 문서별 **도구 상자** 활성 문서를 반영 하도록 업데이트 됩니다.  
  
- **편집기** 도구 모음 및 **테이블** 메뉴가 표시 됩니다 하 고 제목 표시줄 Web Form 창에 맞게 업데이트 합니다.  
  
- 일반적으로 활성 계층 구조 창 **솔루션 탐색기**, 및 해당 제목 표시줄 업데이트를 반영 하도록 현재 컨텍스트에 상황에 맞는 **프로젝트** 메뉴 명령은 활성 웹에 이제 적용 응용 프로그램 프로젝트입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)   
 [계층 구조 및 선택](../../extensibility/internals/hierarchies-and-selection.md)
