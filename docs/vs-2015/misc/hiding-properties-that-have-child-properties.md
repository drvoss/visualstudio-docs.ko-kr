---
title: 자식 속성을 가진 속성 숨기기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822388"
---
# <a name="hiding-properties-that-have-child-properties"></a>자식 속성을 가진 속성 숨기기
자식 속성을 가진 속성 숨기기 하려고 합니다.  
  
- 프로젝트 중첩 된 경우 부모 프로그래밍 방식으로 프로젝트 자식 프로젝트의 일부 측면을 제어 합니다.  
  
- 컨트롤을 사용 하 여 특수 한 디자이너를 사용 하 여 컨트롤의 모든 속성에 대 한 모든 권한을 개발자에 게를 제공 하지 않을 경우.  
  
- 개체의 소유권 범위 속성 보기를 제한 하려는 경우.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>자식 속성을 가진 속성을 숨기려면  
  
1. 설정 된 `pfDisplay` 에서 매개 변수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> 에 `FALSE`입니다.  
  
2. 설정 된 `pfHide` 에서 매개 변수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 에 `TRUE`입니다.  
  
## <a name="see-also"></a>참고 항목  
 [속성 눈금 표시](../extensibility/internals/properties-display-grid.md)