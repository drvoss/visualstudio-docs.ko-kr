---
title: '방법: Visual Studio 솔루션의 일부가 아닌 실행 파일를 사용 하는 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e33233fd313cd6a73013ce55333a860663ddb601
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704520"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>방법: Visual Studio 솔루션의 일부가 아닌 실행 파일를 사용 하는 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

때로는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트에 포함되지 않은 실행 파일을 디버깅해야 하는 경우가 있습니다. 예를 들어 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 외부에서 만든 실행 파일이나 다른 사용자로부터 받은 실행 파일이 이러한 경우입니다.  
  
 이러한 문제는 일반적으로 Visual Studio 외부에서 실행 파일을 시작하고 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버거를 사용하여 이 파일에 연결하는 방법으로 해결합니다. 자세한 내용은[실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)합니다.  
  
 애플리케이션에 연결하려면 몇 가지 단계를 직접 수행해야 하기 때문에 몇 초 정도 걸립니다. 이러한 약간의 시간 지연으로 인해, 시작할 때 발생하는 문제를 디버깅하려는 경우에는 연결 방법을 사용할 수 없습니다. 또한, 사용자가 입력할 때까지 대기하지 않고 바로 종료되는 프로그램을 디버깅하는 경우에는 프로그램에 연결할 시간이 없을 수도 있습니다. [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]가 설치되어 있으면 이러한 프로그램에 대한 EXE 프로젝트를 만들 수 있습니다.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>기존 실행 파일에 대한 EXE 프로젝트를 만들려면  
  
1. 에 **파일** 메뉴에서 클릭 **열려** 선택한 **프로젝트**합니다.  
  
2. 에 **프로젝트 열기** 대화 상자, 드롭다운 목록 옆의 목록을 클릭 합니다 **파일 이름** 상자를 선택한 **모든 프로젝트 파일**합니다.  
  
3. 실행 파일을 찾은 다음 클릭 **확인**합니다.  
  
     실행 파일이 포함된 임시 솔루션이 생성됩니다.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>실행 파일을 Visual Studio 솔루션으로 가져오려면  
  
1. 에 **파일** 메뉴에서 **프로젝트 추가**를 클릭 하 고 **기존 프로젝트**합니다.  
  
2. 에 **기존 프로젝트 추가** 대화 상자, 드롭다운 목록 옆의 목록을 클릭 합니다 **파일 이름** 상자를 선택한 **모든 프로젝트 파일**합니다.  
  
3. 실행 파일을 찾아 선택합니다.  
  
4. **확인**을 클릭합니다.  
  
5. 와 같은 실행 명령을 선택 하 여 실행 파일을 시작 **시작**에서 **디버그** 메뉴.  
  
    > [!NOTE]
    > 모든 프로그래밍 언어가 EXE 프로젝트를 지원하는 것은 아닙니다. 이 기능이 필요하면 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]를 설치합니다.  
  
     디버깅하는 실행 파일에 대한 소스 코드가 없으면, 실행 중인 실행 파일에 연결하는지 실행 파일을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션에 추가하는지 여부에 상관없이 디버깅 기능이 제한됩니다. 실행 파일이 디버그 정보 없이 호환 형식으로 빌드된 경우에는 더욱 많은 기능이 제한됩니다. 따라서, 소스 코드가 있는 경우에는 소스 코드를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]로 가져온 다음 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 실행 파일의 디버그 빌드를 만드는 것이 좋습니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)   
 [디버거 보안](../debugger/debugger-security.md)   
 [DBG 파일](https://msdn.microsoft.com/91e449e9-8b65-4123-960f-2107cd1f1cfd)
