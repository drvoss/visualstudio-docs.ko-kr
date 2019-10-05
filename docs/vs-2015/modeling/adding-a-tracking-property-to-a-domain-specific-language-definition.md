---
title: 도메인별 언어 정의에 추적 속성 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 814327befe538bfaa102b198988e76dbd52090bb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705695"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>도메인별 언어 정의에 추적 속성 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 도메인 모델에 추적 속성을 추가 하는 방법을 보여 줍니다.  
  
 A *도메인 추적* 속성은 사용자가 업데이트할 수는 있지만 다른 요소나 도메인 속성의 값을 사용 하 여 계산 되는 기본 값 속성입니다.  
  
 예를 들어, 도메인 특정 언어 도구 (DSL 도구), 도메인 클래스의 속성에는 도메인 클래스가 아니라 사용자의 이름을 사용 하 여 계산 되는 기본값이 표시 이름을 디자인 타임에 값을 변경 하거나 수 계산된 된 값으로 다시 설정 합니다.  
  
 이 연습에서는 모델의 기본 Namespace 속성을 기반으로 기본 값이 있는 속성을 추적 하는 Namespace가 있는 도메인 특정 언어 (DSL)를 만듭니다. 속성을 추적 하는 방법에 대 한 자세한 내용은 참조 하세요. [추적 속성 정의](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be)합니다.  
  
- 추적 속성 설명자 DSL 도구 지원입니다. 그러나 추적 속성을 추가 하려면 DSL 디자이너를 사용할 수 없습니다. 따라서 정의 및 추적 속성을 구현 하는 사용자 지정 코드를 추가 해야 합니다.  
  
  추적 속성에 두 개의 상태:, 추적 및 사용자가 업데이트 됩니다. 추적 속성에는 다음과 같은 기능이 있습니다.  
  
- 추적 상태에 있을 때 하 고 추적 속성의 값을 계산한 다음 값이 모델 변경의 다른 속성으로 업데이트 됩니다.  
  
- 업데이트 된 경우 추적 속성의 값을 사용자 상태에 의해 사용자 속성이 마지막으로 설정 된 값을 유지 합니다.  
  
- 에 **속성** 창을 **재설정** 속성이 업데이트 된 경우에 추적 속성 가능 명령은 사용자 상태에 따라 합니다. 합니다 **재설정** 추적 속성을 설정 하는 명령 상태를 추적 합니다.  
  
- 에 **속성** 창, 추적 속성 추적 상태를 해당 값은 일반 글꼴로 표시 됩니다.  
  
- 에 **속성** 창 추적 속성이 업데이트 된 경우 사용자 상태에 의해 해당 값은 굵은 글꼴로 표시 됩니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 시작 하기 전에 이러한 구성 요소를 먼저 설치 해야 합니다.  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../includes/dsl-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>DSL 프로젝트 만들기  
 도메인 특정 언어에 대 한 프로젝트를 만듭니다.  
  
#### <a name="to-create-the-project"></a>프로젝트를 만들려면  
  
1. 도메인 특정 언어 디자이너 프로젝트를 만듭니다. 이 EventHandler의 이름을 `TrackingPropertyDSL`로 지정합니다.  
  
2. 에 **도메인별 언어 디자이너 마법사**, 다음 옵션을 설정 합니다.  
  
    1. 선택 된 **MinimalLanguage** 템플릿.  
  
    2. 도메인 특정 언어에 대 한 기본 이름을 사용 하 여 `TrackingPropertyDSL`입니다.  
  
    3. 모델 파일에 대 한 확장을 설정 `trackingPropertyDsl`합니다.  
  
    4. 모델 파일에 대 한 기본 템플릿 아이콘을 사용 합니다.  
  
    5. 제품의 이름을 설정 `Product Name`합니다.  
  
    6. 회사의 이름을 설정 `Company Name`합니다.  
  
    7. 솔루션에서 프로젝트에 대 한 루트 네임 스페이스에 대 한 기본값을 사용 하 여 `CompanyName.ProductName.TrackingPropertyDSL`입니다.  
  
    8. 어셈블리의 강력한 이름 키 파일을 만드는 마법사를 허용 합니다.  
  
    9. 솔루션의 세부 정보를 검토 한 다음 클릭 **완료** DSL 정의 프로젝트를 만듭니다.  
  
## <a name="customizing-the-default-dsl-definition"></a>기본 DSL 정의 사용자 지정  
 이 섹션에서는 다음 항목을 포함 하 여 DSL 정의 사용자 지정 합니다.  
  
- 모델의 모든 요소에 대 한 속성을 추적 하는 Namespace입니다.  
  
- 모델의 모든 요소에 대 한 부울 IsNamespaceTracking 속성입니다. 이 속성은 추적 상태 또는 업데이트 된 추적 속성 인지를 표시 하 여 사용자 상태입니다.  
  
- 모델에 대 한 기본 Namespace 속성입니다. 추적 속성 Namespace의 기본 값을 계산 하려면이 속성을 사용 됩니다.  
  
- 모델에 대 한 계산 CustomElements 속성입니다. 이 속성은 사용자 지정 네임 스페이스를 포함 하는 요소의 비율을 나타냅니다.  
  
#### <a name="to-add-the-domain-properties"></a>도메인 속성을 추가 하려면  
  
1. DSL 디자이너에서 마우스 오른쪽 단추로 클릭 합니다 **ExampleModel** 도메인 클래스를 가리킵니다 **추가**를 클릭 하 고 **DomainProperty**합니다.  
  
    1. 새 속성의 이름을 `DefaultNamespace`입니다.  
  
    2. 에 **속성** 새 속성에 대 한 창 **기본값** 에 `DefaultNamespace`, 설정 **형식** 를 **문자열**.  
  
2. 에 **ExampleModel** 도메인 클래스, 라는 도메인 속성에 추가 `CustomElements`합니다.  
  
     에 **속성** 새 속성에 대 한 창 **종류** 에 **계산**합니다.  
  
3. 에 **ExampleElement** 도메인 클래스, 라는 도메인 속성에 추가 `Namespace`합니다.  
  
     에 **속성** 새 속성에 대 한 창 **Is Browsable** 에 **False**, 설정 **종류** 에 **CustomStorage** .  
  
4. 에 **ExampleElement** 도메인 클래스, 라는 도메인 속성에 추가 `IsNamespaceTracking`합니다.  
  
     에 **속성** 새 속성에 대 한 창 **Is Browsable** 에 **False**설정 **기본값** 를 `true`, 설정 **형식** 하 **부울**합니다.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>다이어그램 요소 및 DSL 세부 정보를 업데이트 하려면  
  
1. DSL 디자이너에서 마우스 오른쪽 단추로 클릭 합니다 **ExampleShape** 기 하 도형, 가리킨 **추가**를 클릭 하 고 **텍스트 Decorator**합니다.  
  
    1. 새 텍스트 decorator 이름을 `NamespaceDecorator`입니다.  
  
    2. 에 **속성** 텍스트 decorator에 대 한 창 **위치** 에 **InnerBottomLeft**합니다.  
  
2. DSL 디자이너에서 연결 하는 선을 선택 합니다 **ExampleElement** 클래스는 **ExampleShape** 셰이프.  
  
    1. 에 **DSL 세부 정보** 창에서 합니다 **Decorator 맵** 탭 합니다.  
  
    2. 에 **데코레이터** 목록에서 **NamespaceDecorator**을 확인란을 선택 한 후는 **속성을 표시** 목록에서 **Namespace**.  
  
3. **DSL 탐색기**, 확장을 **도메인 클래스** 폴더를 마우스 오른쪽 단추로 클릭 합니다 **ExampleElement** 노드를 차례로 클릭 한 다음 **새 도메인 형식 설명자 추가**.  
  
    1. 확장을 **ExampleElement** 노드를 차례로 선택 합니다 **사용자 지정 형식 설명자 (도메인 형식 설명자)** 노드.  
  
    2. 에 **속성** 도메인 형식 설명자에 대 한 창 **사용자 지정 코딩** 에 **True**.  
  
4. **DSL 탐색기**를 선택 합니다 **Xml 직렬화 동작** 노드.  
  
    1. 에 **속성** 창에서 **사용자 지정 게시 로드** 하 **True**합니다.  
  
## <a name="transforming-templates"></a>변환 템플릿  
 Dsl 도메인 클래스 및 속성을 정의 했으므로 프로젝트에 대 한 코드를 다시 생성으로 DSL 정의 올바르게 변환할 수 있습니다를 확인할 수 있습니다.  
  
#### <a name="to-transform-the-text-templates"></a>텍스트 템플릿 변환  
  
1. 에 **솔루션 탐색기** 도구 모음에서 클릭 **모든 템플릿 변환**합니다.  
  
2. 솔루션에 대 한 코드를 다시 생성 하 고 DslDefinition.dsl을 저장 하는 시스템입니다. 정의 파일의 XML 형식에 대 한 정보를 참조 하세요 [DslDefinition.dsl 파일](../modeling/the-dsldefinition-dsl-file.md)합니다.  
  
## <a name="creating-files-for-custom-code"></a>사용자 지정 코드에 대 한 파일 만들기  
 모든 서식 파일을 변환 하는 경우 시스템 Dsl 및 DslPackage 프로젝트에서 도메인 특정 언어를 정의 하는 소스 코드를 생성 합니다. 생성된 된 텍스트를 사용 하 여 방해를 방지 하는 생성된 된 코드 파일에서 고유한 파일에 사용자 지정 코드를 작성 합니다.  
  
 값 및 추적 속성의 상태를 유지 관리 하기 위한 코드를 제공 해야 합니다. 생성된 된 코드에서 사용자 지정 코드를 쉽게 구별할 수 있도록 하 고 파일 이름 충돌을 방지 하려면 별도 하위 폴더에 사용자 지정 코드 파일을 배치 합니다.  
  
#### <a name="to-create-the-code-files"></a>코드 파일을 만들려면  
  
1. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **DSL** 프로젝트를 가리키도록 **추가**, 클릭 하 고 **새 폴더**. 새 폴더 이름을 `CustomCode`입니다.  
  
2. 새을 마우스 오른쪽 단추로 클릭 **CustomCode** 폴더를 가리키고 **추가**를 클릭 하 고 **새 항목**합니다.  
  
3. 선택 합니다 **코드 파일** 템플릿을 설정 합니다 **이름** 에 `NamespaceTrackingProperty.cs`, 클릭 하 고 **확인**.  
  
     NamespaceTrackingProperty.cs 파일을 만들고 편집 하기 위해 열려 있습니다.  
  
4. 폴더에서 다음 코드 파일을 만듭니다: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, 및 `TypeDescriptor.cs`합니다.  
  
5. 에 **DslPackage** 프로젝트를 만들 수도 `CustomCode` 폴더를 추가 하 고는 `Package.cs` 코드 파일.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>추적 속성을 지원 하기 위한 도우미 클래스를 추가 합니다.  
 HelperClasses.cs 파일에 추가 합니다 `TrackingHelper` 고 `CriticalException` 다음과 같이 클래스입니다. 이 연습의 뒷부분에서 이러한 클래스를 참조 하 게 됩니다.  
  
#### <a name="to-add-the-helper-classes"></a>도우미 클래스를 추가 하려면  
  
1. HelperClasses.cs 파일에 다음 코드를 추가 합니다.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>사용자 지정 형식 설명자에 대 한 사용자 지정 코드 추가  
 구현 된 `GetCustomProperties` 에 대 한 형식 설명자에 대 한 메서드는 `ExampleModel` 도메인 클래스입니다.  
  
> [!NOTE]
> DSL 도구에 대 한 사용자 지정 형식 설명자에 대해 생성 하는 코드 `ExampleModel` 호출 `GetCustomProperties`하지만 DSL 도구는 메서드를 구현 하는 코드를 생성 하지 않습니다.  
  
 추적이이 메서드를 정의 하면 추적 속성 Namespace에 대 한 속성 설명자입니다. 또한 사용 추적 속성에 대 한 특성을 제공 합니다 **속성** 창에 속성을 올바르게 표시 합니다.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>ExampleModel 도메인 클래스에 대 한 형식 설명자를 수정 하려면  
  
1. TypeDescriptor.cs 파일에 다음 코드를 추가 합니다.  
  
    ```csharp  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>패키지에 대 한 사용자 지정 코드 추가  
 생성된 된 코드 ExampleElement 도메인 클래스에 대 한 형식 설명 공급자를 정의합니다. 그러나이 형식 설명 공급자를 사용 하 여 DSL을 지시 하는 코드를 추가 해야 합니다.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>에 사용자 지정 형식 설명자를 사용 하 여 DSL 패키지를 업데이트 하려면  
  
1. Package.cs 파일에 다음 코드를 추가 합니다.  
  
    ```csharp  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>모델에 대 한 사용자 지정 코드 추가  
 구현 된 `GetCustomElementsValue` 에 대 한 메서드는 `ExampleModel` 도메인 클래스입니다.  
  
> [!NOTE]
> DSL 도구에 대 한 생성 하는 코드 `ExampleModel` 호출 `GetCustomElementsValue`하지만 DSL 도구는 메서드를 구현 하는 코드를 생성 하지 않습니다.  
  
 정의 된 `GetCustomElementsValue` CustomElements 계산 된 속성에 대 한 논리를 제공 하는 메서드 `ExampleModel`합니다. 이 메서드는 횟수를 계산 `ExampleElement` 사용자 업데이트 값이 모델의 총 요소에 대 한 비율로이 개수를 나타내는 문자열을 반환 하는 속성을 추적 하는 Namespace 있는 도메인 클래스입니다.  
  
 를 추가할는 `OnDefaultNamespaceChanged` 메서드를 `ExampleModel`, 재정의 및를 `OnValueChanged` 메서드를 `DefaultNamespacePropertyHandler` 중첩 된 클래스의 `ExampleModel` 호출 `OnDefaultNamespaceChanged`.  
  
 DefaultNamespace 속성 추적 속성, Namespace 계산에 사용 되기 때문 `ExampleModel` 모든 알려야 `ExampleElement` DefaultNamespace의 값이 변경 된 도메인 클래스입니다.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>추적 된 속성에 대 한 속성 처리기를 수정 하려면  
  
1. ExampleModel.cs 파일에 다음 코드를 추가 합니다.  
  
    ```csharp  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>추적 속성에 대 한 사용자 지정 코드 추가  
 추가 된 `CalculateNamespace` 메서드를는 `ExampleElement` 도메인 클래스입니다.  
  
 이 메서드를 정의의 계산 CustomElements 속성에 대 한 논리를 제공 `ExampleModel`합니다. 이 메서드는 횟수를 계산 `ExampleElement` 도메인 클래스는 Namespace 추적 중인 업데이트 된 속성이 있는 사용자 상태에 따라 모델의 총 요소에 대 한 비율로이 수를 나타내는 문자열을 반환 합니다.  
  
 또한, 저장소 및 가져오고의 Namespace 사용자 지정 저장소 속성을 설정 하는 메서드를 추가 합니다 `ExampleElement` 도메인 클래스입니다.  
  
> [!NOTE]
> 하지만 DSL 도구에 대 한 생성 하는 코드 `ExampleModel` get 호출 메서드를 설정 하 고 DSL 도구 메서드를 구현 하는 코드를 생성 하지 않습니다 됩니다.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>사용자 지정 형식 설명자에 대 한 메서드를 추가 하려면  
  
1. NamespaceTrackingProperty.cs 파일에 다음 코드를 추가 합니다.  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>Serialization을 지원 하기 위해 사용자 지정 코드 추가  
 XML serialization에 대 한 사용자 지정 후 로드 동작을 지 원하는 코드를 추가 합니다.  
  
> [!NOTE]
> 그러나 DSL 도구는 호출을 생성 하는 코드를 `OnPostLoadModel` 및 `OnPostLoadModelAndDiagram` 메서드 DSL 도구는 이러한 메서드를 구현 하는 코드 생성 하지 않습니다.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>사용자 지정 로드 후 동작을 지원 하도록 코드를 추가 하려면  
  
1. Serialization.cs 파일에 다음 코드를 추가 합니다.  
  
    ```csharp  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>언어를 테스트합니다.  
 다음 단계에서에서 빌드 및 실행은 DSL 디자이너의 새 인스턴스를 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 추적 속성 제대로 작동 하는지 확인할 수 있도록 합니다.  
  
#### <a name="to-exercise-the-language"></a>언어를 실행 하려면  
  
1. **빌드** 메뉴에서 **솔루션 다시 빌드**를 클릭합니다.  
  
2. **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.  
  
     실험적 빌드 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 열립니다 합니다 **디버깅** 빈 테스트 파일을 포함 하는 솔루션입니다.  
  
3. **솔루션 탐색기**Test.trackingPropertyDsl 파일을 디자이너에서 열을 두 번 클릭 하 고 디자인 화면을 클릭 합니다.  
  
     되었는지 확인 합니다 **속성** 다이어그램 창을 **Default Namespace** 속성은 **DefaultNamespace**, 및 **사용자지정요소** 속성은 **0/0**합니다.  
  
4. 끌어서를 **ExampleElement** 요소를 **도구 상자** 다이어그램 화면.  
  
5. 에 **속성** 선택 요소에 대 한 창 합니다 **요소 Namespace** 속성에서 값을 변경 하 고 **DefaultNamespace** 를  **OtherNamespace**합니다.  
  
     값 **요소 Namespace** 이제 굵게 표시 됩니다.  
  
6. 에 **속성** 창에서 마우스 오른쪽 단추로 클릭 **요소 Namespace**, 클릭 하 고 **재설정**.  
  
     속성의 값으로 변경 됩니다 **DefaultNamespace**, 값이 일반 글꼴로 표시 됩니다.  
  
     마우스 오른쪽 단추로 클릭 **요소 Namespace** 다시 합니다. 합니다 **재설정** 속성은 현재 추적 상태 때문에 이제 명령이 비활성화 됩니다.  
  
7. 다른 끌어 **ExampleElement** 에서 합니다 **도구 상자** 다이어그램 화면을 변경 해당 **요소 Namespace** 를 **OtherNamespace**합니다.  
  
8. 디자인 화면을 클릭 합니다.  
  
     에 **속성** 다이어그램의 값에 대 한 창 **사용자 지정 요소** 되었습니다 **1/2**합니다.  
  
9. 변경 **Default Namespace** 에서 다이어그램에 대 한 **DefaultNamespace** 하 **NewNamespace**합니다.  
  
     **Namespace** 첫 번째 요소 트랙 합니다 **Default Namespace** 속성을 반면를 **Namespace** 요소 초의 의사용자로업데이트된값을그대로유지 **OtherNamespace**합니다.  
  
10. 솔루션을 저장 하 고 실험적 빌드를 닫습니다.  
  
## <a name="next-steps"></a>다음 단계  
 둘 이상의 추적 속성을 사용 하거나 둘 이상의 DSL에 추적 속성을 구현 하려는 경우 각 추적 속성을 지원 하기 위한 일반적인 코드를 생성 하려면 텍스트 템플릿을 만들 수 있습니다. 텍스트 템플릿에 대 한 자세한 내용은 참조 하세요. [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [도메인 특정 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)   
 [방법: 도메인별 언어 솔루션 만들기](../modeling/how-to-create-a-domain-specific-language-solution.md)   
 [연습: 도메인별 언어 정의 사용자 지정](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)
