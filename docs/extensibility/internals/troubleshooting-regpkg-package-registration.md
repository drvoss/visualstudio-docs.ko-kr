---
title: RegPkg 패키지 등록 문제 해결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 219a21eac296daa442fc2f705eb2758790777333
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344747"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg 패키지 등록 문제 해결
> [!NOTE]
> Visual Studio에서 패키지를 등록 하려면.pkgdef 파일을 사용 하 여는 것이 좋습니다. 따라서 시스템 레지스트리에 액세스 하지 않고도 확장 배포 합니다. Pkgdef 파일을 사용 하 여 만들어진 합니다 [CreatePkgDef 유틸리티](../../extensibility/internals/createpkgdef-utility.md)합니다.

 RegPkg에서 사용 하 여 패키지를 등록할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], RegPkg 패키지에 적절 한 버전을 사용 해야 합니다.

## <a name="regpkg-versions-related-to-package-versions"></a>패키지 버전와 관련 된 RegPkg 버전
 RegPkg의 두 가지 버전이 있습니다. 에 포함 된 하나의 버전 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 다음 어셈블리 중 하나를 사용 하 여 만든 패키지를 등록 하려면이 버전을 사용 합니다.

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   이 이전 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 만든 패키지를 등록할 수 없습니다.

   이전 버전의 RegPkg Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 만든 패키지를 등록할 수 있습니다. 그러나 해당 어셈블리의 이후 버전을 사용 하 여 빌드된 패키지를 등록할 수 없습니다 것입니다.

## <a name="see-also"></a>참고 항목
- [VSPackage](../../extensibility/internals/vspackages.md)