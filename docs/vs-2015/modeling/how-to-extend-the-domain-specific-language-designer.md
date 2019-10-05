---
title: '방법: 도메인 특정 언어 디자이너 확장 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8c02dbf550ca1621a17d2b674a522e1e4f4bcc1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546943"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>방법: 도메인 특정 언어 디자이너 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 정의 편집 하는 데 사용 하는 디자이너에 확장을 만들 수 있습니다. 가능 메뉴 명령을 추가 끌어서 제스처 및 특정 형식의 값 또는 관계 변경 될 때 트리거되는 규칙을 두 번 클릭에 대 한 처리기를 추가 하는 확장의 형식입니다. 확장으로 Visual Studio 통합 확장 (VSIX)를 패키지 하 고 다른 사용자에 게 배포할 수 있습니다.  
  
 샘플 코드 및이 기능에 대 한 자세한 내용은 Visual Studio [Visualization and Modeling SDK (VMSDK) 웹 사이트](http://go.microsoft.com/fwlink/?LinkID=186128)합니다.  
  
## <a name="setting-up-the-solution"></a>솔루션 설정  
 확장 프로그램의 코드를 포함 하는 프로젝트 및 프로젝트를 내보내는 VSIX 프로젝트를 설정 합니다. 솔루션이 동일한 VSIX에 통합 된 다른 프로젝트를 포함할 수 있습니다.  
  
#### <a name="to-create-a-dsl-designer-extension-solution"></a>DSL 디자이너 확장 솔루션을 만들려면  
  
1. 클래스 라이브러리 프로젝트 템플릿을 사용 하 여 새 프로젝트를 만듭니다. 에 **새 프로젝트** 대화 상자, 클릭 **Visual C#** 하 고 클릭 한 다음 가운데 창에서 **클래스 라이브러리**합니다.  
  
     이 프로젝트에는 확장 코드가 포함 됩니다.  
  
2. VSIX 프로젝트 템플릿을 사용 하 여 새 프로젝트를 만듭니다. 에 **새 프로젝트** 대화 상자에서 **Visual C#**, 클릭 **확장성**를 선택한 다음 가운데 창의 선택 **VSIX 프로젝트**합니다.  
  
     선택 **솔루션을 추가할**합니다.  
  
     Source.extension.vsixmanifest은 VSIX 매니페스트 편집기에서 열립니다.  
  
3. 콘텐츠 필드 위에 클릭 **콘텐츠 추가**합니다.  
  
4. 에 **콘텐츠 추가** 대화 상자에서 **콘텐츠 형식 선택** 하 **MEF 구성 요소**, 설정 및 **프로젝트** 클래스 라이브러리 프로젝트에.  
  
5. 클릭 **버전 선택** 했는지 **Visual Studio Enterprise** 확인란이 선택 되어 있습니다.  
  
6. VSIX 프로젝트를 솔루션의 시작 프로젝트 인지 확인 합니다.  
  
7. 클래스 라이브러리 프로젝트에서 다음 어셈블리에 대 한 참조를 추가 합니다.  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## <a name="testing-and-deployment"></a>테스트 및 배포  
 확장을이 항목의 테스트를 빌드하고 솔루션을 실행 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 실험적 인스턴스가 열립니다. 이 인스턴스에서 DSL 솔루션을 엽니다. DslDefinition 다이어그램을 편집 합니다. 확장 동작을 볼 수 있습니다.  
  
 확장을 배포 하는 기본 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 다른 컴퓨터에 다음이 단계를 수행 합니다.  
  
1. Bin의 VSIX 프로젝트에 VSIX 설치 파일을 찾거나\\*\*\\\*.vsix  
  
2. 대상 컴퓨터에이 파일을 복사 하 고 Windows 탐색기 (또는 파일 탐색기)에서 두 번 클릭 합니다.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장이 설치 되어 있는지 확인 하려면 확장 관리자가 열립니다.  
  
   확장을 제거 하려면 다음이 단계를 수행 합니다.  
  
3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 **도구** 메뉴에서 클릭 **확장 관리자**합니다.  
  
4. 확장을 선택 하 여 삭제 합니다.  
  
## <a name="adding-a-shortcut-menu-command"></a>바로 가기 메뉴 명령 추가  
 바로 가기 메뉴 명령 또는 DSL 탐색기 창에서 DSL 디자이너 화면에 표시 되도록 다음과 비슷한 클래스를 작성 합니다.  
  
 클래스를 구현 해야 합니다 `ICommandExtension` 특성이 있어야 하 고 `DslDefinitionModelCommandExtension`입니다.  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## <a name="handling-mouse-gestures"></a>마우스 제스처를 처리합니다.  
 코드 메뉴 명령의 코드와 비슷합니다.  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## <a name="responding-to-value-changes"></a>값이 변경에 응답  
 이 처리기는 제대로 작동 하려면 도메인 모델을 해야 합니다. 간단한 도메인 모델을 제공합니다.  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 다음 코드는 간단한 모델을 구현합니다. 새 GUID 자리 표시자를 만듭니다.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```
