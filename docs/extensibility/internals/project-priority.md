---
title: 우선 순위를 프로젝트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1badd483690ae22f9e314c0f9eb4ac3033d82e4a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328272"
---
# <a name="project-priority"></a>프로젝트 우선 순위
프로젝트 항목에는 일반적으로 솔루션에 프로젝트가 하나만의 멤버인 경우 따라서 IDE 쉽게 확인할 수는 프로젝트가 항목을 열 때 사용 됩니다. 그러나 항목이 둘 이상의 프로젝트의 멤버인 경우 IDE 항목을 열기 위한 최상의 프로젝트를 확인할 수는 우선 순위 체계를 사용 합니다.

 다음은 프로젝트 우선 순위 체계를 보여 줍니다.

- 호출 하 여 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> 문서 해당 프로젝트의 멤버 인지 여부를 확인 하는 솔루션의 각 프로젝트에 대 한 메서드.

- 문서 프로젝트의 멤버인 경우 프로젝트 응답 우선 순위를 사용 하 여 해당 문서 처리에 따라 프로젝트를 매기는 합니다. 예를 들어 언어 프로젝트를 해당 언어 소스 파일에 대 한 우선 순위를 사용 하 여 응답 하지만 해당 빌드 프로세스의 일부로 사용 되지 않는 인식할 수 없는 파일 형식에 대 한 낮은 우선 순위를 사용 하 여 응답 합니다.

- 또한 문서에 대 한 사용자 지정, 프로젝트별 편집기 또는 디자이너를 제공 하는 프로젝트에 높은 우선 순위를 받습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거형 문서 우선 순위 값을 제공 합니다.

- 가장 높은 우선 순위를 지정 하는 프로젝트 컨텍스트 문서를 열도록 지정 됩니다. 두 개의 프로젝트 우선 순위가 같은 값을 반환 하는 경우 활성 프로젝트를 사용 하는 것이 좋습니다. 솔루션에 프로젝트가 없습니다. 응답 문서를 열 수 있도록 하는 경우 IDE는 기타 파일 프로젝트의 문서를 배치 합니다. 자세한 내용은 [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)합니다.

## <a name="see-also"></a>참고 항목
- [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)
- [방법: 열린 문서의 편집기 열기](../../extensibility/how-to-open-editors-for-open-documents.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)