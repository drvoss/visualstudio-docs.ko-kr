---
title: 지 속성 및 실행 중인 문서 테이블 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80932ab926b7ef26eaef10991e4f5782e81c4b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328527"
---
# <a name="persistence-and-the-running-document-table"></a>지속성 및 실행 중인 문서 테이블
에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 프로젝트는 서비스를 사용 하 여를 달성 하는 해당 프로젝트 항목을 유지 관리를 완전히 담당 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>합니다. 문서는 Visual Studio 환경에서 지 속성의 기본 단위입니다. 프로젝트 열기, 저장 및 실행 중인 문서 테이블 (RDT) 모든 열린 문서의 상태를 추적 하는 리소스를 사용 하 여 문서의 이름을 바꿀를 조정 합니다.

## <a name="managing-persistence"></a>지 속성 관리
 구현 하 여 환경 지 속성 서비스를 제어 하는 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 인터페이스입니다. 환경에서 직접 문서를 유지할 수을 요청 하는 동안 문서를 저장할 소유 프로젝트 (또는 계층) 요청 합니다. 이렇게 하면 해당 프로젝트 항목 데이터 로컬 파일, 원격 파일, 데이터베이스, 저장소, 또는 기타 미디어를 저장 하려면 프로젝트에 대 한 합니다.

 전역 환경에는 RDT 유지 관리합니다. 열려 있는 모든 창에 대 한 항목을 관리 하는 환경 및 쉽게 처리할 수 있도록 하는 RDT 문서 솔루션을 닫을 때와 같은 특수 한 알림의 받을 합니다. 또한는 RDT 수 있도록에 해당 노드를 추적 하는 환경을 **솔루션 탐색기**합니다. RDT 프로젝트 파일 및 프로젝트 항목 문서를 포함 하 여 열고, 지속 개체 마다 하나의 레코드를 유지 관리 합니다.

## <a name="see-also"></a>참고 항목
- [문서 테이블 실행](../../extensibility/internals/running-document-table.md)
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)