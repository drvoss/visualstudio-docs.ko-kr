---
title: 인터페이스 추출 리팩터링 (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: deb2e446ff051b52e9c34d28abfa99436c064ad6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680902"
---
# <a name="extract-interface-refactoring-c"></a>인터페이스 추출 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

인터페이스 추출은 기존 클래스, 구조체 또는 인터페이스에서 발생 하는 멤버를 사용 하 여 새 인터페이스를 만들 수는 간편한 방법을 제공 하는 리팩터링 작업 합니다.  
  
 여러 클라이언트 클래스, 구조체 또는 인터페이스 멤버의 동일한 하위 집합을 사용 하는 경우 또는 여러 클래스, 구조체 또는 인터페이스 멤버의 하위 집합에 공통적인 있는 경우에 인터페이스 멤버의 하위 집합을 지킬 유용할 수 있습니다. 인터페이스를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [인터페이스](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)합니다.  
  
 인터페이스 추출 새 파일에서 인터페이스를 생성 하 고 새 파일의 시작 부분에 커서를 놓습니다. 새로운 인터페이스, 새 인터페이스의 이름 및 사용 하 여 생성 된 파일 이름을 추출 하는 멤버를 지정할 수 있습니다 합니다 **인터페이스 추출** 대화 상자.  
  
### <a name="to-use-extract-interface"></a>인터페이스 추출 사용 하려면  
  
1. 라는 콘솔 응용 프로그램을 만듭니다 `ExtractInterface`, 하 고 다음 대체 `Program` 다음 코드를 사용 하 여  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2. 커서가 `MethodB`, 클릭 **인터페이스 추출** 에 **리팩터링** 메뉴.  
  
     합니다 **인터페이스 추출** 대화 상자가 나타납니다.  
  
     바로 가기 키 CTRL + R, I 표시를 입력할 수도 있습니다는 **인터페이스 추출** 대화 상자.  
  
     마우스를을 마우스 오른쪽 단추로 클릭 가리킵니다 **리팩터링**를 클릭 하 고 **인터페이스 추출** 표시 하는 **인터페이스 추출** 대화 상자.  
  
3. 클릭 **모두 선택**합니다.  
  
4. **확인**을 클릭합니다.  
  
     새 파일, IProtoA.cs, 및 다음 코드를 표시 합니다.  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>설명  
 이 기능은 커서가 클래스, 구조체 또는 인터페이스를 추출 하려고 하는 멤버를 포함 하는 경우에 액세스할 수 있습니다. 커서가이 위치에 있는 경우 인터페이스 추출 리팩터링 작업을 호출 합니다.  
  
 클래스 또는 구조체에서 인터페이스 추출을 호출 하면 기본 및 인터페이스 목록은 새 인터페이스 이름을 포함 하도록 수정 됩니다. 인터페이스에서 인터페이스 추출을 호출 하면 기본 및 인터페이스 목록 수정 되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)