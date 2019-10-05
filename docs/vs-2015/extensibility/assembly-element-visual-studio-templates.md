---
title: Assembly 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 10c894f3507ae760624b6ae18f785aae6016cd5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184698"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

서식 파일 프로젝트에 해당 어셈블리 참조를 추가 하는 어셈블리에 대 한 정보를 지정 합니다.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<참조 >  
 \<참조 >  
 \<어셈블리 >  
  
## <a name="syntax"></a>구문  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[참조](../extensibility/reference-element-visual-studio-templates.md)|항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
 이 텍스트는 항목 템플릿이 인스턴스화될 때 프로젝트에 추가할 어셈블리를 지정 합니다. 다음 방법 중 하나에서이 어셈블리 이름을 지정 해야 합니다.  
  
- 전체 어셈블리 이름입니다. 예를 들어:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
- 단순한 텍스트 참조 합니다. 예를 들어:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>설명  
 `Assembly`은 `Reference`의 필수 자식 요소입니다.  
  
 `Reference`, `References,` 하 고 `Assembly` 요소.vstemplate 파일에서 사용할 수 있습니다를 `Type` 특성 값 `Item`.  
  
## <a name="example"></a>예제  
 다음 예제는 `TemplateContent` 항목 템플릿의 요소입니다. 이 XML에는 System.dll 및 System.Data.dll 어셈블리에 대 한 참조를 추가합니다.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
