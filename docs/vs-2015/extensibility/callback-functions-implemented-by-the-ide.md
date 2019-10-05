---
title: IDE에 의해 구현 된 콜백 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: df2daef11303e85d5fe2d0bf33e3df038081db64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184525"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE에서 구현된 콜백 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

와 통합 하 고 통합 된 최종 사용자 환경을 제공 하기 위해 최대한 원활 하 게으로 통합된 개발 환경 (IDE) 소스 제어 플러그 인 사용할 수 IDE에 의해 구현 되는 콜백 함수. 플러그 인이 함수를 호출할 수 이러한 정보는 IDE를 전달 하는 소스 제어 작업 중 적절 한 시간 IDE 기본 UI에 포함 된 요소로이 정보를 표시할 수 있습니다. 사용자 이면 플러그 인 사용 자체 UI 보다이 시나리오에서 덜 조각난 된 환경이 있습니다.  
  
 필수 헤더 파일이 scc.h입니다. 기본 위치는 \Program Files\VSIP 8.0\EnvSDK\common\inc\\합니다. 소스 제어 플러그 인 샘플 \Program Files\VSIP 8.0\MSSCCI에 VSIP 폴더에서 이기도\\합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 사용 되는 콜백 함수를 설명 [SccOpenProject](../extensibility/sccopenproject-function.md) IDE를 통해 플러그 인 소스 제어 메시지를 표시 합니다.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 사용 되는 콜백 함수를 설명 [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE 플러그 인을 버전 제어에서 파일의 전체 목록을 같은 소스 제어에만 사용할 수 있는 정보에 대 한 전체 액세스가 없습니다.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 사용 되는 콜백 함수에 설명 합니다 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 작업 합니다.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 사용 되는 콜백 함수에 설명 합니다 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 작업 합니다.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 콜백 함수를 호출 하 여 설정에 대해 설명 합니다 [SccSetOption](../extensibility/sccsetoption-function.md) 소스 제어 플러그 인 이름 변경 IDE를 다시 전달할 수 있도록 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 프로젝트를 엽니다.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 현재 상태에 대 한 파일 목록을 검사합니다. 또한에서는 합니다 `pfnPopulate` 파일에 대 한 조건과 일치 하지 않는 경우 호출자에 게 알리도록 함수는 `nCommand`합니다.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 프로젝트 또는 소스 제어에서 사용 중인 프로젝트에서 파일과 디렉터리의 목록을 검사 합니다. 각 디렉터리 및 파일 이름은 찾을 수는 콜백 함수에 전달 됩니다.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 파일의 목록에 대 한 이름 변경 내용을 검사 합니다. 각 파일 이름이 변경 상태와 함께 콜백 함수에 전달 됩니다.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 다양 한 옵션을 설정합니다. 각 옵션을 사용 하 여 시작 `SCC_OPT_xxx` 자체 정의 된 값 집합이 있고 합니다.  
  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)  
 소스 제어 플러그 인 SDK의 참조 섹션의 내용을 설명합니다.
