---
title: 제거 ~ SAK 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436333"
---
# <a name="elimination-of-sak-files"></a>~SAK 파일 제거
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

원본 제어 플러그 인 API 1.2에는 ~ SAK 파일 기능 플래그 및 MSSCCPRJ 파일 및 공유 체크 아웃 원본 제어 플러그 인을 지원 하는지 여부를 검색 하는 새 함수로 대체 되었습니다.  
  
## <a name="sak-files"></a>~ SAK 파일  
 Visual Studio.NET 2003 접두사가 추가 된 임시 파일을 만든 ~ SAK 합니다. 이러한 파일을 사용 하 여 소스 제어 플러그 인을 지원 하는지 확인할 수 있습니다:  
  
- MSSCCPRJ 합니다. SCC 파일입니다.  
  
- 여러 (공유) 체크 아웃 합니다.  
  
  플러그 인에 대해 원본 제어 플러그 인 API 1.2에서 제공 하는 고급 함수를 지 원하는, IDE는 새로운 기능, 플래그 및 다음 섹션에 자세히 설명 하는 함수를 사용 하 여 임시 파일을 만들지 않고 이러한 기능을 검색할 수 있습니다.  
  
## <a name="new-capability-flags"></a>새 기능 플래그  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>새 함수  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 선언 경우 소스 제어 플러그 인 (공유) 여러 체크 아웃을 지원 합니다 `SCC_CAP_MULTICHECKOUT` 기능과 구현을 `SccIsMultiCheckOutEnabled` 함수입니다. 소스 제어 프로젝트에서 체크 아웃 작업을 수행할 때마다이 함수가 호출 됩니다.  
  
 소스 제어 플러그 인 경우 생성 및는 MSSCCPRJ의 사용을 지원 합니다. SCC 파일을 선언 합니다 `SCC_CAP_SCCFILE` 기능과 구현 합니다 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)합니다. 이 함수는 파일의 목록을 사용 하 여 호출 됩니다. 함수 반환 `TRUE/FALSE` 각 파일이 Visual Studio는 MSSCCPRJ을 사용할지 여부를 나타냅니다. SCC 파일에 대 한 합니다. 소스 제어 플러그 인이 새 기능 및 기능을 지원 하지 않도록 선택 하면 다음 레지스트리 키를 사용 하 여 이러한 파일의 생성을 사용 하지 않도록 설정 수 것:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl"=dword:00000001  
  
> [!NOTE]
> 이 레지스트리 키를로 dword:00000000은 존재 하지 않는, 되 고 키에 해당 하는 것 하 고 Visual Studio는 여전히 임시 파일을 만들려고 시도 합니다. 그러나 레지스트리 키가 dword:00000001를 설정 하는 경우 Visual Studio 임시 파일을 만들려고 시도 하지 않습니다. 대신 원본 제어 플러그 인을 MSSCCPRJ를 지원 하지 않습니다 가정 합니다. SCC 파일 공유 체크 아웃을 지원 하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
