---
title: 프로젝트 및 편집기에 대 한 추가 소스 제어 지침 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9c04623ed276bf10784ccdf895c5abb1c6e9903
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315865"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>프로젝트 및 편집기에 대 한 추가 소스 제어 지침
프로젝트 및 편집기에 소스 제어를 지원 하기 위해 준수 해야 하는 지침의 여러 가지가 있습니다.

## <a name="guidelines"></a>지침
 프로젝트 또는 편집기 소스 제어를 지원 하려면 다음을 수행 해야 합니다.

|영역|프로젝트|편집기|설명|
|----------|-------------|------------|-------------|
|파일의 개인 복사본|X||환경 개인 파일 복사본을 지원합니다. 즉, 프로젝트에 참여 하는 각 사용자에 해당 프로젝트에서 파일을 자신의 고유한 개인 복사본이 있습니다.|
|ANSI/유니코드 지 속성|X|X|지 속성 코드를 작성 하는 경우 대부분의 원본 제어 프로그램에서 유니코드를 현재 지원 하지 않으므로 ANSI 형식으로 파일을 유지 합니다.|
|파일을 열거|X||프로젝트 내의 모든 파일의 특정 목록이 있어야 하며 사용 하 여 파일 목록을 열거 하는 일을 할 수 있어야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). 프로젝트에서 항목 이름을 노출 해야 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> 구현 및 지원을 이름 조회 (특수 한 파일 포함)를 통해 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> 구현 합니다.|
|텍스트 형식|X|X|가능한 경우 파일 서로 다른 버전의 병합을 지원 하도록 텍스트 형식 이어야 합니다. 파일이 텍스트 형식에 없는 파일의 다른 버전을 사용 하 여 나중에 병합할 수 없습니다. 원하는 텍스트 형식은 XML입니다.|
|참조 기반|X||프로젝트 기반 참조는 쉽게 소스 제어에서 지원 됩니다. 그러나 디렉터리 기반 프로젝트와 프로젝트 파일과 디스크에 있는지 여부에 관계 없이 필요에 따라 해당 파일의 목록을 생성할 수 있습니다도 소스 컨트롤에서 지원 됩니다. 소스 제어에서 프로젝트를 열 때 프로젝트 파일의 모든 파일 하기 전에 먼저 상태로 전환 됩니다.|
|개체 및 예측 가능한 순서로 속성 유지|X|X|병합을 용이 하 게 사전순으로 같은 예측 가능한 순서로 파일을 유지 합니다.|
|다시 로드|X|X|디스크에서 파일이 변경 되 면 편집기 다시 로드 수 있어야 합니다. 소스 제어에 참가 하는 경우 환경은 데이터를 다시 로드를 호출 하 여 프로그램 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 구현 합니다. 가장 어려운 다시 로드 경우 체크 아웃 IVsQueryEditQuerySave를 호출 하는 동안 발생 한 경우::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 및 정보 처리 됩니다. 그러나 다시 로드 코드는이 상황에서 실행 되도록 있어야 합니다.<br /><br /> 환경에는 프로젝트 파일이 자동으로 다시 로드합니다. 그러나 프로젝트를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 계층을 다시 로드를 지원 하기 위해 중첩 프로젝트 파일에 중첩 된 경우.|

## <a name="see-also"></a>참고자료
- [소스 제어를 지원 합니다.](../../extensibility/internals/supporting-source-control.md)