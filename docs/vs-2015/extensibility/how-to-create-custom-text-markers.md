---
title: '방법: 사용자 지정 텍스트 표식 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435978"
---
# <a name="how-to-create-custom-text-markers"></a>방법: 사용자 지정 텍스트 표식 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

강조 하거나 코드를 구성할 사용자 지정 텍스트 마커를 만들려는 경우 다음 단계를 수행 해야 합니다.  
  
- 다른 도구에서 액세스할 수 있도록 새 텍스트 표식에 등록  
  
- 텍스트 마커의 구성과 기본 구현을 제공 합니다.  
  
- 확인 하려면 다른 프로세스에서 사용할 수 있는 서비스 만들기 텍스트 마커에 사용  
  
  텍스트 마커 코드 영역에 적용 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 텍스트 마커를 사용 하 여](../extensibility/how-to-use-text-markers.md)입니다.  
  
### <a name="to-register-a-custom-marker"></a>사용자 지정 마커를 등록 하려면  
  
1. 다음과 같이 레지스트리 항목을 만듭니다.  
  
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* \Text Editor\External Markers\\ *\<MarkerGUID>*  
  
    <em>\<MarkerGUID ></em>되는 `GUID` 추가할 마커를 식별 하는 데 사용  
  
    *\<버전 >* 의 버전이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 예를 들어 8.0  
  
    *\<PackageGUID >* 자동화 개체를 구현 하는 VSPackage의 GUID입니다.  
  
   > [!NOTE]
   > 루트 경로의 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<버전 >* 자세한 내용은 Visual Studio 셸이 초기화 될 때를 대체 루트로 재정의할 수 있습니다 [명령줄 스위치](../extensibility/command-line-switches-visual-studio-sdk.md)합니다.  
  
2. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 아래 4 개의 값을 만듭니다\\ *\<버전 >* \Text Editor\External 표식\\ *\<MarkerGUID >*  
  
   - (기본값)  
  
   - 서비스  
  
   - DisplayName  
  
   - Package  
  
   - `Default` REG_SZ 형식의 선택적 항목이입니다. 항목의 값에 몇 가지 유용한 식별 정보, 예를 들어 "사용자 지정 텍스트 표식"를 포함 하는 문자열은 설정 된 경우.  
  
   - `Service` proffering 하 여 사용자 지정 텍스트 마커를 제공 하는 서비스의 GUID 문자열이 포함 된 REG_SZ 형식의 항목은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>합니다. 형식은 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}입니다.  
  
   - `DisplayName` 사용자 지정 텍스트 마커의 이름의 리소스 ID 포함 된 REG_SZ 형식의 항목입니다. 형식은 #YYYY입니다.  
  
   - `Package` 형식 REG_SZ 포함 하는 항목이 `GUID` 서비스 아래에 나열 된 서비스를 제공 하는 VSPackage의 합니다. 형식은 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}입니다.  
  
### <a name="to-create-a-custom-text-marker"></a>사용자 지정 텍스트 마커를 만들려면  
  
1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 인터페이스를 구현합니다.  
  
     이 인터페이스의 구현에 사용자 지정 표식 유형의 모양과 동작을 정의합니다.  
  
     이 인터페이스는 때 호출 됩니다.  
  
    1. 사용자는 처음으로 IDE를 시작 합니다.  
  
    2. 사용자가 선택 합니다 **기본값 재설정** 단추를 **글꼴 및 색** 속성 페이지에서를 **환경** 의 왼쪽된 창에 있는 폴더를는  **옵션** 대화 상자에서 가져온 합니다 **도구** IDE의 메뉴.  
  
2. 구현 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> 메서드를 지정 하는 `IVsPackageDefinedTextMarkerType` 구현 해야 기반으로 반환 될 표식 유형을 메서드 호출에 지정 된 GUID입니다.  
  
     환경에 사용자 지정 표식 유형을 작성 되 고 사용자 지정 표식 유형을 식별 하는 GUID를 지정 합니다.이 메서드는 첫 번째 시간을 호출 합니다.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>서비스로 사용자 표식 유형을 제공합니다  
  
1. 호출 된 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> 에 대 한 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>합니다.  
  
     에 대 한 포인터 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 반환 됩니다.  
  
2. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> 메서드를 사용자 지정 표식 유형 서비스를 식별 하 고 구현에 대 한 포인터를 제공 하는 GUID를 지정 하는 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 인터페이스. 프로그램 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 구현은 구현에 대 한 포인터를 반환 해야 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> 인터페이스입니다.  
  
     서비스를 식별 하는 고유한 쿠키 반환 됩니다. 나중에이 쿠키를 호출 하 여 사용자 지정 표식 유형 서비스를 취소 하는 데 사용할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 이 쿠키 값을 지정 하는 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [텍스트 마커를 사용 하 여 레거시 API를 사용 하 여](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 표준 텍스트 마커를 추가 합니다.](../extensibility/how-to-add-standard-text-markers.md)   
 [방법: 오류 마커를 구현 합니다.](../extensibility/how-to-implement-error-markers.md)   
 [방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)
