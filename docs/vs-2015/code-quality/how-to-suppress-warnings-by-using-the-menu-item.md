---
title: '방법: 메뉴 항목을 사용 하 여 경고 표시 안 함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5097ecb0f7458e739def275d616eb344a2a6db0d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426562"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>방법: 메뉴 항목을 사용하여 경고 표시 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 웹 사이트 프로젝트에서는 ISS(In source suppression)가 지원되지 않습니다.  
  
 코드 분석 창을 사용하면 코드 분석 경고 표시를 숨길 수 있습니다. 경고 표시 숨김은 경고를 비활성화하는 것과 다릅니다. 경고를 표시 하지 않으려면 위반의 특정 인스턴스에만 적용 됩니다. 여전히 동일한 경고를 다른 위반 오류 목록 창에 보고 됩니다.  
  
 코드 분석을 실행한 후 코드 분석 창에 표시된 하나 이상의 코드 분석 경고가 애플리케이션에 해당되지 않는 것인지 확인할 수 있습니다. 예를 들어 코드 올바른지 확인할 수 있습니다. 또는 일부 위반 낮은 우선 순위 이며 현재 개발 주기에서 수정 되지 않는 경우 수 있습니다. 어떤 이유로든 코드를 검토했으며 해당 경고를 표시하지 않기로 결정했음을 팀 구성원에게 알리기 위해 경고가 상황에 적합하지 않을 수 있다는 사실을 밝히는 것이 좋습니다. ISS(In Source Suppression)는 경고가 생성되는 지점에 가깝게 표시 숨김을 설정할 수 있기 때문에 유용합니다.  
  
 전역 비 표시 오류 파일 또는 소스 코드에서를 억제에 나타날지 여부를 선택할 수 있습니다. 일부 비 표시 오류 전역 비 표시 오류 파일에 배치 되어야 합니다. 이 경우는 **소스** 옵션이 비활성화 됩니다.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>메뉴 항목을 사용 하 여 경고를 표시 하려면  
  
1. 에 **분석** 메뉴 선택 **Windows** 를 선택한 후 **코드 분석**합니다.  
  
2. 에 **코드 분석** 창에서 경고 숨김을 선택 합니다.  
  
3. 작업을 선택한 다음 선택 **메시지 표시 안 함**를 선택 하 고 **소스** 또는 **프로젝트 비 표시 오류 파일의**합니다.  
  
     해당 경고가 표시되지 않고, 취소선이 그려진 상태로 경고가 코드 분석 창에 나타납니다.  
  
> [!NOTE]
> 전역 비 표시 오류 파일의 대상이 되지 않은 비 표시 오류 나타납니다.
