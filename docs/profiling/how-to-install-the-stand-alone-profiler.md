---
title: '방법: 독립 실행형 프로파일러 설치 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55c9e7c6ec4a34d59c45b2a56abedaa6d3fd2974
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942448"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>방법: 독립 실행형 프로파일러 설치
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]은(는) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE를 설치하지 않고 실행할 수 있는 명령줄 기반 독립 실행형 프로파일러를 제공합니다. 이 경우는 컴퓨터에 설치된 개발 환경이 없거나 설치할 수 없는 경우에 발생합니다. 예를 들어 프로덕션 웹 서버에 개발 환경을 설치하면 안 됩니다.  
  
> [!NOTE]
>  독립 실행형 프로파일러를 사용하여 ASP.NET 웹 사이트에 대한 성능 데이터를 수집하는 경우 [VSPerfCmd](../profiling/vsperfcmd.md) 도구보다 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 선 도구를 권장합니다.  
  
### <a name="to-install-the-stand-alone-profiler"></a>독립 실행형 프로파일러를 설치하려면  
  
1. *\독립 실행형 프로파일러* 경로를 포함하고 이를 실행하는 디렉터리의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 설치 미디어에서 독립 실행형 프로필 설치 관리자(*vs_profiler.exe*)를 찾습니다.  
  
2. *vsintr.exe*와 *msdis150.dll*의 경로를 시스템 경로에 추가합니다.  
  
   > [!NOTE]
   >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 기본 설치에서 *vsinstr.exe*와 *msdis150.dll*은 *\Program Files\Visual Studio 10\Team Tools\Performance Tools*에 있습니다.  
  
3. 명령 프롬프트에서 **VSInstr**을 입력합니다.  
  
   > [!NOTE]
   >  vsinstr.exe에 대한 사용 정보가 표시되면 모든 것이 올바르게 설정된 것입니다. vsinstr.exe를 나타내는 오류가 표시되거나 해당 종속성 중 하나가 없는 경우 2단계에 설명된 대로 경로를 정확하게 설정했는지 확인합니다.  
  
4. **_NT_SYMBOL_PATH** variable to **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**를 설정하여 기호 서버를 설정합니다.  
  
5. 시스템 환경 변수를 사용하여 기호 서버를 설정한 후 새 명령 프롬프트에서 명령줄 프로파일러 도구를 실행합니다. 그러면 새 환경 변수가 적용됩니다. 명령 프롬프트 창에서 다음 명령을 입력합니다.  
  
    **start %COMSPEC%**  
  
   > [!NOTE]
   >  기호 서버 패키지를 설정하는 방법에 대한 자세한 지침은 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)를 참조하세요.  
  
6. [VSPerfReport](../profiling/vsperfreport.md) 도구를 사용하여 기호를 프로파일링 데이터(.vsp) 파일로 직렬화합니다. **VSPerfReport /summary:all /packsymbols** 스위치를 사용합니다. 데이터 파일에 삽입된 기호가 없는 경우 _NT_SYMBOL_PATH 환경 변수를 설정했는지 확인합니다.  
  
## <a name="see-also"></a>참고 항목  
 [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [연습: 샘플링을 사용하여 명령줄 프로파일링](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [연습: 계측을 사용하여 명령줄 프로파일링](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)