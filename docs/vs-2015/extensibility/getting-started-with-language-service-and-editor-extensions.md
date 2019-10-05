---
title: 언어 서비스 및 편집기 확장 시작 하기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4c4278679cabb72e9d06f79c1668e7546f24194d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703753"
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>언어 서비스 및 편집기 확장 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

고유한 프로그래밍 언어 또는 모든 콘텐츠 형식에 개요, 중괄호 일치, IntelliSense 및 light bulbs와 같은 언어 서비스 기능을 추가 하려면 편집기 확장을 사용할 수 있습니다. Visual Studio 편집기에서 색 지정, 여백, 프로그램 및 기타 시각적 요소 예를 들어 텍스트의 동작과 모양을 사용자 지정할 수도 있습니다. 또한 고유한 형식의 콘텐츠를 정의 하 고 콘텐츠에 표시 되는 텍스트 보기의 동작과 모양을 지정할 수 있습니다.  
  
 편집기 확장 작성을 시작, Visual Studio SDK의 일부로 설치 되는 편집기 프로젝트 템플릿을 사용 합니다. Visual Studio SDK는 Vspackage를 사용 하 여 또는 Framework MEF (Managed Extensibility)를 사용 하 여 Visual Studio 확장 개발을 쉽게 해 주는 도구 집합을 다운로드 합니다.  
  
> [!NOTE]
> Visual Studio SDK에 대 한 자세한 내용은 참조 하세요. [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
 사용자 고유의 편집기 확장을 작성 하기 전에 다음과 같은 개념과 기술에 대 한 설명 하는 것이 좋습니다.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) 및 편집기 확장  
 Visual Studio 편집기 사용자 인터페이스 (UI)는 Windows Presentation Foundation (WPF)를 사용 하 여 구현 됩니다. WPF는 풍부한 시각적 환경 및 비즈니스 논리에서 코드의 시각적 측면을 구분 하는 일관성 있는 프로그래밍 모델을 제공 합니다. 편집기 확장을 만들 때 여러 가지 WPF 요소와 기능을 사용할 수 있습니다. 자세한 내용은 [Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)합니다.  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) 및 편집기 확장  
 Visual Studio 편집기는 구성 요소와 확장을 관리 하는 프레임 워크 MEF (Managed Extensibility)를 사용 합니다. MEF에는 또한 개발자를 자세한 Visual Studio와 같은 호스트 응용 프로그램에 대 한 확장을 쉽게 만들 수 있습니다. 이 프레임 워크에서는 MEF 계약에 따라 확장을 정의 하 고 MEF 구성 요소 부분으로 내보내야 합니다. 호스트 응용 프로그램 찾을 수 있으며, 등록 하면 올바른 컨텍스트에 적용 되는 선택 되어 있는지 확인 하는 구성 요소 부분을 관리 합니다.  
  
> [!NOTE]
> 편집기에서 MEF에 대 한 자세한 내용은 참조 하세요. [편집기에서 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)합니다.  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 편집기 확장 지점 및 확장  
 편집기 확장 지점은 MEF 구성 요소 파트를 사용자 지정 및 확장할 수 있습니다. 일부 경우에 인터페이스를 구현 하 여 올바른 메타 데이터와 함께 내보내기 확장 지점을 확장 합니다. 다른 경우에만 확장 선언을 특정 형식으로 내보내기.  
  
 다음은 일부 편집기 확장의 기본 종류입니다.  
  
- 여백 및 스크롤 막대  
  
- 태그  
  
- 선의 도구 영역  
  
- 옵션  
  
- IntelliSense  
  
  편집기 확장 지점에 대 한 자세한 내용은 참조 하세요. [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)합니다.  
  
## <a name="deploying-editor-extensions"></a>편집기 확장 배포  
 Visual Studio 편집기 확장 솔루션을 구축 솔루션에 source.extension.vsixmanifest 라는 메타 데이터 파일을 추가한 다음 Visual Studio에 알려져 있는 폴더에 이진 파일 및 매니페스트의 복사본을 추가 하 여 배포 합니다. 매니페스트 파일 (예를 들어, 이름, 작성자, 버전 및 유형의 콘텐츠) 확장에 대 한 기본적인 사항을 정의합니다. VSIX 매니페스트 파일 및 확장을 배포 하는 방법에 대 한 자세한 내용은 참조 하세요. [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)합니다.  
  
 컴퓨터에서 확장을 설치할 때 Visual Studio에 알려진 폴더의 하위 폴더에 이진 파일 및 매니페스트를 포함 합니다.  
  
> [!WARNING]
> Visual Studio에 포함 된 편집기 확장성 템플릿 중 하나를 사용 하는 경우 매니페스트 및 배포 위치 세부 정보에 걱정할 필요가 없습니다. 템플릿을 등록 하 고 확장을 배포 하는 데 필요한 모든 포함 합니다.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>실험적 인스턴스에서 확장을 실행합니다.  
 실험적 폴더 (Windows Vista 및 Windows 7)에 배포 하 여 확장을 개발 하는 동안 작업 버전의 Visual Studio를 분리 수 있습니다.  
  
 *%LOCALAPPDATA%* \VisualStudio\10.0Exp\Extensions\\*Company*\\*ExtensionID*  
  
 여기서 *% LOCALAPPDATA %* 로그온 한 사용자의 이름입니다 *회사* 확장을 소유 하는 회사의 이름 및 *ExtensionID* 확장의 ID입니다.  
  
 실험적 위치로 확장을 배포할 때 디버그 모드에서 실행 됩니다. Visual Studio의 두 번째 인스턴스를 시작 되 고 이름은 **Microsoft Visual Studio 실험적 인스턴스**합니다.  
  
## <a name="managing-extensions"></a>확장 관리  
 Visual Studio 확장에 나오는 **확장 및 업데이트** (에 **도구** 메뉴). 실험적 인스턴스에서 확장을 테스트 하는 경우에 표시 됩니다 **확장 및 업데이트** 실험적 인스턴스에서 되지만 개발 인스턴스에 표시 되지 않으면.  
  
 자세한 내용은 [Visual Studio 확장명 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)을 참조하세요.  
  
## <a name="using-templates-to-create-editor-extensions"></a>편집기 확장을 만드는 템플릿을 사용 하 여  
 분류자, 프로그램 및 여백을 사용자 지정 하는 MEF 확장을 만드는 템플릿 편집기를 사용할 수 있습니다. C# 및 Visual Basic 프로젝트에 대 한 템플릿이 있습니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
 또한 확장 프로그램을 만들의 VSIX 프로젝트 템플릿을 사용할 수 있습니다. 이 템플릿은 모든 유형의 확장을 배포 하 고 source.extension.vsixmanifest 파일, 필요한 어셈블리 참조 및 배포할 수 있도록 하는 빌드 작업을 포함 하는 프로젝트 파일을 포함 하는 데 필요한 요소를 제공 합니다 확장입니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)합니다.  
  
 작업을 Visual Studio 패키지 확장에서 MEF 구성 요소 편집기도 만들 수도 있습니다. 자세한 다음 연습을 참조 하세요.  
  
- [연습: 편집기 확장에서 셸 명령 사용](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
- [연습: 편집기 확장에서 바로 가기 키 사용](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>참고 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
