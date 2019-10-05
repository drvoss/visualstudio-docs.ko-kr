---
title: VSIX 프로젝트 템플릿 시작 하기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc3f461c9e7dbdea1fd8481594292a0a247d2173
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204293"
---
# <a name="getting-started-with-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 프로젝트 템플릿 확장을 만들거나 기존 확장 프로그램 배포에 대 한 패키지를 사용할 수 있습니다. VSIX 프로젝트 템플릿에는 Visual Basic 및 Visual C# 버전 및 Visual Studio SDK의 일부로 설치 됩니다.  
  
 VSIX 프로젝트 템플릿 확장에 대 한 정보를 포함 하는 source.extension.vsixmanifest 파일을 제공 하는 자산만 구성 됩니다.  
  
 VSIX 프로젝트 템플릿을 찾으려면 Visual Studio SDK를 설치 해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>VSIX 프로젝트 템플릿을 사용 하 여 사용자 지정 프로젝트 템플릿 배포  
 다음 단계를 다른 개발자와 공유 하거나 Visual Studio 갤러리에 업로드할 수 있는 프로젝트 템플릿을 패키지 하려면 VSIX 프로젝트를 사용 하는 방법을 보여 줍니다.  
  
1. 프로젝트 템플릿을 만듭니다.  
  
    1. 템플릿을 만드는 데 사용할 프로젝트를 엽니다. 이 프로젝트의 프로젝트 형식일 수 있습니다.  
  
    2. **파일** 메뉴에서 **템플릿 내보내기**를 클릭합니다. 마법사의 단계를 완료 합니다.  
  
         %USERPROFILE%\My Documents\Visual Studio에서에서.zip 파일을 만들  *\<버전 >* \My Exported Templates\\합니다.  
  
2. 빈 VSIX 프로젝트를 만듭니다.  
  
     **파일** 메뉴에서 **새로 만들기** 를 클릭한 다음 **프로젝트**를 클릭합니다. 선택 **Visual Basic** 하거나 **Visual C#** 합니다. 선택한 노드를 선택 **확장성**를 선택한 후 **VSIX 프로젝트**합니다.  
  
3. .Zip 파일을 프로젝트에 추가 합니다. 설정 해당 **출력 디렉터리로 복사** 속성을 `Copy Always`입니다.  
  
4. 에 **솔루션 탐색기**, 두 번 클릭 합니다 `source.extension.vsixmanifest` 에서 열려는 파일을 **VSIX 매니페스트 디자이너**, 다음 다음과 같이 변경 하 고:  
  
    - 설정 된 **Product Name** 필드를 **내 프로젝트 템플릿을**합니다.  
  
    - 설정 된 **제품 ID** 필드를 **MyProjectTemplate-1**합니다.  
  
    - 설정 된 **작성자** 필드를 **Fabrikam**합니다.  
  
    - 설정 된 **설명을** 필드를 **내 프로젝트 템플릿을**합니다.  
  
    - 에 **자산** 섹션에서 추가 **Microsoft.VisualStudio.ProjectTemplate** 입력 하 고.zip 파일의 이름으로 해당 경로 설정 합니다.  
  
5. 저장 하 고 source.extension.vsixmanifest 파일을 닫습니다.  
  
6. 프로젝트를 빌드합니다.  
  
7. 출력 디렉터리의.vsix 파일을 두 번 클릭 합니다.  
  
8. A **VSIX 설치 관리자** 메시지 상자가 나타납니다. 확장을 설치 하려면 지침을 따릅니다.  
  
9. Visual Studio를 닫고 다시 엽니다.  
  
10. 선택 **확장 및 업데이트** (에 **도구** 메뉴) 선택 합니다 **템플릿** 범주. 사용 가능한 확장 중 하나 **내 프로젝트 템플릿을**합니다.  
  
11. 새 프로젝트 템플릿이 표시 합니다 **새 프로젝트** 원래 프로젝트 템플릿으로 동일한 위치에서 대화 합니다. 예를 들어 명명 템플릿을 만든 경우 **VB 콘솔** Visual Basic 콘솔 응용 프로그램에서 **VB 콘솔** Visual Basic의 경우 동일한 창에 나타납니다 **콘솔 응용 프로그램**템플릿.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에서 서식 파일의 위치를 지정 합니다.  
  
1. 템플릿 폴더에 위치한 합니다 *Visual Studio 설치 경로*\Common7\IDE\ProjectTemplates 및 *Visual Studio 설치 경로*\Common7\IDE\ItemTemplates 디렉터리입니다. 새 프로젝트 대화 상자에서 최상위 섹션의 이름을 템플릿 폴더의 이름을 일치 정확 하지 않습니다. 다른 템플릿 폴더의 이름을 사용 합니다.  
  
     .Vsix 파일 확장명을.zip으로 변경 하 고 파일을 엽니다.  
  
2. 새 프로젝트 대화 상자에 템플릿이 나타납니다 섹션과 동일한 이름의 새 폴더를 만듭니다.  
  
3. 템플릿을 하위 섹션에 표시 하려는 경우, 동일한 이름의 하위 폴더를 만듭니다.  
  
4. 템플릿.zip 파일을 새 폴더로 이동 합니다.  
  
5. .Vsix를.zip 확장명을 변경 합니다.  
  
6. VSIX 매니페스트를 엽니다.  
  
7. VSIX 매니페스트를 업데이트 합니다 **자산** 한다는 템플릿 파일이 포함 된 디렉터리 트리의 루트를 가리키는 있도록 템플릿의 경로입니다. 예를 들어 템플릿을 \CSharp\Windows에 대 한 참조 \CSharp를 가리켜야 합니다.
