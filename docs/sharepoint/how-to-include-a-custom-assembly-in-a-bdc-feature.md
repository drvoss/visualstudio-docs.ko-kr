---
title: '방법: BDC 기능에 사용자 지정 어셈블리 포함 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6de3313dad06c009244a8b784e81bf7d2a768c3b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443110"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>방법: BDC 기능에 사용자 지정 어셈블리 포함
  프로젝트가 동일한 솔루션의 다른 프로젝트에서 어셈블리를 참조할 수 있습니다. 그러나 사용 하 여 프로젝트의 기능 파일에 이러한 어셈블리를 추가 해야 합니다는 합니다 **할당 참조 어셈블리를 Lobsystem** 대화 상자.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>비즈니스 데이터 연결 (BDC) 기능에는 사용자 지정 어셈블리를 포함 하려면

1. **솔루션 탐색기**, BDC 모델이 포함 된 폴더를 선택 합니다.

2. **보기** 메뉴에서 **속성 창**을 클릭합니다.

3. 에 **속성** 창에서 선택 합니다 **어셈블리** 속성을 한 다음 줄임표 단추 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")).

     합니다 **할당 참조 어셈블리를 Lobsystem** 대화 상자가 나타납니다.

4. 에 **어셈블리를 선택할** 목록에서 사용자 지정 어셈블리를 선택 합니다.

    > [!NOTE]
    > 어셈블리에만 표시 합니다 **할당 참조 어셈블리를 Lobsystem** 어셈블리를 포함 하는 프로젝트에 대 한 참조를 추가한 경우 대화 상자. 자세한 내용은 [방법: 참조 추가 또는 제거 참조 추가 대화 상자를 사용 하 여](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)입니다.

5. 에 **참조 속성** 그룹에서 대해 표시 되는 목록을 연를 **LobSystem 범위** 속성을 사용자 지정 어셈블리를 사용 하 고 다음을 선택 하는 메서드의 LOB 시스템는 **확인**  단추입니다.

    > [!NOTE]
    > 사용자 지정 어셈블리에서 코드를 디버깅 하려면 솔루션 패키지에 어셈블리를 추가 해야 합니다. 자세한 내용은 [방법: 추가 어셈블리 추가 및 제거](../sharepoint/how-to-add-and-remove-additional-assemblies.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한을 지정 합니다.](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)
- [SharePoint에 Integragte 비즈니스 데이터](../sharepoint/integrating-business-data-into-sharepoint.md)
