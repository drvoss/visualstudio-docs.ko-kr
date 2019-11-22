---
title: 프록시 권한 필요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297822"
---
# <a name="proxy-authorization-required"></a>프록시 권한 필요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

The **Proxy authorization required** error generally occurs when users are connected to Visual Studio online resources through a proxy server, and the proxy server blocks the calls.

To correct this error, try one or more of the following steps:

- Visual Studio를 다시 시작합니다. 프록시 인증 대화 상자가 나타납니다. 대화 상자에서 자격 증명을 입력합니다.

- 위의 단계를 수행해도 문제가 해결되지 않으면 프록시 서버에서 https://go.microsoft.com 주소가 아닌 *.visualStudio.com 주소에 대한 자격 증명을 입력하라는 메시지를 표시하기 때문일 수 있습니다. For these servers, you need to add the following URLs to the allow list to unblock all sign-in scenarios in Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- You can remove the https://go.microsoft.com address from the allow list so that the proxy authentication dialog shows up for both the https://go.microsoft.com address and the server endpoints when Visual Studio is restarted.

- If you want to use your default credentials with your proxy, do the following:

   1. **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (또는 **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**)에서 devenv.exe.config(devenv.exe 구성 파일)를 찾습니다.

   2. 구성 파일에서 `<system.net>` 블록을 찾아 다음 코드를 추가합니다.

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Insert the correct proxy address for your network in `proxyaddress="<http://<yourproxy:port#>`.

- Follow the instructions in [this blog post](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) to add code that allows you to use the proxy.
