---
title: Etki alanına özgü dil tanımına Izleme özelliği ekleme | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 382d5dc5ee416d901e1b73b7b2fb346e83abbef6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545580"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Etki Alanına Özgü Dil Tanımıma İzleme Özelliği Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir izleme özelliğinin bir etki alanı modeline nasıl ekleneceğini gösterir.

 Bir *izleme etki alanı* özelliği, Kullanıcı tarafından güncelleştirilebilen ancak diğer etki alanı özelliklerinin veya öğelerinin değerleri kullanılarak hesaplanan bir varsayılan değere sahip olan bir özelliktir.

 Örneğin, Alana Özgü Dil Araçları (DSL araçları), bir etki alanı sınıfının görünen ad özelliği, etki alanı sınıfının adı kullanılarak hesaplanan bir varsayılan değere sahiptir, ancak kullanıcı tasarım zamanında değeri değiştirebilir veya hesaplanan değere sıfırlayabilir.

 Bu kılavuzda, modelin varsayılan ad alanı özelliğini temel alan varsayılan değere sahip bir ad alanı izleme özelliğine sahip bir etki alanına özgü dil (DSL) oluşturursunuz. İzleme özellikleri hakkında daha fazla bilgi için bkz. [Izleme özelliklerini tanımlama](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- DSL araçları izleme özelliği tanımlayıcılarını destekler. Ancak, DSL Tasarımcısı bir dile izleme özelliği eklemek için kullanılamaz. Bu nedenle, izleme özelliğini tanımlamak ve uygulamak için özel kod eklemeniz gerekir.

  İzleme özelliğinin iki durumu vardır: izleme ve Kullanıcı tarafından güncelleme. İzleme özellikleri aşağıdaki özelliklere sahiptir:

- İzleme durumundayken, izleme özelliğinin değeri hesaplanır ve model değiştiğinde bu değer güncellenir ve değeri güncellenir.

- Kullanıcı durumundayken, izleme özelliğinin değeri kullanıcının özelliği en son ayarlayabileceği değeri korur.

- **Özellikler** penceresinde, izleme özelliği için **Reset** komutu yalnızca özellik kullanıcı durumunda olduğunda etkindir. **Reset** komutu izleme özelliği durumunu izleme olarak ayarlar.

- **Özellikler** penceresinde, izleme özelliği izleme durumundaysa, değeri normal bir yazı tipinde görüntülenir.

- **Özellikler** penceresinde, izleme özelliği kullanıcı durumunda olduğunda, değeri kalın yazı tipinde görüntülenir.

## <a name="prerequisites"></a>Ön koşullar
 Bu yönergeyi başlatabilmeniz için önce şu bileşenleri yüklemeniz gerekir:

|Ürün|İndirme bağlantısı|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio görselleştirme ve modelleme SDK|[Modelleme SDK Indirmesi](https://www.microsoft.com/download/details.aspx?id=48148)|

## <a name="creating-the-dsl-project"></a>DSL projesi oluşturma
 Etki alanına özgü diliniz için projeyi oluşturun.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. Alana Özgü Dil Tasarımcısı projesi oluşturun. Bunu, `TrackingPropertyDSL` olarak adlandırın.

2. **Alana özgü dil Tasarımcısı sihirbazında**, aşağıdaki seçenekleri ayarlayın:

    1. En **az Allanguage** şablonunu seçin.

    2. Etki alanına özgü dil için varsayılan adı kullanın `TrackingPropertyDSL` .

    3. Model dosyalarının uzantısını olarak ayarlayın `trackingPropertyDsl` .

    4. Model dosyaları için varsayılan şablon simgesini kullanın.

    5. Ürünün adını olarak ayarlayın `Product Name` .

    6. Şirketin adını olarak ayarlayın `Company Name` .

    7. Çözümdeki projeler için kök ad alanı için varsayılan değeri kullanın `CompanyName.ProductName.TrackingPropertyDSL` .

    8. Sihirbazın derlemeleriniz için tanımlayıcı ad anahtar dosyası oluşturmasına izin verin.

    9. Çözümün ayrıntılarını gözden geçirin ve ardından DSL tanımı projesini oluşturmak için **son** ' a tıklayın.

## <a name="customizing-the-default-dsl-definition"></a>Varsayılan DSL tanımını özelleştirme
 Bu bölümde, DSL tanımını aşağıdaki öğeleri içerecek şekilde özelleştirirsiniz:

- Modelin her öğesi için bir ad alanı izleme özelliği.

- Modeldeki her öğe için bir Boolean IsNamespaceTracking özelliği. Bu özellik, izleme özelliğinin izleme durumunda mi, yoksa Kullanıcı durumunda mı olduğunu gösterir.

- Model için varsayılan bir ad alanı özelliği. Bu özellik, ad alanı izleme özelliğinin varsayılan değerini hesaplamak için kullanılacaktır.

- Model için CustomElements hesaplanmış özelliği. Bu özellik özel bir ad alanı olan öğelerin oranını gösterir.

#### <a name="to-add-the-domain-properties"></a>Etki alanı özelliklerini eklemek için

1. DSL tasarımcısında, **ExampleModel** etki alanı sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve **DomainProperty**' ye tıklayın.

    1. Yeni özelliği adlandırın `DefaultNamespace` .

    2. Yeni özelliğin **Özellikler** penceresinde, **varsayılan değeri** olarak ayarlayın `DefaultNamespace` ve **Type** öğesini **String**olarak ayarlayın.

2. **ExampleModel** etki alanı sınıfına, adlı bir etki alanı özelliği ekleyin `CustomElements` .

     Yeni özellik için **Özellikler** penceresinde, **tür** ' ü **hesaplanacak**olarak ayarlayın.

3. **ExampleElement** etki alanı sınıfına, adlı bir etki alanı özelliği ekleyin `Namespace` .

     Yeni özellik için **Özellikler** penceresinde, set **yanlış**olarak **gözatılabilir** ve **tür** ' i **CustomStorage**olarak ayarlayın.

4. **ExampleElement** etki alanı sınıfına, adlı bir etki alanı özelliği ekleyin `IsNamespaceTracking` .

     Yeni özellik için **Özellikler** penceresinde **, Ayarla özelliği** **yanlış**olarak, **varsayılan değeri** olarak ayarlayın `true` ve **tür** ' i **Boolean**olarak ayarlayın.

#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Diyagram öğelerini ve DSL ayrıntılarını güncelleştirmek için

1. DSL tasarımcısında, **ExampleShape** Geometry şekline sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **metin dekoratörü**' ne tıklayın.

    1. Yeni metin dekoratisini adlandırın `NamespaceDecorator` .

    2. Metin dekoratörü için **Özellikler** penceresinde, **konumu** **InnerBottomLeft**olarak ayarlayın.

2. DSL Tasarımcısı ' nda **ExampleElement** sınıfını **ExampleShape** şekline bağlayan çizgiyi seçin.

    1. **DSL ayrıntıları** penceresinde **dekoratör haritalar** sekmesini seçin.

    2. **Dekoratörler** listesinde **NamespaceDecorator**öğesini seçin, onay kutusunu işaretleyin ve ardından **görüntü özelliği** listesinde **ad alanı**' nı seçin.

3. **DSL Gezgini**' nde, **etki alanı sınıfları** klasörünü genişletin, **ExampleElement** düğümüne sağ tıklayın ve ardından **yeni etki alanı türü tanımlayıcısı Ekle**' ye tıklayın.

    1. **ExampleElement** düğümünü genişletin ve **özel tür tanımlayıcısı (etki alanı türü tanımlayıcısı)** düğümünü seçin.

    2. Etki alanı türü tanımlayıcısının **Özellikler** penceresinde, **özel kodlamalı** ' i **true**olarak ayarlayın.

4. **DSL Gezgini**' nde **XML serileştirme davranışı** düğümünü seçin.

    1. **Özellikler** penceresinde, **Özel gönderi yükleme** ' yi **true**olarak ayarlayın.

## <a name="transforming-templates"></a>Şablonları dönüştürme
 Artık DSL 'niz için etki alanı sınıflarını ve özelliklerini tanımladığınıza göre, bu durumda, projenizin kodu yeniden oluşturmak için DSL tanımının doğru şekilde dönüştürülebildiğini doğrulayabilirsiniz.

#### <a name="to-transform-the-text-templates"></a>Metin şablonlarını dönüştürmek için

1. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür**' e tıklayın.

2. Sistem çözüm için kodu yeniden oluşturur ve DslDefinition. dsl 'yi kaydeder. Tanım dosyalarının XML biçimi hakkında daha fazla bilgi için, bkz. [DslDefinition. dsl dosyası](../modeling/the-dsldefinition-dsl-file.md).

## <a name="creating-files-for-custom-code"></a>Özel kod için dosyalar oluşturma
 Tüm şablonları dönüştürdüğünüzde, sistem, DSL ve DslPackage projelerinde, etki alanına özgü dilinizi tanımlayan kaynak kodu oluşturur. Oluşturulan metinle kesintiye uğramadan kaçınmak için, oluşturulan kod dosyalarından farklı olan dosyalara özel kodunuzu yazın.

 Değerin ve izleme özelliğinin durumunun sürdürülmesi için kod sağlamalısınız. Özel kodunuzu oluşturulan koddan ayırmanıza yardımcı olmak ve dosya adlandırma çakışmalarını önlemek için özel kod dosyalarınızı ayrı bir alt klasöre yerleştirin.

#### <a name="to-create-the-code-files"></a>Kod dosyalarını oluşturmak için

1. **Çözüm Gezgini**, **DSL** projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' e tıklayın. Yeni klasörü adlandırın `CustomCode` .

2. Yeni **CustomCode** klasörüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.

3. **Kod dosyası** şablonunu seçin, **adını** olarak ayarlayın `NamespaceTrackingProperty.cs` ve ardından **Tamam**' a tıklayın.

     NamespaceTrackingProperty.cs dosyası oluşturulup düzenlenmek üzere açılır.

4. Klasöründe aşağıdaki kod dosyalarını oluşturun: `ExampleModel.cs,``HelperClasses.cs` , `Serialization.cs` , ve `TypeDescriptor.cs` .

5. **DslPackage** projesinde Ayrıca bir `CustomCode` klasör oluşturun ve bu klasöre bir `Package.cs` kod dosyası ekleyin.

## <a name="adding-helper-classes-to-support-tracking-properties"></a>Izleme özelliklerini desteklemek için yardımcı sınıfları ekleme
 HelperClasses.cs dosyasına `TrackingHelper` ve `CriticalException` sınıflarını aşağıdaki gibi ekleyin. Bu sınıfların ilerleyen kısımlarında bu sınıflara başvurabileceksiniz.

#### <a name="to-add-the-helper-classes"></a>Yardımcı sınıfları eklemek için

1. Aşağıdaki kodu HelperClasses.cs dosyasına ekleyin.

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

## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Özel tür tanımlayıcısı için özel kod ekleme
 `GetCustomProperties`Etki alanı sınıfı için tür tanımlayıcısı için yöntemini uygulayın `ExampleModel` .

> [!NOTE]
> DSL araçlarının çağrılar için özel tür tanımlayıcısı için üretme kodu `ExampleModel` `GetCustomProperties` ; ancak dsl araçları yöntemi uygulayan kod oluşturmaz.

 Bu yöntemin tanımlanması, ad alanı izleme özelliği için izleme özelliği tanımlayıcısı oluşturur. Ayrıca, izleme özelliğinin özniteliklerini sağlamak **Özellikler** penceresinin özelliği doğru görüntülemesini sağlar.

#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>ExampleModel alan sınıfı için tür tanımlayıcısını değiştirme

1. Aşağıdaki kodu TypeDescriptor.cs dosyasına ekleyin.

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

## <a name="adding-custom-code-for-the-package"></a>Paket için özel kod ekleme
 Oluşturulan kod, ExampleElement alanı sınıfı için bir tür açıklaması sağlayıcısı tanımlar; Ancak, bu tür açıklama sağlayıcısını kullanmak için DSL 'ye yönlendirmek üzere kod eklemeniz gerekir.

#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Özel tür tanımlayıcısından kullanılacak DSL paketini güncelleştirmek için

1. Aşağıdaki kodu Package.cs dosyasına ekleyin.

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

## <a name="adding-custom-code-for-the-model"></a>Model için özel kod ekleme
 `GetCustomElementsValue` `ExampleModel` Etki alanı sınıfı için yöntemini uygulayın.

> [!NOTE]
> DSL araçlarının çağrılar için üretme kodu `ExampleModel` `GetCustomElementsValue` ; ancak dsl araçları yöntemi uygulayan kod oluşturmaz.

 Yöntemi tanımlama, ' `GetCustomElementsValue` nin CustomElements 'ın hesaplanan özelliğine ilişkin mantığı sağlar `ExampleModel` . Bu yöntem `ExampleElement` , Kullanıcı tarafından güncelleştirilmiş bir değere sahip bir ad alanı izleme özelliğine sahip olan etki alanı sınıflarının sayısını sayar ve bu sayıyı modeldeki toplam öğelerin bir oranı olarak temsil eden bir dize döndürür.

 Ayrıca, `OnDefaultNamespaceChanged` öğesine bir yöntemi ekleyin `ExampleModel` ve `OnValueChanged` `DefaultNamespacePropertyHandler` çağrısı yapmak için iç içe sınıfının metodunu geçersiz kılın `ExampleModel` `OnDefaultNamespaceChanged` .

 DefaultNamespace özelliği ad alanı izleme özelliğini hesaplamak için kullanıldığından, `ExampleModel` `ExampleElement` DefaultNamespace değerinin değiştiği tüm etki alanı sınıflarını bilgilendirmelidir.

#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>İzlenen özellik için özellik işleyicisini değiştirme

1. Aşağıdaki kodu ExampleModel.cs dosyasına ekleyin.

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

## <a name="adding-custom-code-for-the-tracking-property"></a>Izleme özelliği için özel kod ekleme
 `CalculateNamespace` `ExampleElement` Etki alanı sınıfına bir yöntem ekleyin.

 Bu yöntemin tanımlanması, ' nin CustomElements 'ın hesaplanan özelliğine yönelik mantığı sağlar `ExampleModel` . Bu yöntem, `ExampleElement` Kullanıcı durumunda tarafından güncellenen bir ad alanı izleme özelliğine sahip olan etki alanı sınıflarının sayısını sayar ve bu sayıyı modeldeki toplam öğelerin bir oranı olarak temsil eden bir dize döndürür.

 Ayrıca, ve için depolama alanı ekleyin ve alan sınıfının özel depolama özelliğini alır ve ayarlar `ExampleElement` .

> [!NOTE]
> DSL araçlarının oluşturabileceği kod `ExampleModel` Get ve set yöntemlerini çağırır; ancak dsl araçları, yöntemleri uygulayan kod oluşturmaz.

#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Özel tür tanımlayıcısına yönelik yöntemi eklemek için

1. Aşağıdaki kodu NamespaceTrackingProperty.cs dosyasına ekleyin.

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

## <a name="adding-custom-code-to-support-serialization"></a>Serileştirme desteği için özel kod ekleme
 XML serileştirme için özel yükleme sonrası davranışını desteklemek üzere kod ekleyin.

> [!NOTE]
> DSL araçlarının üretme kodu `OnPostLoadModel` ve `OnPostLoadModelAndDiagram` yöntemlerini çağırır; ancak, dsl araçları bu yöntemleri uygulayan kod oluşturmaz.

#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Özel yükleme sonrası davranışını desteklemek üzere kod eklemek için

1. Aşağıdaki kodu Serialization.cs dosyasına ekleyin.

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

## <a name="testing-the-language"></a>Dili test etme
 Sonraki adım, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] izleme özelliğinin doğru çalıştığını doğrulayabilmeniz IÇIN DSL tasarımcısını yeni bir örneğinde derleyip çalıştırmak için kullanılır.

#### <a name="to-exercise-the-language"></a>Dili uygulamak için

1. **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.

2. **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.

     Deneysel derlemesi, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] boş bir test dosyası Içeren **hata ayıklama** çözümünü açar.

3. **Çözüm Gezgini**, test. trackingPropertyDsl dosyasına çift tıklayarak tasarımcı içinde açın ve tasarım yüzeyine tıklayın.

     Diyagramın **Özellikler** penceresinde, **varsayılan ad alanı** özelliği **defaultnamespace**ve **özel öğeler** özelliği **0/0**olduğunu fark edersiniz.

4. **Araç kutusundan** bir **ExampleElement** öğesini Diyagram yüzeyine sürükleyin.

5. Öğesinin **Özellikler** penceresinde, **öğe ad alanı** özelliğini seçin ve **DefaultNamespace** ' den **OtherNamespace**' a değeri değiştirin.

     **Öğe ad alanının** değeri artık kalın olarak gösterildiğine dikkat edin.

6. **Özellikler** penceresinde, **öğe ad alanı**' na sağ tıklayın ve ardından **Sıfırla**' ya tıklayın.

     Özelliğin değeri **DefaultNamespace**olarak değiştirilir ve değer normal bir yazı tipinde gösterilir.

     **Öğe ad alanını** yeniden sağ tıklatın. Özelliği şu anda izleme durumunda olduğundan, **Reset** komutu artık devre dışı bırakıldı.

7. **Araç kutusundan** başka bir **ExampleElement öğesini** Diyagram yüzeyine sürükleyin ve **öğe ad alanını** **OtherNamespace**olarak değiştirin.

8. Tasarım yüzeyine tıklayın.

     Diyagramın **Özellikler** penceresinde, **özel öğelerin** değeri artık **1/2**' dir.

9. **DefaultNamespace** öğesinden **NewNamespace**'e diyagramın **varsayılan ad alanını** değiştirin.

     İlk öğenin **ad** alanı **varsayılan ad alanı** özelliğini izler, ancak Ikinci öğenin **ad alanı** **diğer**ad alanının kullanıcı tarafından güncelleştirilmiş değerini korur.

10. Çözümü kaydedin ve deneysel derlemeyi kapatın.

## <a name="next-steps"></a>Sonraki Adımlar
 Birden fazla izleme özelliği kullanmayı veya birden fazla DSL 'de izleme özellikleri uygulamayı planlıyorsanız, her izleme özelliğini desteklemek için ortak kodu oluşturmak üzere bir metin şablonu oluşturabilirsiniz. Metin şablonları hakkında daha fazla bilgi için bkz. [kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor> <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
 [Etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md) [nasıl yapılır: etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md) [izlenecek yol: etki alanına özgü dil tanımını özelleştirme](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)
