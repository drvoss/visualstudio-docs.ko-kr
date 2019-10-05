---
title: '새 프로젝트 생성: 내부적으로 1 부 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a657c59cba31ea48298179a41ab1024a0b7e948f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326622"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>새 프로젝트 생성: 내부 살펴보기, 1부
고유의 프로젝트 형식을 만드는 방법에 대 한 생각 적이 있습니까? 새 프로젝트를 만들 때 실제로 무엇이 발생 궁금해? 살펴보기 해 실제로 그럴까요 참조 보겠습니다.

 Visual Studio를 조정 하는 작업을 여러 가지가 있습니다.

- 모든 사용 가능한 프로젝트 형식 트리의 표시 됩니다.

- 각 프로젝트 형식에 대 한 응용 프로그램 템플릿 목록을 표시 하 고 하나를 선택할 수 있습니다.

- 프로젝트 이름 및 경로 등과 같은 응용 프로그램에 대 한 프로젝트 정보를 수집합니다.

- 프로젝트 팩터리에이 정보를 전달합니다.

- 현재 솔루션의 프로젝트 항목 및 폴더를 생성합니다.

## <a name="the-new-project-dialog-box"></a>새 프로젝트 대화 상자
 모든 새로운 프로젝트의 프로젝트 형식을 선택 하면 시작 됩니다. 클릭 하 여 시작 해 보겠습니다 **새 프로젝트** 에 **파일** 메뉴. 합니다 **새 프로젝트** 대화 상자가 나타나면 다음과 같이 결과 보기:

 ![새 프로젝트 대화 상자](../../extensibility/internals/media/newproject.gif "NewProject")

 좀 더 자세히 살펴보겠습니다. 합니다 **프로젝트 형식** 트리에 나열 다양 한 프로젝트 형식을 만들 수 있습니다. 같은 프로젝트 형식을 선택 하면 **시각적 C# Windows**를 시작 하기 위한 응용 프로그램 템플릿 목록이 표시 됩니다. **Visual Studio 설치 된 템플릿** Visual Studio가 설치 되어 있고 컴퓨터의 모든 사용자에 게 제공 됩니다. 만들거나 수집 하는 새 템플릿을 추가할 수 있습니다 **내 템플릿** 되며에 사용할 수 있습니다.

 과 같은 템플릿을 선택 하면 **Windows 응용 프로그램**,이 경우 대화 상자에 응용 프로그램 유형의 설명이 나타납니다 **Windows 사용자 인터페이스를 사용 하 여 응용 프로그램을 만드는 프로젝트입니다.** 합니다.

 맨 아래에 **새 프로젝트** 대화 상자에서 자세한 정보를 수집 하는 여러 컨트롤이 표시 됩니다. 표시 컨트롤 프로젝트 형식에 따라 달라 지지만 일반적으로 프로젝트를 포함 **이름을** 텍스트 상자에는 **위치** 텍스트 상자 및 관련 **찾아보기** 단추 및를 **솔루션 이름** 텍스트 상자 및 관련 **솔루션용 디렉터리 만들기** 확인란 합니다.

## <a name="populating-the-new-project-dialog-box"></a>새 프로젝트 대화 상자 채우기
 여기서는 합니다 **새 프로젝트** 대화 상자에서 해당 정보를 가져오도록? 작업 여기에서 사용 되지 않는 그 중 하나에 두 가지 메커니즘이 있습니다. 합니다 **새 프로젝트** 대화 상자를 결합 하 고 두 메커니즘에서 가져온 정보를 표시 합니다.

 시스템 레지스트리 항목 및.vsdir 파일을 사용 하는 이전 (사용 되지 않음된) 됩니다. 이 메커니즘에는 Visual Studio를 열 때 실행 됩니다. .Vstemplate 파일을 사용 하는 새로운 방법입니다. Visual Studio 초기화 될 때, 예를 들어, 실행 하 여이 메커니즘에서 실행

```
devenv /setup
```

 또는

```
devenv /installvstemplates
```

### <a name="project-types"></a>프로젝트 형식
 이름과 위치를 **프로젝트 형식** 같은 루트 노드의 **Visual C#** 하 고 **다른 언어**, 시스템 레지스트리 항목에 따라 결정 됩니다. 자식 노드를 구성와 같은 **데이터베이스** 하 고 **스마트 장치**, 해당.vstemplate 파일을 포함 하는 폴더 계층 구조를 반영 합니다. 루트 노드 먼저 살펴보겠습니다.

#### <a name="project-type-root-nodes"></a>프로젝트 유형 루트 노드
 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 은 시스템 레지스트리 키를 빌드하고의 루트 노드 이름을 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs의 하위 키를 통과할 초기화는 **프로젝트 형식** 트리. 이 정보는 나중에 사용할 캐시 됩니다. TemplateDirs 살펴봅니다\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 키입니다. 각 항목에는 VSPackage GUID입니다. 하위 키의 이름 (/ 1)가 무시 되 존재 여부에 따라 임을 나타냅니다는 **프로젝트 형식** 루트 노드. 루트 노드가 있을 수의 모양을 제어 하는 몇 가지 하위 키를 **프로젝트 형식** 트리. 그 중 일부에 대해 살펴보겠습니다.

##### <a name="default"></a>(기본값)
 루트 노드 이름을 지정 하는 지역화 된 문자열의 리소스 ID입니다. 문자열 리소스는 위성 DLL VSPackage GUID가 선택한에 있습니다.

 VSPackage GUID의 예

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 루트 노드의 리소스 ID (기본값) 및 (/ 1)은 #2345

 주변 패키지 키의 GUID를 조회 하 여 SatelliteDll 하위 키를 검사 하는 경우에 문자열 리소스를 포함 하는 어셈블리의 경로 찾을 수 있습니다.

 \<Visual Studio 설치 경로 > \VC#\VCSPackages\1033\csprojui.dll

 이 확인 하려면 파일 탐색기를 열고 csprojui.dll Visual Studio 디렉터리로 끌어... 문자열 테이블 리소스 #2345 캡션이 보여 줍니다 **Visual C#** 합니다.

##### <a name="sortpriority"></a>SortPriority
 루트 노드는 위치를 결정 합니다 **프로젝트 형식** 트리.

 SortPriority REG_DWORD 0x00000014 (20)

 수가 작을수록 더 낮은 우선 순위를 트리에서 높을수록 위치 합니다.

##### <a name="developeractivity"></a>DeveloperActivity
 이 하위 키가 있는 경우 루트 노드의 위치를 개발자 설정 대화 상자에서 제어 됩니다. 예를 들면 다음과 같습니다.

 DeveloperActivity REG_SZVC#

 나타냅니다 Visual C# 루트 노드에 대해 Visual Studio 설정 된 경우 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 개발 합니다. 그렇지 않으면 자식 노드의 됩니다 **다른 언어**합니다.

##### <a name="folder"></a>폴더
 이 하위 키가 있는 경우 루트 노드에 지정된 된 폴더의 자식 노드가 됩니다. 키에서 가능한 폴더 목록이 표시 됩니다.

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 예를 들어, 데이터베이스 프로젝트 항목에는 PseudoFolders 기타 프로젝트 형식 항목을 일치 하는 폴더 키에 있습니다. 따라서 합니다 **프로젝트 형식** 트리에서 **데이터베이스 프로젝트** 자식 노드의 됩니다 **기타 프로젝트 형식**합니다.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>프로젝트 형식 자식 노드와.vstdir 파일
 에 있는 자식 노드의 위치를 **프로젝트 형식** 트리 ProjectTemplates 폴더에서 폴더 계층 구조를 따릅니다. 머신 템플릿에 (**Visual Studio 설치 된 템플릿**), 일반적인 위치는 files\microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ 사용자 템플릿 (**내템플릿**), 일반적인 위치는 documents\visual Studio 14.0\Templates\ProjectTemplates\\합니다. 이 두 위치에서 폴더 계층을 만들려면 병합 되는 **프로젝트 형식** 트리.

 C# 개발자 설정 사용 하 여 Visual Studio에 대 한 합니다 **프로젝트 형식** 트리를 사용 하면 다음과 같은 모양의:

 ![프로젝트 형식](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 해당 ProjectTemplates 폴더는 다음과 같습니다.

 ![프로젝트 템플릿](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 경우는 **새 프로젝트** 대화 상자가 열리고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ProjectTemplates 폴더를 트래버스하 고 해당 구조를 다시 만듭니다는 **프로젝트 형식** 일부 변경 내용 사용 하 여 트리:

- 루트 노드를 **프로젝트 형식** 트리는 응용 프로그램 템플릿에 의해 결정 됩니다.

- 노드 이름을 지역화할 수 및 특수 문자를 포함할 수 있습니다.

- 정렬 순서를 변경할 수 있습니다.

##### <a name="finding-the-root-node-for-a-project-type"></a>프로젝트 형식에 대 한 루트 노드 찾기
 Visual Studio ProjectTemplates 폴더 이동, 모든.zip 파일을 엽니다 및.vstemplate 파일을 추출 합니다. .Vstemplate 파일을 응용 프로그램 템플릿을 설명 하기 위해 XML을 사용 합니다. 자세한 내용은 참조 하세요. [새 프로젝트 생성: 내부적으로 2 부](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)합니다.

 \<ProjectType > 태그에는 응용 프로그램에 대 한 프로젝트 형식을 결정 합니다. 예를 들어 \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 파일에는이 태그를 가진 EmptyProject.vstemplate 파일을 포함 됩니다.

```
<ProjectType>CSharp</ProjectType>
```

 합니다 \<ProjectType > 태그 및 없습니다 ProjectTemplates 폴더의 하위 폴더의 응용 프로그램의 루트 노드를 결정 합니다 **프로젝트 형식** 트리. 예제에서는 Windows CE 응용 프로그램 아래에 표시 됩니다는 **Visual C#** 루트 노드 및 VisualBasic 폴더로 WindowsCE 폴더를 이동 하려는 경우에 Windows CE 응용 프로그램이 여전히 아래에 표시 됩니다는  **Visual C#** 루트 노드입니다.

##### <a name="localizing-the-node-name"></a>노드 이름 지역화
 Visual Studio ProjectTemplates 폴더 트래버스를 찾으면 모든.vstdir 파일을 검사 합니다. .Vstdir 파일은 프로젝트 형식의 모양을 제어 하는 XML 파일을 **새 프로젝트** 대화 상자. .Vstdir 파일을 사용 합니다 \<LocalizedName > 태그 이름에는 **프로젝트 형식** 노드.

 예를 들어 \CSharp\Database\TemplateIndex.vstdir 파일에는이 태그 포함 됩니다.

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 이 경우 루트 노드 이름을 지정 하는 지역화 된 문자열의 위성 DLL 및 리소스 ID를 결정 **데이터베이스**합니다. 지역화 된 이름을 사용할 수 없는 폴더 이름에 대해 같은 특수 문자를 포함할 수 있습니다 **.NET**합니다.

 없으면 \<LocalizedName > 태그를 사용할 수 있는지, 프로젝트 형식 자체 폴더 이름은 **SmartPhone2003**합니다.

##### <a name="finding-the-sort-order-for-a-project-type"></a>프로젝트 형식에 대 한 정렬 순서를 찾기
 프로젝트 형식의 정렬 순서를 확인 하려면.vstdir 파일 사용을 \<SortOrder > 태그입니다.

 예를 들어 \CSharp\Windows\Windows.vstdir 파일에는이 태그 포함 됩니다.

```
<SortOrder>5</SortOrder>
```

 \CSharp\Database\TemplateIndex.vstdir 파일에 더 큰 값을 가진 태그가 있습니다.

```
<SortOrder>5000</SortOrder>
```

 에 낮은 숫자가 합니다 \<SortOrder > 태그, 트리에서 높을수록 위치 하므로 **Windows** 노드 보다 위에 표시를 **데이터베이스** 에서 노드를 **프로젝트 형식**  트리.

 없으면 \<SortOrder > 프로젝트 형식에 대해 포함 하는 모든 프로젝트 형식에 따라 사전순으로 표시 하는 태그를 지정 \<SortOrder > 사양입니다.

 내 문서에는 없는.vstdir 파일이 있습니다 (**내 템플릿**) 폴더입니다. 사용자 응용 프로그램 프로젝트 형식 이름 지역화 되지 및 사전순으로 표시 합니다.

#### <a name="a-quick-review"></a>빠른 검토
 수정 해 보겠습니다 합니다 **새 프로젝트** 대화 상자 및 새 사용자 프로젝트 템플릿 만들기.

1. \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp 폴더로 MyProjectNode 하위 폴더를 추가 합니다.

2. 임의의 텍스트 편집기를 사용 하 여 MyProjectNode 폴더에 MyProject.vstdir 파일을 만듭니다.

3. .Vstdir 파일에 다음이 줄을 추가 합니다.

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. 저장 하 고.vstdir 파일을 닫습니다.

5. 임의의 텍스트 편집기를 사용 하 여 MyProjectNode 폴더에 MyProject.vstemplate 파일을 만듭니다.

6. .Vstemplate 파일에 다음이 줄을 추가 합니다.

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. The.vstemplate 파일을 저장 하 고 편집기를 닫습니다.

8. 압축된 된 새 MyProjectNode\MyProject.zip 폴더에.vstemplate 파일을 보냅니다.

9. Visual Studio 명령 창에서 다음을 입력 합니다.

    ```
    devenv /installvstemplates
    ```

   Visual Studio를 엽니다.

10. 열기는 **새 프로젝트** 대화 상자 및 확장을 **Visual C#** 프로젝트 노드.

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** 는 Windows 노드 바로 아래 Visual C#의 자식 노드로 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [새 프로젝트 생성: 내부 살펴보기, 2부](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)