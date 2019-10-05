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
ms.openlocfilehash: 1a508acaf174e5e4e4b4b615e5f38c600f0669ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323389"
---
# <a name="web-site-support-attributes"></a>웹 사이트 지원 특성
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 웹 사이트 프로젝트 프로그래밍 언어로 웹에 대 한 지원을 제공 하기 위해 확장할 수 있습니다. 언어를 사용 하 여 자체 등록 해야 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 템플릿에 나타날 수 있도록 합니다 **새 웹 사이트** 언어 선택 대화 상자.

IronPython Studio 샘플 웹 사이트 지원이 포함 됩니다. 샘플은 새 웹 프로젝트에 대 한 코드 숨김 언어로 IronPython을 등록 하는 다음 특성 클래스를 포함 합니다.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 이 특성은 언어 프로젝트에 배치 됩니다. 언어에서 프로그래밍 언어는 웹의 목록에 추가 합니다 **언어** 목록에 **새 웹 사이트** 대화 상자. 예를 들어, 다음 코드는 목록에 IronPython을 추가 합니다.

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 이 특성에는 템플릿 경로를 템플릿 폴더를 가리키도록 설정 합니다. 템플릿 폴더의 위치에 대 한 자세한 내용은 참조 하세요. [웹 사이트 지원 템플릿](../../extensibility/internals/web-site-support-templates.md)합니다.

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 이 특성은 언어 프로젝트에 배치 됩니다. 다른 파일 형식 (기본)에서 웹 사이트 프로젝트 파일 형식 (관련)을 중첩 시킬 수 있도록 합니다 **솔루션 탐색기**합니다.

 예를 들어, 다음 코드는.aspx 파일에 IronPython 코드 숨김 파일로 관련 되어 있다고 지정 합니다. IronPython 웹 사이트 솔루션에 새.aspx 웹 페이지를 만들면 새.py 소스 파일을 생성 되 고.aspx 페이지의 자식 노드로 나타납니다.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 이 특성은 언어 프로젝트 패키지에 배치 됩니다. 언어에 대 한 IntelliSense 공급자를 선택합니다.

 예를 들어, 다음 코드를 지정 하는 PythonIntellisenseProvider 구현 하는 인스턴스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, 언어 서비스를 제공 하는 요청 시 다시 만들어야 합니다.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject 구현 참조를 처리 하 고 코드를 사용 하 여 웹 페이지를 요청 하지만 캐시 되지 않을 경우 언어 컴파일러를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [웹 사이트 지원](../../extensibility/internals/web-site-support.md)