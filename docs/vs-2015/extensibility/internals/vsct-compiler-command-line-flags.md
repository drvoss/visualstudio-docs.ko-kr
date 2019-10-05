---
title: VSCT 컴파일러 명령줄 플래그 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98cd0ec51ead200a904baeb409551cd1084f1f11
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440825"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT 컴파일러 명령줄 플래그
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 명령 테이블 (VSCT) 컴파일러.vsct 파일의 컴파일이 성공 하도록 명령줄 스위치를 제공 합니다.  
  
## <a name="command-line-parameters"></a>명령줄 매개 변수  
 기본 VSCT 도움말을 보려면를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **명령** 창으로 이동 합니다 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Tools\Bin\ 폴더 및 형식:  
  
```  
vsct /?  
```  
  
 여기서 반환합니다.  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indicate what additional include paths to send to the preprocessor  
  -L    Specify the language to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        followed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependency checks  
  -v    Verbose output  
```  
  
> [!NOTE]
> 문자-(dash) 및 / (슬래시)은 모두 허용 된 표기법 명령줄 매개 변수를 나타냅니다.  
  
 허용 가능한 플래그 및 그 의미는 다음과 같습니다.  
  
|전환|설명|  
|------------|-----------------|  
|-D|모든 추가 정의 된 기호를 지정 합니다.|  
|-I|추가 포함 파일 참조를 확인할 때 사용 해야 하는 경로 나타냅니다.|  
|-L|지정 된 <xref:System.Globalization.CultureInfo> 예를 들어 "EN-US" 문화권 이름입니다.|  
|-E|내보내기 C# 뒤에 명령 항목에 대 한 지정된 된 네임 스페이스에서 개체 [C&#124;H&#124;N]:*filename*여기서 C = C#, H = C++ 헤더, N 네임 스페이스 =. 네임 스페이스는 C#에 대 한 필요 합니다.|  
|-v|자세한 정보를 출력 합니다.|  
  
 -L 스위치에 해당 하는 이진.cto 파일을 생성 하는 문자열의 그룹을 선택 하려면 컴파일러에 지시 합니다 지정 <xref:System.Globalization.CultureInfo> 문화권 이름입니다. 지정 된 문화권 이름에는 하나 이상의 언어 특성과 일치 해야 [Strings 요소](../../extensibility/strings-element.md) .vsct 파일에서 합니다. 포함 하는에서 상속 된 문자열 요소를 언어 특성이 없는 경우 [CommandTable 요소](../../extensibility/commandtable-element.md)합니다.  
  
 .Vsct 파일을 여러 문자열 요소가 있을 수 있습니다 하 고 각각 다른 언어 특성을 갖고 있습니다. 세계화는 VSCT 컴파일러인을 여러 번 실행 하 고 각 문화권 이름에 대해-L 스위치를 변경 하 여 이루어집니다.  
  
 -L 스위치에서 지정 된 문화권 이름 문자열 요소의 언어 특성 일치 하지 않는 경우 컴파일러는 해당 언어 및 지역이 아닌 일치 하려고 합니다. 예를 들어 "EN-US"를 찾을 수 없는 경우 컴파일러는 대신 "en"입니다. 실패 하는 운영 체제의 현재 문화권을 찾으려고 합니다. 실패 하는 첫 번째 문자열 요소를 찾으면 컴파일됩니다.  
  
 명령 테이블에서 사용 되는 기호를 포함 하는 C 스타일 헤더 파일 또는 명령 기호에 대 한 개체를 포함 하는 C# 파일을 내보내지-E 스위치를 사용할 수 있습니다.  
  
 -D 및-I 스위치 동일한 이름을 가진 Cl.exe C 전처리기 플래그 구문을 사용 해야 합니다. – D XML 기반 확장에 대 한 X = Y 형식이 정의 되 \<정의 > 테스트 `Condition` 특성입니다. 경로 포함 하려는 해결 하는 데 사용 됩니다 \<Include >, \<Extern > 및 \<비트맵 > 파일에서 참조 합니다. 자세한 내용은 참조는 [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)합니다.  
  
 VSCT 컴파일러인 이전에 빌드한 이진 파일로 디컴파일할 수도 수 있습니다. 이 작업을 수행 하려면에 대 한 이진 파일을 제공 합니다 \<infile >.   이진 파일을 VSCT 컴파일러에서 생성 된 경우 해당 기호를 이미 포함 해야 하 고는 기호화 된 이름 사용 하 여 출력을 생성 한 \<기호 > 출력 섹션입니다. 이진 CTC 컴파일러에서 생성 된 경우 실제 Guid 및 Id를 출력에 포함 됩니다. *.Ctsym 파일 Ctc.exe의 현재 버전에서 생성 되는 이진 입력 파일과 동일한 폴더에 있으면 기호를 해당 파일에서 로드 하 고 출력에 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)   
 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
