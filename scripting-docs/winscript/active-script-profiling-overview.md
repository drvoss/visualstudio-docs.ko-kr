---
title: 액티브 스크립트 프로파일링 개요 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 777d20ecb51b09b282f88dc08464727b9ff2a945
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432970"
---
# <a name="active-script-profiling-overview"></a>액티브 스크립트 프로파일링 개요
[액티브 스크립트 프로파일러 인터페이스](../winscript/reference/active-script-profiler-interfaces.md)는 스크립팅 엔진의 프로파일링을 사용하도록 설정합니다. 액티브 스크립트 프로파일링은 다음 부분으로 구성됩니다.  
  
- 언어 엔진  
  
- 호스트  
  
- 프로파일러  
  
## <a name="language-engine"></a>언어 엔진  
 언어 엔진은 스크립트를 실행합니다. 스크립트 코드를 실행할 때 프로파일링을 사용하는 메서드를 제공합니다. 프로파일링이 사용되면 언어 엔진에서 프로파일러 COM 개체의 CLSID(클래스 식별자)를 인수로 사용합니다. 프로파일러 COM 개체의 인스턴스를 만든 다음 다양한 이벤트가 발생할 때 프로파일러를 호출합니다.  
  
 언어 엔진은 [IActiveScriptProfilerControl 인터페이스](../winscript/reference/iactivescriptprofilercontrol-interface.md)를 구현합니다.  
  
> [!NOTE]
> [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 언어 런타임은 작성 시 JS_PROFILER 환경 변수를 확인하여 프로파일링을 사용해야 하는지 여부를 결정합니다. 이 변수가 프로파일러의 CLSID로 설정되면 언어 런타임에서 만들 프로파일러를 결정하기 위해 해당 변수의 값을 사용하여 프로파일러 COM 개체의 인스턴스를 만듭니다.  
  
## <a name="host"></a>호스트  
 호스트는 언어 엔진을 만들고 실행될 스크립트를 언어 엔진에 제공합니다. 또한 스마트 호스트는 디버그하거나 프로파일링할 때 더 나은 정보를 제공하기 위해 디버거 또는 프로파일러에서 사용할 수 있는 문서 컨텍스트를 제공합니다.  
  
## <a name="profiler"></a>프로파일러  
 프로파일러는 다양한 이벤트가 발생할 때 언어 엔진에서 호출을 받습니다. 프로파일러는 COM 개체로 등록되어야 하며 [IActiveScriptProfilerCallback 인터페이스](../winscript/reference/iactivescriptprofilercallback-interface.md)를 구현해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 프로파일러 인터페이스](../winscript/reference/active-script-profiler-interfaces.md)