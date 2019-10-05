---
title: 기능 플래그 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 831a52818cfc5c7b75c01a9551b70cd26b95dbcf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184513"
---
# <a name="capability-flags"></a>기능 플래그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SCC_CAP_*xxx* 플래그는 비트 플래그는 소스 제어 플러그 인의 기능을 나타내는 데 사용 합니다. SCC_EXCAP_*xxx* 플래그는 정수 값으로 확인 및 확장 된 기능을 나타내는 플래그를 증분 합니다.  
  
|기능 코드|값|설명|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|지원 합니다 [SccRemove](../extensibility/sccremove-function.md) 및 명령.|  
|`SCC_CAP_RENAME`|0x00000002L|지원 합니다 [SccRename](../extensibility/sccrename-function.md) 및 명령.|  
|`SCC_CAP_DIFF`|0x00000004L|지원 합니다 [SccDiff](../extensibility/sccdiff-function.md) 및 명령.|  
|`SCC_CAP_HISTORY`|0x00000008L|지원 합니다 [SccHistory](../extensibility/scchistory-function.md) 및 명령.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|지원 합니다 [SccProperties](../extensibility/sccproperties-function.md) 및 명령.|  
|`SCC_CAP_RUNSCC`|0x00000020L|지원 합니다 [SccRunScc](../extensibility/sccrunscc-function.md) 및 명령.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|지원 합니다 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 및 명령.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|지원 합니다 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 및 명령.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|지원 합니다 [SccGetEvents](../extensibility/sccgetevents-function.md) 및 명령.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|지원 합니다 [SccGetProjPath](../extensibility/sccgetprojpath-function.md) 및 명령.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|지원 합니다 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) 및 명령.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|체크 아웃 시 의견을 지원합니다.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|체크 인에 메모를 지원합니다.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|추가 주석을 지원합니다.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|제거 시 의견을 지원합니다.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|텍스트 출력을 IDE가 제공한 함수를 씁니다.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|델타 없이 파일 저장을 지원 합니다.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|여러 파일 히스토리를 지원합니다.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|대/소문자 구분 파일 비교를 지원합니다.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|파일 공백 문자를 구분 하지 않는 비교를 지원 합니다.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|추가 파일을 찾는 데를 지원 합니다.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|지원에 대 한 주석 프로젝트를 만듭니다.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|컨트롤의 경우 모든 상태의 차이 지원 합니다.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|플러그 인을 지원 하지는 UI에 대 한 Get, 않지만 IDE를 여전히 호출할 수 있습니다 [SccGet](../extensibility/sccget-function.md)합니다.|  
|`SCC_CAP_REENTRANT`|0x40000000L|플러그 인은 재진입 및 스레드로부터 안전 합니다. 버전 1.0에서는 없는 플러그 인 재진입 및 스레드로부터 안전한 것으로 가정 되었습니다. 이 비트를 설정 하는 플러그 인을 1.1, 호스트 병렬로 여러 프로젝트를 열려면 허용 됩니다.|  
  
## <a name="capability-bits-added-in-version-12"></a>버전 1.2에 추가 하는 기능 비트  
  
|기능 코드|값|설명|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|지원 합니다 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)합니다.|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|지원 합니다 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)합니다.|  
|`SCC_CAP_BATCH`|0x00040000L|지원 합니다 [SccBeginBatch](../extensibility/sccbeginbatch-function.md) 하 고 [SccEndBatch](../extensibility/sccendbatch-function.md)합니다.|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|지원 합니다 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)합니다.|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|지원 합니다 [SccDirDiff](../extensibility/sccdirdiff-function.md)합니다.|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|파일에서 여러 체크 아웃을 지원 하며 [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)합니다.|  
|`SCC_CAP_SCCFILE`|0x80000000L|MSSCCPRJ를 지원합니다. SCC 파일 (사용자/관리자 재정의) 될 수 있습니다 및 [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)합니다.|  
  
## <a name="capability-bits-added-in-version-13"></a>버전 1.3에에서 추가 하는 기능 비트  
 이러한 플래그를 한 번에 하나씩 전달 되는 [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) 기능이 지원 되는지 여부를 결정 하는 함수입니다.  
  
|확장된 기능 코드|값|Description|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|지원 된 `SCC_CHECKOUT_LOCALVER` 체크 아웃에 대 한 옵션입니다.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|지원 합니다 [SccBackgroundGet](../extensibility/sccbackgroundget-function.md)합니다.|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|지원 합니다 [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)합니다.|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|추가 디렉터리 검색을 지원 합니다.|  
|`SCC_EXCAP_QUERYCHANGES`|5|파일 변경 내용 열거를 지원 합니다.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|지원 합니다 [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)합니다.|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|지원 합니다 [SccGetUserOption](../extensibility/sccgetuseroption-function.md)합니다.|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|SccQueryInfo 여러 스레드에서 호출을 지원 합니다.|  
|`SCC_EXCAP_REMOVE_DIR`|9|SccRemoveDir 함수를 지원합니다.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|체크 아웃 된 파일을 삭제할 수 있습니다.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|체크 아웃 된 파일 이름을 바꿀 수 있습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
