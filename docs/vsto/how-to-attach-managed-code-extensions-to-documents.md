---
title: '방법: 문서에 관리 코드 확장명 연결'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f56d51817491726e6011e965bfd6d68630bb0dbf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441798"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>방법: 문서에 관리 코드 확장명 연결
  기존 Microsoft Office Word 문서 또는 Microsoft Office Excel 통합 문서에 사용자 지정 어셈블리를 연결할 수 있습니다. Microsoft Office 프로젝트와 Visual Studio에 개발 도구에서 지원 되는 모든 파일 형식 문서 또는 통합 문서를 수 있습니다. 자세한 내용은 [의 문서 수준 사용자 지정 아키텍처](../vsto/architecture-of-document-level-customizations.md)합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Word 또는 Excel 문서에 사용자 지정 연결을 사용 합니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 메서드는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 클래스입니다. 때문에 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 클래스는 Microsoft Office가 설치 되지 않은 컴퓨터에서 실행 되도록 설계 되었습니다, Microsoft Office 개발 (예: 콘솔 또는 Windows Forms 응용 프로그램)에 직접 관련 되지 않은 솔루션에서이 메서드를 사용할 수 있습니다.

> [!NOTE]
> 사용자 지정 코드를 지정된 된 문서에 없는 컨트롤을 필요로 하는 경우 로드 되지 것입니다.

 ![비디오 링크](../vsto/media/playvideo.gif "비디오 링크") 관련된 비디오 데모를 참조 하세요. [어떻게 할까요? 연결 또는 분리를 VSTO 어셈블리 Word 문서에서? ](http://go.microsoft.com/fwlink/?LinkId=136782).

### <a name="to-attach-managed-code-extensions-to-a-document"></a>문서에 관리 코드 확장명 연결

1. 콘솔 응용 프로그램 또는 Windows Forms 프로젝트와 같은 Microsoft Office를 필요 하지 않은 프로젝트에 대 한 참조를 추가 합니다 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* 고  *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* 어셈블리입니다.

2. 다음을 추가 합니다 **가져오기를** 또는 **사용 하 여** 문을 코드 파일의 맨 위에 있습니다.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. 정적 호출 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 메서드.

     다음 코드 예제에서는 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 오버 로드 합니다. 이 오버 로드 된 문서의 전체 경로 및 <xref:System.Uri> 문서에 연결 하려는 사용자 지정에 대 한 배포 매니페스트의 위치를 지정 하는 합니다. 이 예제에서는 Word 문서에 명명 된 가정 **WordDocument1.docx** 바탕 화면에 및 배포 매니페스트 라는 폴더에 위치한 **게시** 바탕 이기도 합니다.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. 프로젝트를 빌드하고 사용자 지정을 연결 하려는 컴퓨터의 응용 프로그램을 실행 합니다. 컴퓨터는 Visual Studio 2010 Tools for Office Runtime 설치 있어야 합니다.

## <a name="see-also"></a>참고자료
- [ServerDocument 클래스를 사용 하 여 서버의 문서 관리](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [방법: 문서에서 관리 코드 확장명 제거](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Office 솔루션에서 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)
