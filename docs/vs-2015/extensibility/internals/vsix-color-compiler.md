---
title: VSIX 색 컴파일러 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1607ec4863c7e2b21cd69dd57ca4203e3cf4dbf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147940"
---
# <a name="vsix-color-compiler"></a>VSIX 색 컴파일러
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 확장명 색 컴파일러 도구는 기존 Visual Studio 테마에 대 한 색을 나타내는.xml 파일을 사용 하는 콘솔 응용 프로그램 및 변환 하는.pkgdef 파일에 Visual Studio에서 해당 색을 사용할 수 있습니다. .Xml 파일 간의 차이점을 비교 하기가 쉽지 이기 때문에이 도구는 소스 제어에서 사용자 지정 색을 관리 하는 데 유용 합니다. 것도 연결 될 수 있습니다 빌드 환경에 빌드 출력이 잘못.pkgdef 파일을 되도록 합니다.  
  
 **테마 XML 스키마**  
  
 전체 테마.xml 파일은 다음과 같습니다.  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **테마**  
  
 \<테마 > 요소는 전체 테마를 정의 합니다. 테마를 하나 이상 있어야 \<범주 > 요소입니다. 테마 요소는 다음과 같이 정의 됩니다.  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**특성**|**정의**|  
|이름|[필수] 테마의 이름|  
|GUID|[필수] 테마의 GUID (일치 해야 GUID 서식 지정)|  
  
 Visual Studio에 대 한 사용자 지정 색을 만들 때 해당 색 다음 테마에 대 한 정의 해야 합니다. 없는 색은 특정 테마에 존재 하는 경우 Visual Studio에서는 밝은 테마에서 누락 된 색을 로드 하려고 합니다.  
  
|||  
|-|-|  
|**테마 이름**|**테마 GUID**|  
|밝게|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|어둡게|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|파랑|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|고대비|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **범주**  
  
 \<범주 > 요소는 테마의 색의 컬렉션을 정의 합니다. 범주 이름 논리적 그룹화를 제공 및 좁은 최대한으로 정의 해야 합니다. 범주를 하나 이상 있어야 \<색 > 요소입니다. 범주 요소는 다음과 같이 정의 됩니다.  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**특성**|**정의**|  
|이름|[필수] 범주 이름|  
|GUID|[필수] (일치 해야 GUID 서식 지정) 하는 범주 GUID|  
  
 **Color**  
  
 \<색 > 요소는 구성 요소 또는 UI의 상태에 대 한 색을 정의 합니다. 색에 대 한 기본 명명 스키마는 [UI 유형] [State]. 중복 그대로 단어 "색"을 사용 하지 마세요. 요소 형식 및 경우를 "상태" 색을 적용할 색을 명확 하 게 나타내야 합니다. 색 비어 있어야 하며 하나 또는 둘 다 포함 해야 합니다는 \<백그라운드 > 및 \<전경 > 요소입니다. 색 요소는 다음과 같이 정의 됩니다.  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**특성**|**정의**|  
|이름|[필수] 색의 이름|  
  
 **백그라운드 및/또는 포그라운드**  
  
 \<백그라운드 > 및 \<전경 > 요소를 색의 값 및 배경이 나 전경 UI 요소 중 하나에 대 한 형식을 정의 합니다. 이러한 요소에 자식이 없습니다.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**특성**|**정의**|  
|형식|[필수] 형식 색입니다. 다음 중 하나일 수 있습니다.<br /><br /> *CT_INVALID:* 색이 잘못 되었거나 설정 하지 않습니다.<br /><br /> *CT_RAW:* 원시 ARGB 값입니다.<br /><br /> *CT_COLORINDEX:* 사용 하지 마세요.<br /><br /> *CT_SYSCOLOR:* SysColor에서 Windows 시스템 색입니다.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX에서 Visual Studio 색입니다.<br /><br /> *CT_AUTOMATIC:* 자동 색입니다.<br /><br /> *CT_TRACK_FOREGROUND:* 사용 하지 마세요.<br /><br /> *CT_TRACK_BACKGROUND:* 사용 하지 마세요.|  
|Source|[필수] 16 진수에서 표시 색상 값|  
  
 __VSCOLORTYPE 열거에 의해 지원 되는 모든 값 형식 특성에서 스키마에에서 의해 지원 됩니다. 그러나 CT_RAW 및 CT_SYSCOLOR만 사용 하는 것이 좋습니다.  
  
 **모두 함께**  
  
 올바른 테마.xml 파일의 간단한 예는 다음과 같습니다.  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법  
 **구문**  
  
 VsixColorCompiler \<XML 파일 > \<PkgDef 파일 > \<선택적 인수 >  
  
 **인수**  
  
||||  
|-|-|-|  
|**스위치 이름**|**참고**|**필수 또는 선택**|  
|(.Mp 파일) 명명 되지 않은|이 명명 되지 않은 첫 번째 매개 변수 이며 변환할 XML 파일의 경로입니다.|필수|  
|(.Pkgdef 파일) 명명 되지 않은|두 번째 명명 되지 않은 매개 변수 이며 생성 된.pkgdef 파일에 대 한 출력 경로입니다.<br /><br /> 기본값: \<XML 파일 이름 >.pkgdef|Optional|  
|/noLogo|인쇄에서 제품 및 저작권 정보를 중지이 플래그를 설정 합니다.|Optional|  
|/?|도움말 정보를 인쇄 합니다.|Optional|  
|/help|도움말 정보를 인쇄 합니다.|Optional|  
  
 **예제**  
  
- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
- VsixColorCompiler D:\xml\colors.xml /noLogo  
  
## <a name="notes"></a>참고  
  
- 이 도구를 최신 버전의 VC + + 런타임 설치 해야 합니다.  
  
- 단일 파일만 지원 됩니다. 폴더 경로 통해 대량 변환은 지원 되지 않습니다.  
  
## <a name="sample-output"></a>샘플 출력  
 .Pkgdef 파일 도구로 생성 되는 것과 비슷하지만 키 아래:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```
