---
title: 프로젝트 형식 디자인 결정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd26e08ab153e96fc601e89788008cb0e9ca38c8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704080"
---
# <a name="project-type-design-decisions"></a>프로젝트 형식 디자인 결정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

새 프로젝트 형식을 만들기 전에 프로젝트 형식에 대 한 몇 가지 디자인 결정 해야 합니다. 프로젝트를 포함 하는 항목, 프로젝트 파일은 유지 하는 방법 및 어떤 약정 모델 유형을 사용할지 결정 해야 합니다.  
  
## <a name="project-items"></a>프로젝트 항목  
 프로젝트 파일 또는 추상 개체를 사용 합니까? 파일을 사용 하는 경우 해당 참조 또는 디렉터리 기반 파일을 수는? 로컬 또는 원격 파일 또는 진행 하는 추상 개체?  
  
 프로젝트 항목 파일 수 또는 인터넷을 통해 데이터베이스 저장소 또는 데이터 연결의 개체와 같은 더 추상적인 개체 수입니다. 항목 파일 경우 프로젝트 참조 기반 또는 디렉터리 기반 프로젝트를 수 있습니다.  
  
 프로젝트 기반 참조의에서 항목은 둘 이상의 프로젝트에 나타날 수 있습니다. 그러나 실제 파일 항목을 나타내는 하나의 디렉터리에 있습니다. 디렉터리 기반 프로젝트에서 모든 프로젝트 항목 디렉터리 구조에 존재 합니다. 자세한 내용은 [NIB: 항목 관리 프로젝트에서](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)합니다.  
  
 로컬 항목은 응용 프로그램이 설치 되어 있는 동일한 컴퓨터에 저장 됩니다. 로컬 네트워크에서 별도 서버 또는 다른 곳에서 인터넷에서 원격 항목을 저장할 수 있습니다.  
  
## <a name="project-file-persistence"></a>프로젝트 파일 지 속성  
 데이터는 구조적된 저장소 또는 일반적인 플랫 파일 시스템에 저장? 표준 편집기 또는 프로젝트별 편집기를 사용 하 여 파일 열립니다.  
  
 해당 데이터를 유지 하려면 대부분의 응용 프로그램 파일에서 해당 데이터를 저장 하 고 해당 사용자를 검토 하거나 정보를 변경 해야 하는 경우에 다시 읽습니다.  
  
 복합 파일이 라고도 하는 구조적된 저장소, 여러 구성 요소 개체 모델 (COM) 개체를 단일 파일에 지속형된 데이터를 저장 해야 하는 경우에 일반적으로 사용 됩니다. 구조적된 저장소를 사용 하 여 여러 다른 소프트웨어 구성 요소는 단일 디스크 파일을 공유할 수 있습니다.  
  
 프로젝트의 항목에 대 한 지 속성 관련 하 여 고려할 몇 가지 옵션이 있습니다. 다음 옵션 중 하나를 수행할 수 있습니다.  
  
- 가 변경 된 경우 각 파일을 개별적으로 저장 합니다.  
  
- 단일에서 트랜잭션 수를 캡처할 **저장할** 작업 합니다.  
  
- 파일을 로컬로 저장 서버에 게시 하거나 항목이 나타내는 원격 개체의 데이터 연결 하는 경우 프로젝트 항목을 저장 하는 다른 방법 사용 합니다.  
  
  지 속성에 대 한 자세한 내용은 참조 하세요. [프로젝트 지 속성](../../extensibility/internals/project-persistence.md) 하 고 [열기 및 프로젝트 항목 저장](../../extensibility/internals/opening-and-saving-project-items.md)합니다.  
  
## <a name="project-commitment-model"></a>프로젝트 약정 모델  
 지속형된 데이터 개체를 열 수는 직접 모드 또는 트 랜 잭 트 모드에서?  
  
 데이터 개체는 직접 모드에서 열면 즉시 사용자는 수동으로 파일을 저장 하는 경우 또는 데이터에 대 한 변경 내용은 통합 됩니다.  
  
 열리면 데이터 개체는 트랜잭션된 모드를 사용 하 여 변경 내용을 메모리에 임시 위치에 저장 되 고 사용자가 파일을 저장 하도록 수동으로 선택 될 때까지 커밋되지 않습니다. 이때 모든 변경 내용을 함께 발생 해야 합니다 또는 변경 되는 내용이 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [프로젝트의 NIB: 항목 관리](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [열기 및 프로젝트 항목 저장](../../extensibility/internals/opening-and-saving-project-items.md)   
 [프로젝트 지 속성](../../extensibility/internals/project-persistence.md)   
 [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)   
 [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)   
 [프로젝트 형식 만들기](../../extensibility/internals/creating-project-types.md)
