---
title: 프로젝트 계층 구조 노드 이름 바꾸기 (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686581"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>프로젝트 계층 구조 노드 이름 바꾸기(C++)
관리 되지 않는 HierUtil7 프로젝트 프레임 워크를 사용 하 여 프로젝트 폴더 계층 노드의 이름을 바꿀 수 있습니다 C++입니다. 자세한 내용은 [HierUtil7 샘플](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11)합니다.  
  
## <a name="expanding-the-hierarchy-node"></a>계층 노드를 확장합니다.  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>계층 노드를 확장 하 여 폴더 이름 바꾸기  
  
1. 다음 메서드를 사용 하 여 계층 구조 노드를 선택 합니다.  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` 계층 컨테이너인 폴더에 해당 하 고 `EXPF_SelectItem` 에서는 <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> 열거형. 합니다 `GUID_MacroExplorer` Vsshell.idl에 정의 된 GUID 상수 이며에 대 한 예로 `rguidPersistenceSlot` 함수 시그니처에 `ExtExpand`Hu_node.h에 정의 된 합니다.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     폴더에서 Hu_node.h 파일을 찾을 수 있습니다 \<설치 루트 > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2. 폴더 이름 바꾸기 명령을 사용 하 여 게시 하 여 이름 바꾸기 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 포인터: `<IVsUIShell>``srpVsUIShell`합니다. `guiVSStd97` 명령 그룹의 고유 식별자는 명령을 `cmdidRename` 속한 Vsshlids.h에 정의 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 형식 만들기](../extensibility/internals/creating-project-types.md)   
 [VSSDK 샘플](../misc/vssdk-samples.md)