---
title: 소스 제어 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156069"
---
# <a name="supporting-source-control"></a>소스 제어 지원
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 파일 체크 아웃, 체크 인 및 프로젝트 또는 편집기에 대 한 다른 소스 제어 작업을 지원합니다. 원본 제어 클라이언트로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 와 같은 소스 제어 패키지를 상호 작용 하도록 설계 됩니다 [!INCLUDE[vsvss](../../includes/vsvss-md.md)], 보관, 버전 관리 및 동적으로 정의 된 파일 집합에 대 한 제어 기능을 제공 하는.  
  
## <a name="in-this-section"></a>섹션 내용  
 [소스 제어 패키지 모델](../../extensibility/internals/model-for-source-control-packages.md)  
 프로젝트 형식을 구현 해야 하는 인터페이스에 설명 합니다. 소스 제어를 지원 하도록 합니다.  
  
 [디자인 결정](../../extensibility/internals/source-control-design-decisions.md)  
 해당 대답 프로젝트 형식을 구현 하는 방법을 변경 하는 질문을 제공 합니다.  
  
 [구성 세부 정보](../../extensibility/internals/source-control-configuration-details.md)  
 소스 제어를 지 원하는 프로젝트 형식 구현의 변경 하는 방법을 설명 합니다.  
  
 [프로젝트 및 편집기에 대한 추가 지침](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 프로젝트 형식 및 편집기에 대 한 모범 사례를 설명합니다.  
  
 [런타임 세부 정보](../../extensibility/internals/source-control-runtime-details.md)  
 사용자 소스 제어 시스템에 추가 하는 경우 프로젝트를 등록 하는 방법을 설명 합니다.  
  
## <a name="reference"></a>참조  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 메모리에서 변경 되거나 저장 될 파일에는 원본 제어 패키지를 환경에 나타냅니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 프로젝트 및 계층 소스 제어를 사용 하 여 자체를 등록 하 고 소스 제어 상태에 대 한 정보를 얻을 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 프로젝트 파일 및 프로젝트 항목에 대 한 소스 제어를 제공 하는 프로젝트 시스템에서 구현 됩니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 쿼리를 추가, 제거 또는 파일 또는 솔루션의 디렉터리 이름 바꾸기 사용 권한에 대 한 환경 프로젝트에서 사용 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 프로젝트 파일 또는 디렉터리에 대 한 변경 내용을 클라이언트를 알립니다.  
  
## <a name="related-sections"></a>관련 단원  
 [프로젝트 형식](../../extensibility/internals/project-types.md)  
 기본 빌딩 블록으로 프로젝트의 개요를 제공 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE)입니다. 프로젝트 빌드 및 컴파일 코드를 제어 하는 방법을 설명 하는 추가 항목 링크가 제공 됩니다.
