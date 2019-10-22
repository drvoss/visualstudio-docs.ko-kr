---
title: XSLT 코드를 디버깅 하는 방법
ms.date: 03/05/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: bb358efb711211d58525afb8d30d5cb4cad6b2e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646078"
---
# <a name="debugging-xslt"></a>XSLT 디버깅

Visual Studio에서 XSLT 코드를 디버그할 수 있습니다. XSLT 디버거는 중단점 설정, XSLT 실행 상태 보기 등을 지원 합니다. Xslt 디버거를 사용 하 여 xslt 스타일 시트 또는 XSLT 응용 프로그램을 디버그할 수 있습니다.

코드를 한 단계씩 코드 실행, 프로시저 단위 실행 또는 프로시저 나가기를 수행 하 여 한 번에 한 줄씩 코드를 실행할 수 있습니다. XSLT 디버거의 코드 단계별 실행 기능을 사용 하는 명령은 다른 Visual Studio 디버거와 동일 합니다.

디버깅을 시작하면 XSLT 디버거에서 입력 문서와 XSLT 출력을 창에 표시합니다.

> [!NOTE]
> XSLT 디버거는 Visual Studio Professional 및 Enterprise edition 에서만 사용할 수 있습니다.

## <a name="debug-from-the-xml-editor"></a>XML 편집기에서 디버그

편집기에서 스타일 시트 또는 입력 XML 파일을 연 경우 디버거를 시작할 수 있습니다. 이를 통해 스타일 시트를 디자인 하는 동안 디버그할 수 있습니다.

1. Visual Studio에서 스타일 시트 또는 XML 파일을 엽니다.

1. **XML** 메뉴에서 **XSLT 디버깅 시작** 을 선택 하거나 **Alt** +**f5**키를 누릅니다.

## <a name="debug-from-an-app-that-uses-xslt"></a>XSLT를 사용 하는 앱에서 디버그

응용 프로그램을 디버깅 하는 동안 XSLT를 한 단계씩 실행 할 수 있습니다. @No__t_1 호출에서 **F11** 키를 누르면 디버거가 XSLT 코드를 한 단계씩 코드 실행 할 수 있습니다.

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> 클래스에서 XSLT를 한 단계씩 실행하는 것이 지원되지 않습니다. <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 디버깅하는 동안 XSLT를 한 단계씩 실행하도록 지원하는 유일한 XSLT 프로세서입니다.

### <a name="to-start-debugging-an-xslt-application"></a>XSLT 애플리케이션 디버깅을 시작하려면

1. <xref:System.Xml.Xsl.XslCompiledTransform> 개체를 인스턴스화할 때 코드에서 `enableDebug` 매개 변수를 `true`로 설정합니다. 그러면 XSLT 프로세서에서 코드를 컴파일할 때 디버그 정보가 생성됩니다.

1. **F11** 키를 눌러 XSLT 코드를 한 단계씩 코드 실행 합니다.

   XSLT 스타일 시트가 새 문서 창에 로드 되 고 XSLT 디버거가 시작 됩니다.

   또는 스타일시트에 중단점을 추가하고 애플리케이션을 실행할 수 있습니다.

### <a name="example"></a>예제

다음은 C# XSLT 프로그램의 예로, XSLT 디버깅을 활성화하는 방법을 보여 줍니다.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT 프로파일러

[Xslt 프로파일러](../xml-tools/xslt-profiler.md) 는 자세한 xslt 성능 보고서를 만들어 xslt 코드의 성능 관련 문제를 측정, 평가 및 대상으로 지정할 수 있는 도구입니다. 자세한 내용은 [XSLT profiler](../xml-tools/xslt-profiler.md)를 참조 하세요.

## <a name="see-also"></a>참조

- [연습: XSLT 스타일 시트 디버깅](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [먼저 Visual Studio 디버거 살펴보기](../debugger/debugger-feature-tour.md)
- [디버깅 기본 사항: 중단점](../debugger/using-breakpoints.md)
