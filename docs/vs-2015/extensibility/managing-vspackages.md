---
title: Vspackage 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194383"
---
# <a name="managing-vspackages"></a>VSPackage 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

대부분의 프로젝트 및 항목 템플릿을 등록 하 고 패키지를 자동으로 로드 되므로 Vspackage, 관리에 대해 걱정할 필요가 없습니다. 그러나 일부 경우에 패키지를 관리 하기 위해 좀 더 자세한 내용을 알아보려면 해야 할 수 있습니다.  
  
## <a name="using-the-experimental-instance"></a>실험적 인스턴스를 사용 하 여  
 실험적 인스턴스에 대 한 자세한 내용을 참조 하세요 [의 실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다.  
  
## <a name="registering-and-unregistering-vspackages"></a>VSPackage 등록 및 등록 취소  
 등록 및 Vspackage 및 다른 유형의 확장을 등록 취소 하는 방법을 알아보려면 참조 [등록 및 등록 취소 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)합니다.  
  
## <a name="loading-a-vspackage"></a>VSPackage를 로드합니다.  
 Vspackage는 CMDUICONTEXT GUID 켜져 특정 autoload를 설정할 수 있습니다. 자세한 내용은 [Vspackage 로드](../extensibility/loading-vspackages.md)합니다.  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>AsyncPackage를 사용 하 여 백그라운드에서 Vspackage를 로드 합니다.  
 AsyncPackage 클래스에는 Visual Studio에서 UI 응답성 향상에 대 한 백그라운드 스레드에서 로드 패키지 수 있습니다. 자세한 내용은 [방법: AsyncPackage를 사용 하 여 백그라운드에서 Vspackage를 로드](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)합니다.  
  
## <a name="rule-based-ui-context-for-extensions"></a>확장에 대 한 규칙 기반 UI 컨텍스트  
 규칙 기반 UI 컨텍스트 확장 작성자를는 UI 컨텍스트의 활성화 되 고 연결된 Vspackage 로드 정확한 조건을 정의할 수 있습니다. 자세한 내용은 [방법: 규칙 기반 UI 컨텍스트를 사용 하 여 Visual Studio 확장에 대 한](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)합니다.  
  
## <a name="troubleshooting-vspackages"></a>VSPackage 문제 해결  
 Vspackage 로드 안 함 또는 오류가 발생 하는 문제 해결을 위한 기술을 확인 합니다. [VSPackage 문제 해결](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>관련 항목  
 [VSPackage](../extensibility/internals/vspackages.md)
