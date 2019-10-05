---
title: Windows Installer 기본 사항 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc52f846d7883d32f567df449a93c2626a710f81
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323055"
---
# <a name="windows-installer-basics"></a>Windows Installer 기본 사항
Windows 설치 관리자를 설치 하 고 Windows 설치 관리자 구성 요소 (WICs 또는 구성 요소 라고도 함) 라는 단위로 이러한 작업을 수행 합니다. 응용 프로그램 또는 사용자의 컴퓨터에서 소프트웨어 제품 제거. 설치 및 Windows Installer를 사용 하 여 설정에 대 한 계산 참조의 기본 단위는 각 WIC를 식별 하는 GUID입니다.

 Windows Installer의 포괄적인 설명서 Platform SDK 항목을 참조 하세요 [Windows Installer](/previous-versions/2kt85ked(v=vs.120))합니다.

## <a name="authoring-a-vspackage"></a>VSPackage를 작성합니다.
 Windows 설치 관리자는 Windows Installer 설치, 제거 또는 제품을 복구 하는 데 설치 사용자 인터페이스 (UI)를 실행 해야 하는 정보가 포함 된 설치 패키지를 사용 합니다. 각 설치 패키지에는 데이터베이스를 설치, 요약 정보 스트림 및 다양 한 부분 설치에 대 한 데이터 스트림을 포함 하는.msi 파일을 포함 합니다. 설치 관리자를 사용 하려면 설치를 작성 해야 합니다. 설치 관리자 구성 요소 개념의 설치를 구성 하 고 관계형 데이터베이스의 설치에 대 한 정보를 저장, 때문에 광범위 하 게 설치 패키지를 작성 하려면 해야 다음 단계:

1. Side-by-side-전략과 버전 관리를 지원 하기 위해 제작 설치를 계획 합니다.

2. 사용자에 게 표시 기능을 식별 합니다.

3. 구성 요소에는 VSPackage 및 종속성을 구성 합니다.

4. 정보를 사용 하 여 설치 데이터베이스를 채웁니다.

5. 설치 패키지의 유효성을 검사 합니다.

   이 설명서는 프로세스의 첫 번째 및 세 번째 단계를 사용 하 여 주로 관련이 있습니다. 이러한 단계를 구성 하면 VSPackage 기능 WICs 버전 및 서비스의 후속 버전에 대 한 계정에 대 한 전략 프레임 수 있도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]입니다. 나머지 세 단계를 Platform SDK의 Windows Installer 설명서에서 자세히 설명 되어 있습니다.

## <a name="key-terms"></a>주요 용어
 다음은 Windows Installer 기술과 관련 된 주요 용어의 정의 합니다.

 리소스 파일, 레지스트리 키, 바로 가기 또는 등 컴퓨터에 설치할 수 있습니다. 이러한 리소스는 Windows 설치 관리자 구성 요소에 논리적으로 그룹화 됩니다.

 Windows Installer 구성 요소 (WIC) 설치 및 하나의 단위로 제거 되는 관련 된 리소스의 논리적 그룹화를 나타내는 설치의 기본 단위입니다. Windows Installer 구성 요소가 고유한 구성 요소 ID 또는 GUID로 식별 됩니다. 또한 Windows Installer WIC 수준에서 계산 참조를 유지 합니다. 최대 버전 관리 유연성에 대 한 DLL 같은 둘 이상의 기본 리소스 지정된 WIC에 포함 합니다. 참고를 식별 하 고는 WIC를 채우는 GUID를 지정 하 고 나면 배포, 해당 구성을 변경할 수 없습니다. 자세한 내용은 [구성 요소를 응용 프로그램 구성](/windows/desktop/Msi/organizing-applications-into-components)합니다.

 .Msi 파일 및 외부 소스 파일을이 파일을 가리킬 수 있습니다 구성 된 배포 패키지 (재배포 가능 패키지)는 단위입니다. 패키지는 Windows 설치 관리자 UI를 실행 하 고 설치 하거나 응용 프로그램을 제거 하는 모든 정보를 포함 합니다.

 지침과 응용 프로그램을 설치 하는 데 필요한 데이터를 포함 하는.msi 파일은 COM-구조적 저장소 파일입니다. 모든 패키지에는.msi 파일을 하나 이상 포함합니다. .Msi 파일에는 설치 관리자 데이터베이스, 요약 정보 스트림 및 가능한 경우 하나 이상의 변환 및 내부 소스 파일 포함 되어 있습니다. 파일을 설치할 수 캐비닛 압축 및 스트림에.msi 파일에 저장 된 또는 저장, 압축 하거나 압축 되지 않은 원본 미디어의.msi 파일을 외부입니다. 자세한 내용은 [Windows Installer 파일 확장명](/windows/desktop/Msi/windows-installer-file-extensions)합니다.

## <a name="windows-installer-rules-enforcement"></a>Windows Installer 규칙 적용
 두 가지 규칙 설정의 구성 요소를 통해 리소스의 배포를 확인합니다. 하나의 규칙 집합은 설치 작성자로 두 번째 집합을 적용 해야 하는 동안 자체 Windows 설치 프로그램에서 유지 됩니다.

> [!NOTE]
> Windows Installer 규칙 적용에는.msi 파일의 유효성 검사를 실행 하는 경우에 발생 합니다. 그럼에도 불구 하 고 모범 사례를 이러한 규칙을 처리 하도록 있습니다 주의가 요구 됩니다. 자세한 내용은 [설치 데이터베이스 유효성 검사](/windows/desktop/Msi/validating-an-installation-database) 하 고 [패키지 유효성 검사](/windows/desktop/Msi/package-validation)합니다.

#### <a name="installer-enforced-rules"></a>설치 관리자 적용 규칙

- 지정된 된 구성 요소에 있는 모든 파일을 동일한 디렉터리에 설치 되어야 합니다. 반대로, 별개의 폴더에 설치 된 파일은 구성 요소 구분에 속해야 합니다.

- 구성 요소별 키 경로가 하나만 있을 수 있습니다. 키 경로 단순히 파일 또는 레지스트리 키를 전체 구성 요소를 나타냅니다.

#### <a name="component-provider-responsibilities"></a>구성 요소 공급자 책임

- 이후 버전에서는 개별적으로 제공할 수 있는 두 리소스는 별도 구성 요소에 있어야 합니다. 이러한 리소스는 별도로 제공 되지 특정 경우에 동일한 구성 요소도 리소스를 그룹화 할 수 해야 합니다. 사실, 것이 좋습니다 모든 기본 리소스 (예: Dll) 별도 WICs에 항상 존재 합니다. 자세한 내용은 [설치 관리자 구성 요소 정의](/windows/desktop/Msi/defining-installer-components)합니다.

- 버전이 지정 된 리소스가 해야 적이 둘 이상의 WIC에서 제공 됩니다.

## <a name="see-also"></a>참고 항목
- [구성 요소 규칙을 위반 하는 경우 어떻게 되나요?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)