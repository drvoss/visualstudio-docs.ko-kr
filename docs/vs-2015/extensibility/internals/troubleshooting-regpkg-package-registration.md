---
title: RegPkg 패키지 등록 문제 해결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441179"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg 패키지 등록 문제 해결
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Visual Studio에서 패키지를 등록 하려면.pkgdef 파일을 사용 하 여는 것이 좋습니다. 따라서 시스템 레지스트리에 액세스 하지 않고도 확장 배포 합니다. Pkgdef 파일을 사용 하 여 만들어진 합니다 [CreatePkgDef 유틸리티](../../extensibility/internals/createpkgdef-utility.md)합니다.  
  
 RegPkg에서 사용 하 여 패키지를 등록할 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], RegPkg 패키지에 적절 한 버전을 사용 해야 합니다.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>패키지 버전와 관련 된 RegPkg 버전  
 RegPkg의 두 가지 버전이 있습니다. 에 포함 된 하나의 버전 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 다음 어셈블리 중 하나를 사용 하 여 만든 패키지를 등록 하려면이 버전을 사용 합니다.  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   이 이전 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 만든 패키지를 등록할 수 없습니다.  
  
   이전 버전의 RegPkg Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 만든 패키지를 등록할 수 있습니다. 그러나 해당 어셈블리의 이후 버전을 사용 하 여 빌드된 패키지를 등록할 수 없습니다 것입니다.  
  
## <a name="see-also"></a>참고 항목  
 [제품 릴리스](../../misc/releasing-a-visual-studio-integration-product.md)
