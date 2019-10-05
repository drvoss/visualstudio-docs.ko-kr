---
title: CreatePkgDef 유틸리티 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab5866949d6ccfa9f3b1037abf7801ce40ace3d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332279"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 유틸리티
만들고 매개 변수로 Visual Studio 확장명.dll 파일을 *.pkgdef* 함께 파일을 *.dll* 파일입니다. 합니다 *.pkgdef* 파일 그렇지 않으면 작성 될 수 있는 시스템 레지스트리에 확장을 설치할 때 모든 정보를 포함 합니다.

> [!NOTE]
> 대부분 자동으로 Visual Studio SDK에 포함 된 프로젝트 템플릿 만들기 *.pkgdef* 빌드 프로세스의 일부로 파일입니다. 이 문서는 패키지를 수동으로 만들거나 사용 하도록 기존 패키지를 변환 하려는 사람 *.pkgdef* 배포 합니다.

## <a name="syntax"></a>구문

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>인수
**/out=&lt;FileName&gt;** \
필수 요소. 이름을 가져오거나 설정 합니다 *.pkgdef* 출력 파일을 &lt;FileName&gt;합니다.

**/codebase**\
선택 사항입니다. 등록을 강제로 수행 합니다 **코드 베이스** 유틸리티입니다.

**/assembly**\
등록을 강제로 수행 합니다 **어셈블리** 유틸리티입니다.

**&lt;AssemblyPath&gt;** \
경로 *.dll* 생성 하려는 파일을 *.pkgdef*합니다.

## <a name="remarks"></a>설명
사용 하 여 확장 배포 *.pkgdef* 파일의 이전 버전의 Visual Studio 레지스트리 요구 사항을 대체 합니다.

::: moniker range=">=vs-2019"

합니다 *.pkgdef* 파일이 다음 위치 중 하나에 설치 되어야 합니다.

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

설치 폴더는 경우 *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\* , 확장은 Visual Studio에서 인식할 수 있지만 기본적으로 비활성화 됩니다. 사용자를 사용 하 여 확장을 설정할 수 있습니다 **확장 관리**합니다.

설치 폴더는 경우 *%vsinstalldir%\Common7\IDE\Extensions\\* , 확장은 기본적으로 사용 됩니다.

> [!NOTE]
> 합니다 **확장 관리** VSIX 패키지의 일부로 설치 되어 있지 않으면 확장에 액세스 하는 도구를 사용할 수 없습니다.

::: moniker-end

::: moniker range="vs-2017"

합니다 *.pkgdef* 파일이 다음 위치 중 하나에 설치 되어야 합니다.

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

설치 폴더는 경우 *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\* , 확장은 Visual Studio에서 인식할 수 있지만 기본적으로 비활성화 됩니다. 사용자를 사용 하 여 확장을 설정할 수 있습니다 **확장 및 업데이트**합니다.

설치 폴더는 경우 *%vsinstalldir%\Common7\IDE\Extensions\\* , 확장은 기본적으로 사용 됩니다.

> [!NOTE]
> 합니다 **확장 및 업데이트** VSIX 패키지의 일부로 설치 되어 있지 않으면 확장에 액세스 하는 도구를 사용할 수 없습니다.

::: moniker-end

## <a name="see-also"></a>참고자료
- [CreateExpInstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)
