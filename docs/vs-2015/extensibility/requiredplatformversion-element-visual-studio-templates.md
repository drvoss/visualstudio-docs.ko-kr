---
title: RequiredPlatformVersion 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159280"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 템플릿이 제대로 작동 하는 데 필요한 운영 체제의 최소 버전을 지정 합니다. 이 요소는 프로젝트 템플릿을 만드는 데 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱.  
  
 `RequiredPlatformVersion` 운영 체제의 버전을 사용 하 여 직접 값과 비교 됩니다. 경우는 `RequiredPlatformVersion` 운영 체제 버전 보다 높은 템플릿이 표시 되지 않습니다 합니다 **새 프로젝트** 대화 상자. 에 대 한 템플릿을 지정 하려면 [!INCLUDE[win8](../includes/win8-md.md)] 더 높고, 설정 또는 `RequiredPlatformVersion` 6.2.0 하 합니다. 에 대 한 템플릿을 지정 하려면 [!INCLUDE[win81](../includes/win81-md.md)] 또는 더 높고, 설정 RequiredPlatformVersion를 6.3.0으로 합니다.  
  
 지정 하는 템플릿 `RequiredPlatformVersion`= 8 이전 고객와 호환 되는 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 템플릿.  
  
 VSTemplate  
TemplateData  
... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>구문  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 없음  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|프로젝트 템플릿의 대상 플랫폼을 지정합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
## <a name="remarks"></a>설명  
 이 텍스트 템플릿에 필요한 최소 운영 체제 버전을 지정 합니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 프로젝트 템플릿이 [!INCLUDE[win8](../includes/win8-md.md)] 이상을 대상으로 하도록 지정합니다.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>관련 항목  
 [TargetPlatformName 요소 (Visual Studio 템플릿)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
