---
title: '방법: 상태 표시줄 업데이트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703140"
---
# <a name="how-to-update-the-status-bar"></a>방법: 상태 표시줄 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 **상태 표시줄** 는 하나 이상의 상태 텍스트 줄 또는 표시기를 포함 하는 여러 응용 프로그램 창의 아래쪽에 있는 컨트롤 막대입니다.  
  
### <a name="to-update-the-status-bar"></a>상태 표시줄을 업데이트 하려면  
  
1. 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 폼 보기와 코드 보기와 같은 편집기를 제공 하는 각 개별 뷰 개체 (DocView).  
  
2. IDE가 호출 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>에서 정보를 업데이트 합니다 **상태 표시줄** 의 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>입니다.  
  
    > [!NOTE]
    > IDE 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 만 하면 문서 창의 처음 활성화 합니다. 문서 창 활성화 되어 있는 경우의 나머지 부분에서는 업데이트 해야 합니다 **상태 표시줄** 편집기 변경의 상태 정보.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 A **상태 표시줄** 네 개의 별도 필드를 포함 합니다.  
  
- 상태 텍스트  
  
- 진행률 표시줄  
  
- 애니메이션된 아이콘  
  
- 편집기 정보  
  
  자세한 내용은 [상태 표시줄](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)합니다.  
  
  IDE에서 자동으로 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 메서드의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 구현에 문서 창을 활성화할 때입니다.  
  
  VSPackage 구현자는 상태 표시줄에서 상태 텍스트를 업데이트 하는 일을 담당 합니다. IDE 상태 텍스트 필드를 빈 텍스트로 설정 된 경우이 문자열 "READY"로 다시 설정 ("") 유휴 시간에 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [상태 표시줄](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
