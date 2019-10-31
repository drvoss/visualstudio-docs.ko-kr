---
title: 도구 창 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34fddd6513aad612398c700b935c6d1d3ee72b59
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186269"
---
# <a name="register-a-tool-window"></a>도구 창 등록
<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 및 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>를 사용 하 여 도구 창을 등록할 수 있습니다.

## <a name="example"></a>예제

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 위의 코드에서 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>는 Visual Studio를 사용 하 여 `PersistedWindowPane` 및 `DynamicWindowPane` 도구 창을 등록 합니다. 지속형 도구 창은 고정 되어 있고 **솔루션 탐색기**탭 하 고 동적 창에는 기본 시작 위치와 크기가 지정 됩니다. 동적 창이 일시적으로 수행 되어 시작할 때 생성 되지 않았음을 나타냅니다. 그러면 시스템 레지스트리의 `ToolWindows` 키에 `DontForceCreate` 값이 기록 됩니다. 자세한 내용은 [도구 창 표시 구성](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015)을 참조 하세요.
