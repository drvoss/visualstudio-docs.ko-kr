---
title: 웹 사이트 지원 특성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144303"
---
# <a name="web-site-support-attributes"></a>웹 사이트 지원 특성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 웹 사이트 프로젝트 프로그래밍 언어로 웹에 대 한 지원을 제공 하기 위해 확장할 수 있습니다. 언어를 사용 하 여 자체 등록 해야 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 템플릿에 나타날 수 있도록 합니다 **새 웹 사이트** 언어 선택 대화 상자.  
  
 IronPython Studio 샘플 웹 사이트 지원이 포함 됩니다. 사용 하 여 찾을 수 있습니다 합니다 [VSSDK 샘플](../../misc/vssdk-samples.md)합니다. 새 웹 프로젝트에 대 한 코드 숨김 언어로 IronPython을 등록 하는 다음 특성 클래스를 포함 합니다.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 이 특성은 언어 프로젝트에 배치 됩니다. 언어에서 프로그래밍 언어는 웹의 목록에 추가 합니다 **언어** 목록에 **새 웹 사이트** 대화 상자. 예를 들어, 다음 IronPython 목록에 추가 합니다.  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 이 특성에는 템플릿 경로를 템플릿 폴더를 가리키도록 설정 합니다. 템플릿 폴더의 위치에 대 한 자세한 내용은 참조 하세요. [웹 사이트 지원 템플릿](../../extensibility/internals/web-site-support-templates.md)합니다.  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 이 특성은 언어 프로젝트에 배치 됩니다. 다른 파일 형식 (기본)에서 웹 사이트 프로젝트 파일 형식 (관련)을 중첩 시킬 수 있도록 합니다 **솔루션 탐색기**합니다.  
  
 예를 들어:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 IronPython 코드 숨김 파일로.aspx 파일와 관련 되어 있는지를 지정 합니다. IronPython 웹 사이트 솔루션에 새.aspx 웹 페이지를 만들면 새.py 소스 파일을 생성 되 고.aspx 페이지의 자식 노드로 나타납니다.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 이 특성은 언어 프로젝트 패키지에 배치 됩니다. 언어에 대 한 Intellisense 공급자를 선택합니다.  
  
 예:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 지정 PythonIntellisenseProvider 구현 하는 인스턴스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, 언어 서비스를 제공 하는 요청 시 다시 만들어야 합니다.  
  
 IVsIntellisenseProject 구현 참조를 처리 하 고 코드를 사용 하 여 웹 페이지를 요청 하지만 캐시 되지 않은 경우 언어 컴파일러를 호출 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [웹 사이트 지원](../../extensibility/internals/web-site-support.md)
