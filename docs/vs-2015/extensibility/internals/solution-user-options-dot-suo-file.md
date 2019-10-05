---
title: 솔루션 사용자 옵션 (합니다. Suo) 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a9825fabe08940e8950cf88a1dbf2bc149af0b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197331"
---
# <a name="solution-user-options-suo-file"></a>솔루션 사용자 옵션(.Suo) 파일
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

솔루션 사용자 옵션 (.suo) 파일 사용자별 솔루션 옵션을 포함합니다. 소스 코드 제어에이 파일을 체크 해야 합니다.  
  
 솔루션 사용자 옵션 (.suo) 파일에는 구조적된 저장소 또는 복합을 이진 형식으로 저장 된 파일입니다. .Suo 파일에 정보를 확인 하는 데 사용할 수 있는 키가 아닌 스트림의 이름을 사용 하 여 스트림으로 사용자 정보를 저장 합니다. 솔루션 사용자 옵션 파일 사용자 기본 설정을 저장 하는 데 사용 되 고 Visual Studio 솔루션을 저장 하는 경우 자동으로 생성 됩니다.  
  
 환경.suo 파일을 열면 모든 현재 로드 된 Vspackage를 열거 합니다. VSPackage 구현 하는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 인터페이스를 호출 하 여 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> .suo 파일에서 모든 데이터를 로드 하려면 VSPackage 요청 메서드.  
  
 것이 고 스트리밍합니다 무엇 인지 알고 있어야 해야 하는 VSPackage의.suo 파일에 작성할 수 있습니다. 이 작성 한 각 스트림에 대 한 VSPackage를 다시 호출을 통해 환경을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 스트림의 이름을 키로 식별 되는 특정 스트림을 로드 합니다. 환경 다시 호출 스트림의 이름을 전달 하는 특정 스트림을 읽는 데 VSPackage 및 `IStream` 에 대 한 포인터를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 메서드.  
  
 이 시점에서 다른 호출 `LoadUserOptions` 를 읽을 수 있는.suo 파일의 다른 섹션 인지 확인 합니다. 이 프로세스는 모든.suo 파일에 데이터 스트림의 읽이 되어 환경에서 처리 될 때까지 계속 됩니다.  
  
 솔루션을 저장 하거나 닫을, 환경 호출 하는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 에 대 한 포인터를 사용 하 여 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 메서드. `IStream` 넘어갑니다 저장할 이진 정보를 포함 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 다음.suo 파일 및 호출 정보를 기록 하는 메서드를 `SaveUserOptions` 다시 다른 스트림의 정보를.suo에 쓸 수 있는지 확인 하는 메서드 파일입니다.  
  
 이러한 두 메서드 `SaveUserOptions` 하 고 `WriteUserOptions`에 대 한 포인터를 전달.suo 파일에 저장 되는 정보의 각 스트림에 대해 재귀적으로 호출 됩니다 `IVsSolutionPersistence`합니다. .Suo 파일에 여러 개의 스트림 작성할 수 있도록 재귀적으로 호출 됩니다. 이러한 방법으로 사용자 정보 솔루션을 사용 하 여 유지 되 고에 솔루션을 열 수 있습니다 되도록 보장 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [솔루션](../../extensibility/internals/solutions-overview.md)
