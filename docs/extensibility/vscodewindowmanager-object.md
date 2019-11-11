---
title: VSCodeWindowManager 개체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c67fb719c6ec87e7707a406e2e7f67cd71569b39
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189040"
---
# <a name="vscodewindowmanager-object"></a>VSCodeWindowManager 개체

언어 서비스는 코드 창 관리자를 구현 하며 장식 (예: 드롭다운 모음) 관리를 담당 합니다. 자세한 내용은 [레거시 API를 사용 하 여 코드 창 사용자 지정](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)을 참조 하세요.

다음 표에서는 `VSCodeWindowManager` 개체의 인터페이스를 보여 줍니다.

|인터페이스|설명|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|코드 창에서 장식 (예: 드롭다운 모음)을 추가 하거나 제거할 수 있습니다.|