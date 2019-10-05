---
title: '&lt;compatibleFrameworks&gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99db3d51414197df469aaa2eabe97e0967c31b05
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746035"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; 요소 (ClickOnce 배포)
이 애플리케이션이 설치 및 실행할 수 있는 .NET Framework의 버전을 식별합니다.

> [!NOTE]
> [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) 지원 하지 않습니다는 `compatibleFrameworks` 요소는 응용 프로그램 매니페스트를 저장할 때 사용 하 여 인증서로 서명 된 이미 [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)합니다. 대신, [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)를 사용해야 합니다.

## <a name="syntax"></a>구문

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `compatibleFrameworks` 배포 매니페스트는 대상에 대 한 요소는 필수는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 런타임 또는 나중에.NET Framework 4에서 제공 합니다. 합니다 `compatibleFrameworks` 요소 하나 이상 포함 `framework` 이 응용 프로그램 실행 될 수 있는.NET Framework 버전을 지정 하는 요소입니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 런타임 첫 번째 응용 프로그램을 실행 합니다 사용 가능한 `framework` 이 목록에 있습니다.

 다음 표에서 특성은는 `compatibleFrameworks` 요소를 지원 합니다.

|특성|설명|
|---------------|-----------------|
|`S` `upportUrl`|선택 사항입니다. 호환 되는 기본.NET Framework 버전을 다운로드할 수 있는 URL을 지정 합니다.|

## <a name="framework"></a>프레임워크
 필수 요소. 다음 표에서 특성을 나열 하는 `framework` 요소를 지원 합니다.

|특성|설명|
|---------------|-----------------|
|`targetVersion`|필수 요소. 대상.NET Framework의 버전 번호를 지정합니다.|
|`profile`|필수 요소. 대상.NET Framework의 프로필을 지정합니다.|
|`supportedRuntime`|필수 요소. 대상.NET Framework와 관련 된 런타임 버전 번호를 지정 합니다.|

## <a name="remarks"></a>설명

## <a name="example"></a>예제
 다음 코드 예제는 `compatibleFrameworks` 요소에는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포 매니페스트 합니다. 이 배포에서 실행할 수는 [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]합니다. 상위 집합 이므로.NET Framework 4에서 실행할 수도 있습니다는 [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]합니다.

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>참고자료
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)