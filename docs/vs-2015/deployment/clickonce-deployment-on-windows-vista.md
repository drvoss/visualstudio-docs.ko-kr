---
title: Windows Vista의 ClickOnce 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675469"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista의 ClickOnce 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 응용 프로그램 구축 Windows Vista에서 사용자 계정 컨트롤 (UAC)에 일반적으로 포함된 된 매니페스트 생성에 대 한 응용 프로그램의 실행 파일의 XML 데이터를 이진으로 인코딩됩니다. 등록이 필요 없는 COM 및 ClickOnce 응용 프로그램 외부 매니페스트가 필요 하기 때문에 Visual Studio는 이러한 프로젝트 형식에 대 한 포함 된 매니페스트 대신 UAC 데이터가 포함 된 파일을 생성 합니다. 기본적으로 Visual Studio (등록 필요 없는 COM 및 ClickOnce 배포)에 대 한 외부 UAC 매니페스트 정보를 생성 하거나 응용 프로그램의 실행 파일 (다른 모든 경우)에 포함할 app.manifest 라는 파일에서 정보를 사용 합니다. Visual Studio 매니페스트 생성을 위한 다음 옵션을 제공합니다.  
  
- 포함된 된 매니페스트를 사용 합니다. 응용 프로그램의 실행 파일에 UAC 데이터를 포함 하 고 일반 사용자로 실행 합니다.  
  
   (사용 하지 않는 경우 ClickOnce) 기본 설정입니다. 이 설정은 Visual Studio는 작동 하는 일반적인 방법으로 Windows vista; 지원 즉, 둘 다 사용 하는 내부 및 외부 매니페스트 생성 `AsInvoker`합니다.  
  
- 외부 매니페스트를 사용 합니다. App.manifest를 사용 하 여 외부 매니페스트를 생성 합니다.  
  
   그러면 외부 매니페스트만 app.manifest에서 정보를 사용 하 여 생성 됩니다. ClickOnce 또는 등록이 필요 없는 COM을 사용 하 여 응용 프로그램을 게시할 때 Visual Studio는 프로젝트에 app.manifest를 추가 하 고이 옵션을 추가 합니다.  
  
- 매니페스트가 없는 사용 합니다. 매니페스트 없이 응용 프로그램을 만듭니다.  
  
   이 접근 방식은 라고도 *가상화*합니다. 이전 버전의 Visual Studio에서 기존 응용 프로그램과 호환성에 대 한이 옵션을 사용 합니다.  
  
  새 속성에서 사용할 수는 **응용 프로그램** 프로젝트 디자이너 (Visual C# 프로젝트에만 해당)의 페이지 및 MSBuild 프로젝트 파일 형식입니다.  
  
  Visual Studio IDE에서 UAC 매니페스트 생성을 구성 하기 위한 메서드 (Visual C# 및 Visual Basic) 프로젝트 형식에 따라 다른 것을 참고 합니다.  
  
  매니페스트 생성에 대 한 Visual C# 프로젝트를 구성 하는 방법에 대 한 내용은 [응용 프로그램 페이지, 프로젝트 디자이너 (C#)](../ide/reference/application-page-project-designer-csharp.md)합니다.  
  
  매니페스트 생성에 대 한 Visual Basic 프로젝트를 구성 하는 방법에 대 한 내용은 [응용 프로그램 페이지, 프로젝트 디자이너 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)   
 [사용자 권한 및 Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [프로젝트 디자이너, 응용 프로그램 페이지(C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [프로젝트 디자이너, 응용 프로그램 페이지(Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
