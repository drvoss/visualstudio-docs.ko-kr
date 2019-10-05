---
title: 색, 선 스타일 및 기타 모양 속성 제어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cff60ca7fc76563db73c4fc839688e0fba4ab975
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159645"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>색, 선 스타일 및 기타 모양 속성 제어
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

몇 가지 모양 속성 같은 색 노출 될 수 있지만' ' – 즉, 연결 모양의 도메인 속성에 합니다. 다른 사용자가 직접 제어 해야 합니다.  
  
## <a name="exposing-a-property"></a>속성을 노출합니다.  
 도메인 속성의 값으로 색와 같은 일부 셰이프 속성을 연결할 수 있습니다.  
  
 DSL 정의에서 모양, 연결선 또는 다이어그램 클래스를 선택 합니다. 해당 상황에 맞는 메뉴에서 선택 **Add Exposed**를 채우기 색 등의 원하는 속성을 선택 합니다.  
  
 셰이프는 이제 프로그램 코드 또는 사용자로 설정할 수 있는 도메인 속성이 있습니다.  
  
## <a name="dynamically-updating-an-exposed-property"></a>동적으로 노출 된 속성 업데이트  
 일반적으로 노출 된 속성을 다른 속성에 종속 되 게 하려고 합니다. 예를 들어 좋습니다 0 보다 작은 셰이프를 특정 도메인 속성은 때마다 빨간색으로 바뀝니다. 이 종속성을 만듭니다는 [규칙](../modeling/rules-propagate-changes-within-the-model.md)합니다. 예를 들어:  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with class:  
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class CarShapeAddRule : AddRule  
 {  
 // Override the abstract method:  
 public override void ElementAdded(ElementAddedEventArgs e)  
 {  
 base.ElementAdded(e);  
 CarShape shape = e.ModelElement as CarShape;  
 Store store = shape.Store;  
 // Ignore this call if we're currently loading a model:  
 if (store.TransactionManager.CurrentTransaction.IsSerializing)   
  return;  
 Car car = shape.ModelElement as Car;  
 // Code here propagates change as required - for example:  
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;   
 }  
}  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
 protected override Type[] GetCustomDomainModelTypes()  
 {  
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
  types.Add(typeof(CarShapeAddRule));  
  // If you add more rules, list them here.   
  return types.ToArray();  
 }  
 }  
}  
```
