---
title: 편집기 및 언어 서비스 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674779"
---
# <a name="extending-the-editor-and-language-services"></a>편집기 및 언어 서비스 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

언어 서비스 기능 (예: IntelliSense) 자체 편집기를 추가할 수 있으며 Visual Studio code 편집기의 대부분의 기능을 확장할 수 있습니다.  확장할 수 있습니다의 전체 목록을 참조 하세요 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)합니다.  
  
 Framework MEF (Managed Extensibility)를 사용 하 여 대부분의 편집기 기능을 확장 합니다. 예를 들어, 구문 색 지정을 확장 하려면 편집기 기능을 사용 하는 경우는 MEF 작성할 수 있습니다 *구성 요소 파트* 다른 색 지정 및 원하는 방식 처리 하려는 분류를 정의 하는 합니다. 편집기는 또한 여러 확장 같은 기능을 지원합니다.  
  
 편집기 프레젠테이션 계층 기반 (WPF (Windows Presentation Framework). WPF에는 또한 그래픽 및 애니메이션 같은 시각화를 제공 및 유연한 텍스트 서식 지정에 대 한 그래픽 라이브러리를 제공 합니다.  
  
 Visual Studio SDK 라고도 하는 어댑터를 제공 *shim* 이전 버전용으로 작성 된 Vspackage를 지원 하도록 합니다. 그럼에도 불구 하 고는 기존 VSPackage가 더 나은 성능 및 안정성을 가져올 새 기술 업데이트 하는 것이 좋습니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[언어 서비스 및 편집기 확장 시작](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|편집기에 대 한 확장을 만드는 방법에 설명 합니다.|  
|[편집기 기본 사항](../extensibility/inside-the-editor.md)|편집기의 일반 구조를 설명 하 고 해당 기능의 일부를 나열 합니다.|  
|[편집기의 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|편집기는 Framework MEF (Managed Extensibility)를 사용 하는 방법에 설명 합니다.|  
|[언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)|편집기의 확장 지점을 나열합니다. 확장 지점을 확장 될 수 있는 편집기 기능을 나타냅니다.|  
|[연습: 보기 장식, 명령 및 설정(열 안내선) 만들기](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|과정을 안내 하 고 코드를 특정 표시 너비를 유지 하기 위해 열 gudie 줄을 그릴 수 있는 보기 장식 빌드를 설명 합니다.  또한 읽기 및 쓰기 설정 뿐만 아니라 선언 및 명령 창에서 호출할 수 있는 명령을 구현도 보여 줍니다.|  
|[편집기 가져오기](../extensibility/editor-imports.md)|확장을 가져올 수 있는 서비스를 나열 합니다.|  
|[레거시 코드를 편집기로 조정](../extensibility/adapting-legacy-code-to-the-editor.md)|레거시 코드 편집기를 확장 하려면 (전 Visual Studio 2010)를 조정 하는 다양 한 방법에 설명 합니다.|  
|[레거시 언어 서비스 마이그레이션](../extensibility/internals/migrating-a-legacy-language-service.md)|기반 VSPackage 언어 서비스를 마이그레이션하는 방법에 설명 합니다.|  
|[연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|콘텐츠 형식을 파일 이름 확장명에 연결 하는 방법을 보여 줍니다.|  
|[연습: 여백 문자 모양 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)|아이콘에 여백을 추가 하는 방법을 보여 줍니다.|  
|[연습: 텍스트 강조 표시](../extensibility/walkthrough-highlighting-text.md)|사용 하는 방법을 보여 줍니다 *태그* 텍스트를 강조 표시 합니다.|  
|[연습: 개요](../extensibility/walkthrough-outlining.md)|특정 종류의 중괄호에 대 한 개요를 추가 하는 방법을 보여 줍니다.|  
|[연습: 괄호 일치 표시](../extensibility/walkthrough-displaying-matching-braces.md)|일치 하는 중괄호를 강조 표시 하는 방법을 보여 줍니다.|  
|[연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|속성, 메서드 및 이벤트와 같은 코드의 요소를 설명 하는 요약 정보 팝업을 표시 하는 방법을 보여 줍니다.|  
|[연습: 시그니처 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)|서명에서 매개 변수의 형식과 수에 대 한 정보를 제공 하는 팝업을 표시 하는 방법을 보여 줍니다.|  
|[연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)|문 완성 기능을 구현 하는 방법을 보여 줍니다.|  
|[연습: 코드 조각 구현](../extensibility/walkthrough-implementing-code-snippets.md)|코드 조각 확장을 구현 하는 방법을 보여 줍니다.|  
|[연습: 밝은 전구 추천 표시](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|코드 제안 전구를 표시 하는 방법을 보여 줍니다.|  
|[연습: 편집기 확장에서 셸 명령 사용](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|MEF 구성 요소를 사용 하 여 VSPackage에서 메뉴 명령과 연결 하는 방법을 보여 줍니다.|  
|[연습: 편집기 확장에서 바로 가기 키 사용](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|VSPackage에서 메뉴 바로 가기는 MEF 구성 요소를 사용 하 여 연결 하는 방법을 보여 줍니다.|  
|[MEF(Managed Extensibility Framework)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|에 대 한는 Framework MEF (Managed Extensibility) 정보를 제공 합니다.|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Windows Presentation Foundation (WPF)에 대 한 정보를 제공 합니다.|  
  
## <a name="reference"></a>참조  
 Visual Studio 편집기는 다음 네임 스페이스를 포함 합니다.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>
