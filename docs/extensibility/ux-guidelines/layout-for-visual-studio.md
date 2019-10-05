---
title: Visual Studio에 대 한 레이아웃 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef763f3142f41e63effa1f76bb6bebdc95f0ee3a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335352"
---
# <a name="layout-for-visual-studio"></a>Visual Studio에 대 한 레이아웃
대부분의 Visual Studio 대화 상자 [유틸리티 대화 상자 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), 다음 표준에 대화 상자는 unthemed 되 [Windows Desktop 대화 상자 레이아웃 원칙](/windows/desktop/uxguide/win-dialog-box)합니다. Visual Studio UI를 새로 고치려면 이동, 띄 대화 상자의 일부 환경으로 제품 정의 설정 하는 새 디자인을가지고 있습니다. 이러한 [테마가 지정 된 대화 상자 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) 모양이 테마를 지정 합니다.

## <a name="BKMK_UtilityDialogLayout"></a> 유틸리티 대화 상자 레이아웃

- 유틸리티 대화 상자 내에서 모든 컨트롤 위쪽/왼쪽에서 시작 하 고 아래쪽으로 전달 해야 합니다.

- 되지 center 대화 상자에 컨트롤 큰 영역을 채우도록 합니다.

- 모든 대화 상자 텍스트에 대 한 환경 글꼴을 사용 합니다. Visual 사양을 작성할 때는 특정 글꼴 및 크기를 선택 하는 대신 환경 글꼴을 지정 합니다. 참조 [글꼴로](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)합니다.

- 장인의 품질에 대 한 목표를 지원 하기 위해 일관 된 제어 간격 및 배치를 사용 합니다.

- 대화 상자에서 컨트롤, 컨트롤의 고유 juxtaposition 또는 둘 다에 대해 많은 더 복잡할 수 있습니다. 이러한 복잡 한 상황에 대 한 구문 분석 하는 논리 흐름 사용자에 게 컨트롤 그룹 간에 충분 한 공간을 허용 합니다.

### <a name="utility-dialog-layout-examples"></a>유틸리티 대화 상자 레이아웃 예제
 모든 치수 (픽셀)로 표현 됩니다.

 ![컨트롤 위의 레이블에 대 한 대화 상자 간격 조정](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")

 **그림 a 08.01: 컨트롤 위의 레이블에 사용 하 여 유틸리티 대화 상자에 대 한 간격 지침**

 ![대화 상자 간격 조정 컨트롤의 왼쪽에 레이블을](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")

 **그림 08.01-b: 레이블이 컨트롤 왼쪽에 있는 유틸리티 대화 상자에 대 한 간격 지침**

### <a name="layout-details"></a>레이아웃 정보

#### <a name="margins"></a>여백

- 모든 대화 상자에는 12 픽셀 테두리 가장자리 모두 있어야 합니다.

- 그룹 안에 여백 프레임의 가장자리에서 9 픽셀 이어야 합니다.

- 탭 컨트롤 내에서 여백을 탭 컨트롤의 가장자리에서 6 픽셀 이어야 합니다.

#### <a name="command-buttons"></a>명령 단추

- 명령 단추 콘텐츠에 없는 대화 프레임에서 작동합니다. 맨 오른쪽 하며 명확 하 게 구분 단추를 설정 하려면 위의 변수 충분 한 공간이 있어야 합니다.

- 가로 단추 대화 상자 내에서 작동 하는 경우 대체 명령 단추 구성은 오른쪽 위에 세로로 쌓입니다. 참조 [내부 명령 단추](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) 아래.

- 명령 단추 (왼쪽/의 아래쪽 가운데 대화 상자)의 왼쪽에 공간에는 작업 대화 상자 컨트롤의 "밴드"의 일부로 간주 됩니다. 해당 공간에 방해가 해야 하는 유일한은 전체 작업 또는 대화 상자와 관련 된 도움말 링크입니다.

- 명령 단추 75 x 23 픽셀 이어야 합니다.

- 명령 단추 떨어져 6 픽셀 이어야 합니다.

  ![기본 단추 맞춤](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")

  **그림 08.01-c: 기본 단추 맞춤**

#### <a name="labels"></a>레이블

- 왼쪽에 맞추려면 모든 레이블이 있습니다.

- 컨트롤 위에 있는 레이블의 경우 왼쪽-맞추어야 아래 컨트롤과 정확 하 게 하 고 레이블 아래쪽에 다른 컨트롤 (예를 들어, 콤보 상자)의 맨 위에서 5 픽셀 이어야 합니다.

- 컨트롤의 왼쪽에 있는 레이블의 경우 레이블 및 입력된 컨트롤 간의 최소 너비는 10 픽셀입니다. 암시 된 열 두 번째 텍스트 상자, 콤보 상자 또는 기타 컨트롤을 정렬 하기 위해 설정 됩니다.

- 레이블과 문장 뒤에 콜론이 됩니다. 참조 [텍스트 스타일](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)합니다.

#### <a name="distance-between-controls"></a>컨트롤 사이의 간격
 합리적으로 컨트롤을 쌓습니다. 누적된 컨트롤 사이의 간격에 대 한 절대 지침 없는 경우 컨트롤 간의 다듬기 대화 상자가 약간 달라질 수 있습니다. 권장 되는 간격은 세로 컨트롤/레이블 쌍에 대 한 20 픽셀이 고 가로 컨트롤/레이블 쌍에 대 한 9 픽셀입니다. 가로 쌍에 대 한 최소 컨트롤 간격은 6 픽셀입니다.

 ![컨트롤 사이의 거리를 권장](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")

 **그림 08.01-d: 컨트롤 사이의 거리에 대 한 권장 사항**

#### <a name="control-indentation"></a>컨트롤의 들여쓰기
 컨트롤은 중첩 된 경우 위의 일반적으로 레이블이 컨트롤의 왼쪽된 가장자리를 사용 하 여 가로로 내부 컨트롤을 정렬 합니다.

 ![컨트롤 맞춤 중첩](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")

 **그림 08.01-e: 중첩 된 컨트롤 맞춤**

#### <a name="control-width"></a>컨트롤 너비
 텍스트 상자 또는 다른 유사한 컨트롤의 너비 필드에 대 한 평균 입력 미만 이어야 합니다. 평균 영어 단어는 5 자입니다. 예를 들어, 긴 경로 이름이 필요로 하는 텍스트 상자에서는 가로 레이아웃으로 있어야 드롭다운을 하는 동안 플랫폼 이름 길이가 긴 항목을 사용할 수 있는 이어야만 합니다.

#### <a name="helper-text"></a>도우미 텍스트

- 대화는 대화의 목적에 대 한 자세한 정보를 제공 하는 도우미 텍스트를 표시할 수 있습니다. 이 일반적으로 맨 위에 있는 위치 및 1-2 문장이 될 수 있습니다.

- 줄 길이 읽고 구문 분석 하는 사용자에 대 한 너비를 편리 하 게 해야 합니다. 보통 대화 550 개 이하의 픽셀 이어야 합니다.

#### <a name="BKMK_InteriorCommandButtons"></a> 내부 명령 단추
 더 복잡 한 대화 상자에서 내부 컨트롤에는 대화의 커밋 단추 있는 영향을 줄 수 있는 관련된 단추 자체 있을 수 있습니다.

- 사용 하 여 내부의 세로 맞춤 (열) 단추로 **확인**/**취소** 오른쪽 아래 모퉁이의 가로 방향으로 합니다.

- 사용 하 여 내부의 가로 맞춤 (행) 단추로 **확인**/**취소** 오른쪽 위 모퉁이에서 세로 방향으로 합니다. 이 상황은 일반적이 지 않습니다.

- 내부 단추 크기 75 x 23 픽셀의 크기와 일치 하는 표준 단추 크기를 대상으로 해야 **확인**/**취소** 가능 하면 단추입니다. 단추 레이블 표준 단추 크기를 초과 하는 단추를 만드는 경우 해당 집합의 다른 단추는 광범위 한 크기를 사용 하 여 일치 해야 합니다.

  ![가로 확인 및 취소 단추가](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")

  **그림 08.01-f: 가로 확인/취소를 사용 하 여 세로 내부 단추**

  ![세로 확인 및 취소 단추가](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")

  **그림 08.01-g: 세로 확인/취소를 사용 하 여 내부 가로 단추**

#### <a name="browse-button"></a>[찾아보기...] 단추
 **[찾아보기...]**  단추 텍스트 상자에 나오는 "찾아보기..." 꿈꾸고 해야 전체에서 줄임표를 포함합니다. 공간이 긴밀 하 게 또는 여러 개 있을 경우 **[찾아보기...]**  방금 줄임표 단추 화면에서 단추를 줄일 수 있습니다.

## <a name="BKMK_ThemedDialogLayout"></a> 테마가 지정 된 대화 상자 레이아웃
 Visual Studio에서 테마가 지정 된 대화 상자에는 밝은 모양이 및 자세한 백서 공간을 제공 합니다. 입력 체계 강조 점점 더 개방적 줄 간격 및 글꼴 크기 및 중량의 변형을 제공 관심을 제공 합니다. 가능한 경우, chrome 및 제목 표시줄 감소 되거나 제거 되었습니다. 이러한 대화 상자 레이아웃이 기본 패턴을 따라야 합니다.

1. 대화 상자의 배경색은 흰색입니다.

2. 중간 값 회색 규칙 1 픽셀 테두리는 있습니다.

3. 대화 상자 제목을 더 이상 제목 표시줄에 위치 하 하지만 시각적 효과 지점 크기의 강조를 제공 합니다. (에서 글꼴 크기 섹션을 참조 하세요 [텍스트 스타일](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. 레이블, 설명 등의 추가 텍스트와 결합 해야 **환경 글꼴 + 굵게**합니다.

5. 내부 열은 연한 회색 1 픽셀 너비 규칙에 의해 구분 됩니다.

6. 기본 링크에는 밑줄 없이 합니다. 가리키기 및 누름된 상태 경우 밑줄과 색 변경

7. 커밋 단추 (같은 **확인**/**취소**) 오른쪽 아래 모퉁이에 배치 합니다.

### <a name="themed-dialog-layout-examples"></a>테마가 지정 된 대화 상자 레이아웃 예제
 ![테마가 지정 된 대화 상자 레이아웃](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")

 **그림 08.01-h: 테마가 지정 된 대화 상자**

 ![테마가 지정 된 대화 크기](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")

 **그림 08.01-i: 테마가 지정 된 대화 상자-차원**

 ![테마가 지정 된 대화 상자 글꼴](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")

 **그림 08.01-j: 테마가 지정 된 대화 상자-글꼴**

 ![테마가 지정 된 대화 상자 색](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")

 **그림 08.01-k: 테마가 지정 된 대화 상자-색**

## <a name="see-also"></a>참고 항목
- [Visual Studio의 애플리케이션 패턴](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [컨트롤 (Windows)](/windows/desktop/uxguide/controls)
- [대화 상자 (Windows)](/windows/desktop/uxguide/win-dialog-box)