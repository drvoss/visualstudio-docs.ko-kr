---
title: Project Context | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 175ee37628b1794377a6b4e9e94cef52466cd291
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328352"
---
# <a name="project-context"></a>프로젝트 컨텍스트
사용자 추가, 프로젝트 및 프로젝트 항목을 사용 하 여 작동 하는 경우 IDE 다양 한 작업을 수행할지 결정할 프로젝트 컨텍스트의 개념을 사용 합니다.

 일반적으로 파일은 사용자가 명시적으로 선택 하 여 작성 하는 표준 프로젝트 개체를 **새 프로젝트** 명령 또는 선택 하 여 사용할 수 있도록 설정 합니다 **프로젝트 열기** 명령을  **파일** 메뉴. 이러한 경우 파일을 만들고 프로젝트의 컨텍스트에서 열 및 프로젝트 형식 문서를 편집 하는 것에 대 한 컨텍스트를 정의 합니다.

 일부 프로젝트는 매우 다양 한 컨텍스트를 제공 합니다. 예를 들어, 프로젝트에는 프로젝트 범위, 프로그래밍 방식으로 네임 스페이스 또는 데이터 바인딩에 대 한 프로젝트 범위의 데이터베이스 연결을 관리합니다. 사용자 파일 또는 데이터베이스 연결 솔루션 탐색기에 표시 된 프로젝트 항목을 같은 특정 프로젝트 개체를 사용 하 여 직접 자주 열 수 있습니다.

 다른 시간에 항목의 프로젝트 컨텍스트를 명시적으로 지정 하지. 예를 들어 항목의 컨텍스트에서 사용할 수 없는 사용자가 선택 하 여 파일을 열면 합니다 **기존 파일 열기** 명령을 합니다 **파일** 메뉴에서 파일 또는 사용자가 클릭할 때 디버거가 작동 하는 경우는 **파일에서 찾기** 명령에 **찾기 및 바꾸기** 대화 상자. IDE 호출 하 여 이러한 상황을 처리할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> 모범 프로젝트 문서를 찾는 프로세스를 관리 합니다.

## <a name="see-also"></a>참고 항목
- [프로젝트 우선 순위](../../extensibility/internals/project-priority.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)