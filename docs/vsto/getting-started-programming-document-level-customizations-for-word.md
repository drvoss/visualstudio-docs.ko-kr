---
title: Word 용 문서 수준 사용자 지정 프로그래밍 시작
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b2872ca6496444cbb3878dc39800a8661400a76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971799"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Word 용 문서 수준 사용자 지정 프로그래밍 시작
  바로 시작 하는 Visual Studio를 사용 하 여 Microsoft Office Word 용 문서 수준 사용자 지정 만들기를 하는 경우 알아야 할 내용을 다음과 같습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Word 작업에 대 한 문서 수준 사용자 지정 이해
 만드는 각 단어 사용자 지정은 단일 문서를 기반으로 합니다. 를 사용자 지정을 사용 하려면 최종 사용자가 문서 또는 Word 서식 파일에서 문서를 만듭니다. 예를 들어 특정 영역으로 커서를 이동 하거나 단추 및 메뉴 항목을 클릭 하 여 문서에서 이벤트 어셈블리에서 이벤트 처리 메서드를 호출할 수 있습니다. 문서를 닫을 때에 사용자 지정에서 제공 하는 기능와 Word에서 사용할 수 없습니다.

 자세한 내용은 [의 문서 수준 사용자 지정 아키텍처](../vsto/architecture-of-document-level-customizations.md)합니다.

## <a name="create-document-level-projects-for-word"></a>Word 용 문서 수준 프로젝트를 만들려면
 Word 용 문서 수준 사용자 지정을 만들려면에서 Word 문서 또는 Word 서식 파일 프로젝트 템플릿을 사용 합니다 **새 프로젝트** 대화 상자. 이러한 템플릿에는 필요한 어셈블리 참조 및 프로젝트 파일이 포함되어 있습니다.

 Word 용 문서 수준 프로젝트를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다. 프로젝트 템플릿에 대 한 자세한 내용은 참조 하세요. [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)합니다.

## <a name="program-word-documents-by-using-host-items-host-controls"></a>호스트 항목 및 호스트 컨트롤을 사용 하 여 프로그램 Word 문서
 *호스트 항목* 하 고 *컨트롤을 호스팅할* 문서 수준 사용자 지정 프로그래밍 모델을 제공 하는 클래스입니다.

 코드에 대 한 진입점을 제공 하는 호스트 항목 및 호스트 컨트롤 및 Windows Forms 컨트롤에 대 한 컨테이너로 서의 역할도 있습니다. Word 용 문서 수준 프로젝트에서 호스트 항목으로 표시 됩니다는 `ThisDocument` 클래스입니다.

 호스트 컨트롤은 콘텐츠 컨트롤, 책갈피, XML 노드 등의 네이티브 Word 개체를 기반으로 합니다. 호스트 컨트롤은 네이티브 Word 개체에 유사한 기능을 제공 하지만 새로운 이벤트, 디자이너 지원 및 데이터 바인딩 기능입니다. 프로젝트 코드에 쉽게 Word 개체 모델을 이동 하지 않고도 코드에서 직접 특정 개체를 참조 하는 IntelliSense를 최고의 개체로 표시 됩니다.

 자세한 내용은 다음 항목을 참조하세요.

- [문서 수준 사용자 지정 프로그래밍](../vsto/programming-document-level-customizations.md)

- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)

- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Word의 사용자 인터페이스 사용자 지정
 대부분의 Microsoft Office 솔루션 솔루션을 사용 하 여 상호 작용 하는 사용자에 대 한 몇 가지 방법을 제공 하는 Office 응용 프로그램의 사용자 인터페이스 (UI)을 수정 합니다. 여러 가지 방법으로는 문서 수준 사용자 지정을 사용 하 여 Word의 UI를 수정할 수 있습니다. 예를 들어 리본 메뉴에 컨트롤을 추가할 수 있습니다 하 고 작업 창에 표시할 수 있습니다. 자세한 내용은 [Office UI 사용자 지정](../vsto/office-ui-customization.md)합니다.

 또한 Visual Studio에서 직접 프로젝트와 연결 된 문서를 열 수 있습니다. 문서를 Visual Studio에서 연 Word 사용자 인터페이스를 사용 하 여 문서를 수정할 수 있습니다. 컨트롤을이 끌 수 있는 디자인 화면으로 문서를 사용할 수도 있습니다. 자세한 내용은 [Visual Studio 환경의 Office 프로젝트](../vsto/office-projects-in-the-visual-studio-environment.md)합니다.

## <a name="bind-controls-to-data"></a>데이터에 컨트롤 바인딩
 콘텐츠 컨트롤 및 <xref:Microsoft.Office.Tools.Word.Bookmark> 컨트롤에서 끌 수 있는 컨트롤의 목록에는 **데이터 원본** 창입니다. 콘텐츠 컨트롤 및이 방식으로 자동으로 책갈피를 설정 추가 창을 사용 하 여 설정 하는 데이터 소스에 바인딩합니다. 모든 코드를 작성 하지 않고도 데이터베이스, 서비스 및 비즈니스 개체에서 데이터를 표시할 수 있습니다. 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)합니다.

## <a name="next-steps"></a>다음 단계
 Word 용 문서 수준 사용자 지정을 만드는 방법에 알아보려면 참조 [연습: Word 용 첫 문서 수준 사용자 지정 만들기](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)합니다. 이 연습에서는 Word 문서 수준 사용자 지정 프로그래밍 모델은 Visual Studio에서 Office 개발 도구를 소개합니다.

 Word 프로젝트에서 일반적인 작업 중 몇 가지를 안내 하는 항목의 목록을 참조 하세요 [Office 프로그래밍에서 일반적인](../vsto/common-tasks-in-office-programming.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [문서 수준 사용자 지정 프로그래밍](../vsto/programming-document-level-customizations.md)
- [Word 솔루션](../vsto/word-solutions.md)
- [연습: Word 용 첫 문서 수준 사용자 지정 만들기](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Word를 사용 하 여 연습](../vsto/walkthroughs-using-word.md)
- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)
- [Office 솔루션에서 코드를 작성 합니다.](../vsto/writing-code-in-office-solutions.md)
