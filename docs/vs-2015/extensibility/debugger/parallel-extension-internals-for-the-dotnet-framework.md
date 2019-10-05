---
title: 확장 기능의 내부.NET Framework에 대 한 병렬 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42c472190469e7d008fa8c525f50eabfaf37053f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680936"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework에 대한 병렬 확장 기능 내부
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 섹션에서는 내부 형식, 메서드를 설명 하 고 도움이 되는 클래스의 필드 parallel extensions to.NET Framework에 대 한 사용자 지정 디버거를 구현 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)  
 내부 데이터 멤버를 설명 합니다 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 클래스입니다.  
  
 [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 내부 데이터 멤버를 설명 합니다 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 클래스입니다.  
  
 [ContingentProperties 클래스](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 내부 데이터 멤버를 설명 합니다 `System.Threading.Tasks.ContingentProperties` 클래스입니다.  
  
 [AsyncTaskMethodBuilder 구조체](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 내부 멤버를 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 구조입니다.  
  
 [AsyncTaskMethodBuilder\<TResult> 구조](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 내부 멤버를 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 구조입니다.  
  
 [AsyncVoidMethodBuilder 구조체](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 내부 멤버를 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 구조입니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [병렬 프로그래밍](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
