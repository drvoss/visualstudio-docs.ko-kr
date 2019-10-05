---
title: Bitmap 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184739"
---
# <a name="bitmap-element"></a>Bitmap 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

비트맵을 정의합니다. 비트맵 파일 또는 리소스에서 로드 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|guid|필수 요소. GUID/i D 명령 식별자의 GUID입니다.<br /><br /> 비트맵에 대 한 guid 특성 모든 VSPackage 또는 다른 명령 그룹을 사용 하 여 연결 되지 않습니다.  비트맵 정의에 고유 해야 하 고 다른 목적을 위해 쓰일 수 없습니다.|  
|resID|GUID/i D 명령 식별자의 ID입니다. ResID 또는 href 특성이 필요합니다.<br /><br /> ResID 특성은 명령 테이블을 병합 하는 동안 로드 되는 비트맵 스트립을 결정 하는 정수 리소스 ID입니다.  명령 테이블 로드 되는 경우 리소스 ID 기준으로 지정 된 비트맵은 동일한 모듈의 리소스에서 로드 됩니다.|  
|usedList|ResID 특성 있는지 필요 합니다. 비트맵 스트립에서 사용 가능한 이미지를 선택합니다.|  
|href|비트맵에 대 한 경로입니다. ResID 또는 href 특성이 필요합니다.<br /><br /> 포함 경로 결과 이진에 포함 된 지정 된 이미지 파일에 대해 검색 됩니다.  명령 테이블 병합 중 이미지 복사 되 하 고 추가 리소스 조회 또는 부하 필요 하지 않습니다.  UsedList 특성이 없는 경우 모든 이미지 스트립에서 사용할 수 있습니다. **참고:**  이미지는.bmp,.png,.gif 등 여러 형식 중 하나에서 제공 될 수 있습니다.  이전 버전의 컴파일러는 부분 투명도 대 한 정보가 알파는 32 비트 비트맵 이미지를 지원 하지 않았습니다. 이러한 버전에 대 한 해결 방법은.png 형식을 사용 하는 것입니다.|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[Bitmaps 요소](../extensibility/bitmaps-element.md)|비트맵 요소를 그룹화합니다.|  
  
## <a name="example"></a>예제  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
