---
title: '방법: ASP.NET 예외 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ccd8c399bd92bd98307d44aff913c30390033c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205432"
---
# <a name="how-to-debug-aspnet-exceptions"></a>방법: ASP.NET 예외 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

예외 디버깅은 강력한 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션을 개발하는 데 중요한 요소입니다. 예외를 디버깅 하는 방법에 대 한 일반 정보를 [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)합니다.  
  
 처리되지 않은 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 예외를 디버깅하려면 디버거에서 실행을 중지해야 합니다. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 런타임에는 최상위 예외 처리기가 있습니다. 따라서 디버거는 처리되지 않은 예외에서 기본적으로 중단되지 않습니다. 예외가 throw 될 때 디버거를 중단 하려면를 선택 해야 **예외가 발생할 경우 중단: 발생** 에서 특정 예외에 대 한 설정 된 **예외** 대화 상자.  
  
 내 코드만 사용 하도록 설정한 경우 **예외가 발생할 경우 중단: Throw 된** .NET Framework 메서드 또는 다른 시스템 코드에서 예외가 throw 되 면 즉시 중단 하도록 디버거를 발생 하지 않습니다. 이러한 경우 디버거의 실행은 비시스템 코드를 적중해야 중단됩니다. 그러므로 예외가 발생할 때 시스템 코드를 단계별로 수행할 필요가 없습니다.  
  
 내 코드만 더욱 유용할 수 있는 또 다른 옵션을 제공 합니다. **예외가 중단 합니다. 사용자가 처리 하지 않은**합니다. 예외에 대해 이 설정을 선택하면 디버거는 사용자 코드에서 예외를 catch하여 처리하지 않는 경우에 한해서만 사용자 코드에서 실행을 중단합니다. 이렇게 설정할 경우 최상위 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 예외 처리기가 사용자가 작성하지 않은 코드에 있기 때문에 해당 처리기의 결과가 무시됩니다.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>내 코드만 옵션을 사용하여 ASP.NET 예외 디버깅을 설정하려면  
  
1. **디버그** 메뉴에서 **예외**를 클릭합니다.  
  
     **예외** 대화 상자가 표시됩니다.  
  
2. **Common Language Runtime Exceptions** 행에서 **Throw**되거나 **사용자가 처리하지 않음**을 선택합니다.  
  
     **사용자가 처리하지 않음** 설정을 사용하려면 **내 코드만**을 사용하도록 설정해야 합니다.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>최상의 방법으로 ASP.NET 예외 처리를 수행하려면  
  
- 예측 가능하며 처리 방법을 알고 있는 예외를 throw할 수 있는 코드의 바깥쪽에 `try … catch` 블록을 배치합니다. 예를 들어, XML 웹 서비스 또는 SQL Server에 직접 응용 프로그램 호출을 생성, 코드에 있어야 **try... catch** 되어 발생할 수 있는 다양 한 예외를 차단 합니다.
