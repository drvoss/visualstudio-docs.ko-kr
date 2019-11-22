---
title: 'Walkthrough: Connecting a Host to a Generated Directive Processor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10c9c6cfa1d8553c79b710239a99f8ea9e2438e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301274"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>연습: 생성된 지시문 프로세서에 호스트 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

You can write your own host that processes text templates. A basic custom host is demonstrated in [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md). You could extend that host to add functions such as generating multiple output files.

 In this walkthrough, you expand your custom host so that it supports text templates that call directive processors. When you define a domain-specific language, it generates a *directive processor* for the domain model. The directive processor makes it easier for users to write templates that access the model, reducing the need to write assembly and import directives in the templates.

> [!WARNING]
> This walkthrough builds on [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md). Perform that walkthrough first.

 이 연습에는 다음 작업이 포함됩니다.

- Using [!INCLUDE[dsl](../includes/dsl-md.md)] to generate a directive processor that is based on a domain model.

- Connecting a custom text template host to the generated directive processor.

- Testing the custom host with the generated directive processor.

## <a name="prerequisites"></a>Prerequisites
 DSL을 정의하려면 다음 구성 요소를 설치해야 합니다.

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

 In addition, you must have the custom text template transformation created in [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Using Domain-Specific Language Tools to Generate a Directive Processor
 In this walkthrough, you use the Domain-Specific Language Designer Wizard to create a domain-specific language for the solution DSLMinimalTest.

#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>To use Domain-Specific Language Tools to generate a directive processor that is based on a domain model

1. Create a domain-specific language solution that has the following characteristics:

   - Name: DSLMinimalTest

   - Solution template: Minimal Language

   - File extension: min

   - Company name: Fabrikam

     For more information about creating a domain-specific language solution, see [How to: Create a Domain-Specific Language Solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

   > [!IMPORTANT]
   > This step generates the directive processor and adds the key for it in the registry.

3. **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.

    A second instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] opens.

4. In the experimental build, in **Solution Explorer**, double-click the file **sample.min**.

    The file opens in the designer. Notice that the model has two elements, ExampleElement1 and ExampleElement2, and a link between them.

5. Close the second instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

6. Save the solution, and then close the Domain-Specific Language Designer.

## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Connecting a Custom Text Template Host to a Directive Processor
 After you generate the directive processor, you connect the directive processor and the custom text template host that you created in [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md).

#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>To connect a custom text template host to the generated directive processor

1. Open the CustomHost solution.

2. **프로젝트** 메뉴에서 **참조 추가**를 클릭합니다.

     The **Add Reference** dialog box opens with the **.NET** tab displayed.

3. Add the following references:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. At the top of Program.cs or Module1.vb, add the following line of code:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Locate the code for the property `StandardAssemblyReferences`, and replace it with the following code:

    > [!NOTE]
    > In this step, you add references to the assemblies that are required by the generated directive processor that your host will support.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. Locate the code for the function `ResolveDirectiveProcessor`, and replace it with the following code:

    > [!IMPORTANT]
    > This code contains hard-coded references to the name of the generated directive processor to which you want to connect. You could easily make this more general, in which case it looks for all directive processors listed in the registry and tries to find a match. In that case, the host would work with any generated directive processor.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. **파일** 메뉴에서 **모두 저장**을 클릭합니다.

8. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

## <a name="testing-the-custom-host-with-the-directive-processor"></a>Testing the Custom Host with the Directive Processor
 To test the custom text template host, first you must write a text template that calls the generated directive processor. Then you run the custom host, pass to it the name of the text template, and verify that the directive is processed correctly.

#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>텍스트 템플릿을 만들어 사용자 지정 호스트를 테스트하려면

1. Create a text file, and name it `TestTemplateWithDP.tt`. You can use any text editor, such as Notepad, to create the file.

2. 텍스트 파일에 다음을 추가합니다.

    > [!NOTE]
    > The programming language of the text template does not need to match that of the custom host.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. In the code, replace \<YOUR PATH> with the path of the Sample.min file from the design-specific language you created in the first procedure.

4. 파일을 저장한 후 닫습니다.

#### <a name="to-test-the-custom-host"></a>사용자 지정 호스트를 테스트하려면

1. 명령 프롬프트 창을 엽니다.

2. 사용자 지정 호스트에 대한 실행 가능한 파일의 경로를 입력하고 Enter 키를 누르지 않습니다.

     예를 들어 다음과 같이 입력합니다.

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Instead of typing the address, you can browse to the file CustomHost.exe in **Windows Explorer**, and then drag the file into the Command Prompt window.

3. 공백을 입력합니다.

4. 텍스트 템플릿 파일의 경로를 입력한 다음 Enter 키를 누릅니다.

     예를 들어 다음과 같이 입력합니다.

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Instead of typing the address, you can browse to the file TestTemplateWithDP.txt in **Windows Explorer**, and then drag the file into the Command Prompt window.

     The custom host application runs and starts the text template transformation process.

5. In **Windows Explorer**, browse to the folder that contains the file TestTemplateWithDP.txt.

     The folder also contains the file TestTemplateWithDP1.txt.

6. 이 파일을 열어 텍스트 템플릿 변환의 결과를 확인합니다.

     The results of the generated text output appears and should look like this:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>관련 항목:
 [연습: 사용자 지정 텍스트 템플릿 호스트 만들기](../modeling/walkthrough-creating-a-custom-text-template-host.md)
