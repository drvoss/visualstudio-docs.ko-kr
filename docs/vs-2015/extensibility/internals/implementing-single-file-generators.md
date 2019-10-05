---
title: 단일 파일 생성기 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192696"
---
# <a name="implementing-single-file-generators"></a>단일 파일 생성기 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자 지정 도구-단일 파일 생성기 라고도-확장을 사용할 수는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 하 고 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 프로젝트 시스템에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 사용자 지정 도구는를 구현 하는 COM 구성 요소는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 인터페이스입니다. 이 인터페이스를 사용 하 여 사용자 지정 도구 단일 출력 파일에 단일 입력된 파일을 변환 합니다. 변환의 결과 소스 코드를 수 있습니다 또는 다른 출력 유용 합니다. 사용자 지정 도구에서 생성 된 코드 파일의 두 가지 예는 비주얼 디자이너 및 웹 서비스 설명 언어 (WSDL)를 사용 하 여 생성 된 파일의 변경 내용에 대 한 응답으로 생성 된 코드입니다.  
  
 프로젝트 시스템 호출을 사용자 지정 도구가 로드 되 면 때나 입력된 파일을 저장 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 메서드를에 대 한 참조를 전달 하 고를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 콜백 인터페이스를 도구 사용자에 게 해당 진행 상태를 보고할 수 가능해 집니다.  
  
 사용자 지정 도구를 생성 하는 출력 파일은 입력된 파일에 대 한 종속성을 사용 하 여 프로젝트에 추가 됩니다. 프로젝트 시스템은 자동으로 사용자 지정 도구의 구현에 의해 반환 된 문자열을 기반으로 출력 파일의 이름을 결정 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>합니다.  
  
 사용자 지정 도구를 구현 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 인터페이스입니다. 필요에 따라 사용자 지정 도구를 지원 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 입력된 파일 이외의 원본에서 정보를 검색 하는 인터페이스입니다. 어떤 경우 든, 사용자 지정 도구를 사용 하려면 먼저 등록 해야 또는 시스템과 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 로컬 레지스트리입니다. 사용자 지정 도구를 등록 하는 방법은 참조 하세요 [단일 파일 생성기 등록](../../extensibility/internals/registering-single-file-generators.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트의 기본 Namespace를 결정합니다.](../../misc/determining-the-default-namespace-of-a-project.md)   
 [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)
