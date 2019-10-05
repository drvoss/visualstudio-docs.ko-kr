---
title: 등록 하 고 Vspackage 등록 취소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193825"
---
# <a name="registering-and-unregistering-vspackages"></a>VSPackage 등록 및 등록 취소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

특성을 사용 하 여 VSPackage를 등록 하지만  
  
## <a name="registering-a-vspackage"></a>VSPackage 등록  
 관리 되는 Vspackage의 등록을 제어 하려면 특성을 사용할 수 있습니다. 모든 등록 정보는.pkgdef 파일에 포함 됩니다. 파일 기반 등록에 대 한 자세한 내용은 참조 하세요. [CreatePkgDef 유틸리티](../extensibility/internals/createpkgdef-utility.md)합니다.  
  
 다음 코드에는 표준 등록 특성을 사용 하 여 VSPackage를 등록 하는 방법을 보여 줍니다.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>확장 등록 취소  
 실행 하기만 하면 많은 다른 Vspackage 사용 하 여 실험 되어 있는 경우 실험적 인스턴스에서 제거할 합니다 **재설정** 명령입니다. 검색할 **Visual Studio 실험적 인스턴스 다시 설정** 컴퓨터의 시작 페이지에서 또는 명령줄에서이 명령을 실행 합니다.  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 사용자가 설치한 Visual Studio의 개발 인스턴스에서 확장을 제거 하려는 경우 이동할 **도구 / 확장 및 업데이트**확장을 찾아 클릭 **제거**합니다.  
  
 어떤 이유로 이러한 메서드의 모두 확장을 제거에 성공 하면 명령줄에서 VSPackage 어셈블리를 다음과 같이 등록 취소할 수 있습니다.  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPackage](../extensibility/internals/vspackages.md)
