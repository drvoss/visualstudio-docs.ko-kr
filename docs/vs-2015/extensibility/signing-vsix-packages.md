---
title: VSIX 패키지 서명 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fabe2931310b97f0c0864ea77ceef024f0e57cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447212"
---
# <a name="signing-vsix-packages"></a>VSIX 패키지 서명
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

확장 어셈블리는 Visual Studio에서 실행할 수는 있지만 이렇게 하는 것이 좋습니다 전에 서명할 필요가 없습니다.  
  
 확장 프로그램을 보호 하 고 사용 하 여 손상 되지 않았는지 확인 하려는 경우에 VSIX 패키지에 디지털 서명을 추가할 수 있습니다. VSIX에 서명 하는 경우 VSIX 설치 관리자는 서명 및 서명 자체에 대 한 자세한 정보를 나타내는 메시지가 표시 됩니다. VSIX의 내용을 수정 된 VSIX 다시 서명 되지 않은 경우 VSIX 설치 관리자 서명이 유효한 지 표시 됩니다. 설치 중지 되지 않으면 있지만 사용자에 게 경고가 표시 됩니다.  
  
> [!IMPORTANT]
> 2015 년부터 SHA256 암호화 이외의 사용 하 여 서명 하는 VSIX 패키지에 잘못 된 서명이 있는 것으로 식별 됩니다. VSIX 설치 되지는지 않습니다 하지만 사용자 경고가 표시 됩니다.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>VSIXSignTool 사용 하 여 VSIX를 서명합니다.  
 서명에서 사용할 수 있는 도구를 SHA256 암호화 방법이 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) 에서 nuget.org [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)합니다.  
  
#### <a name="to-use-the-vsixsigntool"></a>VSIXSignTool를 사용 하려면  
  
1. VSIX 프로젝트에 추가 합니다.  
  
2. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 선택 **추가 &#124; NuGet 패키지 관리**합니다.  NuGet 및 NuGet 추가 대 한 자세한 내용은 패키지 참조 [NuGet 개요](http://docs.nuget.org/) 하 고 [대화 상자를 사용 NuGet 패키지 관리](http://docs.nuget.org/Consume/Package-Manager-Dialog)합니다.  
  
3. VSIXSignTool VisualStudioExtensibility에서 검색 하 고 NuGet 패키지를 설치 합니다.  
  
4. 이제 프로젝트의 로컬 패키지 위치에서의 VSIXSignTool를 실행할 수 있습니다. 서명 시나리오에 대 한 도구의 명령줄 도움말을 참조 하십시오. (VSIXSignTool.exe /?).  
  
   예를 들어 암호로 보호 된 인증서 파일을 사용 하 여 로그인 합니다.  
  
   VSIXSignTool.exe sign /f \<certfile> /p \<password> \<VSIXfile>  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
