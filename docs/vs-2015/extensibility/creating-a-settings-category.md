---
title: Creating a Settings Category | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d14e60ec28fb5f8ba80f9986c4316058539b35e6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695018"
---
# <a name="creating-a-settings-category"></a>설정 범주 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 Visual Studio 설정 범주를 만들고 값을 저장 하 고 설정 파일에서 값을 복원 하려면 사용 합니다. 설정 범주는 "사용자 지정 설정 지점;"으로 표시 되는 관련된 속성의 그룹 즉,에서 확인란으로는 **가져오기 및 내보내기 설정을** 마법사. (에서 찾을 수 있습니다 합니다 **도구** 메뉴.) 설정 저장 되거나, 범주로 서 복원 되 고 개별 설정 마법사에 표시 되지 않습니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
 파생 시켜 설정 범주를 만들면는 <xref:Microsoft.VisualStudio.Shell.DialogPage> 클래스입니다.  
  
 이 연습을 시작 하려면 먼저 첫 번째 부분을 완료 해야 [옵션 페이지 만들기](../extensibility/creating-an-options-page.md)합니다. 결과 옵션 속성 표를 사용 하 여 검토 하 고 범주에서 속성을 변경할 수 있습니다. 속성 범주를 설정 파일에서을 저장 한 후 속성 값을 저장 하는 방법을 확인 하려면 파일을 검사 합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-settings-category"></a>설정 범주 만들기  
 이 섹션에서는 사용자 지정 설정 지점을 사용 하 여 저장 하 고 설정 범주 변수의 값 복원.  
  
#### <a name="to-create-a-settings-category"></a>설정 범주를 만들려면  
  
1. 완료 합니다 [옵션 페이지 만들기](../extensibility/creating-an-options-page.md)합니다.  
  
2. VSPackage.resx 파일을 열고 이러한 3 개의 문자열 리소스를 추가 합니다.  
  
    |이름|값|  
    |----------|-----------|  
    |106|내 범주|  
    |107|내 설정|  
    |108|OptionInteger 및 OptionFloat|  
  
     그러면 해당 범주 "My Category"는 개체 "My Settings", 이름과 범주 설명을 "OptionInteger 및 OptionFloat" 리소스가 만들어집니다.  
  
    > [!NOTE]
    > 이 세 가지 범주 이름만 설정 가져오기 및 내보내기 마법사에 나타나지 않습니다.  
  
3. MyToolsOptionsPackage.cs, 추가 `float` 라는 속성이 `OptionFloat` 에 `OptionPageGrid` 다음 예와에서 같이 클래스입니다.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    > 합니다 `OptionPageGrid` 범주 이제 "My Category" 라는 두 속성은 이루어져 `OptionInteger` 및 `OptionFloat`합니다.  
  
4. 추가 된 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 에 `MyToolsOptionsPackage` 클래스 및 CategoryName "My Category"를 지정 하 고, ObjectName "My Settings"를 지정 하 고 isToolsOptionPage true로 설정 합니다. 이전에 만든 Id를 해당 문자열 리소스에 categoryResourceID, objectNameResourceID, 및 DescriptionResourceID를 설정 합니다.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 것을 확인할 수 **그리드 페이지 내** 모두 정수 및 부동 소수점 값을 얻었습니다.  
  
## <a name="examining-the-settings-file"></a>설정 파일을 검사합니다.  
 이 섹션에서는 속성 범주 값 설정 파일을 내보냅니다. 파일을 검사 하 고 속성 범주로 다시 값을 가져옵니다.  
  
1. F5 키를 눌러 디버그 모드에서 프로젝트를 시작 합니다. 실험적 인스턴스에서 시작 됩니다.  
  
2. 엽니다는 **도구 / 옵션** 대화 합니다.  
  
3. 왼쪽 창의 트리 뷰에서 확장 **My Category** 을 클릭 한 다음 **그리드 페이지 내**합니다.  
  
4. 값을 변경 **OptionFloat** 3.1416입니다 하 고 **OptionInteger** 12입니다. **확인**을 클릭합니다.  
  
5. **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택합니다.  
  
     합니다 **설정 가져오기 및 내보내기** 마법사가 나타납니다.  
  
6. 했는지 **선택한 환경 설정 내보내기** 를 선택한 다음 클릭 **다음**합니다.  
  
     합니다 **내보낼 설정 선택** 페이지가 나타납니다.  
  
7. 클릭 **내 설정**합니다.  
  
     합니다 **설명을** 변경 **OptionInteger 및 OptionFloat**합니다.  
  
8. 했는지 **내 설정** 를 선택한 다음 클릭 하는 유일한 범주가 **다음**합니다.  
  
     합니다 **설정 파일 이름** 페이지가 나타납니다.  
  
9. 새 설정 파일의 이름을 `MySettings.vssettings` 적절 한 디렉터리에 저장 합니다. **마침**을 클릭합니다.  
  
     합니다 **내보내기 완료** 페이지 보고 설정을 내보냈습니다.  
  
10. 에 **파일** 메뉴에서 **열려**를 클릭 하 고 **파일**합니다. 찾을 `MySettings.vssettings` 엽니다.  
  
     (사용자 Guid 다릅니다) 파일의 다음 섹션에서 내보낸 된 속성 범주를 찾을 수 있습니다.  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     개체 이름 뒤에 범주 이름에 밑줄 추가 하 여 전체 범주 이름이 형성 되도록 확인 합니다. OptionFloat 및 OptionInteger 범주에는 내보낸된 값과 함께 표시 됩니다.  
  
11. 설정 파일을 변경 하지 않고 닫습니다.  
  
12. 에 **도구** 메뉴에서 클릭 **옵션**를 확장 **My Category**, 클릭 **그리드 페이지 내** 값을 변경한 후  **OptionFloat** 1.0 및 **OptionInteger** 1입니다. **확인**을 클릭합니다.  
  
13. 에 **도구** 메뉴에서 클릭 **설정 가져오기 및 내보내기**를 선택 **선택한 환경 설정 가져오기**를 클릭 하 고 **다음**합니다.  
  
     합니다 **현재 설정 저장** 페이지가 나타납니다.  
  
14. 선택 **아니요, 새 설정을 가져와** 을 클릭 한 다음 **다음**합니다.  
  
     합니다 **가져올 설정 모음 선택** 페이지가 나타납니다.  
  
15. 선택 합니다 `MySettings.vssettings` 파일을 **내 설정** 트리 뷰의 노드. 파일 트리 보기에서 나타나지 않으면, 클릭 **찾아보기** 찾을. **다음**을 클릭합니다.  
  
     합니다 **가져오기 설정 선택** 대화 상자가 나타납니다.  
  
16. 했는지 **내 설정** 를 선택한 다음 클릭 **마침**합니다. 경우는 **전체 가져오기** 페이지에 표시 되 면 클릭 **닫기**합니다.  
  
17. 에 **도구** 메뉴에서 클릭 **옵션**를 확장 **My Category**, 클릭 **그리드 페이지 내** 속성 범주 값이 있는지 확인 복원 되었습니다.
