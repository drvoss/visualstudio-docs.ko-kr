---
title: UsedCommand 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186373"
---
# <a name="usedcommand-element"></a>UsedCommand 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다른.vsct 파일에 정의 된 명령에 액세스 하기 위해 VSPackage를 사용 하도록 설정 합니다. 예를 들어 VSPackage는 표준을 **복사본** 명령에 정의 된는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 셸을 추가할 수 명령을 메뉴나 도구 모음을 다시 구현 하지 않고도 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|guid|필수 요소. 명령을 식별 하는 GUID ID 쌍의 GUID입니다.|  
|id|필수 요소. 명령을 식별 하는 GUID ID 쌍의 ID입니다.|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|없음||  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[UsedCommands 요소](../extensibility/usedcommands-element.md)|UsedCommand 요소를 그룹화 하 고 기타 UsedCommands 그룹화 합니다.|  
  
## <a name="remarks"></a>설명  
 명령을 추가 하 여는 `<UsedCommands>` 요소인 VSPackage 알립니다는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경 VSPackage의 명령에 필요 합니다. 추가 해야는 `<UsedCommand>` 요소는 패키지에 필요한 모든 명령에 대 한 모든 버전 및 Visual Studio의 구성에 포함 되지 않을 수 있습니다. 예를 들어 패키지 visual 특정 명령을 호출 하는 경우 C++를 포함 하지 않으면이 명령은 Visual Web Developer의 사용자에 게 사용할 수 없습니다는 `<UsedCommand>` 명령에 대 한 요소입니다.  
  
## <a name="example"></a>예제  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>참고 항목  
 [UsedCommands 요소](../extensibility/usedcommands-element.md)   
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
