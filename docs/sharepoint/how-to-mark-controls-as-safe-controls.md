---
title: '방법: 안전한 컨트롤로 표시 제어 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30bb597288c19328bb71ce7b5212200991d7181e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443082"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>방법: 안전한 컨트롤로 표시 컨트롤
  보안을 위해 SharePoint가 없는 웹 컨트롤과 웹 컨트롤 스크립트 삽입에 대해 보호 되는 구분 됩니다. 컨트롤을 보호 하거나 *안전 컨트롤*, 신뢰할 수 없는 사용자가 액세스할 수 있습니다. SharePoint 프로젝트 항목의 또는 안전 컨트롤 항목 속성에 안전 하 게 컨트롤을 표시할 수 있습니다 합니다 **패키지 디자이너** 패키지에 어셈블리를 추가 합니다. 자세한 내용은 다음 항목을 참조하세요.

- [web.config 파일 설정 변경](http://go.microsoft.com/fwlink/?LinkId=178965) 하 고 [웹 파트 어셈블리를 안전 컨트롤로 등록](http://go.microsoft.com/fwlink/?LinkId=171013)합니다.

> [!IMPORTANT]
> 이러한 프로시저는 설명 목적으로 합니다. 표시 제어 안전 하다는 확신 하는 경우에 안전 합니다.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>안전 컨트롤 항목 속성에서 안전 컨트롤 표시

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>안전 또는 안전 컨트롤 항목 속성에서 안전 하지 않은 컨트롤 표시 하려면

1. 비주얼 웹 파트 프로젝트를 사용 하 여 SharePoint 솔루션을 만듭니다.

2. 웹 파트 컨트롤 두 개를 추가 합니다: 텍스트 상자와 단추입니다. 각각 이름을 기본값으로, TextBox1과 Button1을 둡니다.

3. 웹 파트의 두 항목을 추가할 **안전 컨트롤 항목** 속성입니다. 이렇게 하려면 줄임표를 선택 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추 옆에 **안전 컨트롤 항목** 합니다 에서속성 **속성** 창입니다.

     합니다 **안전 컨트롤 항목** 대화 상자가 나타납니다.

4. 에 **안전 컨트롤 항목** 대화 상자를 선택 합니다 **추가** 단추 두 안전 컨트롤 항목을 추가 하려면 두 번를 **멤버** 창: 단추 및 텍스트 상자에 대 한 하나.

5. 첫 번째 안전 컨트롤 항목을 선택 하 고 변경한 다음의 값을 해당 **안전한** 속성을 **False**, 해당 **형식 이름** 속성을 **Button1**, 및 해당 **스크립트에 대해 안전** 속성을 **False**합니다.

     이 단계는 안전 하지 않은 컨트롤로 단추 컨트롤을 식별합니다.

6. 목록에서 두 번째 안전 컨트롤 항목을 선택합니다. 값을 지정 하지 해당 **안전** 속성으로 **True** 설정 하 고 해당 **형식 이름** 속성을 **TextBox1** 고 **안전 스크립트에 대해** 속성을 **True**합니다.

     텍스트 상자 컨트롤 스크립트 삽입에 대 한 안전한 컨트롤로 표시 됩니다.

7. **확인** 단추를 선택하여 대화 상자를 닫습니다.

## <a name="marking-safe-controls-in-the-package-designer"></a>패키지 디자이너에서 안전 컨트롤 표시

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>안전 또는 패키지 디자이너에서 안전 하지 않은 컨트롤 표시 하려면

1. 비주얼 웹 파트 프로젝트를 사용 하 여 SharePoint 솔루션을 만듭니다.

2. 웹 파트 컨트롤 두 개를 추가 합니다: 텍스트 상자와 단추입니다. 각각 이름을 기본값으로, TextBox1과 Button1을 둡니다.

     나중에 사용 되 고 있으므로 컨트롤의 네임 스페이스를 기록해 둡니다.

3. 메뉴 모음에서 선택 **빌드합니다** > **솔루션 빌드** 프로젝트를 빌드합니다.

4. 다른 SharePoint 솔루션을 만듭니다.

5. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 *Package.Package* 파일을 선택한 후 **엽니다** 열려는 **패키지 디자이너**.

6. 에 **패키지 디자이너**를 선택 합니다 **고급** 탭 합니다.

7. 아래 **추가 어셈블리**를 선택 합니다 **추가** 단추를 선택한 후 **기존 어셈블리 추가** 목록에서.

8. 에 **기존 어셈블리 추가** 대화 상자에서 줄임표 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추 옆에  **소스 경로**합니다.

9. 1 단계에서에서 만든 SharePoint 솔루션에서 어셈블리를 선택 하 고 선택 합니다 **열고** 단추입니다.

10. 예를 들어 유지 합니다 **배포 대상** GlobalAssemblyCache 옵션입니다.

     이 단계를 수행 하면 어셈블리를 시스템 전역 어셈블리 캐시 (GAC)에 배포 합니다. 웹 응용 프로그램 (Bin) 폴더에 배포 되도록 어셈블리를 하려는 경우 해당 옵션을 대신 선택 합니다. 자세한 내용은 [SharePoint Foundation에서 웹 파트 배포](http://go.microsoft.com/fwlink/?LinkId=177509)합니다.

11. 에 **안전 컨트롤** 상자를 선택 합니다 **새 항목을 추가 하려면 여기를 클릭 하십시오.** 단추.

12. 다음 표에서 속성에 대 한 값을 입력 합니다.

    |속성 이름|값|
    |-------------------|-----------|
    |네임스페이스|컨트롤에 대 한 정규화 된 네임 스페이스와 같은 **BdcModelProject1.VisualWebPart1**합니다.|
    |형식 이름|Button1|
    |어셈블리 이름|강력한 어셈블리 이름, 예: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |안전 하 게 보호|선택을 취소 합니다 **안전한** 확인란 합니다.|
    |스크립트에 대해 안전|유지 된 **스크립트에 대해 안전** 확인란의 선택을 취소 합니다.|

    > [!NOTE]
    > **어셈블리 이름** 를 통해 추가 된 어셈블리에 대 한 값을 **고급** 탭을 **패키지 디자이너** 수 없습니다 토큰 일 이어야 합니다는 강력한 이름의 어셈블리. 자세한 내용은 [강력한 이름의 어셈블리 만들기 및 사용](http://go.microsoft.com/fwlink/?LinkId=177513)을 참조하세요.

13. 선택 된 **탭** 키 다른 안전 컨트롤 항목을 만들어야 합니다.

14. 선택 된 **새 항목을 추가 하려면 여기를 클릭 하십시오.** 단추를 다시 합니다.

15. 다음 표에서 속성에 대 한 값을 입력 합니다.

    |속성 이름|값|
    |-------------------|-----------|
    |네임스페이스|컨트롤에 대 한 정규화 된 네임 스페이스와 같은 **BdcModelProject1.VisualWebPart1**합니다.|
    |형식 이름|TextBox1|
    |어셈블리 이름|강력한 어셈블리 이름, 예: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |안전 하 게 보호|선택 된 **안전한** 확인란 합니다.|
    |스크립트에 대해 안전|선택 된 **스크립트에 대해 안전** 확인란 합니다.|

16. 선택 된 **탭** 키를 선택한 후 합니다 **확인** 대화 상자를 닫으려면 단추를 합니다.

## <a name="see-also"></a>참고자료
- [프로젝트 항목에 패키징 및 배포 정보를 제공 합니다.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
