---
title: 솔루션 사용자 옵션 () .Suo) 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723806"
---
# <a name="solution-user-options-suo-file"></a>솔루션 사용자 옵션(.Suo) 파일
솔루션 사용자 옵션 (.suo) 파일에는 사용자별 솔루션 옵션이 포함 되어 있습니다. 이 파일은 소스 코드 제어에 체크 인 되지 않아야 합니다.

 솔루션 사용자 옵션 (.suo) 파일은 이진 형식으로 저장 된 구조화 된 저장소 또는 복합 파일입니다. .Suo 파일의 정보를 식별 하는 데 사용할 키가 되는 스트림의 이름을 스트림으로 사용자 정보를 저장 합니다. 솔루션 사용자 옵션 파일은 사용자 기본 설정을 저장 하는 데 사용 되며, Visual Studio에서 솔루션을 저장할 때 자동으로 만들어집니다.

 환경에서 .suo 파일을 열면 현재 로드 된 모든 Vspackage를 열거 합니다. VSPackage가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 인터페이스를 구현 하는 경우 환경에서는 VSPackage에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> 메서드를 호출 하 여 .suo 파일에서 모든 데이터를 로드 하도록 요청 합니다.

 .Suo 파일에 작성 했을 수 있는 스트림을 파악 하는 것은 VSPackage의 책임입니다. VSPackage는 작성 된 각 스트림에 대해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 통해 환경을 다시 호출 하 여 키 (스트림의 이름)로 식별 되는 특정 스트림을 로드 합니다. 그러면 환경에서 VSPackage를 다시 호출 하 여 스트림의 이름과 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 메서드에 `IStream` 포인터를 전달 하는 특정 스트림을 읽습니다.

 이 시점에서 다른 호출을 수행 하 여 읽어야 하는 .suo 파일의 다른 섹션이 있는지 확인 `LoadUserOptions` 합니다. 이 프로세스는 .suo 파일의 모든 데이터 스트림이 환경에서 읽고 처리 될 때까지 계속 됩니다.

 솔루션을 저장 하거나 닫으면 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 메서드에 대 한 포인터를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 메서드를 호출 합니다. 저장할 이진 정보를 포함 하는 `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 메서드로 전달 되 고, 그 다음에는이 정보를 .suo 파일에 쓰고 `SaveUserOptions` 메서드를 다시 호출 하 여 .suo 파일에 쓸 다른 정보 스트림이 있는지 확인 합니다.

 @No__t_0 및 `WriteUserOptions`의 이러한 두 메서드는 `IVsSolutionPersistence`에 대 한 포인터를 전달 하 여 .suo 파일에 저장 되는 각 정보 스트림에 대해 재귀적으로 호출 됩니다. 이를 재귀적으로 호출 하 여 .suo 파일에 여러 스트림을 쓸 수 있도록 합니다. 이러한 방식으로 사용자 정보는 솔루션과 함께 유지 되며 다음에 솔루션을 열 때 해당 정보를 가지게 됩니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [솔루션](../../extensibility/internals/solutions-overview.md)