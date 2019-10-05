---
title: '연습: 파일 이름 확장명에 콘텐츠 형식 연결 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e402979dc5b76b8693a4be7a80a3d5d98f889616
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320669"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>연습: 파일 이름 확장명에 콘텐츠 형식 링크
고유의 콘텐츠 형식을 정의 하 고 편집기 프레임 워크 MEF (Managed Extensibility) 확장을 사용 하 여 파일 이름 확장명을 링크 수 있습니다. 경우에 따라 파일 확장명을 언어 서비스로 이미 정의 되었습니다. 하지만 MEF와 함께 사용 하려면 연결 해야 합니다도 콘텐츠 형식입니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 있습니다 다운로드 센터에서 Visual Studio SDK를 설치 하지 마세요. Visual Studio 설치에서 선택적 기능으로 포함 되어 있습니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C# VSIX 프로젝트를 만듭니다. (에 **새 프로젝트** 대화 상자에서 **Visual C# / 확장성**, 한 다음 **VSIX 프로젝트**.) 솔루션의 이름을 `ContentTypeTest`로 지정합니다.

2. **source.extension.vsixmanifest** 파일을 이동 합니다 **자산** 탭을 설정 합니다 **형식** 필드를 **Microsoft.VisualStudio.MefComponent**, **소스** 필드를 **현재 솔루션의 프로젝트**, 및 **프로젝트** 필드를 프로젝트의 이름입니다.

## <a name="define-the-content-type"></a>콘텐츠 형식 정의

1. 클래스 파일을 추가하고 이름을 `FileAndContentTypes`로 지정합니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. 다음 추가 `using` 지시문입니다.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. 정의 포함 하는 정적 클래스를 선언 합니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. 이 클래스에서 내보내기는 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 라는 "hid" 및 "text"를 해당 기본 정의 선언 합니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>파일 이름 확장명을 콘텐츠 형식에 연결

- 이 콘텐츠 형식을 파일 이름 확장명을 매핑할 내보내기는 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 확장명이 *.hid* 및 콘텐츠 형식을 "hid"입니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>편집기 내보내기에 콘텐츠 형식 추가

1. 편집기 확장을 만듭니다. 에 설명 된 여백 문자 모양 확장을 사용할 수는 예를 들어 [연습: 여백 모양 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)합니다.

2. 이 절차에서 정의한 클래스를 추가 합니다.

3. 확장 클래스를 내보낼 때 추가 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "hid" 되도록 하는 형식입니다.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>참고자료
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)