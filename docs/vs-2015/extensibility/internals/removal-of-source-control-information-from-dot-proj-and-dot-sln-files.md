---
title: 소스 제어 정보 제거 합니다. Proj 및 합니다. Sln 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199383"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj 및 .Sln 파일에서 소스 제어 정보 제거
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

SCC는 원본 제어 플러그 인 API 버전 1.2에에서 정보를 MSSCCPRJ에 저장 됩니다. SCC 파일입니다. MSSCCPRJ 활용 합니다. SCC 파일은는 SCC 정보는 원본이 아닌-.proj 및.sln 파일에는 것을 제어 합니다.  
  
## <a name="version-12-changes"></a>버전 1.2 변경  
 원본 제어 플러그 인은 원본 제어 플러그 인 API 버전 1.1 기반으로 하는, 소스 제어에 대 한 정보 (.proj) 프로젝트 및 솔루션 (.sln) 파일에 저장 됩니다. 데이터베이스에 대 한 위치의 소스 제어 정보는 AuxPath 된 되며 데이터베이스 내의 특정 위치 ProjName 지정 됩니다. 이 동작의 ProjName 일반적으로 유효 하지 않음 후 이러한 작업 중 하나 때문에 분기, 분기 또는 복사 작업 후 문제가 발생할 수 있습니다.  
  
 원본 제어 플러그 인 API 사용 되는 버전 1.1에서는 IDE에서에서 ~ SAK 파일 플러그 인 지원 되는 MSSCCPRJ 검색 합니다. 소스 제어 정보를 저장 하는 SCC 메서드. 원본 제어 플러그 인 API 버전 1.2 MSSCCPRJ 지원 검색에 대 한 새로운 기능을 제공 합니다. SCC 파일을 사용 하지 않고는 ~ SAK 파일입니다. 자세한 내용은 [제거 ~ SAK 파일](../../extensibility/internals/elimination-of-tilde-sak-files.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
