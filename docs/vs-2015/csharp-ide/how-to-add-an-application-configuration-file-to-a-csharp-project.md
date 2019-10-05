---
title: '방법: 추가 응용 프로그램 구성 파일을 C# 프로젝트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5c8dbad4d2bb248a3183e2e73d7c2932e7bce4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681720"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>방법: 추가 응용 프로그램 구성 파일을 C# 프로젝트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C# 프로젝트에 애플리케이션 구성 파일(app.config 파일)을 추가하면 공용 언어 런타임에서 어셈블리 파일을 찾고 로드하는 방법을 사용자 지정할 수 있습니다. 응용 프로그램 구성 파일에 대 한 자세한 내용은 참조 하세요. [런타임 어셈블리를 찾는 방법](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)합니다.  
  
> [!NOTE]
> Windows 스토어 지원 하지 않습니다 <xref:System.Configuration>합니다. 결과적으로, 스토어 앱을 app.config 템플릿은 없습니다.  
  
 프로젝트를 빌드할 때 개발 환경 자동으로 app.config 파일을 복사, 실행 파일의 경우에 맞게 복사본의 파일 이름을 변경 및 다음 bin 디렉터리에 복사본을 이동 합니다.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>C# 프로젝트에 응용 프로그램 구성 파일을 추가 하려면  
  
1. 메뉴 모음에서 선택 **프로젝트**하십시오 **새 항목 추가**합니다.  
  
     **새 항목 추가** 대화 상자가 나타납니다.  
  
2. 확장 **설치 됨**, 확장 **Visual C# 항목**를 선택한 후는 **응용 프로그램 구성 파일** 템플릿.  
  
3. **이름** 텍스트 상자에서 이름을 입력하고 **추가** 단추를 선택합니다.  
  
     App.config 라는 파일을 프로젝트에 추가 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [응용 프로그램 설정 관리(.NET)](../ide/managing-application-settings-dotnet.md)   
 [구성 파일 스키마](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [앱 구성](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [방법: .NET Framework 버전을 대상으로 앱 구성](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [C#용 Visual Studio 개발 환경 사용](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)