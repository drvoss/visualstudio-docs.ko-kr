---
title: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 432daff22616950e0a97164190a94082bf2db354
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401492"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기
  빌드, 정리 및 SharePoint 패키지의 유효성 검사 ( *.wsp*) 개발 컴퓨터에서 명령줄 MSBuild 작업을 사용 합니다. 또한 빌드 컴퓨터에서 Team Foundation Server를 사용 하 여 빌드 프로세스를 자동화 하려면 다음이 명령을 사용할 수 있습니다.

## <a name="build-a-sharepoint-package"></a>SharePoint 패키지 빌드

#### <a name="to-build-a-sharepoint-package"></a>SharePoint 패키지를 빌드하려면

1. Windows에서 **시작** 메뉴 선택 **프로그램도** > **Accessories** > **명령 프롬프트**합니다.

2. SharePoint 프로젝트가 위치한 디렉터리로 변경 합니다.

3. 프로젝트에 대 한 패키지를 만들려면 다음 명령을 입력 합니다. 바꿉니다 *ProjectFileName* 프로젝트의 이름입니다.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     예를 들어 ListDefinition1 라는 SharePoint 프로젝트를 패키지 하려면 다음 명령 중 하나를 실행할 수 있습니다.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>SharePoint 패키지를 정리 합니다.

#### <a name="to-clean-a-sharepoint-package"></a>SharePoint 패키지를 정리 하려면

1. 명령 프롬프트 창을 엽니다.

2. SharePoint 프로젝트가 위치한 디렉터리로 변경 합니다.

3. 프로젝트에 대 한 패키지를 정리 하려면 다음 명령을 입력 합니다. 바꿉니다 *ProjectFileName* 프로젝트의 이름입니다.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     예를 들어 ListDefinition1 라는 SharePoint 프로젝트를 정리 하려면 다음 명령 중 하나를 실행할 수 있습니다.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>SharePoint 패키지의 유효성 검사

#### <a name="to-validate-a-sharepoint-package"></a>SharePoint 패키지의 유효성을 검사 하려면

1. 명령 프롬프트 창을 엽니다.

2. SharePoint 프로젝트가 위치한 디렉터리로 변경 합니다.

3. 프로젝트에 대 한 패키지의 유효성을 검사 하려면 다음 명령을 입력 합니다. 바꿉니다 *ProjectFileName* 프로젝트의 이름입니다.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     예를 들어 ListDefinition1 라는 SharePoint 프로젝트의 유효성을 검사 하려면 다음 명령 중 하나를 실행할 수 있습니다.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>SharePoint 패키지의 속성을 설정 합니다.

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>SharePoint 패키지의 속성을 설정 하려면

1. 명령 프롬프트 창을 엽니다.

2. SharePoint 프로젝트가 위치한 디렉터리로 변경 합니다.

3. 프로젝트에 대 한 패키지에서 속성을 설정 하려면 다음 명령을 입력 합니다. 바꿉니다 *PropertyName* 설정 하려는 속성을 사용 하 여 합니다.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     예를 들어 경고 수준을 설정 하려면 다음 명령을 실행할 수 있습니다.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>참고자료
- [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)
- [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
