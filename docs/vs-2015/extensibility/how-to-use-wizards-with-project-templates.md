---
title: '방법: 프로젝트 템플릿에 마법사 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8722cc2990f91446c806bf80f3673dc4c941532
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432553"
---
# <a name="how-to-use-wizards-with-project-templates"></a>방법: 프로젝트 템플릿에 마법사 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서는 사용자가 템플릿을 사용하여 프로젝트를 만들 때 사용자 지정 코드를 실행할 수 있도록 설정하여 구현 시 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스를 제공합니다.  
  
 프로젝트 템플릿 사용자 지정 프로젝트 템플릿을 사용자 지정 파일을 템플릿에 추가할를 입력 하는 사용자 또는 허용 하는 다른 작업을 수집 하는 사용자 지정 UI를 표시 하려면 사용할 수 있습니다.  
  
 합니다 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 프로젝트를 만드는 동안에 사용자가 즉시 시작 인터페이스 메서드는 여러 번 호출 됩니다 **확인** 에 **새 프로젝트** 대화 상자. 인터페이스의 각 메서드는 호출 되는 지점을 설명에 지정 됩니다. 예를 들어, Visual Studio 호출 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 시작 되 면 프로젝트를 만들려면, 즉시 쉽게 사용자 입력을 수집 하는 사용자 지정 코드를 작성 하기 위한 좋은 위치입니다.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>VSIX 프로젝트를 사용 하 여 프로젝트 템플릿 만들기  
 사용 하 여 프로젝트 템플릿 프로젝트를 Visual Studio SDK의 일부인 사용자 지정 템플릿 만들기를 시작 하기. 이 절차에서는 사용 하 여 C# 프로젝트 템플릿 프로젝트를 하지만 Visual Basic 프로젝트 템플릿 수도 있습니다. 그런 다음 프로젝트 서식 파일 프로젝트가 포함 된 솔루션에 VSIX 프로젝트를 추가 합니다.  
  
1. C# 프로젝트 템플릿 프로젝트 만들기 (Visual Studio에서 **파일 / 새로 만들기 / 프로젝트 / Visual C# / 확장성 / C# 프로젝트 템플릿**). 이름을 **MyProjectTemplate**합니다.  
  
    > [!NOTE]
    > Visual Studio SDK를 설치 하 라는 메시지가 표시 될 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
2. 새 VSIX 프로젝트를 추가 (**파일 / 새로 만들기 / 프로젝트 / Visual C# / 확장성 / VSIX 프로젝트**) 프로젝트 템플릿 프로젝트와 동일한 솔루션에서 (에 **솔루션 탐색기**, 솔루션 노드를 선택 마우스 오른쪽 단추로 **추가 / 새로 만들기 프로젝트**). 이름을 **MyProjectWizard 합니다.**  
  
3. VSIX 프로젝트를 시작 프로젝트로 설정 합니다. 에 **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 선택 **시작 프로젝트로 설정**합니다.  
  
4. VSIX 프로젝트의 자산으로 서식 파일 프로젝트를 추가 합니다. 에 **솔루션 탐색기**, VSIX 프로젝트 노드 아래에 **source.extension.vsixmanifest** 파일입니다. 이 두 번 클릭 하 여 매니페스트 편집기에서 엽니다.  
  
5. 매니페스트 편집기에서 선택 합니다 **자산** 창의 왼쪽에 탭 합니다.  
  
6. 에 **자산** 탭을 선택 **새로 만들기**합니다. 에 **새 자산 추가** Type 필드에 대 한 창 **Microsoft.VisualStudio.ProjectTemplate**합니다. 에 **소스** 필드를 선택한 **현재 솔루션의 프로젝트**합니다. 에 **프로젝트** 필드를 선택한 **MyProjectTemplate**합니다. 그런 다음 **확인**을 클릭합니다.  
  
7. 솔루션을 빌드하고 디버깅을 시작합니다. 두 번째 Visual Studio 인스턴스가 표시됩니다. (몇 분 정도 걸릴 수 있습니다.)  
  
8. Visual Studio의 두 번째 인스턴스의 경우에서 새 템플릿을 사용 하 여 새 프로젝트를 만들려고 시도 합니다. (**파일 / 새로 만들기 / 프로젝트 / Visual C# / MyProject 템플릿**). 라는 클래스를 사용 하 여 새 프로젝트가 표시 됩니다 **Class1**합니다. 이제 사용자 지정 프로젝트 템플릿을 만들었습니다! 지금 디버깅을 중지 합니다.  
  
## <a name="creating-a-custom-template-wizard"></a>사용자 지정 템플릿 마법사 만들기  
 이 항목에는 프로젝트를 만들기 전에 Windows 폼을 사용자 지정 마법사를 만드는 방법을 보여 줍니다. 폼을 사용 하면 프로젝트를 만드는 동안 소스 코드에 추가 되는 사용자 지정 매개 변수 값을 추가할 수 있습니다.  
  
1. 어셈블리를 만들 수 있도록 하려면 VSIX 프로젝트를 설정 합니다.  
  
2. 에 **솔루션 탐색기**, VSIX 프로젝트 노드를 선택 합니다. 솔루션 탐색기 아래 표시 된 **속성** 창입니다. 이렇게 하지 않으면 경우 선택 **보기 / 속성 창**를 누르거나 **F4**합니다. 속성 창에서 다음 필드를 선택 `true`:  
  
   - **IncludeAssemblyInVSIXContainer**  
  
   - **IncludeDebugSymbolsInVSIXContainer**  
  
   - **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3. VSIX 프로젝트에 자산으로 어셈블리를 추가 합니다. Source.extension.vsixmanifest 파일을 열고 선택 합니다 **자산** 탭 합니다. 에 **새 자산 추가** 창에 대 한 **유형** 선택 **Microsoft.VisualStudio.Assembly**에 대 한 **원본** 선택 **는 현재 솔루션의 프로젝트**, 및 **프로젝트** 선택 **MyTemplateWizard**합니다.  
  
4. VSIX 프로젝트에 다음 참조를 추가 합니다. (에 **솔루션 탐색기**, VSIX에서 프로젝트 노드 선택 **참조**를 마우스 오른쪽 단추로 **참조 추가**.) 에 **참조 추가** 대화의를 **프레임 워크** 탭, 찾기는 **System.Windows Forms** 어셈블리 선택 합니다. 이제 선택 된 **확장** 탭 찾기는 **EnvDTE** 어셈블리 선택 합니다. 찾을 수도 합니다 **Microsoft.VisualStudio.TemplateWizardInterface** 어셈블리를 선택 합니다. **확인**을 클릭합니다.  
  
5. 마법사 구현에 대 한 클래스를 VSIX 프로젝트를 추가 합니다. (솔루션 탐색기에서 VSIX 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 선택 **추가**, 한 다음 **새 항목**, 한 다음 **클래스**.) 클래스의 이름을 **WizardImplementation**합니다.  
  
6. 코드를 대체 합니다 **WizardImplementationClass.cs** 를 다음 코드로 파일:  
  
   ```csharp  
   using System;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.TemplateWizard;  
   using System.Windows.Forms;  
   using EnvDTE;  
  
   namespace MyProjectWizard  
   {  
       public class WizardImplementation:IWizard  
       {  
           private UserInputForm inputForm;  
           private string customMessage;  
  
           // This method is called before opening any item that   
           // has the OpenInEditor attribute.  
           public void BeforeOpeningFile(ProjectItem projectItem)  
           {  
           }  
  
           public void ProjectFinishedGenerating(Project project)  
           {  
           }  
  
           // This method is only called for item templates,  
           // not for project templates.  
           public void ProjectItemFinishedGenerating(ProjectItem   
               projectItem)  
           {  
           }  
  
           // This method is called after the project is created.  
           public void RunFinished()  
           {  
           }  
  
           public void RunStarted(object automationObject,  
               Dictionary<string, string> replacementsDictionary,  
               WizardRunKind runKind, object[] customParams)  
           {  
               try  
               {  
                   // Display a form to the user. The form collects   
                   // input for the custom message.  
                   inputForm = new UserInputForm();  
                   inputForm.ShowDialog();  
  
                   customMessage = UserInputForm.CustomMessage;  
  
                   // Add custom parameters.  
                   replacementsDictionary.Add("$custommessage$",   
                       customMessage);  
               }  
               catch (Exception ex)  
               {  
                   MessageBox.Show(ex.ToString());  
               }  
           }  
  
           // This method is only called for item templates,  
           // not for project templates.  
           public bool ShouldAddProjectItem(string filePath)  
           {  
               return true;  
           }          
       }  
   }  
   ```  
  
    합니다 **된 userinputform은** 이 참조 코드는 나중에 구현 됩니다.  
  
    합니다 `WizardImplementation` 클래스의 모든 멤버에 대 한 메서드 구현을 포함 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>합니다. 이 예제에서는는 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 메서드 작업을 수행 합니다. 다른 모든 메서드 또는 아무 작업도 수행 하지 반환 `true`합니다.  
  
    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 메서드는 4 개의 매개 변수:  
  
   - <xref:System.Object> 루트에 캐스팅할 수 있는 매개 변수 <xref:EnvDTE._DTE> 개체 프로젝트를 사용자 지정할 수 있도록 합니다.  
  
   - <xref:System.Collections.Generic.Dictionary%602> 템플릿에서 미리 정의 된 모든 매개 변수의 컬렉션을 포함 하는 매개 변수입니다. 템플릿 매개 변수에 대 한 자세한 내용은 참조 하세요. [템플릿 매개 변수](../ide/template-parameters.md)합니다.  
  
   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> 서식 파일의 종류를 사용 하는 방법에 대 한 정보를 포함 하는 매개 변수입니다.  
  
   - <xref:System.Object> Visual Studio에서 마법사에 전달 된 매개 변수 집합을 포함 하는 배열입니다.  
  
     사용자 입력된 폼에서 매개 변수 값을 추가 하는이 예제는 <xref:System.Collections.Generic.Dictionary%602> 매개 변수입니다. 모든 인스턴스는 `$custommessage$` 프로젝트의 매개 변수를 사용자가 입력 한 텍스트를 사용 하 여 바뀝니다. 프로젝트에 다음 어셈블리를 추가해야 합니다.  
  
7. 이제 만들 합니다 **된 userinputform은**합니다. 에 **WizardImplementation.cs** 파일, 종료 된 후 다음 코드를 추가 합니다 **WizardImplementation** 클래스.  
  
   ```csharp  
   public partial class UserInputForm : Form  
       {  
           private static string customMessage;  
           private TextBox textBox1;  
           private Button button1;  
  
           public UserInputForm()  
           {  
               this.Size = new System.Drawing.Size(155, 265);   
  
               button1 = new Button();  
               button1.Location = new System.Drawing.Point(90, 25);  
               button1.Size = new System.Drawing.Size(50, 25);  
               button1.Click += button1_Click;  
               this.Controls.Add(button1);  
  
               textBox1 = new TextBox();  
               textBox1.Location = new System.Drawing.Point(10, 25);  
               textBox1.Size = new System.Drawing.Size(70, 20);  
               this.Controls.Add(textBox1);  
           }  
           public static string CustomMessage  
           {  
               get  
               {  
                   return customMessage;  
               }  
               set  
               {  
                   customMessage = value;  
               }     
           }  
           private void button1_Click(object sender, EventArgs e)  
           {  
               customMessage = textBox1.Text;  
           }  
       }  
   ```  
  
    사용자 입력된 폼을 사용자 지정 매개 변수를 입력 하는 것에 대 한 간단한 양식을 제공 합니다. 라는 텍스트 상자를 포함 하는 폼 `textBox1` 이라는 단추가 `button1`합니다. 입력란의 텍스트에 저장 됩니다 단추를 클릭할 때는 `customMessage` 매개 변수입니다.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>마법사 사용자 지정 템플릿에 연결  
 사용자 지정 마법사를 사용 하 여 사용자 지정 프로젝트 템플릿에 대 한 순서 대로 마법사 어셈블리를 서명 하 고 새 프로젝트를 만들 때 마법사 구현을 찾을 수 있는 위치를 알 수 있도록 사용자 지정 프로젝트 템플릿에 일부 줄을 추가 해야 합니다.  
  
1. 어셈블리에 서명 합니다. 에 **솔루션 탐색기**를 선택 하 고 VSIX 프로젝트를 마우스 오른쪽 단추를 선택 **프로젝트 속성**합니다.  
  
2. 에 **프로젝트 속성** 창에서를 **서명** 탭에는 **서명** 탭 **어셈블리에 서명 합니다**. 에 **강력한 이름 키 파일 선택** 필드를 선택한  **\<새로 만들기 >** 합니다. 에 **강력한 이름 키 만들기** 창에서 합니다 **키 파일 이름** 필드에 입력 **key.snk**합니다. 선택 취소 합니다 **암호로 내 키 파일 보호** 필드입니다.  
  
3. 에 **솔루션 탐색기**VSIX 프로젝트를 선택 하 고 찾기, 합니다 **속성** 창.  
  
4. 설정 된 **복사 빌드 출력에 출력 디렉터리** 필드를 **true**합니다. 이 어셈블리를 솔루션이 다시 빌드될 때 출력 디렉터리로 복사할 수 있습니다. .Vsix 파일에 여전히 포함 되어 있습니다. 해당 서명 키를 알기 위해 어셈블리를 참조 해야 합니다.  
  
5. 솔루션을 다시 빌드합니다.  
  
6. 이제 key.snk 파일로 MyProjectWizard 프로젝트 디렉터리에 있습니다 ( **\<디스크 위치 > \MyProjectTemplate\MyProjectWizard\key.snk**). Key.snk 파일로 복사 합니다.  
  
7. 출력 디렉터리로 이동 하 고 어셈블리를 찾습니다 ( **\<디스크 위치 > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). 여기에 key.snk 파일을 붙여 넣습니다. (반드시 필요 하지 않습니다 하지만는 다음 단계를 쉽게 가져옵니다.)  
  
8. 명령 창을 열고 있는 어셈블리를 만든 디렉터리로 변경 합니다.  
  
9. 찾을 합니다 **sn.exe** 도구를 서명 합니다. 예를 들어, Windows 10 64 비트 운영 체제에서 일반적인 경로 다음과 같습니다.  
  
     **C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools**  
  
     도구를 찾을 수 없는 경우 실행 **여기서 /R 합니다.  sn.exe** 명령 창에 있습니다. 경로 기록해 둡니다.  
  
10. Key.snk 파일에서 공개 키를 추출 합니다. 명령 창에 입력  
  
     **\<sn.exe의 위치 > \sn.exe-p key.snk outfile.key 합니다.**  
  
     디렉터리 이름에 공백이 있는 경우 따옴표로 sn.exe의 경로를 두는 것을 잊지 마세요!  
  
11. Outfile는에서 공개 키를 토큰을 가져옵니다.  
  
     **\<sn.exe의 위치 > \sn.exe-t outfile.key 합니다.**  
  
     다시 따옴표를 잊지 마십시오. 다음과 같은 출력에 줄을 표시 됩니다.  
  
     **공개 키 토큰은 \<토큰 >**  
  
     이 값을 기록해 둡니다.  
  
12. 프로젝트 템플릿의.vstemplate 파일에 사용자 지정 마법사에 대 한 참조를 추가 합니다. 솔루션 탐색기에서 MyProjectTemplate.vstemplate, 라는 파일을 찾을 하 여 엽니다. 종료 된 후의 \<TemplateContent > 섹션에서 다음 섹션을 추가 합니다.  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     여기서 **MyProjectWizard** 어셈블리의 이름 및 **토큰** 이전 단계에서 복사한 토큰입니다.  
  
13. 프로젝트의 모든 파일을 저장 하 고 다시 빌드하십시오.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>템플릿에 사용자 지정 매개 변수를 추가합니다.  
 이 예제에서는 프로젝트를 템플릿으로 사용 되는 사용자 지정 마법사의 사용자 입력된 폼에서 지정 된 메시지를 표시 합니다.  
  
1. 솔루션 탐색기에서로 이동 합니다 **MyProjectTemplate** 프로젝트를 열고 **Class1.cs**합니다.  
  
2. 에 `Main` 응용 프로그램의 메서드는 다음 코드 줄을 추가 합니다.  
  
   ```  
   Console.WriteLine("$custommessage$");  
   ```  
  
    매개 변수 `$custommessage$` 템플릿에서 프로젝트를 만들 때 사용자 입력된 폼에 입력 된 텍스트로 바뀝니다.  
  
   템플릿으로 내보내기 전에 전체 코드 파일을 다음과 같습니다.  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>사용자 지정 마법사를 사용 하 여  
 이제 템플릿에서 프로젝트를 만들고 사용자 지정 마법사를 사용 하는 방법도 수 있습니다.  
  
1. 솔루션 다시 빌드 및 디버깅을 시작 합니다. Visual Studio의 두 번째 인스턴스가 나타납니다.  
  
2. 새 MyProjectTemplate 프로젝트를 만듭니다. (**파일 / 새로 만들기 / 프로젝트 / Visual C# / MyProjectTemplate**)  
  
3. 에 **새 프로젝트** 대화 상자에서 템플릿을 찾고에 이름을 입력 하 고 클릭 **확인**합니다.  
  
     마법사 사용자 입력된 양식이 열립니다.  
  
4. 사용자 지정 매개 변수 값을 입력 하 고 단추를 클릭 합니다.  
  
     마법사 사용자 입력된 양식을 닫고 프로젝트 템플릿에서 만들어집니다.  
  
5. **솔루션 탐색기**소스 코드 파일을 마우스 오른쪽 단추로 클릭 하 고 클릭 **코드 보기**합니다.  
  
     `$custommessage$` 마법사 사용자 입력된 폼에 입력 된 텍스트를 사용 하 여 대체 되었습니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension 요소(Visual Studio 템플릿)](../extensibility/wizardextension-element-visual-studio-templates.md)