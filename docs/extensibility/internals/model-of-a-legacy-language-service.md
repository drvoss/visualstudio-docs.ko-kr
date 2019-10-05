---
title: 레거시 언어 서비스 모델 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6efe97e0a6ca5d2188aee9d44246f1d9fb347cda
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326769"
---
# <a name="model-of-a-legacy-language-service"></a>레거시 언어 서비스 모델
언어 서비스는 특정 언어에 대 한 기능과 요소를 정의 하 고 해당 언어에 대 한 정보를 사용 하 여 편집기를 제공 하는 데 사용 됩니다. 예를 들어, 편집기 구문 색 지정을 지원 하기 위해 요소 및 언어의 키워드를 알고 있어야 합니다.

 언어 서비스는 편집기와 편집기를 포함 하는 보기에서 관리 하는 텍스트 버퍼를 사용 하 여 밀접 하 게 작동 합니다. Microsoft IntelliSense **요약 정보** 옵션은 예제 언어 서비스를 제공 하는 기능입니다.

## <a name="a-minimal-language-service"></a>최소 언어 서비스
 가장 기본적인 언어 서비스는 다음과 같은 두 개체가 포함 되어 있습니다.

- 합니다 *언어 서비스* 구현 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 인터페이스입니다. 언어 서비스를 사용 하면 이름, 파일 이름 확장명을 코드 창 관리자 colorizer 등 언어에 대 한 정보가 있습니다.

- 합니다 *colorizer* 구현 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 인터페이스입니다.

  다음 개념적 그리기 기본적인 언어 서비스의 모델을 보여 줍니다.

  ![언어 서비스 모델 그래픽](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") 기본 언어 서비스 모델

  문서 창 호스트는 *문서 뷰* 이 경우 편집기의는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 핵심 편집기입니다. 편집기에서 문서 보기 및 텍스트 버퍼를 소유 합니다. 이러한 개체를 작업할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 라는 특수 문서 창을 통해를 *코드 창*합니다. 코드 창에 포함 된는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 생성 및 IDE에 의해 제어 되는 개체입니다.

  편집기에서는 해당 확장과 관련 된 언어 서비스를 찾고 및 전달 하 여 코드 창을 호출 하 여 지정된 된 확장을 사용 하 여 파일을 로드 되 면를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 메서드. 언어 서비스는 *코드 창 관리자*를 구현 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 인터페이스.

  다음 표에서 모델에서 개체의 개요를 제공합니다.

| 구성 요소 | 개체 | 함수 |
|------------------| - | - |
| 텍스트 버퍼 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | 유니코드 읽기/쓰기 텍스트 스트림입니다. 다른 인코딩을 사용 하는 텍스트는 것이 가능 합니다. |
| 코드 창 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | 하나 이상의 텍스트 뷰를 포함 하는 문서 창입니다. 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 코드 창 (MDI) 다중 문서 인터페이스 모드로 MDI 자식입니다. |
| 텍스트 보기 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | 사용자가 이동 하 고 키보드 및 마우스를 사용 하 여 텍스트를 볼 수 있는 창입니다. 텍스트 뷰 편집기로 사용자에 게 표시 됩니다. 일반 편집기 창, 출력 창 및 직접 실행 창에 텍스트 뷰를 사용할 수 있습니다. 또한 코드 창 내에서 하나 이상의 텍스트 뷰를 구성할 수 있습니다. |
| 텍스트 관리자 | 관리 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 에서 가져와야 하는 서비스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 포인터 | 앞에서 설명한 모든 구성 요소에 의해 공유 되는 일반적인 정보를 유지 관리 하는 구성 요소입니다. |
| 언어 서비스 | 구현에 따라 다릅니다. 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | 구문 강조 표시, 문 완성 및 중괄호 일치 등의 언어 관련 정보를 사용 하 여 편집기를 제공 하는 개체입니다. |

## <a name="see-also"></a>참고 항목
- [사용자 지정 편집기의 문서 데이터 및 문서 보기](../../extensibility/document-data-and-document-view-in-custom-editors.md)