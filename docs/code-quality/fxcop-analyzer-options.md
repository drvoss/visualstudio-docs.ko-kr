---
title: FxCop 분석기 구성 옵션
ms.date: 09/23/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: de4fdbbdf54976ba3ee12c3621f7038cd4704a76
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449071"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>FxCop 분석기에 대 한 규칙 범위 옵션

일부 FxCop analyzer 규칙을 사용 하 여 코드 베이스에서 적용 해야 하는 부분을 구체화할 수 있습니다. 이 페이지에서는 사용 가능한 범위 구성 옵션, 허용 되는 값 및 적용할 수 있는 규칙을 나열 합니다. 이러한 옵션을 사용 하려면 [Editorconfig 파일](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)에서 지정 합니다.

이러한 구성 옵션은 [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 패키지의 버전 2.6.3부터 사용할 수 있습니다.

> [!TIP]
> 지정 된 버전의 FxCopAnalyzers 패키지에 사용할 수 있는 옵션의 전체 목록을 보려면 패키지의 *문서* 폴더에서 *Analyzer Configuration.md* 파일을 확인 합니다. 파일은 *% USERPROFILE% \\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers \\ \<version \> \documentation\Analyzer Configuration.md*에 있습니다. 이 구성 문서 파일은 버전 2.6.5에서 시작 하 여 패키지의 각 버전에 포함 되어 있습니다. 다음은 *Analyzer Configuration.md* 파일에 옵션을 설명 하는 방법의 예입니다.
>
> 옵션 이름: `sufficient_IterationCount_for_weak_KDF_algorithm` \
> 옵션 값: 정수 값 \
> 기본값: 각 구성 가능한 규칙 (대부분의 규칙에 대해 기본적으로 ' 10만 ')에 한정 됩니다.
> 예: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 분석할 API 표면의 부분 | `public`<br/>`internal` 또는 `friend`<br/>`private`<br/>`all`<br/><br/>여러 값을 쉼표 (,)로 구분 합니다. | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217.md)<br/>[CA2225](ca2225.md)<br/>[CA2226](ca2226.md)<br/>[CA2231](ca2231.md)<br/>[CA2234](ca2234.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 값을 반환 하지 않는 비동기 메서드를 무시할지 여부 | `true`<br/>`false` | `false` | [CA2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> 분석기 패키지의 2.6.3 이전 버전에서는이 옵션의 이름이 `skip_async_void_methods`입니다.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 규칙에서 단일 문자 [형식 매개 변수](/dotnet/csharp/programming-guide/generics/generic-type-parameters) 를 제외할지 여부 (예: `Collection<S>`의 `S`) | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> 분석기 패키지의 2.6.3 이전 버전에서는이 옵션의 이름이 `allow_single_letter_type_parameters`입니다.

## <a name="output_kind"></a>output_kind

| 설명 | 허용 가능한 값 | 기본값 | 구성 가능한 규칙 |
| - | - | - | - |
| 이 어셈블리 유형을 생성 하는 프로젝트의 코드를 분석 해야 함을 지정 합니다. | @No__t-0 열거형의 하나 이상의 필드<br/><br/>여러 값을 쉼표 (,)로 구분 합니다. | 모든 출력 종류 | [CA2007](ca2007-do-not-directly-await-task.md) |
