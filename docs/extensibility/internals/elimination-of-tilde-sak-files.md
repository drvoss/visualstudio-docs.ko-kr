---
title: 제거 ~ SAK 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e409a08ba295bb55eb1fcfcd2a048a9bdb5ea7c9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327530"
---
# <a name="elimination-of-sak-files"></a>제거 ~ SAK 파일
원본 제어 플러그 인 API 1.2에서는 *~ SAK* 기능 플래그를 통해 파일 대체 되었으며 원본 여부를 검색 하는 새 함수 제어 플러그 인 지원 합니다 *MSSCCPRJ* 파일 및 공유 체크 아웃 합니다.

## <a name="sak-files"></a>~ SAK 파일
Visual Studio.NET 2003 접두사로 추가 하는 임시 파일을 만들었습니다 *~ SAK*합니다. 이러한 파일을 사용 하 여 소스 제어 플러그 인을 지원 하는지 확인할 수 있습니다:

- 합니다 *MSSCCPRJ.SCC* 파일입니다.

- 여러 (공유) 체크 아웃 합니다.

플러그 인에 대해 원본 제어 플러그 인 API 1.2에서 제공 하는 고급 함수를 지 원하는, IDE는 새로운 기능, 플래그 및 다음 섹션에 자세히 설명 하는 함수를 사용 하 여 임시 파일을 만들지 않고 이러한 기능을 검색할 수 있습니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>새 함수
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 선언 경우 소스 제어 플러그 인 (공유) 여러 체크 아웃을 지원 합니다 `SCC_CAP_MULTICHECKOUT` 기능과 구현을 `SccIsMultiCheckOutEnabled` 함수입니다. 소스 제어 프로젝트에서 체크 아웃 작업을 수행할 때마다이 함수가 호출 됩니다.

 소스 제어 플러그 인 만들기 및 사용을 지 원하는 경우는 *MSSCCPRJ.SCC* 선언 파일을 `SCC_CAP_SCCFILE` 기능과 구현을 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)합니다. 이 함수는 파일의 목록을 사용 하 여 호출 됩니다. 함수 반환 `TRUE' or 'FALSE` Visual Studio를 사용할지 여부를 나타내는 각 파일에 대 한는 *MSSCCPRJ.SCC* 파일에 대 한 합니다. 소스 제어 플러그 인이 새 기능 및 기능을 지원 하지 않도록 선택 하면 다음 레지스트리 키를 사용 하 여 이러한 파일의 생성을 사용 하지 않도록 설정 수 것:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> 이 레지스트리 키로 설정 되어 있으면 *dword:00000000은*되 존재 하지 않는, 키 및 Visual Studio는 여전히 임시 파일을 만들려고 시도 합니다. 그러나 레지스트리 키로 설정 되어 있으면 *dword:00000001*, 임시 파일을 만들려면 Visual Studio를 시도 하지 않습니다. 소스 제어 플러그 인을 지원 하지 않음을 가정 대신 합니다 *MSSCCPRJ.SCC* 파일과 공유 체크 아웃을 지원 하지 않습니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)