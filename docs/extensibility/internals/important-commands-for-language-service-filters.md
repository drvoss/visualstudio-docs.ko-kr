---
title: 언어에 대 한 중요 명령 필터 서비스 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73ecbad3578c356ed9f82f79cdf9144d4c2bd32d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335081"
---
# <a name="important-commands-for-language-service-filters"></a>언어 서비스 필터에 대한 중요 명령
완전 한 기능의 언어 서비스 필터를 만들려는 경우에 다음 명령을 처리 하는 것이 좋습니다. 명령 식별자의 전체 목록에 정의 되어는 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 관리 되지 않는 관리 되는 코드와 Stdidcmd.h 헤더에 대 한 열거형 파일 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 코드입니다. Stdidcmd.h 파일에서 찾을 수 있습니다 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Common\Inc 합니다.

## <a name="commands-to-handle"></a>핸들에는 명령

> [!NOTE]
> 다음 테이블의 모든 명령에 대 한 필터링 하는 필수적이 지 않습니다.

|명령|설명|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|클릭할 때 보냅니다. 이 명령은 바로 가기 메뉴를 제공 하는 것을 나타냅니다. 이 명령은 처리 하지 않는 경우 텍스트 편집기 모든 언어 관련 명령이 없는 기본 바로 가기 메뉴를 제공 합니다. 이 메뉴에서 직접 명령에 포함 하려면 명령을 처리 하 고 직접 바로 가기 메뉴를 표시 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 CTRL + J를 전송 합니다. 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 문 완성 상자를 표시 하려면.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 문자를 전송 합니다. 이 명령은 트리거 문자를 입력 하 고 문을 제공을 완료, 메서드 팁 및 구문 색 지정 등의 텍스트 마커 중괄호 일치 하는 시기를 결정 하 고 오류 마커를 모니터링 합니다. 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 문 완성을 위해 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 메서드를를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 메서드 팁에 대 한. 텍스트 마커를 지원 하기 위해 입력 한 문자 마커를 업데이트 해야 하는지 여부를 확인 하려면이 명령을 모니터링 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 Enter 키를 전송 합니다. 호출 하 여 메서드 팁 창 해제할 시기를 결정 하려면이 명령을 모니터링 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. 텍스트 뷰는 기본적으로이 명령을 처리합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 백스페이스 키를 전송 합니다. 모니터를 호출 하 여 메서드 팁 창 해제할 때를 결정 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>합니다. 텍스트 뷰는 기본적으로이 명령을 처리합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|메뉴 또는 바로 가기 키를 전송 합니다. 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 메서드를는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 팁 창 매개 변수 정보를 업데이트 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|사용자가 변수를 마우스로 가리킬 또는 변수에 커서를 배치를 선택 하면 전송 **요약 정보** 에서 **IntelliSense** 에 **편집** 메뉴. 호출 하 여 팁에서 변수 형식을 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>합니다. 활성 상태 이면 디버깅 팁 변수의 값도 표시 됩니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 사용자가 CTRL + 스페이스바를 전송 합니다. 이 명령 언어 서비스가 호출 하도록 지시 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|일반적으로 메뉴에서 보낸 **주석 선택** 또는 **주석 선택** 에서 **고급** 에 **편집** 메뉴. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 주석으로 처리 된 선택한 텍스트를 사용자에 게 나타냅니다. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 선택한 텍스트를 주석으로 처리 하는 사용자를 원한다는 것을 나타냅니다. 이러한 명령은 언어 서비스에만 구현할 수 있습니다.|

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)