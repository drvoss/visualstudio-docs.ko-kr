---
title: Extern 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204403"
---
# <a name="extern-element"></a>Extern 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extern 요소는 컴파일 타임에.vsct 파일을 사용 하 여 병합할 모든 외부 헤더 (.h) 파일을 참조 합니다. VSCT 컴파일러인 지정 되거나 참조 포함 경로에 병합할 파일 이어야 합니다는 [포함 요소](../extensibility/include-element.md)합니다. 파일을 다른.vsct 파일을 수 있습니다 또는 C++ 헤더 파일입니다.  
  
 폼의 헤더 파일에 정의 해야 "#define [기호] [Value]" 값을 이전에 정의 된 경우 다른 기호를 수 있습니다. 명령은 항목의 조건문에서 정의 사용할 수 있습니다. 실제로 사용 되는 모든 기호는 무시 됩니다.  
  
 CommandTable 요소  
Extern 요소  
  
## <a name="syntax"></a>구문  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|href|필수 요소. 헤더 파일에 대 한 경로:<br /><br /> href="stdidcmd.h"|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
|language|선택 사항입니다. 모든 기본 언어가 [ \<문자열 >](../extensibility/strings-element.md) 명령 테이블에 있는 요소:<br /><br /> language="en-us"|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|없음|없음|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 요소를 모두 정의-메뉴 항목, 메뉴, 도구 모음 및 콤보 상자,-VSPackage IDE를 제공 하는 합니다.|  
  
## <a name="example"></a>예제  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
