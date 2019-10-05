---
title: 코딩된 UI 테스트에 대한 샘플 Excel 추가 기능 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8588efe9ce460a34fc71f44bc0116b5977afe7aa
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705947"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>코딩된 UI 테스트에 대한 샘플 Excel 추가 기능
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]용 이 샘플 추가 기능은 기록된 Excel 워크시트의 코딩된 UI 테스트를 지원하도록 특별히 설계되었으며 Visual Studio Enterprise에서 실행됩니다. 이 추가 기능은 Visual Studio Tools for Office를 사용해서 생성되었습니다.  
  
 Excel 추가 기능에서 만드는 방법에 대 한 자세한 내용은 참조 하세요. [연습: Excel 용 첫 VSTO 추가 기능에 만드는](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) 하거나 "Excel 추가 기능에 대 한" MSDN을 검색 합니다.  
  
 Excel 추가 기능이 Excel용 코딩된 UI 테스트 확장에 대한 이 설명서의 주요 주제는 아니지만 일부 설명은 도움이 될 수 있습니다.  
  
 다음은 이 추가 기능의 중요한 부분입니다.  
  
- `ThisAddIn`  클래스 - `ExcelUICommunicator`와 [Excel용 샘플 코딩된 UI 테스트 확장명](../test/sample-coded-ui-test-extension-for-excel.md) 사이에서 .NET Remoting 채널을 관리합니다.  
  
- `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  - 추가 기능을 테스트하기 위한 보안 인증서입니다.  
  
- `ExcelUICommunicator`  클래스 - 이 클래스는 `IExcelUICommunication` 인터페이스를 구현합니다.  
  
## <a name="thisaddin-class"></a>ThisAddIn 클래스  
 이 클래스의 대부분은 실제로 Excel 추가 기능 프로젝트를 만들 때 `ThisAddIn.Designer.cs` 파일에서 Visual Studio Tools for Office로 생성되었습니다.  
  
 구현해야 하는 멤버는 이벤트 처리기 `ThisAddIn_Startup()` 및 `ThisAddIn_Shutdown()`입니다. 용도는 `ExcelUICommunicator`에서 사용하는 .NET Remoting 채널을 초기화하거나 닫는 것입니다.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 이 파일에는 Visual Studio Tools for Office로 생성된 임시 보안 인증서가 포함되며, 추가 기능 및 확장을 테스트하기 위해 Excel 프로세스에서 작동하기 위한 추가 기능 어셈블리 권한을 제공합니다. 이 인증서를 삭제하고 프로젝트 **속성** 창의 **서명** 탭에서 새 인증서를 만들거나 고유한 테스트 인증서를 첨부해야 합니다.  
  
## <a name="exceluicommunicator-class"></a>ExcelUICommunicator 클래스  
 이 클래스는 `IExcelUITestCommunication` 인터페이스를 구현하고 Excel 개체 모델에서 요청한 UI 정보를 가져옵니다. 자세한 내용은 [샘플 Excel Communicator 인터페이스](../test/sample-excel-communicator-interface.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Microsoft Excel을 지원하도록 코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [연습: 첫 번째 VSTO 추가 기능 만들기 for Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Office/SharePoint 개발](https://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)
