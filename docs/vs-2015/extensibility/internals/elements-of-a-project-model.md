---
title: 프로젝트 모델의 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3b07068939e34b5c9e9487761177c0e12f5654
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700133"
---
# <a name="elements-of-a-project-model"></a>프로젝트 모델의 요소
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

모든 프로젝트에서 구현 및 인터페이스 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 기본 구조를 공유 합니다: 프로젝트 형식에 대 한 프로젝트 모델. 개발 하는 VSPackage가 프로젝트 모델의 디자인 관련 결정 사항을 준수 하 고 IDE에서 제공 하는 전역 기능와 함께 작동 하는 개체를 만듭니다. 프로젝트 항목을 유지 하는 방법을 제어할 수 있지만 예를 들어 제어 하지 않으면 파일을 유지 해야 하는 알림입니다. 사용자는 열린 항목에 포커스를 배치 하 고 선택 하는 경우 **저장** 에 **파일** 메뉴에서를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 메뉴 모음 프로젝트 형식 코드 해야 IDE에서 명령 가로채기, 파일을 보존 및 파일을 더 이상 변경 알림을 IDE에 다시 보냅니다.  
  
 VSPackage는 IDE 인터페이스에 대 한 액세스를 제공 하는 서비스를 통해 IDE 상호 작용 합니다. 예를 들어 특정 서비스를 통해 모니터 및 경로 명령 및 프로젝트에서 선택한 항목에 대 한 컨텍스트 정보를 제공 합니다. 모든 전역 IDE 기능을 VSPackage에 필요한 서비스에서 제공 됩니다. 서비스에 대 한 자세한 내용은 참조 하세요. [방법: 서비스 가져오기](../../extensibility/how-to-get-a-service.md)합니다.  
  
 다른 구현 고려 사항:  
  
- 단일 프로젝트 모델 프로젝트 형식이 둘 이상 포함할 수 있습니다.  
  
- 프로젝트 형식 및 attendant 프로젝트 팩터리 등록 됩니다 하지 독립적으로 Guid를 포함 합니다.  
  
- 각 프로젝트는 템플릿 파일 또는 마법사를 통해 새 프로젝트를 만들면 새 프로젝트 파일을 초기화할 수 있어야 합니다.는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] UI입니다. 예를 들어를 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 템플릿 결국.vcproj 파일 항목을 초기화 합니다.  
  
  다음 그림에서는 주 인터페이스, 서비스 및 구성 하는 일반적인 프로젝트 구현 하는 개체를 보여 줍니다. 기본 개체를 만들고 다른 프로그래밍 상용구 HierUtil7, 응용 프로그램 도우미를 사용할 수 있습니다. HierUtil7 응용 프로그램 도우미에 대 한 자세한 내용은 참조 하세요. [빌드에 없음: 프로젝트 유형을 구현 하도록 HierUtil7 프로젝트 클래스를 사용 하 여 (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)합니다.  
  
  ![Visual Studio 프로젝트 모델 그래픽](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  프로젝트 모델  
  
  이전 다이어그램에 나열 된 서비스 인터페이스 및 다이어그램에 포함 되지 않은 다른 선택적 인터페이스에 대 한 자세한 내용은 참조 하세요. [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)합니다.  
  
  프로젝트 명령을 지원할 수 고 따라서 구현 해야 합니다는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령 컨텍스트 Guid 통해 명령 라우팅에 참여 하는 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [빌드에 없음: 프로젝트 유형을 구현 하도록 HierUtil7 프로젝트 클래스를 사용 하 여 (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)   
 [프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [방법: 서비스 가져오기](../../extensibility/how-to-get-a-service.md)   
 [프로젝트 형식 만들기](../../extensibility/internals/creating-project-types.md)
