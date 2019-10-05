---
title: IDebugDocumentProvider 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5632134c86b5aa0e3cb769a68d2d4cfd944ff35c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008679"
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider 인터페이스
요청 시 문서를 인스턴스화하는 방법을 제공합니다.  
  
## <a name="remarks"></a>설명  
 문서를 인스턴스화하기 위한이 간접 의미 합니다.  
  
- 문서를 필요할 때 로드할 수 있습니다.  
  
- 문서 개체를에 디버거 IDE 내에 포함 될 수 있습니다.  
  
- 여러 가지 방법으로 동일한 문서 개체에 액세스할 수 있습니다.  
  
  이 효과적으로 해당 공급자에서 문서를 분리 하 고 공급자 추가 런타임 컨텍스트 정보를 전달할 수 있습니다.  
  
  상속 된 메서드 외에도 `IDebugDocumentInfo`, `IDebugDocumentProvider` 인터페이스는 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|로 인해 문서가 아직 존재 하지 않는 경우 인스턴스화할 수 있습니다.|