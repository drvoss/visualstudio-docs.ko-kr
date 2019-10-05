---
title: 형식 컬렉션 편집기 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be2e6bde6c25c1bb515ec3f017f14506c03a3a71
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697064"
---
# <a name="type-collection-editor-dialog-box"></a>형식 컬렉션 편집기 대화 상자
**형식 컬렉션 편집기** 알려진된 형식을 추가 하려면 대화 상자를 사용 합니다 **보낼** 및 **수신** 활동입니다. 이 대화 상자는 또한 제네릭 형식 인수를 추가 합니다 **InvokeMethod** 활동입니다. 에 사용 되는 경우는 **보내기** 및 **수신** 알려진된 형식을 추가 하는 작업을 **형식 컬렉션 편집기** 대화 상자에 추가 된 고유 해야 합니다. 경우 중복 형식을 추가 하 고 클릭 하 여 변경 내용이 커밋됩니다 **확인**, 오류 메시지가 반환 됩니다. 에 사용 되는 경우는 **InvokeMethod** 제네릭 형식 인수를 추가 하는 활동을 **형식 컬렉션 편집기** 대화 상자에는 중복 형식 추가할 수 있습니다.  
  
> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] 는 [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337)서비스에서 메타데이터를 내보낼 때 CLR 형식을 XSD에 매핑합니다.  
  
 다음 표에 사용자 인터페이스 (UI) 요소에는 **형식 컬렉션** 대화 상자.  
  
|UI 요소|설명|  
|----------------|-----------------|  
|**형식 목록**|추가 또는 제거된 형식의 목록입니다.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>형식 컬렉션 편집기를 표시하려면  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Send 및 Receive 활동에 대해 형식 컬렉션 편집기를 표시하려면  
  
1. 선택 합니다 **보낼** 또는 **수신** 디자인 뷰에서 작업 합니다.  
  
2. 키를 눌러 **F4** 불러오려면 합니다 **속성** 창입니다.  
  
3. 에 **속성** 창에서 줄임표 단추 옆에를 클릭 합니다 **KnownTypes** 속성입니다.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>InvokeMethod 활동에 대해 형식 컬렉션 편집기를 표시하려면  
  
1. 선택 된 **InvokeMethod** 디자인 뷰에서 작업 합니다.  
  
2. 키를 눌러 **F4** 불러오려면 합니다 **속성** 창입니다.  
  
3. 에 **속성** 창에서 줄임표 단추 옆에를 클릭 합니다 **GenericTypeArguments** 속성입니다.