---
title: Windows Installer 배포에 대 한 확장 준비 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c958c75088a6e31d9386f1acd423360b8dbe0a6c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336174"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Windows Installer 배포에 대 한 확장 준비
VSIX 패키지를 배포 하려면 Windows Installer 패키지 (MSI)를 사용할 수 없습니다. 그러나 MSI 배포용 VSIX 패키지의 내용을 추출할 수 있습니다. 이 문서에는 해당 기본 출력은 설치 프로젝트에 포함할 VSIX 패키지 프로젝트를 준비 하는 방법을 보여 줍니다.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer 배포에 대 한 확장 프로젝트를 준비
 설치 프로젝트를 추가 하기 전에 새 확장 프로젝트에서 이러한 단계를 수행 합니다.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer 배포에 대 한 확장 프로젝트를 준비 하려면

1. VSPackage, MEF 구성 요소, 편집기 Adornment 또는 VSIX 매니페스트를 포함 하는 다른 확장성 프로젝트 형식을 만듭니다.

2. 코드 편집기에서 VSIX 매니페스트를 엽니다.

3. 설정 된 `InstalledByMsi` VSIX 매니페스트를 요소의 `true`합니다. VSIX 매니페스트에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)합니다.

     이 구성 요소를 설치 하려고 VSIX 설치 관리자를 방지 합니다.

4. 프로젝트를 마우스 오른쪽 단추로 클릭 **솔루션 탐색기** 누릅니다 **속성**합니다.

5. 선택 된 **VSIX** 탭 합니다.

6. 확인란 **다음 위치에 복사 VSIX 콘텐츠** 파일 설치 프로젝트를 선택 하는 위치에 대 한 경로 입력 합니다.

## <a name="extract-files-from-an-existing-vsix-package"></a>기존 VSIX 패키지에서 파일을 추출 합니다.
 원본 파일이 없는 경우 설치 프로젝트에 기존 VSIX 패키지의 콘텐츠를 추가 하려면 다음이 단계를 수행 합니다.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>기존 VSIX 패키지에서 파일을 추출 하려면

1. 이름 바꾸기는 *합니다. VSIX* 파일에서 확장을 포함 하 *filename.vsix* 하려면 *filename.zip*합니다.

2. 내용을 복사 합니다 *.zip* 디렉터리로 파일입니다.

3. 삭제 된 *[Content_types].xml* 디렉터리에서.

4. 이전 절차에서와 같이 VSIX 매니페스트를 편집 합니다.

5. 설치 프로젝트에 나머지 파일을 추가 합니다.

## <a name="see-also"></a>참고자료
- [Visual Studio 설치 관리자 배포](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [연습: 사용자 지정 작업 만들기](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))