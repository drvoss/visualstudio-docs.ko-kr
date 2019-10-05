---
title: IManagedAddin 인터페이스
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 320b20fa40250ca47dd414b362059e152eba2c3b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420989"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin 인터페이스
  로드 하는 구성 요소를 만드는 IManagedAddin 인터페이스를 구현 하는 VSTO 추가 기능을 관리 합니다. 이 인터페이스는 2007 Microsoft Office 시스템에서 추가되었습니다.

## <a name="syntax"></a>구문

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>메서드
 다음 표에서 IManagedAddin 인터페이스에 의해 정의 된 메서드를 나열 합니다.

|이름|설명|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Microsoft Office 애플리케이션에서 관리되는 VSTO 추가 기능을 로드할 때 호출됩니다.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Microsoft Office 애플리케이션에서 관리되는 VSTO 추가 기능을 언로드하기 직전에 호출됩니다.|

## <a name="remarks"></a>설명
 Office VSTO 추가 기능 로드를 돕기 위해 IManagedAddin 인터페이스를 사용 하는 Microsoft Office 응용 프로그램, 2007 Microsoft Office system을 사용 하 여 시작 합니다. 사용자 고유의 VSTO 추가 기능 로더를 만들려면 IManagedAddin 인터페이스를 구현할 수 있습니다 및에 대 한 런타임 VSTO 추가 기능, VSTO 추가 기능 로더를 사용 하는 대신 관리 되는 (*VSTOLoader.dll*) 및 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]합니다. 자세한 내용은 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)을 참조하세요.

## <a name="how-managed-add-ins-are-loaded"></a>관리 되는 추가 기능이 로드 되는 방법
 다음 단계는 애플리케이션을 시작할 때 발생합니다.

1. 애플리케이션에서는 다음 레지스트리 키에서 항목을 검색하여 VSTO 추가 기능을 찾습니다.

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<응용 프로그램 이름 >* \Addins\\**

    이 레지스트리 키의 각 항목은 VSTO 추가 기능의 고유 ID입니다. 일반적으로 VSTO 추가 기능 어셈블리의 이름입니다.

2. 애플리케이션은 각 VSTO 추가 기능에 대한 항목에서 `Manifest` 항목을 찾습니다.

    관리 되는 VSTO 추가 기능 매니페스트의 전체 경로 저장할 수는 `Manifest` 아래에 항목이 **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<응용 프로그램 이름 >_ \Addins\\  _\<-add-in ID >_ **합니다. 매니페스트는 VSTO 추가 기능을 로드하는 데 사용되는 정보를 제공하는 파일(일반적으로 XML 파일)입니다.

3. 애플리케이션에서 `Manifest` 항목을 찾으면 관리되는 VSTO 추가 기능 로더 구성 요소를 로드하려고 합니다. 응용 프로그램 IManagedAddin 인터페이스를 구현 하는 COM 개체를 생성 하 여이 작업을 수행 합니다.

    합니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 는 VSTO 추가 기능 로더 구성 요소를 포함 (*VSTOLoader.dll*), IManagedAddin 인터페이스를 구현 하 여 직접 만들 수 있습니다.

4. 애플리케이션은 [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 메서드를 호출하여 `Manifest` 항목의 값을 전달합니다.

5. [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 메서드는 로드 중인 VSTO 추가 기능을 위한 보안 정책 및 응용 프로그램 도메인을 구성하는 등 VSTO 추가 기능을 로드하는 데 필요한 작업을 수행합니다.

   레지스트리에 대 한 자세한 내용은 Microsoft Office 응용 프로그램 검색 하 고 로드를 사용 하는 키 관리 되는 VSTO 추가 기능을 참조 하십시오 [VSTO 추가 기능에 대 한 레지스트리 항목](../vsto/registry-entries-for-vsto-add-ins.md)합니다.

## <a name="guidance-to-implement-imanagedaddin"></a>IManagedAddin 구현 하기 위한 지침
 IManagedAddin를 구현 하는 경우 다음 CLSID를 사용 하 여 구현이 포함 된 DLL을 등록 해야 합니다.

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 IManagedAddin 구현 하는 COM 개체를 만들려면이 CLSID를 사용 하는 Microsoft Office 응용 프로그램.

> [!CAUTION]
> 이 CLSID 에서도 *VSTOLoader.dll* 에 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]합니다. 따라서 IManagedAddin를 사용 하 여 사용자 고유의 VSTO 추가 기능 로더 및 런타임 구성 요소를 만드는 경우 배포할 수 없습니다 구성 요소는 VSTO 추가 기능에 의존 하는 실행 중인 컴퓨터에는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]합니다.

## <a name="see-also"></a>참고자료
- [관리 되지 않는 API 참조 &#40;Visual Studio에서 Office 개발&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
