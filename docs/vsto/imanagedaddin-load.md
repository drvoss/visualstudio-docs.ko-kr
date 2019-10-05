---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 87fb34e90d36383f49b6369fb1dea4b9854c7300
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956733"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  관리되는 VSTO 추가 기능이 로드되면 호출됩니다.

## <a name="syntax"></a>구문

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*bstrManifestURL*|VSTO 추가 기능에 대한 매니페스트의 전체 경로입니다.|
|*pdispApplication*|VSTO 추가 기능에 로드 하 고 있는 호스트 응용 프로그램을 나타내는 IDispatch 포인터입니다.|

## <a name="return-value"></a>반환 값
 메서드가 성공적으로 완료되었는지 여부를 나타내는 HRESULT 값입니다.

## <a name="remarks"></a>설명
 매니페스트는 VSTO 추가 기능을 로드하는 데 사용되는 정보를 제공하는 파일(일반적으로 XML 파일)입니다. 예를 들어 매니페스트는 VSTO 추가 기능이 로드될 때 인스턴스화할 VSTO 추가 기능 어셈블리 및 진입점 클래스의 위치를 지정할 수 있습니다.

 *bstrManifestURL* 의 값을 포함 하는 매개 변수를 `Manifest` 아래 항목을 **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<응용 프로그램 이름 >_ \Addins\\_\<-add-in ID >_**  VSTO 추가 기능에 대 한 레지스트리 키입니다. 자세한 내용은 [IManagedAddin 인터페이스](../vsto/imanagedaddin-interface.md)합니다.

 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) 메서드를 구현하여 로드되는 VSTO 추가 기능을 위한 애플리케이션 도메인 및 보안 정책 구성 등의 작업을 수행합니다.

## <a name="see-also"></a>참고자료
- [IManagedAddin 인터페이스](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
