---
title: 명령을 사용 하 여 열기를 사용 하 여 파일을 표시 합니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66ca76d7e25d1f9f1fa23605a83b68094686fcd5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351558"
---
# <a name="display-files-by-using-the-open-with-command"></a>연결 프로그램 명령을 사용 하 여 파일을 표시 합니다.
프로젝트를 표시 하기 위해 IDE를 요청할 수 있습니다 합니다 **연결 프로그램** 대화 상자. 이 요청 라는 표준 편집기의 선택 된 파일을 열 수입니다. 다음 단계는이 프로세스를 설명합니다.

1. 프로젝트를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>에 값을 지정 `OSE_UseOpenWithDialog` 에 대 한는 `OSEOpenDocEditor` 매개 변수입니다.

2. 문서의 파일 이름 확장명에 따라 IDE 지정된 된 문서를 열고 레지스트리 있습니다 나열 하는 편집기 결정 및에이 정보를 표시 합니다 **프로그램** 대화 상자.

    > [!NOTE]
    > 에 포함 되어야 하는 내장 함수 편집기를 포함 하는 프로젝트를 **연결 프로그램** 대화 상자는 이러한 각 편집기에 대 한 편집기 팩터리를 등록 해야 합니다. 내장 함수 편집기의 구현에 적용 하는 프로젝트의 특정 형식과 함께 함수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드. IDE에는 핵심 텍스트 편집기 및 바이너리 편집기에 대 한 기본 제공 편집기 팩터리입니다. IDE는 또한 각 등록 된 Windows 파일 연결을 대신 하 여 편집기 팩터리의 인스턴스를 만듭니다. 이러한 파일의 예로 Microsoft Word입니다.

3. 사용자가에서 항목을 선택 합니다 **연결 프로그램** 대화 상자에서 다음 IDE를 호출 하 여 문서를 엽니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드. 자세한 내용은 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)합니다.

## <a name="see-also"></a>참고자료
- [열기 및 프로젝트 항목 저장](../../extensibility/internals/opening-and-saving-project-items.md)
- [파일 열기 명령을 사용 하 여 파일을 표시 합니다.](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)
