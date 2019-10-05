---
title: 기본 명령, 그룹 및 도구 모음 배치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7fc877332f7db7b27c4a30c23f1ac395a4fc22e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196888"
---
# <a name="default-command-group-and-toolbar-placement"></a>기본 명령, 그룹 및 도구 모음 배치
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

제품 일관성 및 안정성에 대 한 UI를 기본적으로 특정 명령 그룹을 표시 하 고 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 명령 및 명령 그룹에 대 한 정의 제공 합니다. 표준 명령 및 명령 그룹 Vspackage를 이용할 수 있습니다.  
  
 기본 명령 그룹은 다음과 같은 세 가지 범주로 분류 됩니다. IDE 명령, 제품 명령 및 편집기 명령입니다.  
  
## <a name="default-ide-commands"></a>기본 IDE 명령  
 기본 IDE 도구 모음에 명령에 포함 된 모든 제품에서 공유 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 다음과 같은 일반 프로젝트 작업에 관련 된 명령은 합니다 **저장** 명령 및 **항목 추가** 명령입니다. Vspackage를 추가 하지 않거나 한 가지 예외로이 도구 모음에서 뺄 해야 합니다. 제품 또는 VSPackage는 새 도구 창을 추가 하는 경우에 사용할 수 있는 도구 창의 목록에 추가할 해야 창 합니다 **보기** 메뉴. 새 제품 또는 Vspackage는 자체 도구 모음을 추가할 수 있습니다.  
  
## <a name="default-product-commands"></a>기본 제품 명령  
 각 제품 중요 한 포함 된 자주 사용 하는 명령 자체 기본 도구 모음을 사용 하 여 IDE를 제공할 수 있습니다. 그러나 기존 메뉴 및 가능한 경우 도구 모음을 사용 하 고 필요에 따라 다른 태스크 별 도구 모음을 사용 하 여 보완 하는 것이 좋습니다 합니다.  
  
 도구 모음에 대 한 우선 순위 필드의 행 위치를 결정합니다. 메뉴 모음 아래에 세 번째 행 (행 3)의 도구 모음을 배치 하는 0 우선 순위 (1 행) 및 **표준** 도구 모음 (2 행). 따라서 다른 도구 모음으로 행에 표시 (우선 순위 + 3). 다음 도구 모음; 공간이 있는 경우 같은 행에 배치 됩니다. 그렇지 않은 경우 자동으로 이동 하는 다음 행.  
  
## <a name="default-editor-commands"></a>기본 편집기 명령  
 사용자 지정 편집기를 제공 하는 VSPackage는 가장 중요 한 포함 하는 편집기에서 자주 사용 되는 명령을 기본 도구 모음을 제공 해야 합니다. 편집기 도구 모음 편집기가 활성 상태일 편집기를 사용 하지 않으면 숨겨야 할 때 표시 됩니다. 이러한 가시성 제어 되는 `VisibilityConstraints Element` .vsct 파일의 합니다.  
  
 제품 및 IDE 도구 모음 아래 편집기 도구 모음을 배치 되어야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
