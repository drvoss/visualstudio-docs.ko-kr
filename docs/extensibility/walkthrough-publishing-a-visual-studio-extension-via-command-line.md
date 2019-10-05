---
title: 명령줄을 사용 하 여 확장 게시
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6b5531bc5dc138f2f90a0a67da39f9583bc4b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320644"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>연습: 명령줄을 통해 Visual Studio 확장 기능 게시

이 연습에서는 Visual Studio 확장 Visual Studio Marketplace에 게시 하는 방법을 명령줄을 사용 하 여. 확장 프로그램을 Marketplace에 추가 하면 개발자가 사용할 수는 [ **확장 및 업데이트** ](../ide/finding-and-using-visual-studio-extensions.md) 을 검색할 수 있는 새 확장과 업데이트 된 대화입니다.

VsixPublisher.exe는 Marketplace에 게시 Visual Studio 확장에 대 한 명령줄 도구입니다. ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe에서에서 액세스할 수 있습니다. 이 도구에서 사용할 수 있는 명령은: **게시**를 **createPublisher**를 **deletePublisher**를 **deleteExtension**,  **로그인**하십시오 **로그 아웃**합니다.

## <a name="commands"></a>명령

### <a name="publish"></a>게시

확장 Marketplace에 게시 합니다. 확장은 vsix, exe/msi 파일로 또는 링크를 수 있습니다. 동일한 버전을 사용 하 여 확장을 이미 있는 경우 확장을 덮어씁니다. 확장을 아직 없는 경우 새 확장을 만들어집니다.

|명령 옵션 |설명 |
|---------|---------|
|페이로드 (필수) | 에 대 한 경로일 게시할 페이로드 또는 "자세한 정보 URL"로 사용 하는 링크입니다. |
|publishManifest (필수) | 사용할 파일을 매니페스트 하는 게시에 대 한 경로입니다. |
|ignoreWarnings | 확장을 게시할 때 무시할 경고의 목록입니다. 이러한 경고는 확장을 게시할 때 명령줄 메시지로 표시 됩니다. (예를 들어, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | 개인 액세스 토큰 (PAT) 게시자를 인증 하는 데 사용 되는 합니다. 지정 하지 않으면 PAT에 로그인 한 사용자 로부터 획득 됩니다. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Marketplace에서 게시자를 만듭니다. 또한 게시자 (예: 확장 삭제/게시) 이후 작업에 대 한 컴퓨터에 기록 합니다.

|명령 옵션 |설명 |
|---------|---------|
|displayName (필수) | 게시자 표시 이름입니다. |
|publisherName (필수) | (예를 들어 식별자) 게시자의 이름입니다. |
|personalAccessToken (필수) | 개인용 액세스 토큰을 게시자를 인증 하는 데 사용 됩니다. |
|shortDescription | 게시자 (파일이 아님)의 간단한 설명입니다. |
|longDescription | 게시자 (파일이 아님)의 긴 설명입니다. |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Marketplace에서 게시자를 삭제합니다.

|명령 옵션 |설명 |
|---------|---------|
|publisherName (필수) | (예를 들어 식별자) 게시자의 이름입니다. |
|personalAccessToken (필수) | 개인용 액세스 토큰을 게시자를 인증 하는 데 사용 됩니다. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Marketplace에서 확장을 삭제합니다.

|명령 옵션 |설명 |
|---------|---------|
|extensionName (필수) | 삭제할 확장의 이름입니다. |
|publisherName (필수) | (예를 들어 식별자) 게시자의 이름입니다. |
|personalAccessToken | 개인용 액세스 토큰을 게시자를 인증 하는 데 사용 됩니다. 지정 하지 않으면 pat에 로그인 한 사용자 로부터 획득 됩니다. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

게시자 컴퓨터에 로그인 합니다.

|명령 옵션 |설명 |
|---------|---------|
|(필수 personalAccessToken | 개인용 액세스 토큰을 게시자를 인증 하는 데 사용 됩니다. |
|publisherName (필수) | (예를 들어 식별자) 게시자의 이름입니다. |
|덮어쓰기 | 새 개인 액세스 토큰을 사용 하 여 모든 기존 게시자를 덮어쓸 수 해야 지정 합니다. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>로그 아웃

컴퓨터에서 게시자를 기록합니다.

|명령 옵션 |설명 |
|---------|---------|
|publisherName (필수) | (예를 들어 식별자) 게시자의 이름입니다. |
|ignoreMissingPublisher | 지정된 된 게시자가 이미 로그인 하지 하는 경우 도구 오류가 아니라 해야 하는 것을 지정 합니다. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest 파일

publishManifest 파일을 사용 합니다 **게시** 명령입니다. Marketplace가 알아야 하는 확장에 대 한 모든 메타 데이터를 나타냅니다. VSIX 확장에서 업로드 되는 확장명 인 "id" 속성 설정 "internalName"만 있어야 합니다. 즉, "id" 속성의 나머지 부분 vsixmanifest 파일에서 생성할 수 있습니다. 확장 된 msi/exe 또는 링크 확장 이면 사용자는 "id" 속성의 필수 필드를 제공 해야 합니다. Marketplace에 대 한 정보를 포함 하는 매니페스트의 나머지 부분 (예를 들어, 범주, 질문 및 답변을 사용할지, 등.).

VSIX 확장 publishManifest 파일 샘플:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE 또는 링크 publishManifest 파일 샘플:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>자산 파일

추가 정보 파일에서 이미지 등을 포함 하는 것에 대 한 자산 파일을 제공할 수 있습니다. 예를 들어, 확장 다음 "개요" Markdown 문서가 있으면:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

이전 예제에서 "images/testlogo.png"를 해결 하기 위해 사용자가 제공할 수 "assetFiles"에 해당 게시 아래와 같은 매니페스트:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>게시 연습

### <a name="prerequisites"></a>전제 조건

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

### <a name="create-a-visual-studio-extension"></a>Visual Studio 확장을 만들려면

이 경우 기본 VSPackage 확장을 사용 하지만 동일한 단계는 모든 종류의 확장에 대 한 유효한 합니다.

1. 메뉴 명령이 포함 된 "TestPublish" 라는 C#에서 VSPackage를 만듭니다. 자세한 내용은 참조 하세요. [첫 번째 확장 만들기: Hello World](../extensibility/extensibility-hello-world.md)합니다.

### <a name="package-your-extension"></a>확장 패키지

1. 확장 vsixmanifest 제품 이름, 만든이 및 버전에 대 한 올바른 정보로 업데이트 합니다.

   ![확장 vsixmanifest 업데이트](media/update-extension-vsixmanifest.png)

2. 확장 프로그램을 빌드할 **릴리스** 모드입니다. 이제 확장 \bin\Release 폴더에는 VSIX로 패키지 됩니다.

3. VSIX 설치를 확인 하려면 두 번 클릭 수 있습니다.

### <a name="test-the-extension"></a>테스트 확장

 확장을 배포 하기 전에 빌드하고 테스트 하 여 Visual Studio의 실험적 인스턴스에서 올바르게 설치 되었는지 확인 합니다.

1. Visual Studio에서 디버깅을 시작 합니다. Visual Studio의 실험적 인스턴스를 엽니다.

2. 실험적 인스턴스를 이동 합니다 **도구** 메뉴를 클릭 **확장 및 업데이트 하는 중...** . TestPublish 확장 가운데 창에 표시 됩니다 하 고 사용 하도록 설정 합니다.

3. 에 **도구** 메뉴에서 테스트 명령 표시 되는지 확인 합니다.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>명령줄을 통해 Marketplace에 확장 게시

1. 확장 프로그램의 릴리스 버전 빌드 및 최신 상태 인지에 있는지 확인 합니다.

2. Publishmanifest.json 파일과 overview.md 만든 있는지 확인 합니다.

3. 명령줄을 열고 ${VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\ 디렉터리로 이동 합니다.

4. 새 게시자를 만들려면 다음 명령을 사용 합니다.

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. 게시자의 성공적으로 만들면 다음과 같은 명령줄 메시지가 표시 됩니다.

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. 로 이동 하 여 만든 새 게시자를 확인할 수 있습니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. 새 확장을 게시 하려면 다음 명령을 사용 합니다.

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. 게시자의 성공적으로 만들면 다음과 같은 명령줄 메시지가 표시 됩니다.

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. 로 이동 하 여 게시 된 새 확장을 확인할 수 있습니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장을 설치 합니다.

확장을 게시 했으므로 Visual Studio에서 설치 하 고 테스트 합니다.

1. Visual Studio에서에 **도구** 메뉴에서 클릭 **확장 및 업데이트 하는 중...** .

2. 클릭 **Online** 고 TestPublish를 검색 합니다.

3. **다운로드**를 클릭합니다. 그런 다음 확장 설치에 대 한 예약 됩니다.

4. 설치를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

컴퓨터에서 Visual Studio Marketplace에서 확장을 제거할 수 있습니다.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>명령줄을 통해 Marketplace에서 확장을 제거 하려면

1. 확장명을 제거 하려는 경우 다음 명령을 사용 합니다.

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. 확장의 제대로 삭제 다음 명령줄 메시지가 표시 됩니다.

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거 하려면

1. Visual Studio에서에 **도구** 메뉴에서 클릭 **확장 및 업데이트**합니다.

2. "MyVsixExtension"를 선택 하 고 클릭 **제거**합니다. 확장 한 다음 제거에 대 한 예약 됩니다.

3. 제거를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.
