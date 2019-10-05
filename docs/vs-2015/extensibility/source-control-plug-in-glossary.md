---
title: 원본 제어 플러그 인 용어집 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160601"
---
# <a name="source-control-plug-in-glossary"></a>소스 제어 플러그 인 용어집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음과 같은 유용한 용어와 정의 소스 제어 플러그 인 SDK 설명서 관련이 있습니다.  
  
## <a name="definitions"></a>정의  
 체크 인  
 사용자의 작업 복사본을 변경 하면 사용자는 중앙 원본 제어 리포지토리로 작업 복사본의 변경 내용을 전송 해야 합니다. 이렇게 하면 다른 사용자에 게 사용할 수 있는 파일의 새 수정 버전이 만들어집니다. 이 프로세스는 체크 인을 이라고 합니다.  
  
 체크 아웃  
 수정 하려는 리포지토리를 알리는 리포지토리에서 작업 복사본을 요청 하는 작업. 작업 복사본을 체크 아웃 하는 시점을 기준으로 프로젝트의 상태를 반영 합니다.  
  
 클라이언트  
 소스 코드 제어 시스템을 사용 하는 프로그램입니다. 이 문서에서는 Visual Studio IDE는 것입니다.  
  
 설명  
 소스 제어 작업을 수행할 때 사용자 수정 버전을 연결할 수 있는 변경 내용을 설명 하는 메시지입니다.  
  
 충돌  
 두 사용자가 동일한 파일의 동일한 지역에 대 한 변경 내용을 체크 인하려고 시도할 때 상황입니다. 일반적으로 병합을 수행 해야 합니다.  
  
 디렉터리  
 클라이언트 쪽 로컬 폴더 디렉터리 라고 합니다. 이 버전은 사용자 변경 내용을 실제로 복사본입니다. 지정 된 프로젝트의 많은 작업 복사본이 있을 수 있습니다. 일반적으로 각 개발자가 자신의 복사본을 있습니다.  
  
 가져오기  
 가져오기 작업을 리포지토리 복사본을 사용 하 여 최신 사용자의 작업 복사본을 제공합니다. 체크 아웃을 달리 사용자에서 단순히 최신 복사본을 해야 하는 변경 되지 않게 하려는 경우 get은 수행 합니다.  
  
 기록  
 이 일반적으로 모든 체크 아웃, 체크 인, 업데이트, 태그 및 소스 제어 저장소에서 수행 하는 릴리스 요약 합니다.  
  
 IDE  
 일반적으로 Visual Studio 통합 개발 환경에 나타냅니다. 그러나 원본 제어 플러그 인 API를 인식 하는 다른 클라이언트 환경에 참조할 수도 있습니다.  
  
 병합  
 프로세스 중 두 개 이상의 소스 코드 파일 결합 되어 이전 파일에서 모든 기능을 통합 하는 새 파일입니다. 이 개념은 여기서 두 개 이상의 개발자가 작업 파일에 동시에 버전 제어에서 중요 합니다.  
  
 Project  
 소스 제어 폴더는 프로젝트 라고도 합니다. Visual Studio에서 프로젝트 또는 솔루션을 사용 하 여 관계가 없습니다.  
  
 플러그 인  
 원본 제어 플러그 인 API를 구현 하 여 소스 제어 기능을 제공 하는 DLL입니다.  
  
 리포지토리  
 원본 시스템을 제어 하는 경우 마스터 복사본을 프로젝트의 전체 수정 기록을 저장 합니다. 각 프로젝트에는 정확히 하나의 저장소를 있습니다.  
  
 Revision  
 파일의 기록 또는 파일 집합에는 커밋된 변경 내용. 수정 버전 하나인 지속적으로 변화는 프로젝트의 스냅숏.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
