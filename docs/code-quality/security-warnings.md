---
title: 보안 경고
ms.date: 10/02/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.securityrules
helpviewer_keywords:
- security [Visual Studio ALM], Enterprise Templates
- security warnings
- managed code analysis warnings, security warnings
- warnings, security
ms.assetid: 60d4e8ea-230a-494f-aa6a-b91db77540e4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf1f318d8138bb455e965d7df44ae45e192904e3
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018759"
---
# <a name="security-warnings"></a>보안 경고

보안 경고는 더 안전한 라이브러리 및 애플리케이션을 지원합니다. 이들 경고는 프로그램의 보안 결함을 방지하는 데 도움이 됩니다. 이들 경고를 비활성화하는 경우 코드에 그 이유를 명확하게 표시하고 개발 프로젝트의 지정된 보안 담당자에게 이 사실을 알려야 합니다.

## <a name="in-this-section"></a>단원 내용

|규칙|설명|
|----------|-----------------|
|[CA2100: 보안 취약성에 대 한 SQL 쿼리 검토 @ no__t-0|메서드가 메서드에 대한 문자열 인수로부터 만들어진 문자열을 사용하여 System.Data.IDbCommand.CommandText 속성을 설정합니다. 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다.|
|[CA2102: 일반 처리기에서 비 CLSCompliant 예외 Catch @ no__t-0|RuntimeCompatibilityAttribute로 표시되지 않거나 RuntimeCompatibility(WrapNonExceptionThrows = false)로 표시된 어셈블리의 멤버에는 System.Exception을 처리하는 catch 블록이 포함되며 바로 뒤의 일반 catch 블록은 포함되지 않습니다.|
|[CA2103: 명령적 보안 검토 @ no__t-0|메서드가 명령적 보안을 사용하고, 요청이 활성 상태인 동안 변경될 수 있는 반환 값 또는 상태 정보를 사용하여 권한을 구성하고 있습니다. 가능하면 선언적 보안을 사용합니다.|
|[CA2104: 변경 가능한 읽기 전용 참조 형식을 선언 하지 마세요. @ no__t-0|외부에서 볼 수 있는 형식에 변경 가능한 참조 형식인, 외부에서 볼 수 있는 읽기 전용 필드가 포함되었습니다. 변경 가능한 형식은 해당 인스턴스 데이터를 수정할 수 있는 형식을 말합니다.|
|[CA2105: 배열 필드는 읽기 전용 이면 안 됩니다. @ no__t-0|배열이 들어 있는 필드에 read-only(Visual Basic의 경우 ReadOnly) 한정자를 적용하면 필드를 변경하여 다른 배열을 참조할 수 없습니다. 그러나 읽기 전용 필드에 저장된 배열의 요소는 변경할 수 있습니다.|
|[CA2106: 보안 어설션 @ no__t-0|메서드에서 권한을 어설션하는데 호출자에 대해 보안 검사가 수행되지 않습니다. 보안 검사를 수행하지 않고 보안 권한을 어설션하면 코드에 보안상 취약한 부분이 남아 있을 수 있습니다.|
|[CA2107: Deny를 검토 하 고 usage @ no__t-0만 허용|PermitOnly 메서드 및 CodeAccessPermission 사용. 보안 거부 동작은 .NET 보안에 대 한 고급 지식이 있는 경우에만 사용 해야 합니다. 이러한 보안 동작을 사용하는 코드는 보안 검토를 거쳐야 합니다.|
|[CA2108: 값 형식에 대 한 선언적 보안 검토 @ no__t-0|public 또는 protected 값 형식이 데이터 액세스 또는 링크 요청에 의해 보안됩니다.|
|[CA2109: 표시 되는 이벤트 처리기 @ no__t-0 검토|public 또는 protected 이벤트 처리 메서드를 발견했습니다. 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다.|
|[CA2111: 포인터는 표시 되지 않아야 함 @ no__t-0|포인터가 전용, 내부 또는 읽기 전용이 아닙니다. 악의적인 코드에서는 해당 포인터 값을 변경하여 메모리 내 임의의 위치에 액세스할 수 있게 되거나 애플리케이션 또는 시스템 오류를 발생시킬 수 있습니다.|
|[CA2112: 보안 형식은 필드를 노출 하면 안 됩니다. @ no__t-0|public 또는 protected 형식이 public 필드를 포함하고 링크 요청에 의해 보안됩니다. 코드에 링크 요청으로 보안된 형식의 인스턴스에 대한 액세스 권한이 있으면 코드에서 링크 요청을 만족하지 않아도 해당 형식의 필드에 액세스할 수 있습니다.|
|[CA2114: 메서드 보안은 @ no__t 형식의 상위 집합 이어야 합니다.|메서드에는 같은 동작에 대해 메서드 수준과 형식 수준의 선언적 보안이 모두 있으면 안 됩니다.|
|[CA2115: GC를 호출 합니다. 네이티브 리소스를 사용 하는 경우 KeepAlive @ no__t-0|이 규칙에서는 관리되지 않는 리소스가 비관리 코드에서 여전히 사용되고 있는데 종료되려고 할 경우 발생할 수 있는 오류를 감지합니다.|
|[CA2116: APTCA 메서드는 APTCA 메서드만 호출 해야 합니다. @ no__t-0|완전히 신뢰할 수 있는 어셈블리에 APTCA(AllowPartiallyTrustedCallers) 특성이 있고 이 어셈블리가 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 다른 어셈블리의 코드를 실행하면 보안상 위험할 수 있습니다.|
|[CA2117: APTCA 형식은 APTCA 기본 형식만 확장 해야 합니다. @ no__t-0|완전히 신뢰할 수 있는 어셈블리에 APTCA(AllowPartiallyTrustedCallers) 특성이 있고 이 어셈블리의 형식이 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 형식에서 상속되면 보안상 위험할 수 있습니다.|
|[CA2118: Review SuppressUnmanagedCodeSecurityAttribute usage @ no__t-0|SuppressUnmanagedCodeSecurityAttribute는 COM interop 또는 플랫폼 호출을 사용하는 비관리 코드를 실행하는 멤버에 대해 기본 보안 시스템 동작을 변경합니다. 이 특성은 기본적으로 성능 향상을 위해 사용되지만 성능이 향상되는 대신 중대한 보안 위험이 발생합니다.|
|[CA2119: 전용 인터페이스를 충족 하는 봉인 메서드 @ no__t-0|상속할 수 있는 public 형식에서는 internal(Visual Basic의 경우 Friend) 인터페이스의 재정의 가능한 메서드 구현을 제공합니다. 이 규칙 위반 문제를 해결하려면 어셈블리 외부에서 메서드가 재정의되지 않도록 합니다.|
|[CA2120: 보안 serialization 생성자 @ no__t-0|이 형식에는 System.Runtime.Serialization.SerializationInfo 개체와 System.Runtime.Serialization.StreamingContext 개체(serialization 생성자 서명)를 사용하는 생성자가 있습니다. 이 생성자는 보안 검사를 통해 보안되지 않지만 형식에 있는 하나 이상의 정규 생성자가 보안됩니다.|
|[CA2121: 정적 생성자는 private이어야 합니다.](../code-quality/ca2121.md)|시스템에서는 형식의 첫 번째 인스턴스가 만들어지거나 static 멤버가 참조되기 전에 static 생성자를 호출합니다. static 생성자가 private이 아니면 시스템 이외의 코드에서 이를 호출할 수 있습니다. 이렇게 되면 생성자에서 수행하는 작업에 따라 예기치 않은 동작이 발생할 수 있습니다.|
|[CA2122: 링크 요청이 있는 메서드를 간접적으로 노출 하지 마십시오. @ no__t-0|public 또는 protected 멤버에 링크 요청이 있으며 해당 멤버가 보안 검사를 수행하지 않는 멤버에 의해 호출됩니다. 링크 요청은 직접 실행 호출자의 권한만 검사합니다.|
|[CA2123: 재정의 링크 요청은 base @ no__t-0과 동일 해야 합니다.|이 규칙에서는 메서드를 다른 형식의 인터페이스이거나 가상 메서드인 기본 메서드에 일치시킨 다음 각각에 대해 링크 요청을 비교합니다. 이 규칙이 위반되면 악의적인 호출자가 보안되지 않은 메서드를 호출함으로써 링크 요청을 우회할 수 있습니다.|
|[CA2124: 취약 한 finally 절을 outer try @ no__t-0에 래핑합니다.|public 또는 protected 메서드에 try/finally 블록이 들어 있습니다. finally 블록이 보안 상태를 다시 설정하는 것으로 나타나며 finally 블록에 포함되어 있지 않습니다.|
|[CA2126: 형식 링크 요청에는 상속 요구가 필요 합니다. @ no__t-0|public unsealed 형식이 링크 요청으로 보호되며 재정의 가능한 메서드를 포함합니다. 형식이나 메서드는 모두 상속 요청으로 보호됩니다.|
|[CA2130: 보안에 중요 한 상수는 ' @ no__t-0 ' 이어야 합니다.|런타임에 조회가 필요하지 않도록 컴파일러에서 상수 값을 인라인하기 때문에 상수 값에 투명성이 적용되지 않습니다. 상수 필드는 보안 투명해야 하므로 코드 검토자는 투명 코드가 상수에 액세스할 수 없다고 가정하지 않습니다.|
|[CA2131: 보안에 중요 한 형식은 동일한 형식 @ no__t에 참여할 수 없습니다.|형식이 동등성에 참여 하 고 형식 자체 또는 형식의 멤버 또는 필드 중 하나가 SecurityCriticalAttribute 특성으로 표시 됩니다. 이 규칙은 중요한 형식 또는 중요한 메서드나 필드를 포함하는 형식이 형식 동등에 참여하는 경우에 적용됩니다. CLR에서 이러한 형식이 검색되면 런타임에 해당 형식이 로드되지 않고 TypeLoadException이 throw됩니다. 일반적으로 이 규칙은 사용자가 tlbimp와 컴파일러를 이용하여 형식 동등을 수행하지 않고 수동으로 형식 동등을 구현하는 경우에만 적용됩니다.|
|[CA2132: 기본 생성자는 최소한 기본 형식 기본 생성자 @ no__t-0 만큼 중요 해야 합니다.|SecurityCriticalAttribute가 있는 형식 및 멤버는 Silverlight 응용 프로그램 코드에서 사용할 수 없습니다. 보안에 중요한 형식 및 멤버는 .NET Framework for Silverlight 클래스 라이브러리의 신뢰할 수 있는 코드에서만 사용할 수 있습니다. 파생 클래스의 public 또는 protected 구성 요소는 투명성이 기본 클래스보다 높거나 같아야 하기 때문에 애플리케이션의 클래스는 SecurityCritical로 표시된 클래스에서 파생될 수 없습니다.|
|[CA2133: 대리자는 투명도 @ no__t-0과 일치 하는 메서드에 바인딩해야 합니다.|이 경고는 SecurityCriticalAttribute를 사용하여 표시된 대리자를 SecuritySafeCriticalAttribute를 사용하여 표시되거나 투명한 메서드에 바인딩하는 메서드에서 발생합니다. 또한 투명하거나 안전에 중요한 대리자를 중요한 메서드에 바인딩하는 메서드에서도 이 경고가 발생합니다.|
|[CA2134: 메서드는 기본 메서드 @ no__t를 재정의할 때 일관 된 투명도를 유지 해야 합니다.|이 규칙은 SecurityCriticalAttribute로 표시된 메서드가 SecuritySafeCriticalAttribute로 표시되거나 투명한 메서드를 재정의할 때 적용됩니다. 또한 SecuritySafeCriticalAttribute로 표시되거나 투명한 메서드가 SecurityCriticalAttribute로 표시된 메서드를 재정의할 때도 이 규칙이 적용됩니다. 이 규칙은 가상 메서드를 재정의하거나 인터페이스를 구현할 때 적용됩니다.|
|[CA2135: 수준 2 어셈블리는 LinkDemands @ no__t를 포함 하지 않아야 합니다.-0|LinkDemands는 수준 2 보안 규칙 집합에서 사용되지 않습니다. JIT(Just-in-Time) 컴파일 시 보안을 적용하는 데 LinkDemands를 사용하는 대신, 해당 메서드, 형식 및 필드를 SecurityCriticalAttribute 특성으로 표시하세요.|
|[CA2136: 멤버는 충돌 하는 투명도 주석을 포함할 수 없습니다. @ no__t-0|투명성 특성은 큰 범위의 코드 요소에서 작은 범위의 요소에 적용됩니다. 범위가 큰 코드 요소의 투명성 특성은 첫 번째 요소에 포함된 코드 요소의 투명성 특성보다 우선합니다. 예를 들어 SecurityCriticalAttribute 특성으로 표시된 클래스에는 SecuritySafeCriticalAttribute 특성으로 표시된 메서드가 포함될 수 없습니다.|
|[CA2137: 투명 한 메서드는 안정형 IL @ no__t를 포함 해야 합니다.-0|메서드가 확인할 수 없는 코드를 포함하거나 형식을 참조로 반환합니다. 이 규칙은 보안 투명 코드에서 확인할 수 없는 MSIL(Microsoft Intermediate Language)을 실행하려고 할 때 적용됩니다. 그러나 이 규칙은 완전한 IL 검증 도구를 포함하지 않으며 대신 추론을 사용하여 MSIL 확인 시 대부분의 위반을 catch합니다.|
|[CA2138: 투명 메서드는 SuppressUnmanagedCodeSecurity 특성 @ no__t를 사용 하 여 메서드를 호출 하면 안 됩니다.|보안 투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 표시된 메서드를 호출합니다.|
|[CA2139: 투명 메서드는 HandleProcessCorruptingExceptions 특성 @ no__t을 사용할 수 없습니다.|이 규칙은 투명 하 고 HandleProcessCorruptedStateExceptionsAttribute 특성을 사용 하 여 프로세스 손상 예외를 처리 하려고 시도 하는 모든 메서드에서 발생 합니다. 프로세스 손상 예외는 <xref:System.AccessViolationException>과 같은 예외의 CLR 버전 4.0 예외 분류입니다. HandleProcessCorruptedStateExceptionsAttribute 특성은 보안에 중요한 메서드에서만 사용할 수 있으며 투명 메서드에 적용되는 경우 무시됩니다.|
|[CA2140: 투명 코드는 보안에 중요 한 항목을 참조 해서는 안 됩니다 @ no__t-0|SecurityTransparentAttribute로 표시된 메서드가 SecurityCritical로 표시된 public이 아닌 멤버를 호출합니다. 이 규칙은 투명 하 고 중요 한 어셈블리의 모든 메서드와 형식을 분석 하 고 투명 코드의 모든 호출을 Securitytreatassafe로로 표시 되지 않은 public이 아닌 중요 코드로 플래그를 표시 합니다.|
|[CA2141: 투명한 메서드는 LinkDemands를 충족해서는 안 됩니다.](../code-quality/ca2141.md)|보안 투명 메서드가 APTCA(AllowPartiallyTrustedCallersAttribute) 특성으로 표시되지 않은 어셈블리의 메서드를 호출하거나, 보안 투명 메서드가 형식 또는 메서드에 대한 LinkDemand를 충족합니다.|
|[CA2142: 투명 코드는 LinkDemands @ no__t로 보호 하면 안 됩니다.-0|이 규칙은 액세스하는 데 LinkDemands가 필요한 투명한 메서드에 적용됩니다. 보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다.|
|[CA2143: 투명 메서드는 보안 요청을 사용 하지 않아야 합니다. @ no__t-0|보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다. 보안 투명 코드는 보안에 중요한 결정을 내리는 데 전체 요청을 사용해야 하며 안전에 중요한 코드는 전체 요청을 위해 투명 코드를 사용해서는 안 됩니다.|
|[CA2144: 투명 코드는 바이트 배열에서 어셈블리를 로드할 수 없습니다. @ no__t-0|투명 코드는 보안에 중요한 동작을 수행할 수 없기 때문에 투명 코드의 보안 검토는 중요 코드에 대한 보안 검토만큼 완벽하지 않습니다. 바이트 배열에서 로드된 어셈블리는 투명 코드에서 발견되지 않을 수 있으며 해당 바이트 배열은 감사할 필요가 없는 중요하거나 특히 안전에 중요한 코드를 포함할 수 있습니다.|
|[CA2145: 투명 메서드는 SuppressUnmanagedCodeSecurityAttribute @ no__t로 데코레이팅 해서는 안 됩니다.|SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅된 메서드에 이를 호출하는 메서드에 대한 암시적 LinkDemand가 배치되어 있습니다. 이 LinkDemand는 호출 코드가 보안을 중요시 하도록 요구합니다. SuppressUnmanagedCodeSecurity를 사용하는 메서드를 SecurityCriticalAttribute 특성으로 표시하면 이 요구 사항이 메서드 호출자에 더욱 명확하게 전달됩니다.|
|[CA2146: 형식은 최소한 기본 형식 및 인터페이스 @ no__t 이상으로 중요 해야 합니다.|이 규칙은 파생 형식에 기본 형식 또는 구현된 인터페이스만큼 중요하지 않은 보안 투명성 특성이 있을 때 적용됩니다. 중요한 기본 형식에서 파생되거나 중요한 인터페이스를 구현할 수 있는 것은 중요한 형식뿐이고, 안전에 중요한 기본 형식에서 파생되거나 안전에 중요한 인터페이스를 구현할 수 있는 것은 중요하거나 안전에 중요한 형식뿐입니다.|
|[CA2147: 투명 메서드는 보안 어설션을 사용할 수 없습니다. @ no__t-0|이 규칙은 100% 투명 어셈블리나 투명/중요 혼합 어셈블리의 모든 메서드와 형식을 분석하고 선언적이거나 명령적인 어설션 사용에 플래그를 지정합니다.|
|[CA2149: 투명 메서드는 네이티브 코드를 호출 해서는 안 됩니다. @ no__t-0|이 규칙은 P/Invoke를 통해 네이티브 코드를 직접 호출 하는 모든 투명 메서드에 대해 발생 합니다. 이 규칙이 위반되면 수준 2 투명성 모델에서 MethodAccessException이 발생하고 수준 1 투명성 모델에서 UnmanagedCode에 대한 완전 요청이 발생합니다.|
|[CA2151: 중요 한 형식이 포함 된 필드는 보안에 중요 @ no__t-0 이어야 합니다.|보안 중요 형식을 사용하려면 이 형식을 참조하는 코드가 보안 중요 또는 보안 안전 중요여야 합니다. 참조가 간접적인 경우에도 마찬가지입니다. 따라서 투명 코드는 필드에 액세스할 수 없으므로 보안 투명 또는 보안 안전 중요 필드가 있을 경우 잘못 해석됩니다.|
|[CA2153: 손상 된 상태 예외를 처리 하지 않습니다. @ no__t-0|[CSE(손상된 상태 예외)](https://msdn.microsoft.com/magazine/dd419661.aspx) 는 프로세스에 메모리 손상이 있음을 나타냅니다. 프로세스 충돌을 허용하는 대신 catch하면 공격자가 손상된 메모리 영역에 익스플로잇을 배치할 수 있는 경우 보안 취약점이 발생할 수 있습니다.|
|[CA2300: 안전 하지 않은 역직렬 변환기 BinaryFormatter @ no__t-0 사용 안 함|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2301: BinaryFormatter를 호출 하지 마세요. 먼저 BinaryFormatter를 설정 하지 않고 Deserialize 합니다. Binder @ no__t-0|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2302: BinaryFormatter를 확인 하십시오. BinaryFormatter를 호출 하기 전에 바인더가 설정 되었는지 확인 하십시오. @ no__t를 Deserialize 합니다.|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2305: 안전 하지 않은 역직렬 변환기 LosFormatter @ no__t 사용 안 함-0|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2310: 안전 하지 않은 역직렬 변환기 NetDataContractSerializer @ no__t 사용 안 함-0|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2311: 먼저 NetDataContractSerializer @ no__t를 설정 하지 않고 deserialize 합니다.|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2312: @ No__t를 deserialize 하기 전에 NetDataContractSerializer이 설정 되어 있는지 확인 하십시오.|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2315: 안전 하지 않은 역직렬 변환기 ObjectStateFormatter @ no__t 사용 안 함-0|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2321: SimpleTypeResolver @ no__t를 사용 하 여 JavaScriptSerializer로 deserialize 안 함-0|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2322: @ No__t를 deserialize 하기 전에 JavaScriptSerializer가 SimpleTypeResolver로 초기화 되지 않았는지 확인 합니다.|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2326: None @ no__t가 아닌 TypeNameHandling 값을 사용 하지 마십시오.|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2327: 안전 하지 않은 JsonSerializerSettings @ no__t 사용 안 함-0|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2328: JsonSerializerSettings이 secure @ no__t-0 인지 확인 합니다.|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2329: 안전 하지 않은 구성을 사용 하 여 JsonSerializer로 deserialize 안 함 @ no__t-0|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2330: @ No__t를 deserialize 할 때 JsonSerializer에 보안 구성이 있는지 확인 합니다.|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA3001: SQL 삽입 취약성에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력 및 SQL 명령으로 작업 하는 경우 SQL 삽입 공격에 유의 해야 합니다. SQL 삽입 공격은 악의적인 SQL 명령을 실행 하 여 응용 프로그램의 보안 및 무결성을 손상 시킬 수 있습니다.|
|[CA3002: XSS 취약점에 대 한 코드 검토 @ no__t-0|웹 요청에서 신뢰할 수 없는 입력으로 작업할 때는 XSS (사이트 간 스크립팅) 공격에 주의 해야 합니다. XSS 공격은 신뢰할 수 없는 입력을 원시 HTML 출력에 삽입 하 여 공격자가 악의적인 스크립트를 실행 하거나 웹 페이지의 콘텐츠를 악의적으로 수정할 수 있도록 합니다.|
|[CA3003: 파일 경로 삽입 취약성에 대 한 코드 검토 @ no__t-0|웹 요청에서 신뢰할 수 없는 입력으로 작업 하는 경우 파일에 대 한 경로를 지정 하는 경우 사용자가 제어 하는 입력을 사용할 수 있습니다.|
|[CA3004: 정보 공개 취약성에 대 한 코드 검토 @ no__t-0|예외 정보를 공개 하면 공격자가 응용 프로그램의 내부 정보를 파악할 수 있으므로 공격자가 다른 취약점을 악용할 수 있습니다.|
|[CA3006: 프로세스 명령 삽입 취약성에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력으로 작업 하는 경우 명령 삽입 공격에 유의 해야 합니다. 명령 삽입 공격은 서버와의 보안 및 무결성을 손상 시키는 기본 운영 체제에서 악성 명령을 실행할 수 있습니다.|
|[CA3007: Open redirect 취약성에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력으로 작업 하는 경우 개방형 리디렉션 취약성에 유의 해야 합니다. 공격자는 오픈 리디렉션 취약성을 악용 하 여 합법적인 URL의 모양을 제공 하는 데 웹 사이트를 사용할 수 있지만, 의심 되는 방문자를 피싱 또는 기타 악성 웹 페이지로 리디렉션할 수 있습니다.|
|[CA3008: XPath 삽입 취약점에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력으로 작업할 때는 XPath 삽입 공격에 유의 해야 합니다. 신뢰할 수 없는 입력을 사용 하 여 XPath 쿼리를 생성 하면 공격자가 쿼리를 악의적으로 조작 하 여 의도 하지 않은 결과를 반환 하 고 쿼리 된 XML의 콘텐츠를 공개할 수 있습니다.|
|[CA3009: XML 삽입 취약점에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력으로 작업 하는 경우 XML 삽입 공격에 유의 해야 합니다.|
|[CA3010: XAML 삽입 취약점에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력으로 작업 하는 경우 XAML 삽입 공격에 유의 해야 합니다. XAML은 개체 인스턴스화 및 실행을 직접적으로 나타내는 태그 언어입니다. 즉, XAML로 생성 된 요소는 시스템 리소스 (예: 네트워크 액세스 및 파일 시스템 IO)와 상호 작용할 수 있습니다.|
|[CA3011: DLL 삽입 취약점에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력으로 작업할 때는 신뢰할 수 없는 코드를 로드 하는 것에 유의 해야 합니다. 웹 응용 프로그램이 신뢰할 수 없는 코드를 로드 하는 경우 공격자가 프로세스에 악성 Dll을 삽입 하 고 악성 코드를 실행할 수 있습니다.|
|[CA3012: Regex 삽입 취약성에 대 한 코드 검토 @ no__t-0|신뢰할 수 없는 입력으로 작업할 때는 regex 삽입 공격에 유의 해야 합니다. 공격자는 regex 주입을 사용 하 여 정규식을 악의적으로 수정 하거나 regex가 의도 하지 않은 결과와 일치 하도록 하거나 regex가 과도 한 CPU를 사용 하 여 서비스 거부 공격을 내릴 수 있습니다.|
|[CA3061: URL @ no__t에서 스키마를 추가 하지 않습니다.-0|위험한 외부 참조를 유발할 수 있으므로 Add 메서드의 unsafe 오버 로드를 사용 하지 마세요.|
|[CA3075: 안전 하지 않은 DTD 처리 @ no__t-0|안전하지 않은 DTDProcessing 인스턴스를 사용하거나 외부 엔터티 소스를 참조하면 파서는 신뢰할 수 없는 입력을 허용하고 공격자에게 중요 한 정보를 공개할 수 있습니다.|
|[CA3076: 안전 하지 않은 XSLT 스크립트 실행 @ no__t-0|.NET 애플리케이션에서 비보안 방식으로 XSLT(Extensible Stylesheets Language Transformations)를 실행하는 경우 프로세서는 공격자에게 중요한 정보를 노출하여 서비스 거부 및 사이트 간 공격을 유발할 수 있는 신뢰할 수 없는 URI 참조를 확인할 수 있습니다.|
|[CA3077: API 디자인, XML 문서 및 XML 텍스트 판독기의 안전 하지 않은 처리 @ no__t-0|XMLDocument 및 XMLTextReader에서 파생된 API를 디자인할 경우 DtdProcessing에 주의해야 합니다. 외부 엔터티 소스를 참조하거나 확인할 때 안전하지 않은 DTDProcessing 인스턴스를 사용하거나 XML에서 안전하지 않은 값을 설정하면 정보가 공개될 수 있습니다.|
|[CA3147: 동사 처리기를 ValidateAntiForgeryToken @ no__t로 표시-0|ASP.NET MVC 컨트롤러를 설계할 때 사이트 간 요청 위조 공격을 염두에 둘 수 있습니다. 교차 사이트 요청 위조 공격은 인증 된 사용자의 악성 요청을 ASP.NET MVC 컨트롤러로 보낼 수 있습니다.|
|[CA5122: P/Invoke 선언은 안전에 중요한 선언이 아니어야 합니다.](../code-quality/ca5122.md)|메서드는 보안에 중요한 작업을 수행할 때 SecuritySafeCritical로 표시되지만, 투명 코드에서도 안전하게 사용할 수 있습니다. 투명 코드는 P/Invoke를 통해 절대 네이티브 코드를 직접 호출할 수 없습니다. 따라서 P/Invoke를 SecuritySafeCritical로 표시할 경우 투명 코드가 P/Invoke를 호출할 수 없으며, 보안 분석에서 잘못 해석하는 원인이 됩니다.|
|[CA5361: 강력한 crypto @ no__t의 SChannel 사용을 사용 하지 않도록 설정 하지 않음-0|@No__t-0을 `true`로 설정 하면 보내는 TLS (전송 계층 보안) 연결에 사용 되는 암호화가 weakens. 약한 암호화는 응용 프로그램과 서버 간 통신의 기밀성을 손상 시켜 공격자가 중요 한 데이터를 보다 쉽게 도청 수 있도록 합니다.|
|[CA5363: 요청 유효성 검사를 사용 하지 않도록 설정 합니다. @ no__t-0|요청 유효성 검사는 HTTP 요청을 검사 하 고 사이트 간 스크립팅을 포함 하 여 삽입 공격으로 이어질 수 있는 잠재적으로 위험한 콘텐츠가 포함 되어 있는지 여부를 확인 하는 ASP.NET의 기능입니다.|
|[CA5364: 사용 되지 않는 보안 프로토콜을 사용 하지 않음 @ no__t-0|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다.|
|[CA5369: XmlReader를 사용 하 여 @ no__t를 Deserialize 합니다.-0|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 해야 하는 위험한 외부 참조를 로드할 수 있습니다.|
|[CA5370: XmlReader를 사용 하 여 판독기 @ no__t의 유효성을 검사 합니다.-0|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 이 위험한 로드는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 하 여 제한할 수 있습니다.|
|[CA5371: 스키마 읽기에 XmlReader 사용 @ no__t-0|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 보안 해결 프로그램을 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않는 XmlReader를 사용 하면이이 제한 됩니다.|
|[CA5372: XPathDocument @ no__t에 XmlReader 사용-0|신뢰할 수 없는 데이터에서 XML을 처리 하면 위험한 외부 참조가 로드 될 수 있으며,이는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 처리를 사용 하지 않도록 설정할 수 있습니다.|
|[CA5373: 사용 하지 않는 키 파생 함수 @ no__t를 사용 하지 마십시오.|이 규칙은 약한 키 파생 메서드 (<xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 및 `Rfc2898DeriveBytes.CryptDeriveKey`)의 호출을 검색 합니다. <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName>은 약한 알고리즘 PBKDF1을 사용 했습니다.|
|[CA5378: ServicePointManagerSecurityProtocols를 사용 하지 않도록 설정 합니다. @ no__t-0|@No__t-0을 `true`로 설정 하면 TLS 1.0를 사용 하 여 Windows Communication Framework의 TLS (전송 계층 보안) 연결을 제한 합니다. 해당 버전의 TLS는 더 이상 사용 되지 않습니다.|
|[CA5380: 루트 저장소에 인증서를 추가 하지 않습니다. @ no__t-0|이 규칙은 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca 집합을 사용 하 여 구성 됩니다.|
|[CA5381: 인증서가 루트 저장소에 추가 되지 않았는지 확인 @ no__t-0|이 규칙은 잠재적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca (인증 기관) 집합으로 구성 됩니다.|
|[CA5386: 하드 코딩 하지 않음 SecurityProtocolType 값 @ no__t-0|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램의 보안을 유지 하려면 프로토콜 버전을 하드 코딩 하지 않고 .NET Framework v 4.7.1 이상을 대상으로 해야 합니다.|
|[CA5389: 대상 파일 시스템 경로에 보관 항목의 경로를 추가 하지 않습니다 @ no__t-0|파일 경로는 상대적일 수 있으며, 예상 된 파일 시스템 대상 경로 외부에서 파일 시스템에 액세스할 수 있으며,이로 인해 악의적인 구성 변경 내용 및 대기 방식 기술을 통해 원격 코드를 실행할 수 있습니다.|
|[CA5397: 사용 되지 않는 SslProtocols 값 @ no__t를 사용 하지 마십시오.|TLS (ransport Layer Security)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다.|
|[CA5398: 하드 코드 되는 SslProtocols 값을 사용 하지 않습니다. @ no__t-0|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램이 안전 하 게 유지 되도록 하려면 프로토콜 버전을 하드 코딩 하지 마십시오.|
