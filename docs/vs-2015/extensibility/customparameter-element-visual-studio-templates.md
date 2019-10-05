---
title: CustomParameter 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59bfec972750a4f893d1cb8b7cf08710bcca761a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555970"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 매개 변수 이름 및 템플릿에서 프로젝트 또는 항목을 만들 때 사용할 값을 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`Name`|필수 요소. 매개 변수의 이름입니다. 매개 변수 형식은 $*이름을*$입니다.|  
|`Value`|필수 요소. 매개 변수에 대해 대체 값입니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|이 마법사에서는 매개 변수 대체를 수행 하는 경우 템플릿 마법사에 전달 되는 사용자 지정 매개 변수를 그룹화 합니다.|  
  
## <a name="remarks"></a>설명  
 템플릿을 포함 하는 경우 `CustomParameter` 요소, 모든 인스턴스를 `Name` 특성으로 대체 됩니다는 `Value` 생성된 프로젝트 또는 항목 파일에는 특성입니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 서식 파일에 여러 사용자 지정 매개 변수를 사용 하는 방법을 보여 줍니다. 프로젝트 또는 항목이 만들어질 때 다음 사용자 지정 매개 변수에서의 모든 인스턴스를 사용 하 여 템플릿에서 `$color1$` 하 고 `$color2$` 템플릿에서 파일 바뀝니다 `Red` 및 `Blue`, 각각.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>참고 항목  
 [CustomParameters 요소 (Visual Studio 템플릿)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [템플릿 매개 변수](../ide/template-parameters.md)   
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
