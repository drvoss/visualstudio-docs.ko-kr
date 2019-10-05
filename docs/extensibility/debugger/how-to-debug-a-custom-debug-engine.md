---
title: '방법: 사용자 지정 디버그 엔진 디버그 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 992440dd137b5622f4c619f1f81008eb38e1ff5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334822"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>방법: 사용자 지정 디버그 엔진 디버그
프로젝트 형식에서 디버그 엔진 (DE)를 시작 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 메서드. 즉, 인스턴스의 제어 하는 DE 시작 되는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 형식을 제어 합니다. 그러나 해당 인스턴스의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 DE를 디버깅할 수 없습니다. 다음에 사용자 지정 DE 디버깅할 수 있도록 하는 단계는 같습니다.

> [!NOTE]
> :     "사용자 지정 디버그 엔진 디버그" 절차를 연결 하기 전에 시작 하는 de 기다려야 합니다. 메시지 상자는 DE 시작 될 때 나타나는 독일의 시작 부분에 배치 하면 해당 지점에 연결할 수 있으며 계속 하려면 메시지 상자의 선택을 취소 한 다음 수 있습니다. 이런 방식으로 catch 할 수 있습니다 모든 DE 이벤트입니다.

> [!WARNING]
> 원격 디버깅 절차를 시도 하기 전에 설치 해야 합니다. 참조 [원격 디버깅](../../debugger/remote-debugging.md) 세부 정보에 대 한 합니다.

## <a name="debug-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 디버그

1. 시작 *msvsmon.exe*, 원격 디버깅 모니터입니다.

2. **도구** 메뉴에서 *msvsmon.exe*를 선택 **옵션** 여는 **옵션** 대화 상자.

3. "인증 없음" 옵션을 선택 하 고 클릭 **확인**합니다.

4. 인스턴스를 시작할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 지정 DE 프로젝트를 엽니다.

5. 두 번째 인스턴스를 시작 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 DE를 시작 하는 사용자 지정 프로젝트를 엽니다 (개발 하는 경우이 일반적으로 VSIP를 설치할 때 설정 된 실험 레지스트리 하이브에서).

6. 이 두 번째 인스턴스의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]사용자 지정 프로젝트에서 소스 파일을 로드 하 고 디버그할 프로그램을 시작 합니다. 로드 하거나 중단점이 적중 될 때까지 대기 DE 허용 하는 데는 몇 분 정도 기다립니다.

7. 첫 번째 인스턴스의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (DE 프로젝트)를 선택 **프로세스에 연결** 에서 합니다 **디버그** 메뉴.

8. 에 **프로세스에 연결** 대화 상자에서 변경 합니다 **전송** 에 **원격 (네이티브만 인증 안 함)** 합니다.

9. 변경 된 **한정자** 컴퓨터의 이름 (참고:는 항목의 기록을 있으므로이 이름을 한 번만 입력 해야) 합니다.

10. 에 **사용 가능한 프로세스** 목록에서 실행 하 고 있는 프로그램 DE 인스턴스를 선택 합니다 **연결** 단추입니다.

11. 기호에 독일에서 로드 한 후 DE 코드에 중단점을 배치 합니다.

12. 중지 하 고 다음 디버깅 프로세스를 다시 시작 될 때마다 6 ~ 10 단계를 반복 합니다.

## <a name="debug-a-custom-project-type"></a>사용자 지정 프로젝트 형식의 디버깅

1. 시작 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 일반 레지스트리 하이브 및 부하 프로젝트가 프로젝트 (이 원본인, 프로젝트 형식에서 프로젝트 형식의 인스턴스화 없습니다)를 입력 합니다.

2. 프로젝트 속성을 열고 다음으로 이동 합니다 **디버그** 페이지입니다. 에 대 한는 **명령**, 경로를 입력 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (이것이 기본적으로 *[드라이브]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. 에 대 한 합니다 **명령 인수**, 형식 `/rootsuffix exp` 실험 레지스트리 하이브에서 (VSIP를 설치할 때 만든)에 대 한 합니다.

4. **확인** 을 클릭하여 변경 내용을 수락합니다.

5. 프로젝트 형식 키를 눌러 시작 **F5**합니다. 그러면 두 번째 인스턴스가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

6. 이 시점에서 프로젝트 형식 소스 코드에서 중단점을 배치할 수 있습니다.

7. 두 번째 인스턴스의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 로드 또는 프로젝트 형식의 새 인스턴스를 만듭니다. 로드 또는 생성 하는 동안 중단점에 도달할 수 있습니다.

8. 프로젝트 형식을 디버그 합니다.

9. DE 시작 프로세스를 디버깅 하려는 경우를 시작한 후에 독일에 연결 하는 "사용자 지정 디버그 엔진 디버그" 절차의 단계를 수행할 수 있습니다. 이렇게 하면 세 개의 인스턴스가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 실행: 인스턴스화된 프로젝트 형식 및 사용자 장치에 연결 된 세 번째에 대 한 두 번째 프로젝트 형식이 소스에 하나입니다.

## <a name="see-also"></a>참고자료
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)