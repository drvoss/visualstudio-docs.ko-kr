---
title: 샘플 Excel Communicator 인터페이스 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 42da15899bb9bab6388d32c87132796eff768d7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158186"
---
# <a name="sample-excel-communicator-interface"></a>샘플 Excel Communicator 인터페이스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

샘플 `IExcelUICommunication` 인터페이스는 `ExcelAddIn` 프로젝트의 `ExcelUICommunicator` 개체에서 사용됩니다.  
  
## <a name="iexceluicommunication-interface"></a>IExcelUICommunication 인터페이스  
 이 인터페이스는 코딩된 UI 테스트 프로세스에서 실행되는 `CodedUIExtension`과 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 프로세스에서 실행되는 `ExcelCodedUIAddIn` 간의 통신 지점을 정의합니다.  
  
 `ExcelCodedUIAddinHelper` 어셈블리에는 이 인터페이스에서 파생되며 Excel 개체 모델을 사용하여 메서드를 처리하는 `ExcelUICommunicator` 클래스가 있습니다.  
  
 일부 메서드는 Excel에서 요청된 정보를 가져온 다음 `CellInformation` 개체와 같은 정보 개체 중 하나를 만들어서 반환합니다.  
  
 그리고 제공된 정보 개체를 사용하여 Excel에서 해당하는 컨트롤을 찾고 컨트롤에 대해 특정 프로세스를 수행하는 메서드도 있습니다. 예를 들어 `ScrollIntoView` 메서드는 지정한 셀이 표시되도록 워크시트를 스크롤합니다.  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample 및 ExcelCodedUIAddinHelper 통신  
 `ExcelCodedUIAddinHelper` 어셈블리는 Excel 프로세스에서 실행되며, `IExcelUITestCommunication` 인터페이스를 구현하고 Excel UI에서 필요한 정보를 직접 가져오거나 설정하는 `UICommunicator` 클래스를 포함합니다.  
  
 `CodedUIExtensibilitySample` 어셈블리는 Visual Studio의 코딩된 UI 테스트 프로세스에서 실행됩니다. 이 어셈블리는 .NET Remoting 채널을 여는 `Communicator` 클래스를 포함하며, `IExcelUICommunication` 인터페이스를 통해 `ExcelCodedUIAddinHelper` 어셈블리의 `UICommunicator` 개체를 사용하여 `CellInformation` 개체 등의 정보 개체 및 요청을 두 어셈블리 간에 전달하는 `Instance` 속성을 제공합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Microsoft Excel을 지원하도록 코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [코딩된 UI 테스트에 대한 샘플 Excel 추가 기능](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Excel용 샘플 코딩된 UI 테스트 확장명](../test/sample-coded-ui-test-extension-for-excel.md)
