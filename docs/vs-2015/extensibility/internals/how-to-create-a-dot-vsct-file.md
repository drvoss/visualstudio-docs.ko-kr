---
title: '방법: 만들기는 합니다. Vsct 파일 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158349"
---
# <a name="how-to-create-a-vsct-file"></a>방법: .Vsct 파일 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

XML 기반 Visual Studio 명령 테이블 (.vsct) 구성 파일을 만드는 방법은 여러 가지가 있습니다.  
  
- 새 VSPackage를 만들 수는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 패키지 템플릿.  
  
- 기존.ctc 파일에서 파일을 생성 하려면 XML 기반 명령 테이블 구성 컴파일러 Vsct.exe를 사용할 수 있습니다.  
  
- Vsct.exe를 사용 하 여 기존.cto 파일에서.vsct 파일을 생성할 수 있습니다.  
  
- 수동으로 새.vsct 파일을 만들 수 있습니다.  
  
  이 항목에서는 새.vsct 파일을 수동으로 만드는 방법에 설명 합니다.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>새.vsct 파일을 수동으로 만들려면  
  
1. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 시작합니다.  
  
2. 에 **파일** 메뉴에서 **새로 만들기**를 클릭 하 고 **파일**합니다.  
  
3. 에 **템플릿을** 창 클릭 **XML 파일** 클릭 하 고 **열기**합니다.  
  
4. 에 **뷰** 메뉴에서 클릭 **속성 창** XML 파일의 속성을 표시 합니다.  
  
5. 에 **속성** 창 스키마 속성에서 찾아보기 (...) 단추를 클릭 합니다.  
  
6. XSD 스키마의 목록에서 vsct.xsd 스키마를 선택 합니다. 목록에 없으면 클릭 **추가** 을 로컬 드라이브에 파일을 찾습니다. 클릭 **확인** 완료 되 면 합니다.  
  
7. XML 파일에 입력 `<CommandTable` 탭을 누릅니다. 입력 하 여 태그를 닫을 `>`합니다.  
  
     이 기본.vsct 파일을 만듭니다.  
  
8. 에 따라, 추가 하려는 XML 파일의 요소를 입력 합니다 [VSCT 스키마](../../extensibility/vsct-xml-schema-reference.md)합니다. 자세한 내용은 참조 하세요. [제작 합니다. Vsct 파일](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>코드 컴파일  
 프로젝트에.vsct 파일을 추가 하기만 하면 수행 되지는 컴파일할 수 것입니다. 빌드 프로세스에 통합 해야 합니다.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>프로젝트 컴파일으로.vsct 파일을 추가 하려면  
  
1. 편집기에서 프로젝트 파일을 엽니다. 프로젝트 로드 되 면 먼저 언로드합니다 해야 있습니다.  
  
2. 추가 된 [ItemGroup 요소](../../msbuild/itemgroup-element-msbuild.md) 다음 예와에서 같이 VSCTCompile 요소를 포함 하는 합니다.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 요소 항상로 설정 해야 `Menus.ctmenu`합니다.  
  
3. 프로젝트에.resx 파일에 있으면 다음 예와에서 같이 MergeWithCTO 요소를 포함 하는 포함 리소스 요소를 추가 합니다.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     이 태그는 포함된 리소스를 포함 하는 ItemGroup 요소 내에서 이동 해야 합니다.  
  
4. 이름은 일반적으로 패키지 파일을 엽니다 *ProjectName*Package.cs 또는 *ProjectName*Package.vb, 편집기에서.  
  
5. 다음 예제에서와 같이 패키지 클래스에 ProvideMenuResource 특성을 추가 합니다.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     첫 번째 매개 변수 값은 프로젝트 파일에서 정의한 ResourceName 특성의 값을 일치 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [작성 합니다. Vsct 파일](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [방법: 만들기는 합니다. 기존 Vsct 파일입니다. Ctc 파일](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [방법: 만들기는 합니다. 기존 Vsct 파일입니다. Cto 인 파일](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
