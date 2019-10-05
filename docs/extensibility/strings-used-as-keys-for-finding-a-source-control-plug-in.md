---
title: 소스 제어 플러그 인을 찾기 위한 키로 사용 되는 문자열 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31c2b30fb41976cdbbab13fa22d438c63bddbbef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331711"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>소스 제어 플러그 인을 찾기 위한 키로 사용되는 문자열
다음 문자열은 정보를 찾기 위해 소스 제어 플러그 인 레지스트리 액세스 키입니다.

 `STR_SCC_PROVIDER_REG_LOCATION`를 `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, 및 `STR_SCCPROVIDERNAME` 레지스트리 키 또는 값을 원본 제어 플러그 인으로 Visual Studio에 대 한 DLL을 등록 하는 데 사용 됩니다.

 `SCC_PROJECTNAME_KEY`를 `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, 및 `SCC_STATUS_FILE` 는 MSSCCPRJ의 형식을 설명 하는 데 사용 됩니다. SCC 파일입니다.

## <a name="string-keys-and-values"></a>문자열 키 및 값

|Key|값|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|소스 코드 제어|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|소스 코드 제어 파일|
|`SCC_NSE`|Namespace 확장|
|`SCC_NSE_PREFIX`|프로토콜 접두사|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [방법: 소스 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC 파일](../extensibility/mssccprj-scc-file.md)