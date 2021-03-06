---
title: Visual Studio 디버거 용어집 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37c0608b5684c9d16041ce89707dd81e665b0623
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757941"
---
# <a name="visual-studio-debugger-glossary"></a>Visual Studio 디버거 용어집
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

다음은에 사용 된 용어는 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debugging SDK.  
  
## <a name="terms"></a>용어  
 바인딩된 중단점  
 코드에서 설정 된 중단점에 대 한 추상화입니다. 바인딩된 중단점 및 코드 스트림의 중단점이 지침을 간에 일대일 관계가 있습니다. 언로드될 때 코드, 바인딩된 중단점 바인딩을 해제할 수 있습니다.  
  
 인과 관계  
 여러 실제 스레드, 프로세스 및 컴퓨터에서 실행의 논리적 스레드를 추적 하 고 해당 스레드의 수명에서 특정된 시점에서 논리적 스레드의 호출 스택을 다시 생성 하는 기능을 제공 합니다.  
  
 코드 컨텍스트  
 디버그 엔진에 알려진 코드 위치의 추상화를 제공 합니다. 대부분의 런타임 아키텍처에 대 한 코드 컨텍스트는 프로그램의 명령 스트림에 주소입니다. 코드 수 수 변수로 표현 되지 내용은 않던 언어에 대 한 코드 컨텍스트를 다른 방법으로 나타낼 수 있습니다.  
  
 코드 경로  
 여기서는 분기를 취하게 됩니다 또는 함수를 호출 하 여 코드의 실행을 나타냅니다. 스택 추적에는 기본적으로 함수 호출 코드 경로의 목록입니다.  
  
 디버그 엔진 (DE)  
 런타임 아키텍처의 디버깅을 허용 하는 구성 요소입니다. 디버그 엔진 인터프리터 또는 운영 체제와 함께 작동 하 고 실행 제어, 중단점 및 식 평가 같은 디버깅 서비스를 제공 합니다.  
  
 문서 컨텍스트  
 디버그 엔진에 알려진 소스 파일 문서의 위치 추상화를 제공 합니다. 대부분의 언어에 대 한 문서 컨텍스트는 원본 파일의 위치입니다. 소스 파일이 아닐 텍스트 않던 언어에 대 한 문서 컨텍스트를 다른 방법으로 표현 될 수 있습니다. 참고 항목 *위치에 문서*합니다.  
  
 문서 위치  
 IDE에 알려진 소스 파일의 위치는 추상화를 제공 합니다. 대부분의 언어를 문서 위치는 원본 파일의 위치입니다. 않던 언어에 대 한 문서 위치는 다른 방법으로 표현 될 수 있습니다. 참고 항목 *문서 컨텍스트*합니다.  
  
 중단점 오류  
 보류 중인 중단점에 오류를 설명 하기 위한 추상화입니다. 오류 중단점을 보류 중인 중단점에 보류 중인 중단점 또는 보류 중인 중단점 코드 위치로 바인딩 되지 못하도록 하는 기타 정보를 사용 하 여 연결 된 식의 위치에 오류를 설명할 수 있습니다.  
  
 평가 컨텍스트  
 식 계산에 대 한 프로그래밍 컨텍스트의 추상화를 제공 합니다. 일반적으로 평가 컨텍스트가 범위입니다. 식 컨텍스트에서 식 계산을 수행 하는 경우 식 컨텍스트 범위 일치 하는 규칙 만들기의 해당 지점 제공 합니다. 예를 들어, 스택 프레임에서 만든 식 컨텍스트를 로컬 변수, 메서드 매개 변수, 클래스 멤버 (있는 경우) 및 전역 변수를 평가 하는 것에 대 한 컨텍스트를 제공 합니다.  
  
 가로챈된 예외  
 현재 스택 프레임의 위치에 없는 예외 처리 메커니즘은 경우에 디버그 엔진에 의해 차단 되는 예외입니다.  
  
 JustMyCode  
 사용자에 속하는 코드를 디버깅 하 고 시스템 코드와 같은 모든 중간 코드를 무시 하 여 개념이-소스 코드 시스템 코드에 사용할 수 있는 경우에 합니다.  
  
 보류 중인 중단점  
 이전, 도중 및 이후 중단점에 대 한 추상화를 제공 코드는 로드 및 중단점을 가상화 하는 방법입니다. 중단점 보류 중인는:  
  
- 하나 이상의 응용 프로그램의 코드에 중단점을 바인딩할 때 필요한 모든 정보를 포함 합니다.  
  
- 하나 이상의 응용 프로그램의 여러 코드 위치에 바인딩할 수 있습니다.  
  
- 코드 자체 바인딩되지 않습니다.  
  
  각 시간 코드를 로드, 프로그램에서 모든 보류 중인 중단점을 확인 하 여 하는 바인딩할 수 있습니다. 보류 중인 중단점 바인딩되기는 바인딩된 모든 중단점을 포함 하도록 라고 합니다.  
  
  process  
  실제 Win32 프로세스입니다. 프로세스는 여러 프로그램을 포함할 수 있습니다. 참고 항목 *프로그램*합니다.  
  
  프로그램  
  특정 런타임 아키텍처 내에서 실행 중인 단일 네임 스페이스입니다. 참고 항목 *프로세스*합니다.  
  
  세션 디버그 관리자 SDM)  
  임의 개수의 임의 개수의 임의 개수의 컴퓨터에서 여러 프로세스에서 프로그램을 디버깅 하는 디버그 엔진을 관리 합니다. 기본적인 수준에서 SDM은 디버그 엔진의 멀티플렉서입니다. 또한 SDM IDE에는 디버깅 세션의 통합된 보기를 제공합니다.  
  
  스택 프레임  
  특정 프레임에 계산의 상태 및 특정 수준의 중첩 된 함수 호출을 나타냅니다.  
  
  스레드  
  일반화 된 개념이 프로그램이 하나 이상에서 실행 되는 스택 기반 명령 실행 합니다.  
  
  경고 중단점  
  보류 중인 중단점에 경고를 설명 하는 추상화입니다. 경고 중단점 이유 보류 중인 중단점에 아직 바인딩되지 코드 위치로 이유를 설명 합니다. 보류 중인 중단점에서 설명 하는 위치 또는 다른 이유로 코드 아직 로드 되지 않은 것 같습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 디버거 확장성](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

