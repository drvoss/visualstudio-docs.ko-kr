---
title: ClickOnce 및 응용 프로그램 설정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 153df515fc762b7262dce81d8c1d1c4fe617ad61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900613"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 및 애플리케이션 설정
Windows Forms에 대 한 응용 프로그램 설정을 쉽게 만들고, 저장 및 사용자 지정 응용 프로그램 및 클라이언트에서 사용자 기본 설정을 유지 합니다. 다음 문서에는 ClickOnce 응용 프로그램에서는 응용 프로그램 설정 파일을 작업 하는 방법 및 다음 버전으로 업그레이드 하는 경우 ClickOnce가 설정을 마이그레이션하는 방법을 설명 합니다.

 아래 정보는 기본 응용 프로그램 설정 공급자에만 적용 됩니다는 \<xref:System.Configuration.LocalFileSettingsProvider > 클래스입니다. 사용자 지정 공급자를 제공 하는 경우 해당 공급자는 해당 데이터를 저장 하는 방법 및 설정 버전 간에 업그레이드 하는 방법을 결정 합니다. 응용 프로그램 설정 공급자에 대 한 자세한 내용은 참조 하세요. [응용 프로그램 설정 아키텍처](/dotnet/framework/winforms/advanced/application-settings-architecture)합니다.

## <a name="application-settings-files"></a>응용 프로그램 설정 파일
 두 파일을 사용 하는 응용 프로그램 설정:  *\<앱 >. exe.config* 하 고 *user.config*여기서 *앱* Windows Forms 응용 프로그램의 이름입니다. *user.config* 응용 프로그램에 사용자 범위 설정을 저장 하는 클라이언트에 처음으로 만들어집니다. *\<앱 >. exe.config*, 반대로 배포 하기 전에 설정에 대 한 기본값을 정의 하는 경우. Visual Studio는이 파일을 자동으로 포함 사용 하는 경우 해당 **게시** 명령입니다. 사용 하 여 ClickOnce 응용 프로그램을 만들면 *Mage.exe* 또는 *MageUI.exe*,이 파일에 포함 되어 있는지 확인 해야 응용 프로그램의 다른 파일을 응용 프로그램 매니페스트를 채울 때.

 ClickOnce를 사용 하는 응용 프로그램의 배포 되지 않은 Windows Forms 응용 프로그램에서  *\<앱 >. exe.config* 파일은 응용 프로그램 디렉터리에 저장 하는 동안 합니다 *user.config* 이 파일은 사용자의 **Documents and Settings** 폴더입니다. ClickOnce 응용 프로그램에서는  *\<앱 >. exe.config* ClickOnce 응용 프로그램 캐시 내에서 응용 프로그램 디렉터리에 거주 하 고 *user.config* ClickOnce 데이터 디렉터리에 거주 하 고 해당 응용 프로그램입니다.

 응용 프로그램을 배포 하는 방법에 관계 없이 응용 프로그램 설정에 안전 하 게 읽기 액세스를 보장  *\<앱 >. exe.config*, 및에 대 한 안전 하 게 읽기/쓰기 액세스 *user.config*합니다.

 ClickOnce 응용 프로그램에서는 응용 프로그램 설정에서 사용 하는 구성 파일의 크기는 ClickOnce 캐시의 크기에 따라 제한 됩니다. 자세한 내용은 [ClickOnce 캐시 개요](../deployment/clickonce-cache-overview.md)합니다.

## <a name="version-upgrades"></a>버전 업그레이드
 ClickOnce 응용 프로그램의 각 버전은 다른 모든 버전에서 격리, 처럼 ClickOnce 응용 프로그램에 대 한 응용 프로그램 설정도 다른 버전에 대 한 설정을 격리 됩니다. 사용자 응용 프로그램의 이후 버전으로 업그레이드 하는 경우 응용 프로그램 설정 병합 설정 새 설정 파일 집합으로 확인 하 고 업데이트 된 버전을 사용 하 여 제공 된 설정에 대해 최신 (가장 높은 번호) 버전의 설정을 비교 합니다.

 다음 표에서 응용 프로그램 설정을 복사 하는 설정을 결정 하는 방법 설명.

|변경 형식|업그레이드 작업|
|--------------------|--------------------|
|설정에 추가할  *\<앱 >. exe.config*|현재 버전의 새 설정을 병합할  *\<앱 >. exe.config*|
|설정에서 제거  *\<앱 >. exe.config*|현재 버전의 기존 설정이 제거 될  *\<앱 >. exe.config*|
|설정의 기본값 변경 로컬 설정에서 원래 기본 여전히로 *user.config*|현재 버전의 설정을 병합할 *user.config* 값으로 새 기본값을 사용 하 여|
|설정의 기본값 변경 집합에서 비-기본 설정을 *user.config*|현재 버전의 설정을 병합할 *user.config* 유지 기본이 아닌 값을 사용 하 여|

있습니다 사용자 고유의 응용 프로그램 설정 래퍼 클래스를 만들고 업데이트 논리 사용자 지정 하려는 경우 재정의할 수 있습니다는 \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > 메서드.

## <a name="clickonce-and-roaming-settings"></a>ClickOnce 및 로밍 설정
 ClickOnce 작동 하지 않습니다 로밍 설정을 사용 하 여 네트워크의 컴퓨터에서 수행 되도록 설정 파일을 수 있습니다. 로밍 설정에 필요한 경우 네트워크를 통해 설정을 저장 하는 응용 프로그램 설정 공급자를 구현 하거나 원격 컴퓨터에 설정을 저장 하기 위한 사용자 고유의 사용자 지정 설정 클래스를 개발 해야 합니다. 설정 공급자에 대 한 자세한 내용은 참조 하세요. [응용 프로그램 설정 아키텍처](/dotnet/framework/winforms/advanced/application-settings-architecture)합니다.

## <a name="see-also"></a>참고자료
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [애플리케이션 설정 개요](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce 캐시 개요](../deployment/clickonce-cache-overview.md)
- [ClickOnce 애플리케이션의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)