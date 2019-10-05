---
title: 목록 코드 조각 (레거시) 설치 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de116d6abb995375ba04ae1e8407eba7754ae5e9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323381"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>연습: 설치된 코드 조각 목록 가져오기(레거시 구현)
코드 조각에서 키나 메뉴 명령 (허용 하는 설치 된 코드 조각 목록 중에서 선택)를 사용 하 여 원본 버퍼에 삽입할 수 있는 코드는 IntelliSense 완성 목록에서 조각 바로 가기를 선택 합니다.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> 메서드는 특정 언어 GUID에 대 한 모든 코드 조각을 가져옵니다. 해당 조각에 대 한 바로 가기는 IntelliSense 완성 목록에 삽입할 수 있습니다.

 참조 [레거시 언어 서비스의 코드 조각에 대 한 지원을](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) 코드 조각 관리 패키지 프레임 워크 (MPF) 언어 서비스의 구현에 대 한 세부 정보에 대 한 합니다.

### <a name="to-retrieve-a-list-of-code-snippets"></a>코드 조각의 목록을 검색 하려면

1. 다음 코드에는 지정된 된 언어에 대 한 코드 조각의 목록을 가져오는 방법을 보여 줍니다. 결과 배열에 저장 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> 구조입니다. 이 메서드는 정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드를 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 에서 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 서비스입니다. 그러나 VSPackage 및 호출에 지정 된 서비스 공급자도 사용할 수는 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 메서드.

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>GetSnippets 메서드를 호출 하려면

1. 다음 메서드를 호출 하는 방법을 보여 줍니다는 `GetSnippets` 메서드 구문 분석 작업을 완료 합니다. 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> 이유인 시작 된 구문 분석 작업을 수행한 후 메서드는 <xref:Microsoft.VisualStudio.Package.ParseReason>합니다.

> [!NOTE]
> `expansionsList` 성능상의 이유로 배열 목록을 캐시 됩니다. 언어 서비스를 중지 하 고 다시 로드 될 때까지 목록에 코드 변경 내용이 반영 되지 않습니다 (예를 들어, 중지 및 다시 시작 하 여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>조각 정보를 사용 하려면

1. 다음 코드를 반환 하는 코드 조각 정보를 사용 하는 방법을 보여 줍니다는 `GetSnippets` 메서드. `AddSnippets` 파서가 코드 조각의 목록을 채우는 데 사용 되는 모든 구문 분석 원인에 대 한 응답에서에서 메서드를 호출 합니다. 전체 구문 분석에 처음으로 완료 된 후 수행 해야이 있습니다.

     `AddDeclaration` 메서드는 나중에 완성 목록에 표시 되는 선언의 목록을 작성 합니다.

     `TestDeclaration` 클래스 선언의 형식 뿐만 아니라 완성 목록에 표시 될 수 있는 모든 정보를 포함 합니다.

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)