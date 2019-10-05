---
title: 등록 하 고 Vspackage 등록 취소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334300"
---
# <a name="register-and-unregister-vspackages"></a>등록 하 고 Vspackage 등록 취소
특성을 사용 하 여 VSPackage를 등록 하지만

## <a name="register-a-vspackage"></a>VSPackage 등록
 관리 되는 Vspackage의 등록을 제어 하려면 특성을 사용할 수 있습니다. 에 포함 된 모든 등록 정보를 *.pkgdef* 파일입니다. 파일 기반 등록에 대 한 자세한 내용은 참조 하세요. [CreatePkgDef 유틸리티](../extensibility/internals/createpkgdef-utility.md)합니다.

 다음 코드에는 표준 등록 특성을 사용 하 여 VSPackage를 등록 하는 방법을 보여 줍니다.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>확장 등록 취소
 실행 하기만 하면 많은 다른 Vspackage 사용 하 여 실험 되어 있는 경우 실험적 인스턴스에서 제거할 합니다 **재설정** 명령입니다. 검색할 **Visual Studio 실험적 인스턴스 다시 설정** 컴퓨터의 시작 페이지에서 또는 명령줄에서이 명령을 실행 합니다.

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 사용자가 설치한 Visual Studio의 개발 인스턴스에서 확장을 제거 하려는 경우 이동할 **도구** > **확장 및 업데이트**확장을 찾고 클릭 **제거**합니다.

 어떤 이유로 이러한 메서드의 모두 확장을 제거에 성공 하면 명령줄에서 VSPackage 어셈블리를 다음과 같이 등록 취소할 수 있습니다.

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>사용자 지정 등록 특성을 사용 하 여 확장명 등록

특정 한 경우 확장 프로그램에 대해 새 등록 특성을 만드는 해야 합니다. 새 레지스트리 키를 추가 하거나 기존 키를 새 값을 추가 하려면 등록 특성을 사용할 수 있습니다. 새 특성에서 파생 되어야 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 및 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> 메서드.

### <a name="create-a-custom-attribute"></a>사용자 지정 특성 만들기

다음 코드에는 새 등록 특성을 만드는 방법을 보여 줍니다.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute> 특성 클래스에는 프로그램 요소 (클래스, 메서드 등)를 특성 관계가 있는,이 사용할 수 있는지 여부를 두 번 이상 상속할 수 있는지 여부를 지정 하는 데 사용 됩니다.

### <a name="create-a-registry-key"></a>레지스트리 키 만들기

다음 코드에서는 사용자 지정 특성 만듭니다는 **사용자 지정** 등록 되는 VSPackage에 대 한 키 아래 하위 키입니다.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>기존 레지스트리 키 아래에서 새 값

기존 키를 사용자 지정 값을 추가할 수 있습니다. 다음 코드를 VSPackage 등록 키를 새 값을 추가 하는 방법을 보여 줍니다.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>참고자료
- [VSPackage](../extensibility/internals/vspackages.md)
