---
title: 프록시 권한 필요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2de40c520bca0ea04f50ec782fec2dda531172e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67822064"
---
# <a name="proxy-authorization-required"></a>프록시 권한 필요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

합니다 **프록시 권한 필요** 오류는 사용자가 프록시 서버를 통해 Visual Studio online 리소스에 연결 및 프록시 서버에서 호출을 차단 하는 경우 발생 합니다.

이 오류를 해결 하려면 다음 단계 중 하나 이상을 수행해 봅니다.

- Visual Studio를 다시 시작합니다. 프록시 인증 대화 상자가 나타납니다. 대화 상자에서 자격 증명을 입력합니다.

- 위의 단계를 수행해도 문제가 해결되지 않으면 프록시 서버에서 http://go.microsoft.com 주소가 아닌 *.visualStudio.com 주소에 대한 자격 증명을 입력하라는 메시지를 표시하기 때문일 수 있습니다. 이러한 서버에 대 한 Visual Studio에서 모든 로그인 시나리오의 차단을 해제를 허용 목록에 다음 Url을 추가 해야 합니다.

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- 제거할 수 있습니다 합니다 http://go.microsoft.com 프록시 인증 대화 상자가 모두에 대 한 표시 되도록 허용 목록에서 주소를 http://go.microsoft.com 주소 및 Visual Studio를 다시 시작할 때 서버 끝점입니다.

- 프록시를 사용 하 여 기본 자격 증명을 사용 하려는 경우 다음을 수행 합니다.

   1. **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (또는 **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**)에서 devenv.exe.config(devenv.exe 구성 파일)를 찾습니다.

   2. 구성 파일에서 `<system.net>` 블록을 찾아 다음 코드를 추가합니다.

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      네트워크에 대 한 올바른 프록시 주소 삽입 `proxyaddress="<http://<yourproxy:port#>`합니다.

- 지침을 따릅니다 [이 블로그 게시물](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) 프록시를 사용할 수 있는 코드를 추가 합니다.
