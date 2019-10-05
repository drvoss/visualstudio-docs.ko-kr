---
title: '오류: 웹 서버에서 요청된 된 리소스를 찾을 수 없습니다 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0b37e96db46a43b869867b8b5e37f857e75aff9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850273"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>오류: 웹 서버에서 요청한 리소스를 찾을 수 없습니다
보안 고려 사항 때문에 IIS에서 일반 오류를 반환했습니다.

한 가지 가능한 원인은 서버의 보안 구성입니다. IIS 6.0 및 이전 버전에서는 URLScan이라는 추가 기능 프로그램을 사용하여 형식이 잘못된 의심스러운 요청을 필터링합니다. IIS 7.0에서는 동일한 목적을 위해 요청 필터링이 기본적으로 제공됩니다. 두 경우 모두 요청 필터링이 지나치게 제한적이면 Visual Studio에서 서버를 디버깅하지 못할 수 있습니다.

다른 가능한이 오류의 원인은 W3SVC 서비스를 IIS에 대 한 시작 되지 않은 것입니다. 서비스 창에서이 서비스 (회색) 시작 되었는지 확인 (*services.msc*).

다양 한 추가이 오류 원인이 있습니다. 가장 일반적인 원인 중 몇 가지는 IIS 설치 또는 구성 문제, 웹 사이트 구성 문제 또는 파일 시스템의 사용 권한 문제입니다. 브라우저를 사용하여 리소스에 액세스할 수 있습니다. IIS가 구성된 방식에 따라 자세한 오류 메시지를 얻으려면 서버에서 로컬 브라우저를 사용하거나 IIS 오류 로그를 검사해야 할 수 있습니다.

 IIS 문제 해결에 대한 자세한 내용은 [IIS 관리](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)를 참조하세요.

## <a name="see-also"></a>참고 항목
- [오류: 웹 서버가 잠겨 있기 때문에 디버깅을 사용하기 위해 필요한 DEBUG 동사를 사용할 수 없습니다.](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)