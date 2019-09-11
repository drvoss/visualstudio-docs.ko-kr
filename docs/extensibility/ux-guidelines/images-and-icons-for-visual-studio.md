---
title: Visual Studio의 이미지 및 아이콘 | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ba4a5c52bf972236914c06ec9672653fbde9cea
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891052"
---
# <a name="images-and-icons-for-visual-studio"></a>Visual Studio의 이미지 및 아이콘
## <a name="BKMK_ImageUseInVisualStudio"></a> Visual Studio에서 이미지 사용
 아트 워크를 만들기 전에 하는 것이 좋습니다에 1,000 개 이상 이미지를 사용 합니다 [Visual Studio 이미지 라이브러리](http://www.microsoft.com/en-my/download/details.aspx?id=35825)합니다.

### <a name="types-of-images"></a>이미지 형식

- **아이콘**합니다. 명령, 계층, 템플릿 및 등에 표시 되는 작은 이미지입니다. Visual Studio에서 사용 되는 기본 아이콘 크기는 16 x 16 PNG입니다. 이미지 서비스에서 자동으로 생성 되는 아이콘 HDPI 지원이 XAML 형식을 생성 합니다.

    > [!NOTE]
    > 이미지 메뉴 시스템에서 사용 되지만, 모든 명령에 대 한 아이콘을 만들지 마십시오. 참조 하세요 [Visual Studio의 메뉴 및 명령](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) 명령 아이콘을 가져와야 하는지 여부를 확인 합니다.

- **미리 보기입니다.** 새 프로젝트 대화 상자와 같은 대화 상자에서 미리 보기 영역에 사용 되는 이미지입니다.

- **대화 상자 이미지입니다.** 대화 상자 또는 마법사 설명이 포함 된 그래픽 또는 메시지 표시기에 표시 되는 이미지입니다. 사용자의 이목을 (경고, 경고) 또는 어려운 개념을 설명 하는 데 필요한 경우에 및 자주 사용 합니다.

- **애니메이션이 적용 된 이미지입니다.** 진행률 표시기, 상태 표시줄 및 작업 대화 상자에 사용 합니다.

- **커서입니다.** 개체 삭제 될 수 있습니다 및 등에 있는 마우스를 사용 하 여 작업이 허용 되는지 여부를 나타내는 데 사용 합니다.

## <a name="BKMK_IconDesign"></a> 아이콘 디자인

### <a name="overview"></a>개요
 Visual Studio 정리 기 하 도형 및 50/50 긍정/부정 (밝은/어두운) 간의 균형 및 직접을 이해할 수 있는 기능을 사용 하 여 최신 스타일 아이콘을 사용 합니다. 중요 아이콘 디자인 중심으로 쉽게 구별할 수 있도록, 간소화 및 컨텍스트를 가리킵니다.

- **쉽게 구별할 수 있도록:** 해당 의미 및 독창성 아이콘을 제공 하는 핵심 메타포에 집중 합니다.

- **간소화:** core 의미 아이콘 줄이는-만 필요한 요소와 없습니다 간단히 테마를 가져옵니다.

- **컨텍스트:** 는 아이콘의 핵심 메타포를 구성 하는 요소를 결정 하는 데 중요 개념 개발 하는 동안 아이콘의 역할의 모든 측면을 고려 합니다.

  아이콘을 사용 하 여 방지 디자인 요소의 사항이 있습니다.

- 해당 하는 경우 제외 하 고 UI 요소를 나타내는 아이콘을 사용 하지 마세요. UI 요소는 일반, 분명, 아니고 고유 추상 또는 기호화 된 더 접근 방식을 선택 합니다.

- 문서, 폴더, 화살표, 돋보기 등 공통 요소를 남용 하지 마십시오. 아이콘의 의미에 필수적인 경우에 이러한 요소를 사용 합니다. 예를 들어, 오른쪽 방향 돋보기 검색만 나타내야 찾아보기 합니다.

- 일부 레거시 아이콘 요소 관점의 사용을 유지 하지만 만들지 새 아이콘 큐브 뷰를 사용 하 여 요소에 없으면 명확 하지 않으면.

- 아이콘에 너무 많은 정보를 cram 하지 마십시오. 쉽게 인식 하거나 인식할 수 있는 기호로 학습 수 있는 간단한 이미지를 지나치게 복잡 한 이미지 보다 훨씬 더 유용 합니다. 아이콘 전체적인 내용을 확인할 수 없습니다.

### <a name="icon-creation"></a>아이콘 만들기

#### <a name="concept-development"></a>개념 개발
 Visual Studio에는 해당 UI 내에서 다양 한 아이콘 형식 아이콘 유형을 개발 하는 동안 주의 합니다. 프로그램 아이콘 요소에 대 한 명확 하지 않거나 일반적이 지 않은 UI 개체를 사용 하지 마세요. 와 같은 이러한 경우에 바로 가기 링크에 대 한 스마트 태그 아이콘을 사용 하 여 선택 합니다. 왼쪽의 추상 의미 태그는 다음과 같습니다. 오른쪽에 모호한, UI 기반 버전과 보다 명확 하 게

|||
|-|-|
|**기호화 된 이미지의 올바른 사용**|**기호화 된 이미지를 잘못 사용 했습니다.**|
|![올바른 스마트 태그 아이콘](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404 01_SmartTagCorrect")|![잘못 된 스마트 태그 아이콘](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 02_SmartTagIncorrect")|

 아이콘에 대 한 작업 수행 표준, 쉽게 인식할 수 있는 UI 요소는 인스턴스가 있습니다. 기간은 이러한 예제 중 하나를 추가 합니다.

|||
|-|-|
|**아이콘에 올바른 UI 요소**|**아이콘에 잘못 된 UI 요소**|
|![올바른 창 추가 아이콘](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 03_AddWindowCorrect")|![잘못 된 창 추가 아이콘](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 04_AddWindowIncorrect")|

 아이콘의 의미 하는 데 중요 하지 않은 문서를 기본 요소로 사용 하지 마세요. 문서 없이 새로 고침을 사용 하 여 문서 요소는 의미를 통신 하는 데 필요한 추가 문서 (아래) 의미 요소 손실 됩니다.

|||
|-|-|
|**올바른 문서 아이콘 사용**|**문서 아이콘을 잘못 사용 했습니다.**|
|![올바른 문서 아이콘](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 05_DocumentIconCorrect")|![잘못 된 문서 아이콘](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 06_DocumentIconIncorrect")|

 "Show"의 개념을 가장 잘 표시 되는 항목을 같은 모든 파일 표시 예제에서와 마찬가지로 표현 하는 아이콘으로 나타나야 합니다. 리소스 뷰 예제와 같이 필요한 경우 "보기"의 개념을 나타내기 위해 렌즈 메타포를 사용할 수 있습니다.

|||
|-|-|
|**"Show"**|**"View"**|
|![표시 아이콘](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 07_Show")|![뷰 아이콘](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 08_View")|

 오른쪽 지향 돋보기 모양 아이콘이 나타내는 검색 하도록, 찾기 및 찾아보기 더하기 또는 빼기 기호를 사용 하 여 왼쪽 지향 변형을 나타내는 유일한 확대/축소 해야 합니다.

|||
|-|-|
|**"Search"**|**"Zoom"**|
|![검색 아이콘](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 09_Search")|![확대/축소 아이콘](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 10_Zoom")|

 트리 보기에서 폴더 아이콘 및 한정자를 사용 하지 마십시오. 사용 가능한 경우에 한정자만 사용 합니다.

|||
|-|-|
|**올바른 트리 뷰 아이콘**|**잘못 된 트리 뷰 아이콘**|
|![올바른 트리 뷰 아이콘 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![올바른 트리 뷰 아이콘 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![잘못 된 트리 뷰 아이콘 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![잘못 된 트리 뷰 아이콘 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 14_ TreeViewIncorrect2")|

### <a name="style-details"></a>스타일 세부 정보

#### <a name="layout"></a>레이아웃
 표준 16 x 16 아이콘에 대 한 예제와 같이 요소를 스택:

 ![16 x 16 아이콘에 대 한 레이아웃 스택](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 15_LayoutStack")<br />16 x 16 아이콘에 대한 레이아웃 스택

 상태 알림 요소는 독립 실행형 아이콘으로 사용 되는 더 합니다. 그러나는 알림을 해야 쌓을 수는 기본 요소에 같은 작업 완료 아이콘을 사용 하 여 컨텍스트 가지가 있습니다.

 ![Visual Studio의 독립 실행형 알림](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")<br />독립 실행형 알림 아이콘

 ![작업 완료 아이콘](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 17_TaskComplete")<br />작업 완료 아이콘

 프로젝트 아이콘은 일반적으로 다양 한 크기를 포함 하는.ico 파일입니다. 대부분의 16 x 16 아이콘에는 동일한 요소를 포함 합니다. 32 x 32 버전에 해당 하는 경우 프로젝트 형식을 포함 한 자세한 내용은 있습니다.

 ![Visual Studio에서 아이콘 프로젝트](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")<br />16 x 16 및 32 x 32 VB Windows 컨트롤 라이브러리 프로젝트 아이콘

 픽셀 프레임 내의 아이콘을 센터입니다. 가능 하지 않은 아이콘이 맨 위에 및/또는 프레임의 오른쪽에 맞춥니다.

 ![픽셀 프레임 내의 가운데에 맞춰진 아이콘](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 19_IconCentered")<br />픽셀 프레임 내의 가운데에 맞춰진 아이콘

 ![맞춰진 아이콘 픽셀 프레임의 오른쪽 위에 있는](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 20_IconTopRight")<br />맨 위에 맞춰진 아이콘 프레임의 오른쪽

 ![아이콘 가운데에 맞춰지고 픽셀 프레임의 위쪽에 맞춥니다](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 21_IconTopAlign")<br />가운데에 맞춰지고 프레임의 위쪽에 정렬 아이콘

 이상적인 맞춤 및 분산 시키려면 작업 문자 모양 사용 하 여 아이콘의 기본 요소를 방해 하지 않습니다. 기본 요소의 위쪽에 있는 문자 모양의 왼쪽 위치입니다. 추가 요소를 추가할 때 정렬 하 고 아이콘의 균형을 고려 합니다.

|||
|-|-|
|**올바른 맞춤 및 분산**|**잘못 된 맞춤 및 분산**|
|![아이콘 균형 및 맞춤을 수정](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![잘못 된 아이콘 균형 및 맞춤](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|

 요소를 공유 하 고 집합에서 사용 되는 아이콘에 대 한 크기 패리티를 확인 합니다. 잘못 된 연결에 원과 화살표 큰 및 일치 하지 마십시오.

|||
|-|-|
|**올바른 크기 패리티**|**잘못 된 크기 패리티**|
|![아이콘 크기 및 패리티를 수정](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 24_SizeParityCorrect")|![잘못 된 아이콘 크기 및 패리티](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 25_SizeParityIncorrect")|

 일관 된 선과 visual 가중치를 사용 합니다. 나란히 비교 하 여 작성 하는 아이콘을 다른 아이콘을 비교 하는 방법을 평가 합니다. 전체 16 x 16 프레임을 사용 하 여 15 15 배 또는 더 작은 사용 하지 않습니다. 음수-긍정 (진한 광원) 비율 50/50 이어야 합니다.

|||
|-|-|
|**올바른 음수-긍정 비율**|**잘못 된 음수-긍정 비율**|
|![아이콘에 대 한 시각적 중량 감을 수정 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![아이콘에 대 한 시각적 중량 감을 수정 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![아이콘에 대 한 시각적 중량 감을 수정 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![아이콘에 대 한 잘못 된 시각적 중량](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 29_VisualWeightIncorrect")|

 요소의 요소 무결성을 희생 하지 않고 빌드를 간단 하 고 비교 가능한 셰이프 및 보색 각도 사용 합니다. 가능한 경우 90 ° 또는 45도 각도 사용 합니다.

 ![수정 아이콘 각도](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 30_IconAnglesCorrect")

#### <a name="perspective"></a>Cube
 아이콘을 명확 하 고 이해 하기 쉽게 유지 합니다. 큐브 뷰 및 광원 필요한 경우에 사용 합니다. 큐브 뷰를 사용 하 여 아이콘 요소에는 피해 야 하지만 일부 요소 없으면 인식할 수 있는있지 않습니다. 이러한 경우 스타일이 지정 된 큐브 뷰는 요소의 명확 하 게를 통신합니다.

 ![3 점 소실점](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 31_3PointPerspective")<br />3점 원근감

 ![1 점 소실점](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 32_1PointPerspective")<br />1점 원근감

 대부분의 요소는 연결 수 또는 오른쪽으로 회전할:

 ![아이콘 오른쪽으로 각 진](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 33_AngledRight")

 개체에 필요한 명확성을 추가 하는 경우에 광원을 사용 합니다.

|||
|-|-|
|**올바른 광원**|**잘못 된 광원**|
|![광원 아이콘에 대 한 수정](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![아이콘에 대 한 잘못 된 광원](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|

 가독성을 향상 시킵니다에 또는 메타포를 잘 전달할 윤곽선을 사용 합니다. 음수 가양성 (진한 광원) 분산 50/50 이어야 합니다.

|||
|-|-|
|**윤곽선의 올바른 사용**|**윤곽선을 잘못 사용 했습니다.**|
|![윤곽선을 수정한](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 36_OutlinesCorrect")|![잘못 된 윤곽선](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 37_OutlinesIncorrect")|

#### <a name="icon-types"></a>아이콘 형식
 **셸 및 명령 모음** 아이콘 다음 요소의 3 개 구성: 하나의 자료, 한정자, 하나의 작업 또는 하나의 상태입니다.

 ![셸 및 명령 모음 아이콘의 예가](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 38_ShellIcons")<br />셸 및 명령 모음 아이콘의 예

 **도구 창 명령 모음** 아이콘 다음 요소의 3 개 구성: 하나의 자료, 한정자, 하나의 작업 또는 하나의 상태입니다.

 ![도구 창의 예 명령 모음 아이콘](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")<br />도구 창 명령 모음 아이콘의 예

 **트리 뷰 disambiguator** 아이콘 다음 요소의 3 개 구성: 하나의 자료, 한정자, 하나의 작업 또는 하나의 상태입니다.

 ![예제 트리 보기 기 아이콘](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 40_TreeViewIcons")<br />예제 트리 보기 기 아이콘

 **값 상태 기반 분류** 상태에서 아이콘 존재: 활성, 사용 하지 않도록 설정, 활성 및 비활성 사용 하지 않도록 설정 합니다.

 ![상태 기반 값 분류 아이콘 예가](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")<br />상태 기반 값 분류 아이콘의 예

 **IntelliSense** 아이콘 다음 요소의 3 개 구성: 하나의 자료, 한정자, 및 하나의 상태입니다.

 ![IntelliSense 아이콘 예가](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 42_IntelliSenseIcons")<br />IntelliSense 아이콘의 예

 **작은 (16 x 16) 프로젝트** 아이콘 2 개 이하의 요소가 있어야 합니다: 하나의 자료 및 한정자입니다.

 ![작은 (16 x 16)의 예제 프로젝트 아이콘](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 43_16x16Project1") ![16x16 프로젝트 아이콘 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 44_16x16Project2") ![16x16 프로젝트 아이콘 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 45_16x16Project3")<br />작은 (16 x 16) 프로젝트 아이콘의 예

 **대규모 (32 x 32) 프로젝트** 아이콘의 다음 요소 중 4 개 구성: 하나의 자료, 1 ~ 2 한정자 및 언어별로 오버레이 합니다.

 ![큰 (32 x 32)의 예제 프로젝트 아이콘](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 46_32x32Project")<br />큰 (32 x 32) 프로젝트 아이콘의 예

### <a name="production-details"></a>프로덕션 세부 정보
 Windows Presentation Foundation (WPF)를 사용 하 여 모든 새 UI 요소를 생성 해야 하 고 WPF에 대 한 모든 새 아이콘은 32 비트 PNG 형식에서 이어야 합니다. 24 비트 PNG은 투명도 지원 하지 않으므로 아이콘에 대 한 권장 되지 하는 레거시 형식입니다.

 96DPI에서 해결을 저장 합니다.

#### <a name="file-types"></a>파일 형식

- **32 비트 PNG:** 아이콘에 대 한 기본 설정된 된 형식입니다. 단일 래스터 (픽셀) 이미지를 저장할 수 있는 무손실 데이터 압축 파일 형식입니다. 32 비트 PNG 파일에는 알파 채널 투명도, 감마 보정 및 인터레이스 지원합니다.

- **32 비트 BMP:** 비 WPF 컨트롤에 대 한 합니다. RGB/A 이미지 형식는 알파 채널 투명도 사용 하 여 true 컬러 이미지를 32 비트 BMP XP 또는 하이 컬러 라고도 합니다. 알파 채널을 사용 하면 다음을 추가 (네 번째)으로 비트맵 내에서 저장 되는 Adobe Photoshop에서 지정 된 투명도 계층이 색 채널입니다. 검은색 배경 색상에 대 한 빠른 시각적 표시를 제공 하는 모든 32 비트 BMP 파일에 아트 워크 프로덕션 중에 추가 됩니다. 이 검은색 배경 영역을 UI에 마스킹되을 나타냅니다.

- **32 비트 ICO:** 프로젝트 아이콘 및 항목을 추가 합니다. 모든 ICO 파일은 32 비트 알파 채널 투명도 사용 하 여 true 색 (RGB/A). ICO 파일 여러 크기와 색 농도 저장할 수 있으므로 Vista 아이콘 16x16, 32x32, 48x48, 256 x 256 이미지 크기 포함 된 ICO 형식이 많습니다. Windows 탐색기에서 제대로 표시를 위해 ICO 파일 해야 수 저장 다운 각 이미지 크기에 대 한 24 비트 및 8 비트 색 농도를 합니다.

- **XAML:** 디자인 화면 및 Windows 표시기 (adorner)에 대 한 합니다. XAML 아이콘은 크기 조정, 회전, 관리 및 투명도 지 원하는 벡터 기반 이미지 파일입니다. 오늘 Visual Studio에서 일반적인 되지 있지만 유연성으로 인해 인기가 점점.

- **SVG**

- **24 비트 BMP:** Visual Studio 명령 모음에 대 한 합니다. True-색 RGB 이미지 형식, 24 비트 BMP는 knock 게임 스케일 아웃 투명도 계층에 대 한 색상 키로 자홍 (R = 255, G = 0, B = 255)를 사용 하 여 계층의 투명도 만드는 아이콘 규칙입니다. 24 비트 BMP, 모든 자홍 표면 배경색을 사용 하 여 표시 됩니다.

- **24 비트 GIF:** Visual Studio 명령 모음에 대 한 합니다. 투명도 지 원하는 한 true 색 RGB 이미지 형식입니다. GIF 파일 마법사 아트 워크 및 GIF 애니메이션에서 자주 사용 됩니다.

### <a name="icon-construction"></a>아이콘 생성
 Visual Studio에서 가장 작은 아이콘 크기는 16 x 16입니다. 가장 일반적인 사용은 32 x 32입니다. 아이콘을 디자인할 때 전체 16x16, 24x24 또는 32 x 32 프레임 찰 필요가 염두에 둡니다. 읽을 수 있고 일관성 아이콘 생성 사용자 인식에 필수적입니다. 아이콘을 작성할 때 다음 사항을 준수 합니다.

- 아이콘은 명확 하 고 이해할 수 있도록 하며 일치 해야 합니다.

- 단일 아이콘으로 상태 알림 요소를 사용 하 고 아이콘 기본 요소를 기반으로 해당 스택 필요가 좋습니다. 특정 컨텍스트에서 UI에는 기본 요소와 연결할 상태 요소가 필요할 수 있습니다.

- 프로젝트 아이콘은 일반적으로 여러 가지 크기를 포함 하는.ico 파일입니다. 16x16, 24x24 및 32x32 크기 아이콘을 업데이트 하는 중입니다. 대부분의 16 x 16 및 24x24 아이콘 같은 요소가 포함 됩니다. 32x32 아이콘 프로젝트 언어 유형에 해당 하는 경우를 비롯 한 자세한 정보를 포함 합니다.

- 32x32 아이콘에 대 한 기본 요소를 일반적으로 경우 2 픽셀 선 두께 세부 정보 요소에 대 한 1 또는 2 픽셀 선 두께 사용할 수 있습니다. 현명한 판단을 더 적합 한 인지 확인 하기 위해 사용 합니다.

- 16 x 16 요소 및 24x24 아이콘 적어도 1 픽셀 간격 경우 32x32 아이콘에 대 한 한정자 및 기본 요소 및 요소 사이의 2 픽셀 간격을 사용 합니다.

  ![16x16, 24x24 및 32x32 크기 아이콘 크기에 대 한 요소 간격](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 47_ElementSpacing")<br />16x16, 24x24 및 32x32 크기 아이콘에 대 한 요소 간격 크기

#### <a name="color-and-accessibility"></a>색 및 내게 필요한 옵션
 Visual Studio 규정 준수 지침 제품에서 모든 아이콘 색과 대비에 대 한 접근성 요구 사항을 전달는 필요 합니다. 아이콘 반전을 통해 얻을 수 고를 디자인할 때 알아야 할 제품에서 프로그래밍 방식으로 반전 됩니다.

 Visual Studio 아이콘의 색을 사용 하 여에 대 한 자세한 내용은 참조 하세요. [이미지에서 색을 사용 하 여](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)입니다.

## <a name="BKMK_UsingColorInImages"></a> 이미지에서 색을 사용 하 여

### <a name="overview"></a>개요
 Visual Studio 아이콘은 주로 단색입니다. 색 특정 정보를 전달 하기 위해 예약 되어 서는 안 장식 합니다. 색이 사용 됩니다.

- 액션을 나타내려면

- 사용자 상태 알림 경고를 발생 시

- 언어 정보를 지정 하려면

- IntelliSense 내의 항목을 구분 하기 위해

### <a name="accessibility"></a>액세스 가능성
 Visual Studio 규정 준수 지침 아이콘을 모두 선택 색과 대비 접근성 요구 사항에 제품 전달에 필요 합니다. 시각적 언어 색상표의 색 거쳤습니다 및 이러한 요구 사항을 충족 합니다.

#### <a name="color-inversion-for-dark-themes"></a>어두운 테마에 대 한 색 반전
 Visual Studio 어두운 테마의 올바른 대비 비율은 표시 아이콘을 만들려면 반전 프로그래밍 방식으로 적용 됩니다. 이 가이드의 색은 올바르게 반전 되도록 일부 선택 된 했습니다. 이 색상표 색의 사용이 제한 또는 반전을 적용 될 때 예기치 않은 결과 얻을 수 있습니다.

 ![해당 색 반전 된 적이 있는 아이콘의 예](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 01_DarkThemeInversion")<br />해당 색 반전 된 적이 있는 아이콘의 예

### <a name="base-palette"></a>기본 색상표
 모든 표준 아이콘 세 가지 기본 색을 포함 합니다. 아이콘 없음 그라데이션을 포함 또는 3D 도구 아이콘에 대 한 하나 또는 두 개의 예외를 사용 하 여 그림자입니다.

|사용|이름|값 (밝은 테마)|견본|예제|
|-----------|----------|---------------------------|------------|-------------|
|배경/어둡게|VS BG|424242 / 66,66,66|![견본 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![기본 색상표 예](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 02_BasePaletteExample")|
|전경/리소스 사용량이 적음|VS FG|F0EFF1 240,239,241 /|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|윤곽선|VS 아웃|F6F6F6 246,246,246 /|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 기본 색을 외에도 각 아이콘 추가 한 확장 된 색상표 색을 포함할 수 있습니다.

### <a name="extended-palette"></a>확장 된 색상표

#### <a name="action-modifiers"></a>작업 한정자
 다음 네 가지 색 작업 한정자에 필요한 동작의 유형을 나타냅니다.

|사용|이름|값 (모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|양수|VS 작업 녹색|388A34 56,138,52 /|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|음수|VS 작업 빨간색|A1260D / 161,38,13|![Swatch A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|중립|VS 작업 파랑|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|/ 새로 만들기|VS 작업 주황색|C27D1A / 194,156,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>예
 녹색 "추가"와 같은 양의 작업 한정자는 "실행" "실행," 및 "유효성 검사 합니다."

|||||
|-|-|-|-|
|![실행 아이콘](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />실행|![쿼리 실행 아이콘](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 04_ExecuteQuery")<br />쿼리 실행|![모든 단계 재생 아이콘](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 05_PlayAllSteps")<br />모든 단계 재생|![컨트롤 추가 아이콘](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 06_AddControl")<br />컨트롤 추가|

 빨간색 "Delete", "중지"와 같은 음수 작업 한정자는 "취소" 및 "닫기"입니다.

|||||
|-|-|-|-|
|![관계 삭제 아이콘](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 07_DeleteRelationship")<br />관계 삭제|![열 삭제 아이콘](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 08_DeleteColumn")<br />열 삭제|![쿼리 중지 아이콘](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 09_StopQuery")<br />쿼리 중지|![라인 연결 상태 아이콘](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 10_ConnectionOffline")<br />오프 라인 연결|

 파란색은 한정자 가장 일반적으로 "열기", "다음" "Previous"와 같은 화살표로 표시 "가져오기" 및 "내보내기" 중립 작업에 적용 됩니다.

|||||
|-|-|-|-|
|![필드 아이콘으로 이동](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 11_GoToField")<br />필드 이동|![확인을 일괄 처리&#45;아이콘에 있는](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 12_BatchedCheckIn")<br />일괄 처리 된 체크인|![주소 편집기 아이콘](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 13_AddressEditor")<br />주소 편집기|![연결 편집기 아이콘](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 14_AssociationEditor")<br />연결 편집기|

 어두운 골드 "New" 한정자에 대 한 주로 사용 됩니다.

|||||
|-|-|-|-|
|![새 프로젝트 아이콘](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 15_NewProject")<br />새 프로젝트|![새 그래프 아이콘 만들기](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 16_CreateNewGraph")<br />새 그래프 만들기|![새 단위 테스트 아이콘](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 17_NewUnitTest")<br />새 단위 테스트|![새 목록 항목 아이콘](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 18_NewListItem")<br />새 목록 항목|

#### <a name="special-cases"></a>특별 한 경우
 특별 한 경우에서 색이 지정 된 작업 한정자를 사용할 수 있습니다 하지 독립적으로 독립 실행형 아이콘으로. 아이콘에 사용 되는 색 아이콘을 사용 하 여 연결 된 작업을 반영 합니다. 이 사용 하이 여 포함 한 아이콘의 작은 하위 집합으로 제한 됩니다.

||||||
|-|-|-|-|-|
|![실행 아이콘](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />실행|![중지 아이콘](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 19_Stop")<br />Stop|![삭제 아이콘](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 20_Delete")<br />삭제|![저장 아이콘](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 21_Save")<br />저장|![뒤로 탐색 아이콘](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 22_NavigateBack")<br />뒤로 탐색|

### <a name="code-hierarchy-palette"></a>코드 계층 색상표

#### <a name="folder"></a>폴더

|사용|이름|값 (모든 테마)|견본|예제|
|-----------|----------|--------------------------|------------|-------------|
|폴더|폴더|DCB67A / 220,182,122|![Swatch DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![폴더 색 아이콘](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio 언어
 각 공용 언어 또는 Visual Studio에서 사용할 수 있는 플랫폼에 연결 된 색을 있습니다. 이러한 색은 기본 아이콘을 또는 복합 아이콘의 오른쪽 위 모서리에 표시 되는 언어 한정자에 사용 됩니다.

|사용|이름|값 (모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF 파랑|0095D 7 0,149,215 /|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP 자주색|9B4F96 155,79,150 /|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS 녹색 (VS 작업 녹색)|388A34 56,138,52 /|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS 빨간색|BD1E2D / 189,30,45|![Swatch BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS 자주색|672878 / 103,40,120|![견본 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS 주황색|F16421 241,100,33 /|![견본 F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB 파란색 (VS 작업 파란색)|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS 주황색|E04C06 / 224,76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY 녹색|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>언어 한정자를 사용 하 여 아이콘의 예

|||||||
|-|-|-|-|-|-|
|![Visual Basic 아이콘](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 25_VB")<br />VB|![C&#35; 아이콘](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 26_CSharp")<br />C#|![C&#43; &#43; 아이콘](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 27_CPlusPlus")<br />C++|![F&#35; 아이콘](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 28_FSharp")<br />F#|![JavaScript 아이콘](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 29_JavaScript")<br />JavaScript|![Python 아이콘](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 30_Python")<br />Python|
|![HTML 아이콘](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 31_HTML")<br />HTML|![WPF 아이콘](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 32_WPF")<br />WPF|![ASP 아이콘](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 33_ASP")<br />ASP|![CSS icon](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript 아이콘](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense 아이콘은 배타적 색 색상표를 사용합니다. 이러한 색은 IntelliSense 팝업 목록에서 여러 항목을 신속 하 게 구분할 수 있도록 하는 데 사용 됩니다.

|사용|이름|값 (모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|이벤트 클래스|VS 작업 주황색|C27D1A / 194,125,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|확장 메서드, 메서드, 모듈, 대리자|VS 작업 자주색|652D90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|필드, 열거형 항목, 매크로, 구조체, 공용 구조체 값 형식, 연산자, 인터페이스|VS 작업 파랑|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS 작업 녹색|388A34 56,138,52 /|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|상수, 예외, 열거형 항목, 맵, 맵 항목, Namespace, 템플릿, 형식 정의|배경 (VS BG)|424242 / 66,66,66|![견본 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense 아이콘의 예

||||||
|-|-|-|-|-|
|![IntelliSense 클래스 아이콘](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 36_IntelliSenseClass")<br />클래스|![IntelliSense private 이벤트 아이콘](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent")<br />Private 이벤트|![IntelliSense 대리자 아이콘](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 38_IntelliSenseDelegate")<br />대리자|![IntelliSense 메서드 친구 아이콘](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend")<br />Friend 메서드|![필드 아이콘](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 40_Field")<br />필드|
|![IntelliSense 보호 열거형 항목 아이콘](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem")<br />보호 된 열거형 항목|![IntelliSense 개체 아이콘](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 42_IntelliSenseObject")<br />Object|![IntelliSense 템플릿 아이콘](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 43_IntelliSenseTemplate")<br />템플릿|![IntelliSense 예외 바로 가기 아이콘](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut")<br />예외 바로 가기||

### <a name="notifications"></a>알림
 Visual Studio의 알림 상태를 나타내는 데 사용 됩니다. 알림 색상표를 검정 또는 흰색 포그라운드 채우기 옵션 뿐만 아니라 다음 네 가지 색을 사용 하 여 다음 상태 수준 사용 하 여 알림을 정의.

|사용|이름|값 (모든 테마)|견본|
|-----------|----------|--------------------------|------------|
|상태: 중립|알림 파란색 (VS 파란색)|1BA1E2 / 27,161,226|![Swatch 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|상태: 긍정|알림 녹색 (VS 녹색)|339933 / 51,153,51|![Swatch 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|상태: 부정|알림 빨간색 (VS 빨간색)|E51400 229,20,0 /|![Swatch E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|상태: 경고|알림 노란색 (VS 주황색)|FFCC00 255,204,0 /|![견본 FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|포그라운드 채우기|알림 검정 (검정)|000000 / 0,0,0|![견본 &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|포그라운드 채우기|알림 허용 (백서)|FFFFFF 255,255,255 /|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>알림 아이콘의 예

|||||
|-|-|-|-|
|![경고 아이콘](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 45_Alert")<br />경고|![경고 아이콘](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 48_Warning")<br />경고|![완료 아이콘](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 46_Complete")<br />완료|![중지 아이콘](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 47_Stop")<br />Stop|

### <a name="visual-studio-online"></a>Visual Studio Online
 일반적으로 Visual Studio Online 기능으로 구성 됩니다 브라우저에 호스트 합니다. 다양 한 환경에서 색 다르지만 스타일 동일 하 게 유지 합니다.

|그룹|사용|이름|값 (모든 테마)|견본|
|-----------|-----------|----------|--------------------------|------------|
|TFS|배경|TFSO BG|656565/ 101, 101, 101|![견본 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|윤곽선|TFSO OUT|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|배경|하얀|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|모나코|배경|하얀|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|배경|하얀|FFFFFF / 255, 255, 255|![견본 FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|일반|F12 Grey_Primary|555555 / 85, 85, 85|![견본 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|가리키기|F12 Blue_Hover|2279BF / 34,121,191|![Swatch 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|사용 안 함|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Swatch ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|가리킨 항목 배경|Hover bg|D9EBF7 217,235,247 /|![Swatch D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|누름된 배경|누름된 bg|B2D7F0 / 178,215,240|![Swatch B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|윤곽선|VS 아웃|F6F6F6 246,246,246 /|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|정보|정보|00BCF2 / 0,188,242|![Swatch 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|경고|경고|F28300 242,131,0 /|![Swatch F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|오류 / 음수|Error_Negative|E81123 232,17,35 /|![Swatch E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|시작 / 양수|Start_Positive|009E49 / 0,158,73|![Swatch 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|광고 유형|광고 유형|9B4F96 155,79,150 /|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|이벤트 표시|이벤트 표시|A51F00 165,31,0 /|![Swatch A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|사용자 표시|사용자 표시|F16220 241,98,32 /|![Swatch F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online 아이콘의 예

|TFS 온라인||||
|----------------|-|-|-|
|![TFS 온라인 팀 아이콘](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 49_TFSOnlineTeam")<br />온라인 팀|![TFS 정보 아이콘](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 50_TFSInformation")<br />정보|![TFS 기록 아이콘](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 51_TFSHistory")<br />기록|![TFS 분기 아이콘](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 52_TFSBranch")<br />분기|

|Napa||||
|----------|-|-|-|
|![Napa 콘텐츠 아이콘](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 53_NapaContent")<br />콘텐츠|![Napa office 메일 아이콘](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 54_NapaOfficeMail")<br />Office 메일|![Napa SharePoint 아이콘](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 55_NapaSharePoint")<br />SharePoint|![Napa 작업 창 아이콘](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 56_NapaTaskPane")<br />작업 창|

|모나코||||
|------------|-|-|-|
|![Monaco 파일 아이콘](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 57_MonacoFiles")<br />파일|![Monaco Git 아이콘](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 58_MonacoGit")<br />Git|![Monaco 검색 아이콘](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 59_MonacoSearch")<br />검색|![Monaco 텍스트 아이콘](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 60_MonacoText")<br />텍스트|

|F12|||
|---------|-|-|
|![F12 깔끔한 코드 아이콘](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 61_F12PrettyCode")<br />깔끔한 코드|![F12 경고 아이콘](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 62_F12Warning")<br />경고|![F12 에뮬레이션 아이콘](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 63_F12Emulate")<br />에뮬레이트|