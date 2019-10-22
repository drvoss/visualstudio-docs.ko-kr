---
title: IActiveScriptAuthor 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576163"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor 인터페이스
IntelliSense 및 정보의 데이터 정렬을 비롯 한 제작 서비스를 나타냅니다.  
  
 @No__t_0에서 상속 된 메서드 외에도 `IActiveScriptAuthor` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|루트 수준 항목의 이름을 스크립트 작성 엔진의 네임 스페이스에 추가 합니다. *루트 수준 항목* 은 속성 및 메서드를 포함할 수 있으며 이벤트 소스도 포함할 수 있는 개체입니다.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Scriptlet 코드를 루트 수준 `IScriptNode` 개체의 자식으로 추가 합니다. 호스트에서 scriptlet의 정규화 된 이름에는 두 수준만 있을 수 있습니다.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|스크립트에 대 한 네임 스페이스에 형식 라이브러리를 추가 합니다.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|요청 된 완료 컨텍스트의 완료 문자 집합을 반환 합니다.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|지정 된 특성이 있는 scriptlet을 반환 합니다.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|코드 블록의 지정 된 문자에 대 한 형식 정보 및 앵커 위치를 반환 합니다. 멤버 IntelliSense, 전역 목록 및 매개 변수 팁에 대 한 정보를 제공 합니다.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|언어 정보를 반환 합니다.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|작성자의 스크립트 트리의 `IScriptNode` 루트를 반환 합니다.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Scriptlet의 텍스트 특성을 반환 합니다.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|스크립트 블록의 텍스트 특성을 반환 합니다.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|지정 된 문자가 응용 프로그램에서 문 완성을 커밋하려고 하는지 여부를 나타내는 값을 반환 합니다.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|스크립트 텍스트를 구문 분석 하 고 제작 스크립트 제작 엔진에 텍스트를 추가한 다음 스크립트 블록에 해당 하는 `IScriptEntry` 개체를 만듭니다.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|스크립트 작성 엔진의 네임 스페이스에서 `NamedItem` 개체를 제거 합니다.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|스크립트 작성 엔진 네임 스페이스에서 형식 라이브러리를 제거 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 작성 인터페이스](../../winscript/reference/active-script-authoring-interfaces.md)