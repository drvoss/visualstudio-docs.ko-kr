---
title: VSCodeWindow 개체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 165855fc6f8e63c6c7ad84cb8432419258b7ba4e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322371"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 개체
코드 창에는 일반적으로 하나 이상의 텍스트 뷰를 포함할 수 있는 특수 문서 창입니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 개체입니다.

 아키텍처 측면에서 코드 창에는 창 프레임 내에 있는 문서 창이입니다. 기능적으로 코드 창에는 추가 기능을 사용 하 여 문서 창 단순히입니다. (MDI) 다중 문서 인터페이스 모드로 코드 MDI 자식 프레임입니다. 자세한 내용은 [레거시 API를 사용 하 여 코드 창을 사용자 지정](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)합니다.

 다음 표에서 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 개체입니다.

|메서드|설명|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|전역적으로 고유 식별자 (GUID)를 식별 하는 서비스를 찾으려면 일반 액세스 메커니즘을 제공 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|하나 이상의 코드 보기를 포함 하는 여러 문서 MDI (인터페이스) 자식을 나타냅니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|창 프레임을 채웁니다.|

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)