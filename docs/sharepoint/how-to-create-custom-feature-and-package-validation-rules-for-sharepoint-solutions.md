---
title: 'SharePoint 솔루션: 사용자 지정 기능을 만들고, 유효성 검사 규칙을 패키지'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a10118a0c83f9e17e32efd293a9a824e38a0942a
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835931"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>방법: SharePoint 솔루션에 대 한 유효성 검사 규칙 사용자 지정 기능 및 패키지 만들기
  Visual Studio에서 생성 하는 솔루션 패키지를 확인 하기 위한 사용자 지정 유효성 검사 규칙을 만들 수 있습니다. 선택 하 여 전체 기능 또는 패키지의 전체 유효성 검사를 수행할 수 있습니다 **유효성 검사** 패키지 또는 기능에서 상황에 맞는 메뉴에서를 **PackagingExplorer**합니다. 부분 유효성 검사 기능을 패키지는 유효한 상태에서 실행될지를 판단 하는 프로젝트에 새 SharePoint 프로젝트 항목 또는 기능을 추가할 때 수행 됩니다.

### <a name="to-create-a-custom-package-validation-rule"></a>사용자 지정 패키지 유효성 검사 규칙을 만들려면

1. 클래스 라이브러리 프로젝트를 만듭니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. 다음 인터페이스 중 하나를 구현 하는 클래스를 만듭니다.

    - 패키지 유효성 검사 규칙을 만들려면 구현 된 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 인터페이스입니다.

    - 기능 유효성 검사 규칙을 만들려면 구현 된 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 인터페이스입니다.

4. 추가 된 <xref:System.ComponentModel.Composition.ExportAttribute> 클래스입니다. 이 특성에는 Visual Studio 검색 하 고 유효성 검사 규칙을 로드할 수 있습니다. 전달 된 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 또는 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 특성 생성자에는 형식입니다.

## <a name="example"></a>예제
 다음 코드 예제에는 사용자 지정 기능 유효성 검사 규칙을 만드는 방법을 보여 줍니다.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- Microsoft.VisualStudio.SharePoint.

- System.ComponentModel.Composition.

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 용 확장 프로그램 배포 도구](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
