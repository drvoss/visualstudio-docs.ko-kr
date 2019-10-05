---
title: VSTextBuffer 개체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a324db2226056fd3f41180055600671a8979a67
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312797"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 개체
텍스트 버퍼 개체는 일반적으로 파일을 사용 하 여 연결 된 유니코드 문자의 스트림을 나타냅니다. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 마법사와 같이 핵심 편집기의 컨텍스트 외부에서 개체를 사용할 수 있습니다.

 다음 표에서의 인터페이스를 보여 줍니다. `VSTextBuffer`합니다.

|메서드|설명|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|표준 OLE 인터페이스입니다. 실행 취소/다시 실행 버퍼에 처리에 사용 됩니다.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|표준 OLE 인터페이스입니다.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|표준 OLE 인터페이스입니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|합성물 동작 (즉, 실행 취소/다시 실행의 단일 단위로 그룹화 되는 동작)를 만들을 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|텍스트 버퍼에 의해 관리 되는 문서 데이터의 지 속성을 사용 하도록 설정 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|기본 서비스를 제공합니다. 여러 클라이언트에서 사용 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|버퍼를 검색 하는 데 사용 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|제공 읽기 및 쓰기 2 차원 좌표를 사용 하 여 기능 합니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|제공 읽기 및 쓰기 1 차원 좌표를 사용 하는 기능입니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|텍스트 버퍼에 스트림 지향, 순차적 액세스를 신속 하 고 제공합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|속성의 제네릭 컬렉션에 대 한 액세스를 제공합니다. 가장 중요 한 속성 이름 또는 버퍼의 모니커를입니다. GUID를 만들고 키로 사용 하 여이 인터페이스를 사용 하 여 버퍼에서 고유한 임의 데이터를 저장할 수 있습니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|이벤트에 대 한 연결점을 지원합니다.|

## <a name="remarks"></a>설명
 `VSTextBuffer` 하 여 일반적으로 발견 되는 `QueryInterface` 호출 `IVsTextBuffer`합니다. 자세한 내용은 [텍스트 버퍼](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)합니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)