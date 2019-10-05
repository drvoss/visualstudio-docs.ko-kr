---
title: 옵션, 텍스트 편집기, C#, 고급 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 73148f8c3f569f3d585f6127b7ec713c766b0f8b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674245"
---
# <a name="options-text-editor-c-advanced"></a>옵션, 텍스트 편집기, C#, 고급
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual C#의 편집기 서식, 코드 리팩터링 및 XML 문서 주석에 대한 설정을 수정하려면 이 대화 상자를 사용합니다. 이 대화 상자에 액세스하려면 **도구** 메뉴에서 **옵션**을 클릭하고, **텍스트 편집기** 폴더를 확장하고, **C#** 을 확장하고, **고급**을 클릭합니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
## <a name="outlining"></a>개요  
 개요 모드로 파일 열기  
 이 옵션을 선택하면 축소 가능한 코드 블록을 만드는 코드 파일이 자동으로 요약됩니다. 파일이 처음 열리면 #regions 블록 및 비활성 코드 블록이 축소됩니다.  
  
## <a name="editor-help"></a>편집기 도움말  
 편집기에서 오류에 밑줄 표시  
 코드에서 빌드 오류를 식별합니다. 이 옵션을 선택하면 물결선 밑줄이 특정 의미가 있는 색으로 표시됩니다.  
  
- 구문 분석 오류는 빨강입니다.  
  
- 빌드 오류는 파랑입니다.  
  
- 빌드 경고는 녹색입니다.  
  
- 잘못된 [편집하며 계속하기](../../debugger/edit-and-continue.md) 편집은 자주입니다.  
  
  밑줄 표시된 코드 세그먼트 위로 포인터를 이동하면 오류에 대한 정보가 있는 도구 설명이 표시됩니다.  
  
  라이브 의미 오류 표시  
  알 수 없는 형식을 선언 및 사용하거나 알 수 없는 속성을 참조하는 것과 같이 명시적 컴파일 없이 특정 컴파일 오류를 식별합니다.  
  
  커서 아래의 기호에 대한 참조 강조  
  기호 내부에 커서를 놓거나 기호를 클릭하면 코드 파일에 있는 해당 기호의 모든 인스턴스가 강조 표시됩니다.  
  
## <a name="refactoring"></a>리팩터링  
 리팩터링 결과 확인  
 빌드 오류가 포함된 코드를 리팩터링하려고 할 경우 또는 리팩터링으로 인해 코드 참조가 원래 바인딩과 다른 항목에 바인딩될 경우 **확인 결과** 대화 상자를 표시합니다.  
  
 컴파일러에서 생성한 참조가 있는 멤버에 대해 경고  
 컴파일러에서 생성한 참조와 같은 이름을 가진 멤버를 리팩터링하려는 경우 경고 대화 상자를 표시합니다.  
  
## <a name="xml-documentation-comments"></a>XML 문서 주석  
 ///에 대해 XML 문서 주석 생성  
 이 옵션을 선택하면 /// 주석 도입부를 입력한 후 XML 문서 주석에 대한 \<summary> 시작 및 끝 태그가 자동으로 삽입됩니다. XML 문서에 대한 자세한 내용은 [XML 문서 주석](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)을 참조하세요.  
  
## <a name="implement-interface"></a>인터페이스 구현  
 #region으로 생성된 코드 감싸기  
 인터페이스 구현 또는 명시적으로 인터페이스 구현이 사용될 경우 메서드 주위에 #region \<*interface name*> 멤버를 삽입합니다.  
  
## <a name="organize-usings"></a>Using 구성  
 using 정렬 시 ‘System’ 지시문 먼저 배치  
 이 옵션을 선택하면 `System` using 지시문이 다른 using 지시문 앞에 표시됩니다. 자세한 내용은 [Using 정렬](../../misc/sort-usings.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [XML 문서 주석](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [언어별 편집기 옵션 설정](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
