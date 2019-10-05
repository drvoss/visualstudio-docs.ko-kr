---
title: 지역화를 위한 중립 리소스 언어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da39ed9373daaa1dbef21ad36931ce97ea1f1e1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558270"
---
# <a name="neutral-resources-languages-for-localization"></a>지역화를 위한 중립 리소스 언어
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.NeutralResourcesLanguageAttribute> 클래스는 주 어셈블리에 포함된 리소스의 문화권을 지정합니다. 이 특성은 성능 향상으로 사용되므로 <xref:System.Resources.ResourceManager> 개체는 주 어셈블리에 포함된 리소스를 검색하지 않습니다.  
  
 다음 코드에서는 중립 리소스 언어를 설정하는 방법을 보여 줍니다. 코드는 AssemblyInfo.vb 또는 AssemblyInfo.cs 파일이나 빌드 스크립트에 삽입할 수 있습니다.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Resources.ResourceManager>   
 [.NET Framework 기반의 국가별 애플리케이션 소개](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [지역화를 위한 리소스의 계층적 구성](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [애플리케이션 지역화](../ide/localizing-applications.md)   
 [애플리케이션 전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)
