---
title: 편집기 항목 템플릿을 사용 하 여 확장을 만드는 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bef42c67f34b8a24ac26a7765fecddc104ae74a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350994"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>편집기 항목 템플릿을 사용 하 여 확장 만들기
편집기 분류자, 프로그램 및 여백을 추가 하는 기본 편집기 확장을 만들려면 Visual Studio SDK에 포함 된 항목 템플릿을 사용할 수 있습니다. 편집기 항목 템플릿은 Visual C# 또는 Visual Basic VSIX 프로젝트에 사용할 수 있습니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-classifier-extension"></a>분류자 확장명 만들기
 편집기 분류자 항목 템플릿은 적절 한 텍스트 색 편집기 분류자를 만듭니다 (이 경우 모든) 텍스트 파일에서입니다.

1. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 을 클릭 한 다음 **확장성**합니다. 에 **템플릿을** 창 **VSIX 프로젝트**합니다. **이름** 상자에 `TestClassifier`을 입력합니다. **확인**을 클릭합니다.

2. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 이동 하 여 Visual C# **확장성** 노드와 선택 **편집기 분류자**합니다. 기본 파일 이름 (*EditorClassifier1.cs*).

3. 4 개의 코드 파일은 다음과 같습니다.

    - *EditorClassifier1.cs* 포함 된 `EditorClassifier1` 클래스입니다.

    - *EditorClassifier1ClassificationDefinition.cs* 포함 된 `EditorClassifier1ClassificationDefinition` 클래스입니다.

    - *EditorClassifier1Format.cs* 포함 된 `EditorClassifier1Format` 클래스입니다.

    - *EditorClassifier1Provider.cs* 포함 된 `EditorClassifier1Provider` 클래스입니다.

4. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 됩니다.

     텍스트 파일을 열면 모든 텍스트는 보라색 배경과 밑줄이 표시 됩니다.

## <a name="create-a-text-relative-adornment-extension"></a>텍스트에 상대적인 adornment 확장명 만들기
 편집기 텍스트 장식 템플릿은 만듭니다 텍스트 문자의 모든 인스턴스를 데코레이팅하는 텍스트에 상대적인 adornment 파란색 배경 및 빨간 윤곽선이 있는 상자를 사용 하 여 ' a'입니다. 텍스트에 상대적인 것 때문에 상자를 'a' 문자를 이동 하거나 다시 포맷 하는 경우에 항상 오버레이 합니다.

1. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 을 클릭 한 다음 **확장성**합니다. 에 **템플릿을** 창 **VSIX 프로젝트**합니다. **이름** 상자에 `TestAdornment`을 입력합니다. **확인**을 클릭합니다.

2. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 이동 하 여 Visual C# **확장성** 노드와 선택 **편집기 텍스트 장식**합니다. 기본 파일 이름 (*TextAdornment1.cs/vb*).

3. 두 코드 파일은 다음과 같습니다.

    - *TextAdornment1.cs* 포함 된 `TextAdornment1` 클래스입니다.

    - *TextAdornment1TextViewCreationListener.cs* 포함 된 `TextAdornment1TextViewCreationListener` 클래스입니다.

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다. 텍스트 파일을 열면 텍스트 'a' 문자는 파란색 배경의 대해 빨간색 요약 되어 있습니다.

## <a name="create-a-viewport-relative-adornment-extension"></a>뷰포트에 상대적인 adornment 확장명 만들기
 편집기 뷰포트 Adornment 템플릿은 뷰포트의 오른쪽 위 모서리에 빨간색 윤곽선이 있는 보라색 상자를 추가 하는 상대 뷰포트 adornment를 만듭니다.

> [!NOTE]
> 합니다 **뷰포트** 현재 표시 된 텍스트 보기의 영역입니다.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>편집기 뷰포트 Adornment 템플릿을 사용 하 여 뷰포트 adornment 확장 프로그램을 만들려면

1. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 을 클릭 한 다음 **확장성**합니다. 에 **템플릿을** 창 **VSIX 프로젝트**합니다. **이름** 상자에 `ViewportAdornment`을 입력합니다. **확인**을 클릭합니다.

2. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 이동 하 여 Visual C# **확장성** 노드와 선택 **편집기 뷰포트 Adornment**합니다. 기본 파일 이름 (*ViewportAdornment1.cs/vb*).

3. 두 코드 파일은 다음과 같습니다.

    - *ViewportAdornment1.cs* 포함 된 `ViewportAdornment1` 클래스입니다.

    - *ViewportAdornment1TextViewCreationListener.cs* 포함 된 `ViewportAdornment1TextViewCreationListener` 클래스

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다. 새 텍스트 파일을 만든 경우 뷰포트의 오른쪽 위 모서리에 빨간색 윤곽선이 있는 보라색 상자가 표시 됩니다.

## <a name="create-a-margin-extension"></a>여백 확장 만들기
 편집기 여백 템플릿은 만듭니다 단어와 함께 표시 되는 녹색 여백을 **Hello world!* 가로 스크롤 막대 아래.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>편집기 여백 템플릿을 사용 하 여 여백 확장 프로그램을 만들려면

1. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 을 클릭 한 다음 **확장성**합니다. 에 **템플릿을** 창 **VSIX 프로젝트**합니다. **이름** 상자에 `MarginExtension`을 입력합니다. **확인**을 클릭합니다.

2. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 이동 하 여 Visual C# **확장성** 노드와 선택 **편집기 여백**합니다. 기본 파일 이름 (EditorMargin1.cs/vb)을 그대로 둡니다.

3. 두 코드 파일은 다음과 같습니다.

    - *EditorMargin1.cs* 포함 된 `EditorMargin1` 클래스입니다.

    - *EditorMargin1Factory.cs* 포함 된 `EditorMargin1Factory` 클래스입니다.

4. 이 프로젝트를 빌드하고 디버깅을 시작 합니다. 실험적 인스턴스가 표시 됩니다. 단어에 있는 녹색 여백을 텍스트 파일을 열면 **Hello EditorMargin1** 가로 스크롤 막대 아래에 표시 됩니다.

## <a name="see-also"></a>참고자료
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
