---
title: 소스 제어 디자인 결정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89d125dc52340e8528ee9692d5de00784632e6f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187894"
---
# <a name="source-control-design-decisions"></a>소스 제어 디자인 결정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어를 구현 하는 경우 다음 디자인 결정 사항은 프로젝트에 대 한 고려 되어야 합니다.  
  
## <a name="will-information-be-shared-or-private"></a>공유 또는 개인 정보 수 있습니까?  
 가능 하면 가장 중요 한 디자인 결정 중 이며 어떤 정보를 공유할 수 있는 개인 란 예를 들어 프로젝트 파일 목록을 공유는 있지만 파일의이 목록에 일부 사용자가 해야 할 개인 파일. 컴파일러 설정을 공유 하지만 시작 프로젝트는 일반적으로 전용입니다. 순수 하 게 공유, 재정의 하 여 공유 또는 순수 하 게 개인 설정은입니다. 기본적으로 개인 항목을 솔루션 사용자 옵션 (.suo) 파일 같은를 확인 하지 [!INCLUDE[vsvss](../../includes/vsvss-md.md)]합니다. .Suo 파일, 예를 들어 만든 특정 개인 파일 등 개인 파일에 개인 정보를 저장 해야 합니다.는. csproj.user 파일에 대 한 Visual C# 또는. vbproj.user 파일 Visual Basic에 대 한 합니다.  
  
 이 의사 결정 일체 이며 항목-단위로 수 있습니다.  
  
## <a name="will-the-project-include-special-files"></a>특수 한 파일 포함 된 프로젝트?  
 다른 중요 한 디자인 결정 프로젝트 구조를 특수 한 파일을 사용 하는지 여부입니다. 특수 한 파일은 솔루션 탐색기에서에 체크 표시 인 및 체크 아웃 대화 상자에 있는 파일의 기반이 되는 숨겨진된 파일입니다. 특수 한 파일을 사용 하는 경우 다음이 지침을 따르세요.  
  
1. 프로젝트 루트 노드를 사용 하 여 특수 한 파일을 연결 하지 않는-즉, 프로젝트 파일 자체입니다. 프로젝트 파일에는 단일 파일 이어야 합니다.  
  
2. 특수 한 파일 추가, 제거 또는 적절 한 프로젝트의 이름을 바꿀 때 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 파일은 특수 한 파일을 지정 하는 플래그 집합을 사용 하 여 이벤트를 발생 해야 합니다. 적절 한 호출 프로젝트에 대 한 응답으로 환경에서 이러한 이벤트 라고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 메서드.  
  
3. 프로젝트 또는 편집기를 호출 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 파일의 경우 해당 파일에 연결 된 특수 파일이 자동으로 체크 아웃 되지 않은 합니다. 파일의 부모와 함께 특수 파일을 전달 합니다. 환경에서 전달 되는 모든 파일 간의 관계를 감지 하 고 적절 하 게 체크 아웃 UI에 특수 한 파일을 숨깁니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
