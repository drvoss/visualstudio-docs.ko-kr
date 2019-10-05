---
title: 클래스 디자이너의 Visual C++ 구조체 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed47509467bd8691b6f81dbd52fac47cf21c3715
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698190"
---
# <a name="visual-c-structures-in-class-designer"></a>클래스 디자이너의 Visual C++ 구조체
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

클래스 디자이너는 `struct` 키워드로 선언된 C++ 구조체를 지원합니다. 예를 들면 다음과 같습니다.  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 `struct` 형식을 사용하는 방법에 대한 자세한 내용은 [구조체](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)를 참조하세요.  
  
 레이블이 **구조체**를 읽고 둥근 모서리 대신 사각형 모서리를 갖고 있다는 점을 제외하고, 클래스 다이어그램에서 C++ 구조체 모양은 클래스 모양처럼 보이고 실제 그러한 작용을 합니다.  
  
|코드 요소|클래스 디자이너 보기|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 구조체|  
  
## <a name="see-also"></a>참고 항목  
 [Visual C++ 코드 작업(클래스 디자이너)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [클래스 및 구조체](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)
