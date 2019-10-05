---
title: 프로젝트의 기본 Namespace 결정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705768"
---
# <a name="determining-the-default-namespace-of-a-project"></a>프로젝트의 기본 네임스페이스 확인
에 대 한 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]이면 합니다 `CustomToolNamespace` 속성은 입력된 파일의 값에 설정 `CustomToolNamespace` 에 전달 된 기본 네임 스페이스 매개 변수 값이 됩니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 메서드. 이 고, 그렇지 합니다 `wszDefaultNamespace` 전달 된 매개 변수가 `Generate` 은 항상 루트 네임 스페이스와 동일 합니다. 네임 스페이스에 대 한 자세한 내용은 참조 하세요. [Namespace 키워드](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b)합니다.  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 폴더 기반 네임 스페이스를 사용합니다. 즉, 네임 스페이스는 루트 네임 스페이스와 사용자 지정 도구가 포함 된 폴더의 이름으로 구성 됩니다. 각 폴더 이름은 올바른 식별자로 변환 됩니다 및 기간에는 모든 이름을 구분 합니다. 예를 들어 경우 입력된 파일은 FolderA\FolderB\FolderC\MyInput.txt, 이며 루트 네임 스페이스 CL9에 계산 된 기본 네임 스페이스는 됩니다 **CL9 합니다. FolderA.FolderB.FolderC**합니다.  
  
 웹 참조 폴더를 포함 하는 계층 구조 체인이이 규칙에 예외가 발생 합니다. 예를 들어 경우:  
  
- FolderC 된 웹 참조 폴더, 네임 스페이스 **CL9 합니다. FolderC**합니다.  
  
- FolderB 된 웹 참조 폴더, 네임 스페이스 **CL9 합니다. FolderB.FolderC**합니다.  
  
  즉, 네임 스페이스에는 다음 형식을 사용 합니다.  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>참고 항목  
 [단일 파일 생성기 구현](../extensibility/internals/implementing-single-file-generators.md)   
 [단일 파일 생성기 등록](../extensibility/internals/registering-single-file-generators.md)   
 [비주얼 디자이너에 형식 노출](../extensibility/internals/exposing-types-to-visual-designers.md)