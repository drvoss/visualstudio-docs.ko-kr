---
title: 원본 제어 플러그 인에 대 한 호환성 경고 해제 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dc8edcb6ee10be8b020424d8f8c247770a98f27
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324803"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>방법: 원본 제어 플러그 인에 대 한 호환성 경고 해제
사용자의 소스 제어를 적용 하는 경우 몇 가지 호환성 경고가 표시 될 수 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]입니다. 경고 표시를 소스 제어 플러그 인의 기능에 따라 달라 집니다 있으며 자세한 다음과 같이 해제할 수 있습니다.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>경고를 사용 하지 않도록 설정 합니다. "Visual Studio를 사용 하 여 최적의 소스 제어 통합 되도록"

- 다음 레지스트리 항목 (필요한 경우 값 추가)를 설정 합니다.

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   모든에 대해이 경고를 표시 하는 비-[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 플러그 인입니다.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>경고를 사용 하지 않도록 설정 합니다. "설치 된 원본 제어 공급자는 모든 기능을 지원 하지 않습니다"

- (필요한 경우 값 추가)는 다음 두 레지스트리 값을 설정 합니다.

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     이 경고는 소스 제어 플러그 인을 지원 하지 않는 경우 명시적으로 재진입 여러 프로젝트에 대 한 (즉, 하는 경우 한 번에 하나의 파일 및 프로젝트에서 확인할 수)에 표시 됩니다.

     재진입을 지원 하는 것이 좋습니다 (`SCC_CAP_REENTRANT` 기능);이 경고가 제거 됩니다. 그러나 이러한 지원이 가능 하지 않은 이러한 레지스트리 항목을 설정할 수 있습니다.

## <a name="see-also"></a>참고자료
- [기능 플래그](../extensibility/capability-flags.md)