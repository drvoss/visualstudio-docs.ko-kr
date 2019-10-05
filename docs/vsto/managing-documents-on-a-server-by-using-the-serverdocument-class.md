---
title: ServerDocument 클래스를 사용 하 여 서버에서 문서 관리
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 739946fc7fc6ea7014fb93010ca85094a7fc7056
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251929"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>ServerDocument 클래스를 사용 하 여 서버에서 문서 관리
  Word와 Microsoft Office Excel `ServerDocument` 이 설치 되어 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 있지 않은 Microsoft Office 경우에도의 클래스를 사용 하 여 문서 수준 사용자 지정의 여러 측면을 관리할 수 있습니다. 다음 작업을 수행할 수 있습니다.

- 문서 또는 통합 문서의 데이터 캐시에 있는 데이터에 액세스 하 고 수정 합니다. 자세한 내용은 [문서에서 캐시 된 데이터](#CachedData)에 대 한 작업을 참조 하세요.

- 문서와 연결 된 사용자 지정 어셈블리를 관리 합니다. 자세한 내용은 [문서 사용자 지정 관리](#CustomizationInfo)를 참조 하세요.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>ServerDocument 클래스 이해
 클래스 `ServerDocument` 는 Office가 설치 되지 않은 컴퓨터에서 사용 하도록 설계 되었습니다. 따라서 일반적으로 office 프로젝트가 아닌 콘솔 프로젝트 또는 Windows Forms 프로젝트와 같이 Office와 통합 되지 않는 응용 프로그램에서이 클래스를 사용 합니다. ServerDocument 어셈블리 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 의 클래스를 사용 합니다. *VisualStudio* .

 클래스 `ServerDocument` 는를 사용 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]하 여 만든 문서 수준 사용자 지정에 대해 작동 하는 데 사용할 수 있습니다.

 Visual Studio 2010 Tools for Office Runtime 및 .NET Framework Office 확장에 대 한 자세한 내용은 [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)를 참조 하세요.

> [!NOTE]
> `Visual Studio Tools for Office` 시스템 (버전 3.0런타임`ServerDocument` )에서 클래스를 사용 하는 레거시 응용 프로그램이 있는 경우 응용 프로그램을 실행 하는 컴퓨터에 시스템(버전3.0런타임)을설치해야합니다.`Visual Studio Tools for Office` 는 `Visual Studio 2010 Tools for Office runtime` 이러한 응용 프로그램을 실행할 수 없습니다.

## <a name="CachedData"></a>문서에서 캐시 된 데이터 작업
 클래스 `ServerDocument` 는 사용자 지정 된 문서에서 데이터 캐시 작업에 사용할 수 있는 멤버를 제공 합니다. 캐시 된 데이터에 대 한 자세한 내용은 [데이터 캐시](../vsto/caching-data.md) 및 [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)를 참조 하세요.

 다음 표에서는 캐시 된 데이터로 작업 하는 데 사용할 수 있는 멤버를 나열 합니다.

|작업|사용할 멤버|
|----------|-------------------|
|문서에 데이터 캐시가 있는지 여부를 확인 합니다.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 메서드|
|문서의 캐시 된 데이터에 액세스 하려면입니다.<br /><br /> 자세한 내용은 [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)를 참조 하세요.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 속성|

## <a name="CustomizationInfo"></a>문서 사용자 지정 관리
 `ServerDocument` 클래스의 멤버를 사용 하 여 문서와 연결 된 사용자 지정 어셈블리를 관리할 수 있습니다. 예를 들어 문서가 더 이상 사용자 지정에 포함 되지 않도록 문서에서 사용자 지정을 프로그래밍 방식으로 제거할 수 있습니다.

 다음 표에서는 사용자 지정 어셈블리를 관리 하는 데 사용할 수 있는 멤버를 나열 합니다.

|작업|사용할 멤버|
|----------|-------------------|
|문서가 문서 수준 사용자 지정의 일부 인지 여부를 확인 합니다.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 메서드|
|런타임에 프로그래밍 방식으로 문서에 사용자 지정을 연결 하려면입니다.<br /><br /> 자세한 내용은 [방법: 문서에 관리 코드 확장명 연결](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 메서드 중 하나입니다.|
|런타임에 프로그래밍 방식으로 문서에서 사용자 지정을 제거 하려면입니다.<br /><br /> 자세한 내용은 [방법: 문서](../vsto/how-to-remove-managed-code-extensions-from-documents.md)에서 관리 코드 확장을 제거 합니다.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 메서드|
|-문서와 연결 된 배포 매니페스트의 URL을 가져옵니다.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 속성|

## <a name="see-also"></a>참고 항목
- [방법: 문서에 관리 코드 확장명 연결](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [방법: 문서에서 관리 코드 확장 제거](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [데이터 캐시](../vsto/caching-data.md)
