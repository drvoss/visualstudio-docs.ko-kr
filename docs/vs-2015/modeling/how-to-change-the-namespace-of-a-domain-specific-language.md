---
title: '방법: 도메인 특정 언어의 Namespace 변경 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e86fa8f220cdd31beae12e050a1cbaa592624a74
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690559"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>방법: 도메인 특정 언어의 네임스페이스 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도메인 특정 언어의 네임 스페이스를 변경할 수 있습니다. 변경 해야 합니다 **DSL 탐색기**, Dsl 패키지 프로젝트의 속성 및 어셈블리 정보입니다.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>도메인 특정 언어의 네임 스페이스를 변경 하려면  
  
1. **DSL 탐색기**를 클릭 합니다 **Dsl** 노드.  
  
2. 에 **속성** 창에서 변경 합니다 **Namespace** 속성입니다.  
  
3. 솔루션을 저장 하 고 템플릿을 변형 합니다.  
  
4. 에 **프로젝트** 메뉴에서 클릭 **Dsl 속성**합니다.  
  
     프로젝트에 대 한 속성이 표시 됩니다.  
  
5. **응용 프로그램** 탭을 클릭합니다.  
  
6. 변경 된 **기본 네임 스페이스** 속성을 새 네임 스페이스 이름입니다.  
  
7. 어셈블리의 이름을 변경 하려면 변경 된 **어셈블리 이름 속성입니다.**  
  
8. 어셈블리 이름을 변경한 경우 DslPackage\Package.tt 열고이 줄을 업데이트 합니다.  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. 사용자 지정 코드를 작성 하는 경우에 코드 파일에서 네임 스페이스 및 클래스 참조를 변경 해야 합니다.  
  
10. Visual Studio 실험적 인스턴스 다시 설정 합니다.  
  
    1. 삭제할 **\Users\\** _{name}_ **\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2. Windows에서 **시작** 메뉴에서 선택 **모든 프로그램**를 **Microsoft Visual Studio 2010 SDK**를 **도구**, **다시 설정 합니다 실험적 인스턴스에서**합니다.  
  
11. 에 **빌드할** 메뉴에서 선택 **솔루션 다시 빌드**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
