---
title: 도구 창 표시 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186390"
---
# <a name="tool-window-display-configuration"></a>도구 창 표시 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage는 도구 창, 기본 위치, 크기, 도킹 스타일 및 다른 표시 유형 정보를 등록 하는 경우 옵션 값에 지정 됩니다. 도구 창 등록에 대 한 자세한 내용은 참조 하세요. [레지스트리에서 Windows 도구](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>정보 창 표시  
 도구 창의 기본 표시 구성 옵션 값에 최대 6 개에 저장 됩니다.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|이름|형식|보기|설명|  
|----------|----------|----------|-----------------|  
|이름|REG_SZ|"짧은 이름"|도구 창을 설명 하는 짧은 이름입니다. 레지스트리에서 참조용 으로만 사용 합니다.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|4 개의 쉼표로 구분 된 값입니다. X1, Y1는 도구 창의 왼쪽 위 모퉁이의 좌표입니다. X2 Y2은 오른쪽 아래 모퉁이의 좌표입니다. 모든 값은 화면 좌표입니다.|  
|스타일|REG_SZ|"MDI"<br /><br /> "Float"<br /><br /> "연결"<br /><br /> "탭"<br /><br /> "AlwaysFloat"|도구 창의 상태를 표시 하는 초기를 지정 하는 키워드입니다.<br /><br /> "MDI" = MDI 창을 사용 하 여 도킹 합니다.<br /><br /> "부동" 부동 =.<br /><br /> "연결" = 다른 창 (창 항목에 지정 됨)를 사용 하 여 연결 합니다.<br /><br /> "탭" = 다른 도구 창을 사용 하 여 결합 합니다.<br /><br /> "AlwaysFloat" = 도킹 될 수 없습니다.<br /><br /> 자세한 내용은 아래 의견 섹션을 참조 하세요.|  
|창|REG_SZ|*\<GUID>*|GUID는 도구 창 수 연결 되거나 탭 창입니다. GUID는 고유한 창 중 하나 또는 창 중 하나에 속할 수는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|방향|REG_SZ|"왼쪽"<br /><br /> "오른쪽"<br /><br /> "Top"<br /><br /> "아래쪽"|아래 설명 섹션을 참조 하세요.|  
|DontForceCreate|REG_DWORD|0 또는 1|이 항목은 있는 0이 아닌 값을 창 로드 되었지만 즉시 표시 됩니다.|  
  
### <a name="comments"></a>주석  
 방향 항목 도구 창 제목 표시줄 두 번 클릭할 때 도킹 하는 있는 위치를 정의 합니다. 창 항목에 지정 된 창의 상대적 위치가입니다. 스타일 항목을 "연결"로 설정 하면 "왼쪽", "오른쪽", "Top" 또는 "아래쪽" 방향 항목 수 있습니다. 스타일 항목 "탭", 방향을 항목 유지할 수 있습니다"" 또는 "오른쪽" 이며 탭은 추가 하는 위치를 지정 합니다. 스타일 항목을 "고정" 하는 경우 먼저 도구 창을 부동 합니다. 제목 표시줄 두 번 클릭할 때 방향 및 창 항목에 적용 하 고 창 "탭" 스타일을 사용 합니다. "AlwaysFloat" 스타일 항목을 사용 하는 경우 도구 창을 고정할 수 없습니다. "MDI" 스타일 항목을 사용 하는 경우 도구 창이 MDI 영역에 연결 하 고 창 항목 무시 됩니다.  
  
### <a name="example"></a>예제  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>도구 창 표시  
 선택적 가시성 하위 키 값에는 도구 창의 표시 여부 설정을 결정합니다. 창의 표시 해야 하는 명령의 Guid를 저장 하는 값의 이름은 사용 됩니다. 명령이 실행 되는 경우 IDE 도구 창을 생성 되어 표시할 보장 합니다.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|이름|형식|보기|설명|  
|----------|----------|----------|-----------------|  
|(기본값)|REG_SZ|없음|비워 둡니다.|  
|*\<GUID>*|REG_DWORD 또는 REG_SZ|0 또는 설명 문자열입니다.|선택 사항입니다. 항목의 이름에는 가시성 요구 명령의 GUID 여야 합니다. 방금 값 정보를 제공 하는 문자열을 포함합니다. 값은 일반적으로 `reg_dword` 0으로 설정 합니다.|  
  
### <a name="example"></a>예제  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPackage Essentials](../misc/vspackage-essentials.md)
