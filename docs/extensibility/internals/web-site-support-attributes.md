---
title: 웹 사이트 지원 특성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07486ea3a962bcb81f65ad0b61ea2e41b3248678
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721606"
---
# <a name="web-site-support-attributes"></a>웹 사이트 지원 특성
웹 프로그래밍 언어에 대 한 지원을 제공 하도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 웹 사이트 프로젝트를 확장할 수 있습니다. 언어가 선택 된 경우 **새 웹 사이트** 대화 상자에 프로젝트 템플릿이 표시 될 수 있도록 언어는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 등록 해야 합니다.

IronPython Studio 샘플에는 웹 사이트 지원이 포함 되어 있습니다. 이 샘플에는 새 웹 프로젝트에 대 한 코드 숨김 언어로 IronPython을 등록 하는 다음 특성 클래스가 포함 되어 있습니다.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 이 특성은 언어 프로젝트에 배치 됩니다. **새 웹 사이트** 대화 상자의 **언어** 목록에서 웹 프로그래밍 언어 목록에 언어를 추가 합니다. 예를 들어 다음 코드는 IronPython을 목록에 추가 합니다.

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 또한이 특성은 템플릿 폴더를 가리키도록 템플릿 경로를 설정 합니다. 템플릿 폴더의 위치에 대 한 자세한 내용은 [웹 사이트 지원 템플릿](../../extensibility/internals/web-site-support-templates.md)을 참조 하세요.

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 이 특성은 언어 프로젝트에 배치 됩니다. 이를 통해 웹 사이트 프로젝트는 **솔루션 탐색기**의 다른 파일 형식 (기본) 아래에 하나의 파일 형식 (관련)을 중첩할 수 있습니다.

 예를 들어 다음 코드는 IronPython codebehind 파일이 .aspx 파일에 연결 되도록 지정 합니다. 새 .aspx 웹 사이트를 IronPython 웹 사이트 솔루션에 만들면 새 py 원본 파일이 생성 되 고 .aspx 페이지의 자식 노드로 표시 됩니다.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 이 특성은 언어 프로젝트 패키지에 배치 됩니다. 언어에 대 한 IntelliSense 공급자를 선택 합니다.

 예를 들어 다음 코드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>를 구현 하는 PythonIntellisenseProvider 인스턴스를 요청 시 생성 하 여 언어 서비스를 제공 하도록 지정 합니다.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject 구현은 참조를 처리 하 고 코드를 포함 하는 웹 페이지가 요청 되었지만 캐시 되지 않을 때 언어 컴파일러를 호출 합니다.

## <a name="see-also"></a>참조
- [웹 사이트 지원](../../extensibility/internals/web-site-support.md)