---
title: 격리 된 셸 응용 프로그램 서비스에 대 한 지침 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159276"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>격리 셸 애플리케이션에 대한 지침 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 격리 셸 응용 프로그램을 배포 하는 경우에 설치 된 후 응용 프로그램에 대 한 소프트웨어 업데이트를 제공할 수 해야 합니다. 이 위해 Microsoft Installer (MSI) 파일을 사용 하 여 응용 프로그램을 설치 해야 합니다. 이 종류의 설치에는 웹에서 재배포할 수 하기 위해 Microsoft에서 제공 하는 소프트웨어 업데이트 다운로드 및 사용자 지정의 개입 없이 고객에 게 사용 수 있습니다.  
  
## <a name="servicing-requirements"></a>서비스 요구 사항  
 격리 셸 설치 설치 프로그램에는 다음 세 가지 조건을 충족 하는지 확인 하 여 업데이트를 수 있는지 확인할 수 있습니다.  
  
### <a name="redistribute-by-using-an-msi"></a>MSI를 사용 하 여 재배포  
 MSI를 사용 하 여 응용 프로그램 재배포에 MSI 제품 관련 정보를 유지 하 고 있는지 확인 하기 때문에 응용 프로그램 클라이언트 컴퓨터의 실제 위치입니다. 병합 모듈 (.msm 파일) 이러한 보증을 제공 하지 않습니다 하 고 사용할 수 없습니다.  
  
### <a name="accounting-for-custom-actions"></a>사용자 지정 작업에 대 한 계정  
 사용자 지정 작업은 설치 프로그램의 비표준 설치 지시문입니다. 사용자 지정 동작 파일 위치, 레지스트리 설정, 사용자 설정 또는 기타 설치 항목 같은 매개 변수를 변경 합니다. 사용자 지정 작업 설치 시 데이터를 조작할 수 있습니다.  
  
 설치 프로그램에서 사용자 지정 작업을 사용 하는 경우 사용자 응용 프로그램을 제거 하는 경우 작업을 취소 하려면 해당 하는 사용자 지정 작업을 모든 설치 시 사용자 지정 작업에 있어야 함을 확인 해야 합니다. 해당를 제공 하 여 설치 프로그램 실패는 사용자 지정 작업을 제거 하는 경우 응용 프로그램 제거 상태로 유지 됩니다 부분적으로 설치 합니다.  
  
- 소프트웨어 업데이트 이러한 버전을 변경 하거나 값을 해시 하는 경우 파일 또는 해시 값의 특정 버전을 사용 하는 사용자 지정 작업을 실패 합니다. 이 경우 사용자 지정 작업 이러한 값을 수동으로 업데이트 해야 합니다. 또 다른 문제는 버전의 파일 또는 해시 값이 제품 버전 간에 공유 되 면 발생 합니다. 가능 하면이 종속성을 방지 합니다.  
  
### <a name="accounting-for-shared-files"></a>공유 파일에 대 한 계정  
 공유 파일 이름이 같은 및 여러 제품으로 같은 위치에 설치 됩니다. 이러한 제품 버전, 재고 유지 단위 (SKU) 또는 둘 다 다를 수 있습니다 및 제품 지정된 된 컴퓨터에 공존할 수 있습니다. 그러나 파일 공유는 여러 가지 이유로 서비스 문제를 만듭니다.  
  
- 공유 파일을 업데이트 한 응용 프로그램에 대 한 업데이트는 업데이트 되지 않은 두 번째 응용 프로그램을 사용 하는 파일의 버전 변경 될 수 있으므로 응용 프로그램 호환성 문제가 발생할 수 있습니다. 설치 관리자 파일을 공유 하는 제품에 대 한 공유 파일에 대 한 참조를 계산 합니다. 따라서 제품을 제거 해도 설치 된 인스턴스 수가 감소 초과 공유 파일 적용 되지 않습니다.  
  
- 엔지니어링 QFE (Quick Fix) 설치 관리자를 처리 하는 QFE 설치 관리자 제품의 버전에는 파일의 버전을 되돌립니다. 이 프로세스는 잠재적으로 업데이트 된 공유 파일을 배달 해야 하는 응용 프로그램을 중단 합니다.
