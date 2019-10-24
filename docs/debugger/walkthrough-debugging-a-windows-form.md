---
title: Windows Form 디버깅 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 701d156d5fdc23a5e98ac1de43c1882f3065171e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728326"
---
# <a name="walkthrough-debugging-a-windows-form"></a>연습: Windows Form 디버깅
Windows Form은 가장 일반적으로 관리 되는 응용 프로그램 중 하나입니다. Windows Form은 표준 Windows 응용 프로그램을 만듭니다. Visual Basic, C#또는 C++를 사용 하 여이 연습을 완료할 수 있습니다.

 먼저 열려 있는 솔루션을 모두 닫아야 합니다.

### <a name="to-prepare-for-this-walkthrough"></a>이 연습을 준비하려면

- 열려 있는 솔루션이 이미 열려 있는 경우 닫습니다. ( **파일** 메뉴에서 **솔루션 닫기**를 선택 합니다.)

## <a name="create-a-new-windows-form"></a>새 Windows Form 만들기
 다음에는 새 Windows Form을 만듭니다.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>이 연습에 대 한 Windows form을 만들려면

1. **파일** 메뉴에서 **새로 만들기** 를 선택 하 고 **프로젝트**를 클릭 합니다.

     **새 프로젝트** 대화 상자가 나타납니다.

2. 프로젝트 형식 창에서 **Visual Basic**, **시각적 개체 C#** 또는 **시각적 C++**  노드를 연 다음

    1. Visual Basic 또는 시각적 개체 C#의 경우 Windows **바탕 화면**  > **windows Form 앱**을 선택 합니다.

    2. 시각적 개체 C++에 대해 **Windows 데스크톱 응용 프로그램**을 선택 합니다.

3. **이름** 상자에서 프로젝트에 고유한 이름 (예: Walkthrough_SimpleDebug)을 지정 합니다.

4. **확인**을 클릭합니다.

     Visual Studio에서 새 프로젝트를 만들고 Windows Forms 디자이너에 새 폼을 표시 합니다. 자세한 내용은 [Windows Forms 디자이너](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\))를 참조 하세요.

5. **보기** 메뉴에서 **도구 상자**를 선택 합니다.

     도구 상자가 열립니다. 자세한 내용은 [도구 상자](../ide/reference/toolbox.md)를 참조하세요.

6. 도구 상자에서 **단추** 컨트롤을 클릭 하 고 컨트롤을 폼 디자인 화면으로 끌어 옵니다. 폼에 단추를 놓습니다.

7. 도구 상자에서 **TextBox** 컨트롤을 클릭 하 고 컨트롤을 폼 디자인 화면으로 끌어 옵니다. 폼에 **텍스트 상자** 를 놓습니다.

8. 양식 디자인 화면에서 단추를 두 번 클릭 합니다.

     그러면 코드 페이지로 이동 합니다. 커서는 `button1_Click` 이어야 합니다.

10. `button1_Click` 함수에 다음 코드를 추가합니다.

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

     프로젝트가 오류 없이 빌드되어야 합니다.

## <a name="debug-your-form"></a>폼 디버그
 이제 디버깅을 시작할 준비가 되었습니다.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>이 연습을 위해 만든 Windows Form을 디버깅 하려면

1. 소스 창에서 추가한 텍스트와 같은 줄에서 왼쪽 여백을 클릭 합니다.

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     빨간 점이 나타나며 해당 줄의 텍스트가 빨간색으로 강조 표시됩니다. 빨간 점은 중단점을 나타냅니다. 자세한 내용은 [중단점](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)을 참조하세요. 디버거에서 애플리케이션을 실행하면 코드가 적중되는 위치에서 디버거가 실행을 중단합니다. 그런 다음 애플리케이션의 상태를 보고 디버깅할 수 있습니다.

    > [!NOTE]
    > 코드 줄을 마우스 오른쪽 단추로 클릭 하 고 **중단점**을 가리킨 다음 **중단점 삽입** 을 클릭 하 여 해당 줄에 중단점을 추가할 수도 있습니다.

2. **디버그** 메뉴에서 **시작**을 선택합니다.

     Windows Form이 실행 되기 시작 합니다.

3. Windows Form에서 추가한 단추를 클릭 합니다.

     Visual Studio에서는 코드 페이지에서 중단점을 설정 하는 줄로 이동 합니다. 이 줄은 노란색으로 강조 표시되어 있어야 합니다. 이제 애플리케이션의 변수를 보고 해당 애플리케이션의 실행을 제어할 수 있습니다. 이제 응용 프로그램의 실행이 중지 되어 사용자의 작업을 기다리는 중입니다.

4. **디버그** 메뉴에서 **창**을 선택한 다음 **조사식**을 클릭 하 고 **조사식 1**을 클릭 합니다.

5. **조사식 1** 창에서 빈 행을 클릭 합니다. **이름** 열에 `textBox1.Text` (Visual Basic 또는 시각적 개체 C#를 사용 하는 경우) 또는 `textBox1->Text` (를 사용 C++하는 경우)를 입력 한 다음 enter 키를 누릅니다.

     **조사식 1** 창에는이 변수의 값이 따옴표로 묶여 표시 됩니다.

    `""`

6. **디버그** 메뉴에서 **한 단계씩 코드 실행**을 선택합니다.

     **조사식 1** . 텍스트의 값은 다음으로 조사식 창에서 변경 됩니다.

    `Button was clicked!`

7. **디버그** 메뉴에서 **계속** 을 선택 하 여 프로그램 디버깅을 다시 시작 합니다.

8. Windows Form에서 단추를 다시 클릭 합니다.

     Visual Studio가 실행을 다시 중단 합니다.

9. 중단점을 나타내는 빨간색 점을 클릭 합니다.

     이렇게 하면 코드에서 중단점이 제거 됩니다.

10. **디버그** 메뉴에서 **디버깅 중지**를 선택합니다.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>디버깅을 위해 Windows Form 응용 프로그램에 연결
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]에서는 실행 중인 프로세스에 디버거를 연결할 수 있습니다. Express Edition을 사용 하는 경우에는이 기능이 지원 되지 않습니다.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>디버깅을 위해 Windows Form 응용 프로그램에 연결 하려면

1. 위에서 만든 프로젝트에서 왼쪽 여백을 클릭 하 여 추가 된 줄에 중단점을 다시 설정 합니다.

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. **디버그** 메뉴에서 **디버깅 하지 않고 시작**을 선택 합니다.

     Windows Form은 실행 파일을 두 번 클릭 한 것 처럼 Windows에서 실행 되기 시작 합니다. 디버거가 연결 되어 있지 않습니다.

3. **디버그** 메뉴에서 **프로세스에 연결**을 선택 합니다. 이 명령은 **도구** 메뉴 에서도 사용할 수 있습니다.

     **프로세스에 연결** 대화 상자가 나타납니다.

4. **사용 가능한 프로세스** 창의 **프로세스** 열에서 프로세스 이름 (Walkthrough_SimpleDebug)을 찾아 클릭 합니다.

5. **연결** 단추를 클릭 합니다.

6. Windows Form에서 한 번만 단추를 클릭 합니다.

     디버거는 중단점에서 Windows Form의 실행을 중단 합니다.

## <a name="see-also"></a>참조
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [디버거 보안](../debugger/debugger-security.md)
