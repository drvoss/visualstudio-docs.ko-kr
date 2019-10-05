---
title: 언어 서버 프로토콜 개요 | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f6f114d7165b85051092234ea33dfc7f73e1487
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309618"
---
# <a name="language-server-protocol"></a>언어 서버 프로토콜

## <a name="what-is-the-language-server-protocol"></a>언어 서버 프로토콜 란?

지 원하는 풍부한 편집 기능 같은 원본 코드 자동 완성 또는 **정의로 이동** 편집기 또는 IDE에서 프로그래밍 언어는 일반적으로 매우 까다롭고 시간이 많이 소요 됩니다. 일반적으로 편집기 또는 IDE의 프로그래밍 언어에서 스캐너, 파서, 형식 검사기, 작성기를 등 도메인 모델을 작성 해야 합니다. 예를 들어 c d T Eclipse 플러그 인 C에 대 한 지원을 제공 하는 /C++ Eclipse IDE에서은 Java로 작성 되므로 Eclipse IDE 자체은 Java로 작성 합니다. 이 방법에 따라 의미 C 구현 /C++ Visual Studio Code에 대 한 TypeScript의 도메인 모델 및에서 별도 도메인 모델 C# Visual Studio에 대 한 합니다.

언어별 도메인 모델을 만드는 개발 도구로 기존 언어별 라이브러리를 다시 사용할 수 있습니다 하는 경우 훨씬 더 쉽게 이기도 합니다. 그러나 이러한 라이브러리는 일반적으로 자체 프로그래밍 언어로 구현 (예를 들어 적절 한 C /C++ 도메인 모델은 C에서 구현 되는 /C++). C를 통합 /C++ TypeScript로 작성 된 편집기에 라이브러리는 기술적으로 가능 하지만 수행 하기가 어렵습니다.

### <a name="language-servers"></a>언어 서버

다른 방법은 자체 프로세스에서 라이브러리를 실행 하 여 프로세스 간 통신을 사용 하 여 해당 하 게 하는 것입니다. 앞뒤로 전달 되는 메시지 프로토콜을 형성 합니다. 언어 서버 프로토콜 LSP ()는 개발 도구와 언어 서버 프로세스 간에 교환 되는 메시지 표준화 하 고 제품입니다. 언어 서버나 악마 사용 하지 않는 새 또는 명백한 좋습니다. Vim 및 Emacs 수행이 의미 체계 자동 완성 기능 지원을 제공 하는 데 시간이 같은 편집기입니다. LSP의 목적은 이러한 종류의 통합을 간소화 하 고 다양 한 도구를 언어 기능을 노출 하기 위한 유용한 프레임 워크를 제공 하는 것 이었습니다.

일반 프로토콜을 하면 언어의 도메인 모델의 기존 구현을 다시 사용 하 여 간단 하 게 사용 하 여 개발 도구에 대 한 프로그래밍 언어 기능 통합. PHP, Python 또는 Java 언어 서버 백 엔드를 작성할 수 있습니다 및 LSP 수 다양 한 도구에 쉽게 통합할 수 있습니다. 프로토콜 도구를 완벽 하 게 기본 도메인 모델에 특정 미묘한 차이 이해 하지 않고도 다양 한 언어 서비스를 제공할 수 있도록 일반적인 추상화 수준에서 작동 합니다.

## <a name="how-work-on-the-lsp-started"></a>시작 하면 귀하의 LSP에서 작동 하는 방법

LSP 시간이 지남에 따라 발전 하 고 버전 3.0에는 현재 합니다. 언어 서버 개념 받았음을 OmniSharp 하 여 C#에 대 한 풍부한 편집 기능을 제공 하는 경우 시작 합니다. 처음에 OmniSharp JSON 페이로드를 사용 하 여 HTTP 프로토콜을 사용 하 고 포함 하 여 여러 편집기에 통합 되었습니다 [Visual Studio Code](https://code.visualstudio.com)합니다.

같은 시간대에 Microsoft는 TypeScript Emacs 및 Sublime Text와 같은 편집기에서 지 원하는 개념을 사용 하 여 TypeScript 언어 서버의 작동 하기 시작 했습니다. 이 구현에서는 편집기 TypeScript 서버 프로세스를 사용 하 여 stdin/stdout을 통해 통신 하 고 요청 및 응답에 V8 디버거 프로토콜에서 영감을 얻은 JSON 페이로드를 사용 합니다. TypeScript 서버는 다양 한 TypeScript 편집에 대 한 TypeScript Sublime 플러그 인 및 VS Code에 통합 되었습니다.

두 명의 서로 다른 언어 서버와 통합 한 후 VS Code 팀은 편집기 및 Ide에 대 한 일반적인 언어 서버 프로토콜을 탐색 하기 시작 했습니다. 다양 한 Ide에서 사용할 수 있는 단일 언어 서버를 만들려면 언어 공급자를 활성화 하는 일반적인 프로토콜입니다. 언어 서버 소비자만 한 번 프로토콜의 클라이언트측 구현 해야 합니다. 이 인해 win-윈 상황에서 언어 공급자 및 언어 소비자 모두에 대 한 합니다.

언어 서버 프로토콜 VS 코드 언어 API에서 영감을 얻은 더 많은 언어 기능을 사용 하 여 확장 된 TypeScript 서버에 의해 사용 된 프로토콜을 사용 하 여 시작 합니다. 프로토콜은 간단 하 고 기존 라이브러리 인해 원격 호출에 대 한 JSON RPC를 사용 하 여 지원 됩니다.

VS 코드 팀 프로토타입화 lint (검색)에 응답 하는 몇 가지 linter 언어 서버 프로토콜 요청을 파일을 열고 검색 된 경고 및 오류 집합을 반환 합니다. 목표가 였습니다 lint 할 파일을 문서 있습니다 됩니다 수 많은 linting 요청 편집기 세션 중에 사용자 편집 합니다. 구성 서버와 새 linting 프로세스 하지 않아도 각 사용자 편집 하기 위해 시작할 수 있도록 실행 되도록 것이 좋습니다. VS Code를 포함 하 여 여러 linter 서버 구현 된 ESLint 및 TSLint 확장 합니다. 두 linter 서버 TypeScript/JavaScript에서 구현 및 Node.js에서 실행 됩니다. 프로토콜의 클라이언트 및 서버 부분을 구현 하는 라이브러리를 공유 합니다.

## <a name="how-the-lsp-works"></a>LSP의 작동 원리

자체 프로세스에서 실행 되는 언어 서버 및 Visual Studio 또는 VS Code와 같은 도구를 언어 프로토콜을 사용 하 여 JSON RPC를 통해 서버와 통신 합니다. 언어 서버 전용된 프로세스에서 운영의 또 다른 이점은 단일 프로세스 모델에 관련 된 성능 문제 방지 됩니다. 실제 전송 채널 수 stdio, 소켓, 명명 된 파이프 또는 노드 ipc 클라이언트와 서버는 Node.js에 작성 된 경우.

루틴 중 도구와 언어 서버 간의 통신 하는 방법에 대 한 예제 세션을 편집 하는 아래는:

![lsp 흐름 다이어그램](media/lsp-flow-diagram.png)

* **사용자 도구에서 (문서 라고도 함) 파일을 엽니다**: 도구는 문서가 열려 있는 언어 서버 알립니다 (' textDocument/didOpen '). 지금부터 문서의 내용에 대 한 진실을 파일 시스템에 더 이상 하지만 메모리에서 도구를 통해 유지 합니다.

* **사용자가 편집**: 도구 문서 변경 (' textDocument/didChange ')에 대 한 서버 알리고 언어 서버에서 프로그램의 의미 체계 정보가 업데이트 됩니다. 이런 언어 서버가이 정보를 분석 하 고 검색 된 오류 및 경고 (' textDocument/publishDiagnostics ')를 사용 하는 도구에 알립니다.

* **사용자의 편집기에서 기호 "정의로 이동"을 실행할**: 이 도구는 두 개의 매개 변수를 사용 하 여 ' textDocument/정의 ' 요청을 보냅니다. (1) 문서 URI 및 (2) 서버에 요청 정의로 이동 된 시작한 텍스트 위치 합니다. 서버 문서 URI 및 문서 내에서 기호 정의의 위치를 사용 하 여 응답합니다.

* **사용자 문서 (파일)를 닫고**: 문서가 더 이상 메모리에 현재 콘텐츠는 이제 파일 시스템에 대 한 최신 언어 서버에 게 알리는 도구에서 ' textDocument/didClose ' 알림이 전송 됩니다.

이 예제에서는 "정의로 이동", "모든 참조 찾기"와 같은 편집기 기능 수준에서 언어 서버 프로토콜을 통신 하는 방법을 보여 줍니다. 프로토콜에서 사용 되는 데이터 형식은 편집기 또는 IDE '데이터 형식' 현재 열려 있는 텍스트 문서 등 커서의 위치입니다. 데이터 형식 추상 구문 트리 및 컴파일러 기호 (예를 들어 확인 된 형식, 네임 스페이스,...) 일반적으로 제공 되는 프로그래밍 언어 도메인 모델 수준에서 않습니다. 이 프로토콜을 크게 간소화합니다.

이제 좀 더 자세히 ' textDocument/정의 ' 요청에 살펴보겠습니다. 클라이언트 도구와 "정의로 이동" 요청에 대 한 언어 서버 간에 이동 하는 페이로드는 다음과 같습니다는 C++ 문서.

다음은 요청입니다.

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

다음은 응답입니다.

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

되돌아보면, 편집기의 수준 대신 프로그래밍 언어 모델 수준에서 데이터 형식을 설명 하는 경우 언어 서버 프로토콜의 성공 여부에 대 한 이유 중 하나 텍스트 문서 URI를 표준화 하는 것이 훨씬 또는 커서 위치는 추상 구문 트리 및 컴파일러 기호를 표준화 하 고 여러 다른 프로그래밍 언어와 비교 합니다.

사용자가 다른 언어를 사용 하 여 작업을 하는 경우 VS Code는 일반적으로 각 프로그래밍 언어에 대 한 언어 서버를 시작 합니다. 아래 예제에서는 Java 및 SASS 파일에 사용자가 근무 하는 위치는 세션을 보여 줍니다.

![java 및 sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>기능

일부 언어 서버 프로토콜에 의해 정의 된 모든 기능을 지원할 수 있습니다. 따라서 클라이언트와 서버 '기능'을 통해 해당 지원 되는 기능 집합을 알립니다. 예를 들어 서버가 알립니다 ' textDocument/정의 ' 요청을 처리할 수는 ' 작업 영역/기호 ' 요청을 처리 하지 않을 수 있습니다. 마찬가지로, '에 대 한 저장'을 제공할 수는 클라이언트를 알릴 수 있습니다 서버를 자동으로 편집된 된 문서의 서식을 지정 하려면 텍스트 편집을 계산할 수 있도록 문서를 저장 하기 전에 알림.

## <a name="integrating-a-language-server"></a>언어 서버 통합

특정 도구에 실제 언어 서버 통합 언어 서버 프로토콜에 의해 정의 되지 않은, 도구 구현자에 유지 됩니다. 일부 도구를 시작 하 고 모든 종류의 언어 서버와 통신할 수 있는 확장 함으로써 언어 서버 일반적으로 통합 합니다. 다른 같이 VS Code를 만들 언어 서버당 사용자 지정 확장 프로그램을 확장은 일부 사용자 지정 언어 기능을 제공할 수 있도록 합니다.

를 간소화 하기 위해 구현 언어 서버 및 클라이언트의 경우 라이브러리 또는 Sdk 클라이언트 및 서버 부분 이러한 라이브러리는 다른 언어로 제공 됩니다. 예를 들어를 [언어 클라이언트 npm 모듈](https://www.npmjs.com/package/vscode-languageclient) 손쉽게 언어 서버의 VS Code 확장을 통합 하기 위해 [언어 server npm 모듈](https://www.npmjs.com/package/vscode-languageserver) Node.js를 사용 하는 language 서버에 쓸입니다. 이 현재 [목록](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) 지원 라이브러리입니다.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>언어 서버 프로토콜을 사용 하 여 Visual Studio에서

* [언어 서버 프로토콜 확장 추가](adding-an-lsp-extension.md) -Visual Studio 언어 서버 통합에 대해 알아봅니다.
