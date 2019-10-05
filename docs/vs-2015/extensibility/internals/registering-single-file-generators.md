---
title: 단일 파일 생성기 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696097"
---
# <a name="registering-single-file-generators"></a>단일 파일 생성기 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자 지정 도구에서 사용할 수 있도록 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 따라서를 등록 해야 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 인스턴스화할 수 있습니다 및 특정 프로젝트 형식에 연결 합니다.  
  
### <a name="to-register-a-custom-tool"></a>사용자 지정 도구를 등록 하려면  
  
1. 사용자 지정 도구 DLL을 하거나 등록에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 로컬 레지스트리 또는 시스템 레지스트리의 HKEY_CLASSES_ROOT 아래.  
  
     예를 들어, 여기는와 함께 제공 되는 관리 되는 MSDataSetGenerator 사용자 지정 도구에 대 한 등록 정보 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. 원하는 레지스트리 키를 만듭니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 생성기에서 hive\\*GUID* 여기서 *GUID* 특정 언어의 프로젝트 시스템 또는 서비스에 의해 정의 된 GUID입니다. 키의 이름에는 사용자 지정 도구의 프로그래밍 방식으로 이름이 됩니다. 사용자 지정 도구 키에는 다음 값:  
  
    - (기본값)  
  
         선택 사항입니다. 사용자 지정 도구 설명 해 놓은 제공합니다. 이 매개 변수 선택 사항 이지만 권장 됩니다.  
  
    - CLSID  
  
         필수 요소. 구현 하는 COM 구성 요소의 클래스 라이브러리의 식별자를 지정 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>합니다.  
  
    - GeneratesDesignTimeSource  
  
         필수 요소. 이 사용자 지정 도구에서 생성 된 파일에서 형식을 사용할 수 있는 비주얼 디자이너를 수행 하는지 여부를 나타냅니다. 이 매개 변수의 값 (0) 0 비주얼 디자이너에 사용할 수 없는 형식에 대 한 또는 비주얼 디자이너를 사용할 수 있는 형식 (1) 1 있어야 합니다.  
  
    > [!NOTE]
    > 사용자 지정 도구 사용 가능 하도록 사용자 지정 도구는 원하는 각 언어에 대해 별도로 등록 해야 합니다.  
  
     예를 들어를 MSDataSetGenerator 자신을 등록 한 번 각 언어에 대 한 합니다.  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)   
 [프로젝트의 기본 Namespace를 결정합니다.](../../misc/determining-the-default-namespace-of-a-project.md)   
 [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager 개체 소개](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
