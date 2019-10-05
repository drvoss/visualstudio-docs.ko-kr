---
title: 메뉴 명령 지역화 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62c6011d1a04b60d1bd0cc538e9560d8977f9799
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344665"
---
# <a name="localize-menu-commands"></a>메뉴 명령 지역화
지역화 된 만들어 메뉴 및 도구 모음 명령에 대 한 지역화 된 텍스트를 제공할 수 있습니다 *.vsct* 파일과 지역화 *.resx* 통합 하기 위해 VSPackage를 및 프로젝트 파일을 업데이트 한 다음 파일을 변경 내용입니다.

 설치 환경이 지역화 하는 방법에 대 한 정보를 참조 하세요 [지역화 VSIX 패키지](../extensibility/localizing-vsix-packages.md)합니다.

## <a name="localize-command-names"></a>명령 이름을 지역화합니다
 Vspackage에서 메뉴 명령 및 도구 모음 단추에 정의 되어는 *.vsct* 파일입니다.

1. **솔루션 탐색기**의 이름을 변경 합니다 *.vsct* 에서 파일 *filename.vsct* 에 *filename.en US.vsct*합니다.

2. 복사본을 만듭니다 *filename.en US.vsct* 각각에 대 한 지역화 된 언어입니다.

    각 복사본의 이름을 *파일 이름입니다. { 로캘}.vsct*, 여기서 *{로캘}* 특정 문화권 이름입니다. 문화권 이름 값의 목록을 참조 하세요 [Locale IDs assigned by Microsoft](/windows/uwp/publish/supported-languages)합니다.

    이러한 *파일 이름입니다. Locale.vsct* 파일 패키지에 대 한 지역화 된 메뉴 텍스트가 포함 됩니다.

3. 각 열 *파일 이름입니다. Locale.vsct* 텍스트를 지역화할 파일입니다.

   1. 수정 된 [ButtonText](../extensibility/buttontext-element.md) 값 요소는 해당 언어에 적합 하 게 합니다.

   2. 지역화 된 아이콘을 제공 하는 경우 수정 합니다 [비트맵](../extensibility/bitmap-element.md) 대상 파일을 가리키도록 값입니다.

      다음 예제에서는 패밀리 트리 탐색기 도구 창을 열려면 명령에 대 한 영어와 스페인어 단추 텍스트를 보여 줍니다.

      [*FamilyTree.en-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>

   ```

## <a name="localize-other-text-resources"></a>다른 텍스트 리소스를 지역화 합니다.
 명령 이름 이외의 텍스트 리소스는 리소스에서 정의 ( *.resx*) 파일입니다.

1. 이름 바꾸기 *VSPackage.resx* 하 *VSPackage.en US.resx*합니다.

2. 복사본을 *VSPackage.en US.resx* 파일 각각에 대 한 지역화 된 언어입니다.

     각 복사본의 이름을 *VSPackage. { 로캘}.resx*, 여기서 *{로캘}* 특정 문화권 이름입니다.

3. 이름 바꾸기 *Resources.resx* 하 *저장할 US.resx*합니다.

4. 복사본을 *저장할 US.resx* 파일 각각에 대 한 지역화 된 언어입니다.

     각 복사본의 이름을 *리소스입니다. { 로캘}.resx*, 여기서 *{로캘}* 특정 문화권 이름입니다.

5. 각 엽니다 *.resx* 파일 문자열을 수정 하는 특정 언어 및 문화권에 적합 하 게 값입니다. 다음 예제에서는 도구 창의 제목 표시줄에 대 한 지역화 된 리소스 정을 보여 줍니다.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>

    ```

## <a name="incorporate-localized-resources-into-the-project"></a>프로젝트에 지역화 된 리소스를 통합
 수정 해야 합니다 *assemblyinfo.cs* 파일과 지역화 된 리소스를 통합 하기 위해 프로젝트 파일입니다.

1. **속성** 노드에서 **솔루션 탐색기**엽니다 *assemblyinfo.cs* 또는 *assemblyinfo.vb* 편집기에서.

2. 다음 항목을 추가 합니다.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     이 설정 된 기본 언어로 영어 (미국) 합니다.

3. 프로젝트를 언로드하십시오.

4. 편집기에서 프로젝트 파일을 엽니다.

5. 찾을 합니다 `ItemGroup` 포함 하는 요소 `EmbeddedResource` 요소입니다.

6. 에 `EmbeddedResource` 를 호출 하는 요소 *VSPackage.en US.resx*, 대체를 `ManifestResourceName` 요소를 `LogicalName` 로 설정 하는 요소 `VSPackage.en-US.Resources`같이 합니다.

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

7. 각 지역화 된 언어에 대 한 복사를 `EmbeddedResource` 요소에 대 한 `VsPackage.en-US`를 설정 합니다 **포함** 특성 및 **LogicalName** 요소 다음에 표시 된 대로 대상 로캘로 복사본 예입니다.

8. 지역화 된 각 `VSCTCompile` 요소를 추가 `ResourceName` 가리키는 요소의 `Menus.ctmenu`다음 예제에서와 같이 합니다.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

9. 프로젝트 파일을 저장 하 고 프로젝트를 다시 로드 합니다.

10. 프로젝트를 빌드합니다.

     이 주 어셈블리와 각 언어에 대 한 리소스 어셈블리를 만듭니다. 배포 프로세스를 지역화에 대 한 정보를 참조 하세요. [지역화 VSIX 패키지](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>참고자료
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [Menucommand 및 OleMenuCommand](../extensibility/menucommands-vs-olemenucommands.md)
- [전역화 및 지역화 응용 프로그램](../ide/globalizing-and-localizing-applications.md)