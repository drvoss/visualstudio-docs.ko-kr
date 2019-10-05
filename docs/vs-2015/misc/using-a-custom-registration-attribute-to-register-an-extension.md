---
title: 사용자 지정 등록 특성을 사용 하 여 확장명 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935786"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>사용자 지정 등록 특성을 사용하여 확장 등록
특정 한 경우 확장 프로그램에 대해 새 등록 특성을 만드는 해야 합니다. 새 레지스트리 키를 추가 하거나 기존 키를 새 값을 추가 하려면 등록 특성을 사용할 수 있습니다. 새 특성에서 파생 되어야 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 및 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 메서드.  
  
## <a name="creating-a-custom-attribute"></a>사용자 지정 특성 만들기  
 다음 코드에는 새 등록 특성을 만드는 방법을 보여 줍니다.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute> 특성 클래스에는 프로그램 요소 (클래스, 메서드 등)를 특성 관계가 있는,이 사용할 수 있는지 여부를 두 번 이상 상속할 수 있는지 여부를 지정 하는 데 사용 됩니다.  
  
### <a name="creating-a-registry-key"></a>레지스트리 키 만들기  
 다음 코드에서는 사용자 지정 특성 만듭니다는 **사용자 지정** 등록 되는 VSPackage에 대 한 키 아래 하위 키입니다.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>기존 레지스트리 키 아래에 새 값 만들기  
 기존 키를 사용자 지정 값을 추가할 수 있습니다. 다음 코드를 VSPackage 등록 키를 새 값을 추가 하는 방법을 보여 줍니다.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
  
```