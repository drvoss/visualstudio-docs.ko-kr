---
title: 자동화 모델을 사용 하 여 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ee836f5a4330c551181f01229e82eb14623fb8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675204"
---
# <a name="using-the-automation-model"></a>자동화 모델 사용
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

속성 및 메서드를 호출 하 여 가져올 수 있습니다 자동화에 VSPackage를 연결한 후 합니다 <xref:EnvDTE.DTEClass.GetObject%2A> 메서드는 <xref:EnvDTE._DTE> 개체를 검색 하려는 개체를 나타내는 문자열을 전달 합니다.  
  
## <a name="obtaining-project-objects"></a>프로젝트 개체 가져오기  
 Automation 소비자를 가져오는 프로젝트 자동화 개체를 보여 주는 두 가지 코드 예제는 다음과 같습니다. DTE 개체를 가져오는 방법에 대 한 자세한 내용은 [방법: DTE 및 DTE2 개체에 대 한 참조 가져오기](https://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)합니다.  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 이 시점에서 계층 모델 아래로 이동 하려면 특정 VSPackage의 일부인 표준 프로젝트 개체를 사용할 수 있습니다.  
  
 다음 코드 예제에는 사용자 지정 프로젝트 형식의 속성에는 사용자 지정 개체를 가져오는 방법을 보여 줍니다.:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 다음 코드는 모든 속성의 이름을 나열 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 환경 **일반** 옵션을 합니다 **도구** 메뉴:  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>참고 항목  
 <xref:EnvDTE.DTEClass.GetObject%2A>
