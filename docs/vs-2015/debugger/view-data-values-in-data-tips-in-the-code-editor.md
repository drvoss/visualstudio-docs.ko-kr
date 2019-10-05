---
title: 코드 편집기에서 데이터 팁의 데이터 값 보기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700102"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>코드 편집기에서 데이터 팁의 데이터 값 보기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataTips를 통해 디버깅하는 동안 프로그램의 변수에 대한 정보를 손쉽게 볼 수 있습니다. DataTips는 중단 모드에서 현재 실행 범위 내의 변수에 대해서만 작동합니다.  
  
 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]DataTips를 소스 파일 내의 특정 위치에 고정할 수 있습니다, 또는 모두를 기반으로 부동 상태로 있을 수 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>DataTip을 표시하려면(중단 모드에서만)  
  
1. 소스 창에서 현재 범위에 있는 변수 위에 마우스 포인터를 놓습니다.  
  
    DataTips가 나타납니다.  
  
   > [!NOTE]
   > DataTip은 커서가 가리키고 있는 컨텍스트가 아니라 실행이 일시 중단된 컨텍스트에서 항상 평가됩니다. 현재 컨텍스트에 있는 변수와 이름이 같은 또 다른 함수의 변수를 가리키는 경우 다른 함수의 변수 값이 현재 컨텍스트의 변수 값으로 표시됩니다.  
  
2. 마우스 포인터를 제거하면 DataTip이 사라집니다. 파일을 열린 상태로 유지 됩니다 있도록 DataTip을 고정 하려면 클릭 합니다 **소스에 고정** 아이콘 또는  
  
   - 변수를 마우스 오른쪽 단추로 클릭 **소스에 고정**합니다.  
  
     고정된 DataTip은 디버깅 세션이 종료될 때 닫힙니다.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>DataTip의 고정을 해제하고 다른 위치에 배치하려면  
  
- 고정 된 DataTip을 클릭 합니다 **소스에서 고정 해제** 아이콘입니다.  
  
     고정 아이콘이 고정 해제된 위치로 변경됩니다. 이제 DataTip이 열린 창 위에 배치됩니다. 부동 DataTip은 디버깅 세션이 종료될 때 닫힙니다.  
  
### <a name="to-repin-a-floating-datatip"></a>부동 DataTip을 다시 고정하려면  
  
- DataTip에서 고정 아이콘을 클릭합니다.  
  
     고정 아이콘이 고정된 위치로 바뀝니다. DataTip이 소스 창 밖에 있으면 고정 아이콘을 사용할 수 없으며 DataTip을 고정할 수 없습니다.  
  
### <a name="to-close-a-datatip"></a>DataTip을 닫으려면  
  
- 마우스 포인터를 DataTip 위에 놓고 클릭 합니다는 **닫기** 아이콘입니다.  
  
### <a name="to-close-all-datatips"></a>모든 DataTips를 닫으려면  
  
- 에 **디버그** 메뉴에서 클릭 **모든 DataTips 지우기**합니다.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>특정 파일에 대한 모든 DataTips를 닫으려면  
  
- 에 **디버그** 메뉴에서 클릭 **지우기 모든에 고정 된 DataTips** *파일*합니다.  
  
## <a name="expanding-and-editing-information"></a>정보 확장 및 편집  
 DataTips를 사용하면 배열, 구조체 또는 개체를 확장하여 해당 멤버를 볼 수 있습니다. DataTips에서 변수 값을 편집할 수도 있습니다.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>변수를 확장하여 해당 요소를 보려면  
  
- DataTip에서 위에 마우스 포인터를 놓고 합니다 **+** 변수 이름 앞에 오는 로그인 합니다.  
  
     변수가 확장되어 해당 요소가 트리 형태로 표시됩니다.  
  
     변수가 확장되면 키보드의 화살표 키를 사용하여 위아래로 이동할 수 있습니다. 또는 마우스를 사용할 수 있습니다.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>DataTip을 사용하여 변수 값을 편집하려면  
  
1. DataTip에서 값을 클릭합니다. 읽기 전용 값에는 사용할 수 없습니다.  
  
2. 새 값을 입력하고 Enter 키를 누릅니다.  
  
## <a name="making-a-datatip-transparent"></a>DataTips 투명하게 만들기  
 DataTip 뒤에 있는 코드를 보려면 DataTip을 임시로 투명하게 만듭니다. 고정 또는 부동 DataTips에는 적용되지 않습니다.  
  
#### <a name="to-make-a-datatip-transparent"></a>DataTips를 투명하게 만들려면  
  
- DataTip에서 Ctrl 키를 누릅니다.  
  
     Ctrl 키를 누르고 있는 동안에는 DataTip이 투명한 상태로 유지됩니다.  
  
## <a name="visualizing-complex-data-types"></a>복잡한 데이터 형식 시각화  
 하나 이상의 DataTip에서 변수 이름 옆에 돋보기 모양 아이콘이 나타나면 [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md) 해당 데이터 형식의 변수에 사용할 수 있습니다. 시각화 도우미를 사용하면 정보를 더 의미 있는 방식(대개 그래픽 방식)으로 표시할 수 있습니다.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>시각화 도우미를 사용하여 변수의 내용을 보려면  
  
- 돋보기 아이콘을 클릭하고 데이터 형식에 대한 기본 시각화 도우미를 선택합니다.  
  
     또는  
  
     시각화 도우미 옆의 팝업 화살표를 클릭하고 시각화 도우미 목록에서 데이터 형식에 적절한 시각화 도우미를 선택합니다.  
  
     시각화 도우미가 정보를 표시합니다.  
  
## <a name="adding-information-to-a-watch-window"></a>조사식 창에 정보 추가  
 변수 조사를 계속 하려는 경우에 변수를 추가할 수 있습니다 합니다 **조사식** DataTip에서 창입니다.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>조사식 창에 변수를 추가하려면  
  
- DataTip을 마우스 오른쪽 단추로 누른 **조사식 추가**합니다.  
  
     추가할 변수를 **조사식** 창. 여러를 지 원하는 버전을 사용 하는 경우 **조사식** windows 변수의 추가할 **조사식 1입니다.**  
  
## <a name="importing-and-exporting-datatips"></a>DataTips 가져오기 및 내보내기  
 DataTips를 XML 파일로 내보내서 동료와 공유하거나 텍스트 편집기를 사용하여 편집할 수 있습니다.  
  
#### <a name="to-export-datatips"></a>DataTips를 내보내려면  
  
1. 디버그 메뉴에서 클릭 **DataTips 내보내기**합니다.  
  
     합니다 **DataTips 내보내기** 대화 상자가 나타납니다.  
  
2. 표준 파일 기술을 사용 하 여 파일의 이름을 입력 XML 파일을 저장 하려는 위치로 이동 합니다 **파일 이름** 상자를 선택한 다음 클릭 **확인**합니다.  
  
#### <a name="to-import-datatips"></a>DataTips를 가져오려면  
  
1. 디버그 메뉴에서 클릭 **DataTips 가져오기**합니다.  
  
     합니다 **DataTips 가져오기** 대화 상자가 나타납니다.  
  
2. 대화 상자를 사용 하 여 열고 클릭 하려는 XML 파일을 찾습니다 **확인**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)   
 [방법: 간략 한 조사식 대화 상자를 사용 합니다.](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md)   
 [방법: 디버거 Windows의 숫자 형식 변경](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
