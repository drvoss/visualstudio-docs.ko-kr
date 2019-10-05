---
title: DSL 정의에 확장 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd45a2345e6e5b28b74cb27fac226514c3f92a04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159074"
---
# <a name="adding-extensions-to-dsl-definitions"></a>DSL 정의에 확장 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 정의 확장을 사용 하면 도메인 특정 언어 (DSL)에 대 한 확장의 패키지를 만들 수 있습니다. 에 VSIX Visual Studio Integration Extension ()에 포함 되는 DSL 확장을 동일한 방식으로 DSL에서 사용자의 컴퓨터에 설치할 수 있습니다. 추가 기능 동적으로 사용 하도록 설정 하 고 런타임 시 사용 하지 않도록 설정 될 수 있습니다. Dsl 확장에 대 한 명시적으로 디자인할 수 없고 확장 디자인할 수 있습니다 나중 또는 제 3 자에서 확장 된 DSL을 변경 하지 않고 있습니다.  
  
 추가 기능을 다음과 같습니다.  
  
- 모델 및 프레젠테이션 요소에 대 한 속성  
  
- 모양 및 연결선에 대 한 decorator  
  
- 클래스, 관계, 모양 및 연결선  
  
- 유효성 검사 제약 조건  
  
- 도구 상자 항목 및 탭  
  
  확장된을 사용 하는 DSL의 사용자 만들고 추가 기능의 인스턴스가 포함 된 모델을 저장할 수 있으며 적절 한 확장명 설치 되어 있는 다른 사용자가 읽을 수 있습니다. 확장을 설치 하지 않은 사용자는 추가 기능을 사용할 수 없습니다 하지만 업데이트 하 고 추가 기능을 손실 하지 않고 모델을 저장할 수 있습니다.  
  
  샘플 코드와이 기능에 대 한 자세한 정보에 대 한 참조를 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128) 웹 사이트입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)
