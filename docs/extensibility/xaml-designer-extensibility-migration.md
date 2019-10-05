---
title: XAML 디자이너 확장성 마이그레이션
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 9f5085c7a655f186c3c8a4a6eecada8b440650cd
ms.sourcegitcommit: 528178a304e66c0cb7ab98b493fe3c409f87493a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273214"
---
# <a name="xaml-designer-extensibility-migration"></a>XAML 디자이너 확장성 마이그레이션

Visual Studio 2019에서 XAML 디자이너는 두 가지 아키텍처, 즉 디자이너 격리 아키텍처와 최신 표면 격리 아키텍처를 지원 합니다. 이 아키텍처 전환은 .NET Framework 프로세스에서 호스팅될 수 없는 대상 런타임을 지원 하기 위해 필요 합니다. Surface 격리 아키텍처로 전환 하면 타사 확장성 모델에 대 한 주요 변경 내용이 도입 됩니다. 이 문서에서는 Visual Studio 2019 이상 버전 16.3에서 사용할 수 있는 이러한 변경 내용에 대해 간략하게 설명 합니다.

**디자이너 격리** 는 .NET Framework를 대상으로 하는 프로젝트에 대해 WPF 디자이너에서 사용 되며, *디자인 .dll* 확장명을 지원 합니다. 사용자 코드, 컨트롤 라이브러리 및 타사 확장은 실제 디자이너 코드 및 디자이너 패널과 함께 외부 프로세스 (*xdesproc.exe*)에 로드 됩니다.

**Surface 격리** 는 UWP 디자이너에서 사용 됩니다. .NET Core를 대상으로 하는 프로젝트에 대해서도 WPF 디자이너에서 사용 됩니다. 화면 격리에서 사용자 코드와 컨트롤 라이브러리는 개별 프로세스로 로드 되 고 디자이너와 패널은 Visual Studio 프로세스 (*devenv.exe*)에서 로드 됩니다. 사용자 코드 및 컨트롤 라이브러리를 실행 하는 데 사용 되는 런타임은 실제 디자이너와 타사 확장성 코드의 .NET Framework에서 사용 하는 런타임과 다릅니다.

![확장성-마이그레이션-아키텍처](media/xaml-designer-extensibility-migration-architecture.png)

이러한 아키텍처 전환으로 인해 타사 확장은 더 이상 타사 컨트롤 라이브러리와 동일한 프로세스에 로드 되지 않습니다. 확장은 더 이상 컨트롤 라이브러리에 대 한 직접 종속성을 가지 지 않거나 런타임 개체에 직접 액세스할 수 없습니다. 이전에는 *Microsoft.* m a m. d m l을 사용 하 여 디자이너 격리 아키텍처용으로 작성 된 확장을 surface 격리 아키텍처를 사용 하는 새로운 방법으로 마이그레이션해야 합니다. 실제로 기존 확장은 새 확장성 API 어셈블리에 대해 컴파일해야 합니다. 컨트롤 라이브러리가 다른 프로세스에서 로드 되었으므로 [typeof](/dotnet/csharp/language-reference/keywords/typeof) 또는 런타임 인스턴스를 통해 런타임 컨트롤 형식에 대 한 액세스를 대체 하거나 제거 해야 합니다.

## <a name="new-extensibility-api-assemblies"></a>새 확장성 API 어셈블리

새 확장성 API 어셈블리는 기존 확장성 API 어셈블리와 유사 하지만 다른 이름 지정 체계를 따라 구분 합니다. 마찬가지로, 네임 스페이스 이름이 새 어셈블리 이름을 반영 하도록 변경 되었습니다.

| 디자이너 격리 API 어셈블리            | Surface 격리 API 어셈블리                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>새 파일 확장명 및 검색

*디자인 .dll* 파일 확장명을 사용 하는 대신 *. designtools .dll* 파일 확장명을 사용 하 여 새 노출 확장을 검색 합니다. *. 디자인 .dll* 및 *designtools .dll* 확장명은 동일한 *디자인* 하위 폴더에 있을 수 있습니다.

타사 컨트롤 라이브러리가 실제 대상 런타임 (.NET Core 또는 UWP)에 대해 컴파일되기는 하지만, *designtools .dll* 확장명은 항상 .NET Framework 어셈블리로 컴파일해야 합니다.

## <a name="decouple-attribute-tables-from-run-time-types"></a>런타임 형식에서 특성 테이블 분리

Surface 격리 확장성 모델에서는 확장이 실제 컨트롤 라이브러리에 종속 되는 것을 허용 하지 않으므로 확장 프로그램은 컨트롤 라이브러리의 형식을 참조할 수 없습니다. 예를 들어 *Mylibrary* . *c l i*e n t. c l i d.

이러한 종속성은 특성 테이블을 통해 형식에 대 한 메타 데이터를 등록할 때 가장 일반적입니다. [Typeof](/dotnet/csharp/language-reference/keywords/typeof) 또는 [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) 을 통해 컨트롤 라이브러리 형식을 직접 참조 하는 확장 코드는 문자열 기반 형식 이름을 사용 하 여 새 api로 대체 됩니다.

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>기능 공급자 및 모델 API

기능 공급자는 확장 어셈블리에서 구현 되 고 Visual Studio 프로세스에 로드 됩니다. `FeatureAttribute`는 [typeof](/dotnet/csharp/language-reference/keywords/typeof)를 사용 하 여 기능 공급자 형식을 직접 참조 합니다.

현재 지원 되는 기능 공급자는 다음과 같습니다.

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`
* `DesignModeValueProvider`는 또는 디자이너에서 수정할 때 `TranslatePropertyValue` 를 통해 `InvalidateProperty` 호출 되는 제한 사항으로 지원 됩니다. 런타임 코드에서 수정할 때 호출 되지 않습니다.

기능 공급자는 이제 실제 런타임 코드 및 컨트롤 라이브러리와 다른 프로세스에서 로드 되므로 더 이상 런타임 개체에 직접 액세스할 수 없습니다. 대신 이러한 모든 상호 작용을 해당 모델 기반 Api를 사용 하도록 변환 해야 합니다. 모델 API가 <xref:System.Type> 업데이트 되 고 또는 <xref:System.Object> 에 대 한 액세스를 더 이상 사용할 수 없거나 `TypeIdentifier` 및 `TypeDefinition`로 대체 되었습니다.

`TypeIdentifier`형식을 식별 하는 어셈블리 이름이 없는 문자열을 나타냅니다. 는 형식에 대 한 추가 `TypeDefinition` 정보를 쿼리 하기 위해로 확인 될 수있습니다.`TypeIdenfifier` `TypeDefinition`인스턴스는 확장 코드에서 캐시할 수 없습니다.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

Surface 격리 확장성 API 집합에서 제거 된 Api:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`
* `AssemblyReferences.GetTypes(Type baseType)`

대신를 사용 `TypeIdentifier` 하는 api: <xref:System.Type>

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ModelFactory.ResolveType(EditingContext context, Type)`를 `MetadataFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`로 변경
* `ModelService.ResolveType(TypeIdentifier typeIdentifier)`를 `MetadataService.ResolveType(TypeIdentifier typeIdentifier)`로 변경
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

대신를 사용 `TypeIdentifier`하는 api는더이상생성자인수를지원하지않습니다.<xref:System.Type>

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

대신를 사용 `TypeDefinition` 하는 api: <xref:System.Type>

* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`
* `PropertyEntry.PropertyType`

대신를 사용 `AssemblyIdentifier` 하는 api: `<xref:System.Reflection.AssemblyName?displayProperty=fullName>`

* `AssemblyReferences.ReferencedAssemblies`
* `AssemblyReferences.LocalAssemblyName`를 `AssemblyReferences.LocalAssemblyIdentifier`로 변경

또한와 같은 `SetValue` api는대상런타임으로변환될수있는기본형식또는기본제공.NETFramework형식의인스턴스만지원합니다.`ModelItem` 현재 다음과 같은 형식이 지원 됩니다.

* 기본 .NET Framework 형식: `Boolean`, `Byte`, `Char` `DateTime` ,,`Double` ,`Guid`, ,,`SByte` ,, ,`Nullable` `Int16` `Enum` `Int32` `Int64` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* 알려진 WPF .NET Framework 형식 (및 파생 형식): `Brush` `CornerRadius` `Duration` `EasingMode` `Color` `CompositeTransform` `EasingFunctionBase` ,,`EllipseGeometry`, ,,,,,,,`FontFamily` `GeneralTransform` `Geometry` , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

예:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

[Xaml 디자이너-확장성-샘플](https://github.com/microsoft/xaml-designer-extensibility-samples) 리포지토리에서 더 많은 코드 샘플을 사용할 수 있습니다.

## <a name="limited-support-for-designdll-extensions"></a>. 디자인 .dll 확장에 대 한 지원이 제한적입니다.

컨트롤 라이브러리에 대해 *designtools .dll* 확장명이 검색 되 면이를 먼저 로드 하 고를 검색 *합니다. 디자인 .dll* 확장을 건너뜁니다.

*Designtools .dll* 확장명이 없지만 *. design .DLL* 확장명이 있으면 XAML 언어 서비스는 기본 편집기 및 속성 검사자 시나리오를 지원 하기 위해이 어셈블리를 로드 하 여 특성 테이블 정보를 추출 하려고 합니다. 이 메커니즘은 범위 내에서 제한 됩니다. 기능 공급자를 실행 하기 위해 디자이너 격리 확장을 로드 하는 것을 허용 하지 않지만 기존 WPF 컨트롤 라이브러리에 대 한 기본 지원을 제공할 수 있습니다.
