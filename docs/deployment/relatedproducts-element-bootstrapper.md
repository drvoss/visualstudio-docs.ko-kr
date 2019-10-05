---
title: '&lt;RelatedProducts&gt; 요소 (부트스트래퍼) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42756b21e631ec14e9c590833f6f0e95a317cc22
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747466"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; 요소 (부트스트래퍼)
`RelatedProducts` 요소에 종속 되거나 현재 제품에 포함 된 다른 제품을 정의 합니다.

## <a name="syntax"></a>구문

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 합니다 `RelatedProducts` 요소인 자식은 `Product` 요소입니다. 특성이 없습니다.

## <a name="dependsonproduct"></a>DependsOnProduct
 `DependsOnProduct` 요소 나타냅니다 현재 전에 명명된 된 제품을 설치 해야 하 고 현재 제품 명명된 된 제품에 따라 달라 집니다. 자식 이기는 `RelatedProducts` 요소입니다. A `RelatedProducts` 요소는 하나 이상의 있을 `DependsOnProduct` 요소입니다.

 `DependsOnProduct` 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Code`|에 지정 된 대로 포함된 된 제품의 코드명 합니다 `ProductCode` 특성을 `Product` 요소. 자세한 내용은 [ \<제품 > 요소](../deployment/product-element-bootstrapper.md)합니다.|

## <a name="eitherproducts"></a>EitherProducts
 `EitherProducts` 요소는 0 개 이상 정의 `DependsOnProduct` 요소에 특성이 없습니다. 하나 이상의 `DependsOnProduct` 이 집합의 현재 제품 하기 전에 설치 수 해야 합니다. A `RelatedProducts` 요소는 0 개 이상 포함할 수 있습니다 `EitherProducts` 요소입니다.

## <a name="includesproduct"></a>IncludesProduct
 `IncludesProduct` 제품 현재 설치에 포함 되며 별도 설치 하지 않아도 요소를 나타냅니다. 자식 이기는 `RelatedProducts` 요소입니다. A `RelatedProducts` 요소는 하나 이상의 있을 `IncludesProduct` 요소입니다.

 `IncludesProduct` 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Code`|에 지정 된 대로 포함된 된 제품의 코드명 합니다 `ProductCode` 특성을 `Product` 요소. 자세한 내용은 [ \<제품 > 요소](../deployment/product-element-bootstrapper.md)합니다.|

## <a name="example"></a>예제
 다음 코드 예제에서는 Microsoft Installer.NET Framework와 함께 설치 하 고 따라서 별도 설치 하지 않아도 됩니다 지정 합니다.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>참고자료
- [\<제품 > 요소](../deployment/product-element-bootstrapper.md)