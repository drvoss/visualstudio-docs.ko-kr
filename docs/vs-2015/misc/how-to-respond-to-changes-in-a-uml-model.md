---
title: 'How to: Respond to Changes in a UML Model | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293395"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>방법: UML 모델의 변경 내용에 응답
Visual Studio의 UML 모델에서 변경이 발생할 때마다 실행되는 코드를 작성할 수 있습니다. 사용자 및 다른 Visual Studio 확장에 의해 직접 수행된 변경에 대해 똑같이 반응합니다. UML 모델을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

> [!WARNING]
> 이러한 방법은 UML API에서 지원되지 않습니다. Visual Studio의 이후 버전에서 작동하지 않을 수 있습니다.

## <a name="see-also"></a>관련 항목:
 [Navigate the UML model](../modeling/navigate-the-uml-model.md) [Event Handlers Propagate Changes Outside the Model](../modeling/event-handlers-propagate-changes-outside-the-model.md) [Sample: Color by Stereotype](https://go.microsoft.com/fwlink/?LinkId=213841)