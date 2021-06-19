---
title: DSL tanımına izleme özelliği ekleme
description: İzleme etki alanı özelliği ve bir etki alanı modeline izleme özelliği ekleme hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 546636ec3de4656bf0f6480dfaa5141d38e963d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384921"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Alana Özgü Dil Tanımına İzleme Özelliği ekleme

Bu kılavuzda, bir etki alanı modeline izleme özelliğinin nasıl ekli olduğu gösterir.

İzleme *etki alanı* özelliği, kullanıcı tarafından güncelleştirilebilir ancak diğer etki alanı özelliklerinin veya öğelerinin değerleri kullanılarak hesaplanan varsayılan bir değere sahip olan bir özelliktir.

Örneğin, Domain-Specific Dil Araçları'nda (DSL Araçları) bir etki alanı sınıfının Görünen Ad özelliği, etki alanı sınıfının adı kullanılarak hesaplanan varsayılan bir değere sahiptir, ancak bir kullanıcı tasarım zamanında değeri değiştirebilir veya hesaplanan değere sıfırlar.

Bu kılavuzda, modelin Varsayılan Ad Alanı özelliğini temel alan varsayılan değere sahip bir Ad Alanı izleme özelliğine sahip olan etki alanına özgü bir dil (DSL) oluşturabilirsiniz. İzleme özellikleri hakkında daha fazla bilgi için [bkz. İzleme Özelliklerini Tanımlama.](/previous-versions/cc825929(v=vs.100))

- DSL Araçları, özellik tanımlayıcılarını izleme desteği sunar. Ancak DSL tasarımcısı, bir dile izleme özelliği eklemek için kullanılamaz. Bu nedenle, izleme özelliğini tanımlamak ve uygulamak için özel kod eklemeniz gerekir.

  bir izleme özelliği iki eyalete sahip: izleme ve kullanıcı tarafından güncelleştirildi. İzleme özellikleri aşağıdaki özelliklere sahiptir:

- İzleme durumuna geldiğinde, izleme özelliğinin değeri hesaplanır ve değer model değişikliğinde diğer özellikler olarak güncelleştirilir.

- Kullanıcı durumuna göre güncelleştirildiğinde, izleme özelliğinin değeri, kullanıcının özelliği son ayara sahip olduğu değeri korur.

- Özellikler **penceresinde,** izleme **özelliği için Reset** komutu yalnızca özellik kullanıcı durumuna göre güncelleştirildiğinde etkinleştirilir. Reset **komutu** izleme özelliği durumunu izlemeye ayarlar.

- Özellikler **penceresinde,** izleme özelliği izleme durumuna geldiğinde değeri normal bir yazı tipiyle görüntülenir.

- Özellikler **penceresinde,** izleme özelliği kullanıcı durumuna göre güncelleştirildiğinde değeri kalın yazı tipiyle görüntülenir.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu başlatamadan önce şu bileşenleri yüklemeniz gerekir:

| Bileşen | Bağlantı |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>Proje oluşturma

1. Domain-Specific Dil Tasarımcısı projesi oluşturun. Bunu, `TrackingPropertyDSL` olarak adlandırın.

2. Alana Özgü Dil Tasarımcısı **Sihirbazı'nda** aşağıdaki seçenekleri ayarlayın:

    1. **MinimalLanguage şablonunu** seçin.

    2. Etki alanına özgü dil olan için varsayılan adı `TrackingPropertyDSL` kullanın.

    3. Model dosyalarının uzantısını olarak `trackingPropertyDsl` ayarlayın.

    4. Model dosyaları için varsayılan şablon simgesini kullanın.

    5. Ürünün adını olarak `Product Name` ayarlayın.

    6. Şirketin adını olarak `Company Name` ayarlayın.

    7. Çözümde projeler için kök ad alanı için varsayılan değeri `CompanyName.ProductName.TrackingPropertyDSL` kullanın.

    8. Sihirbazın derlemeleriniz için bir güçlü ad anahtar dosyası oluşturmasına izin ver.

    9. Çözümün ayrıntılarını gözden geçirip Dsl tanım **projesini oluşturmak** için Son'a tıklayın.

## <a name="customize-the-default-dsl-definition"></a>Varsayılan DSL Tanımını Özelleştirme
 Bu bölümde DSL tanımını aşağıdaki öğeleri içermesi için özelleştirebilirsiniz:

- Modelin her öğesi için ad alanı izleme özelliği.

- Modelin her öğesi için Bir Boole IsNamespaceTracking özelliği. Bu özellik, izleme özelliğinin izleme durumda mı yoksa kullanıcı durumuna göre güncelleştirilmiş durumda mı olduğunu belirtecek.

- Model için Varsayılan Ad Alanı özelliği. Bu özellik, Ad alanı izleme özelliğinin varsayılan değerini hesaplamak için kullanılır.

- Model için CustomElements hesaplanan özelliği. Bu özellik, özel ad alanına sahip öğelerin oranını belirtecek.

### <a name="to-add-the-domain-properties"></a>Etki alanı özelliklerini eklemek için

1. DSL tasarımcısında **ExampleModel** etki alanı sınıfına sağ tıklayın, Ekle'nin üzerine **gelin** ve **Ardından DomainProperty 'ye tıklayın.**

    1. Yeni özelliği olarak ad `DefaultNamespace` girin.

    2. Yeni **özelliğin** Özellikler penceresinde Varsayılan Değer'i **olarak, Tür'i** `DefaultNamespace` ise Dize **olarak** **ayarlayın.**

2. **ExampleModel etki alanı** sınıfına adlı bir etki alanı özelliği `CustomElements` ekleyin.

     Yeni **özelliğin** Özellikler penceresinde Tür'leri Hesaplanan **olarak** **ayarlayın.**

3. **ExampleElement etki alanı** sınıfına adlı bir etki alanı özelliği `Namespace` ekleyin.

     Yeni **özelliğin** Özellikler penceresinde Gözatılabilir'i **False** olarak,  Tür'i **ise CustomStorage olarak ayarlayın.** 

4. **ExampleElement etki alanı** sınıfına adlı bir etki alanı özelliği `IsNamespaceTracking` ekleyin.

     Yeni **özelliğin** Özellikler penceresinde Gözatılabilir'i **False** olarak, Varsayılan Değer'i olarak ve   `true` Tür'i **Boole olarak ayarlayın.** 

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Diyagram öğelerini ve DSL ayrıntılarını güncelleştirmek için

1. DSL tasarımcısında **ExampleShape** geometri şekline sağ tıklayın, Ekle'nin üzerine **gelin** ve Ardından Metin **Dekoratörü'ne tıklayın.**

    1. Yeni metin dekoratörüne adını `NamespaceDecorator` verir.

    2. Metin **dekoratör** için Özellikler penceresinde  Konum'u **InnerBottomLeft olarak ayarlayın.**

2. DSL tasarımcısında **ExampleElement** sınıfını **ExampleShape** şekline bağlayan satırı seçin.

    1. DSL **Ayrıntıları penceresinde** Dekoratör Haritaları **sekmesini** seçin.

    2. **Dekoratörler listesinde** **NamespaceDecorator'ı** seçin, onay kutusunu seçin ve ardından Görüntüleme özellik **listesinde Ad** Alanı'ı **seçin.**

3. **DSL Gezgini'nde,** Etki **Alanı Sınıfları** klasörünü genişletin, **ExampleElement** düğümüne sağ tıklayın ve ardından Yeni Etki **Alanı Türü Tanımlayıcısı Ekle'ye tıklayın.**

    1. **ExampleElement düğümünü** genişletin ve Özel **Tür Tanımlayıcısı (Etki Alanı Türü Tanımlayıcısı) düğümünü** seçin.

    2. Etki **alanı tür** tanımlayıcısının Özellikler penceresinde Özel Kodlu'ları True **olarak** **ayarlayın.**

4. **DSL Gezgini'nde** **Xml Serileştirme Davranışı düğümünü** seçin.

    1. Özellikler penceresinde **Özel** Yükleme **Sonrası'nın True olarak** **ayarlayın.**

## <a name="transform-templates"></a>Şablonları Dönüştürme

DSL'nizin etki alanı sınıflarını ve özelliklerini tanımlandığına göre, dsl tanımının projenizin kodunu yeniden oluşturması için doğru şekilde dönüştürülenin doğru olduğunu doğruabilirsiniz.

1. Uygulama araç **Çözüm Gezgini** Tüm Şablonları **Dönüştür'e tıklayın.**

2. Sistem çözümün kodunu yeniden üreter ve DslDefinition.dsl'i kaydeder. Tanım dosyalarının XML biçimi hakkında bilgi için bkz. [DslDefinition.dsl Dosyası.](../modeling/the-dsldefinition-dsl-file.md)

## <a name="create-files-for-custom-code"></a>Özel Kod için Dosya Oluşturma

Tüm şablonları dönüştüren sistem, Dsl ve DslPackage projelerinde etki alanına özgü dilinizi tanımlayan kaynak kodu oluşturur. Oluşturulan metni engellememek için özel kodunuzu oluşturulan kod dosyalarından ayrı dosyalara yazın.

İzleme özelliğinizin değerini ve durumunu korumak için kod sağlanız gerekir. Özel kodunuzu oluşturulan koddan ayırt etmeye yardımcı olmak ve dosya adlandırma çakışmalarını önlemek için özel kod dosyalarınızı ayrı bir alt klasöre koyabilirsiniz.

1. Bu **Çözüm Gezgini** DSL projesine sağ **tıklayın, Ekle'nin** üzerine **gelin** ve ardından Yeni **Klasör'e tıklayın.** Yeni klasöre adını `CustomCode` girin.

2. Yeni CustomCode klasörüne **sağ tıklayın,** Ekle'nin **üzerine gelin ve** ardından Yeni **Öğe'ye tıklayın.**

3. Kod Dosyası **şablonunu seçin,** Ad'ı **olarak ayarlayın** ve `NamespaceTrackingProperty.cs` ardından Tamam'a **tıklayın.**

     NamespaceTrackingProperty.cs dosyası oluşturulur ve düzenleme için açılır.

4. klasöründe şu kod dosyalarını oluşturun: `ExampleModel.cs,``HelperClasses.cs` , `Serialization.cs` ve `TypeDescriptor.cs` .

5. **DslPackage projesinde** ayrıca bir klasör `CustomCode` oluşturun ve buna bir kod dosyası `Package.cs` ekleyin.

## <a name="add-helper-classes-to-support-tracking-properties"></a>İzleme Özelliklerini Desteklemek için Yardımcı Sınıfları Ekleme

HelperClasses.cs dosyasına ve `TrackingHelper` sınıflarını `CriticalException` aşağıdaki gibi ekleyin. Bu kılavuzda daha sonra bu sınıflara başvurabilirsiniz.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Özel Tür Tanımlayıcısı için Özel Kod Ekleme

Etki `GetCustomProperties` alanı sınıfı için tür tanımlayıcısı için `ExampleModel` yöntemini uygulama.

> [!NOTE]
> DSL Araçları'nın çağrıları için özel tür tanımlayıcısı için oluşturduğu kod; ancak `ExampleModel` `GetCustomProperties` DSL Araçları yöntemini uygulayan kod oluşturmaz.

Bu yöntemin tanımlanması, Ad alanı izleme özelliği için izleme özelliği tanımlayıcısını oluşturur. Ayrıca, izleme özelliği için öznitelikler sağlamak Özellikler **penceresinin** özelliği doğru görüntülemeye olanak sağlar.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>ExampleModel etki alanı sınıfının tür tanımlayıcısını değiştirmek için

1. TypeDescriptor.cs dosyasına aşağıdaki kodu ekleyin.

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

## <a name="adding-custom-code-for-the-package"></a>Paket için Özel Kod Ekleme

Oluşturulan kod, ExampleElement etki alanı sınıfı için bir tür açıklaması sağlayıcısı tanımlar; ancak, DSL'ye bu tür açıklama sağlayıcısını kullanma talimatı veren kod eklemeniz gerekir.

1. Package.cs dosyasına aşağıdaki kodu ekleyin.

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

## <a name="add-custom-code-for-the-model"></a>Model için Özel Kod Ekleme

Etki `GetCustomElementsValue` alanı sınıfı için `ExampleModel` yöntemini uygulama.

> [!NOTE]
> DSL Araçlarının çağrıları için oluşturulan `ExampleModel` `GetCustomElementsValue` kod; ancak DSL Araçları yöntemini uygulayan kod oluşturmaz.

yönteminin `GetCustomElementsValue` tanımlanması, CustomElements hesaplanan özelliğinin mantığını `ExampleModel` sağlar. Bu yöntem, kullanıcı tarafından güncelleştirilmiş bir değere sahip bir Ad alanı izleme özelliğine sahip etki alanı sınıflarının sayısını sayar ve bu s sayımı modelde toplam öğelerin oranı olarak temsil eden bir dize `ExampleElement` döndürür.

Ayrıca, içine bir `OnDefaultNamespaceChanged` yöntem ekleyin ve çağrısı yapmak için iç içe geçmiş sınıfının yöntemini geçersiz `ExampleModel` `OnValueChanged` `DefaultNamespacePropertyHandler` `ExampleModel` `OnDefaultNamespaceChanged` kılın.

DefaultNamespace özelliği Ad Alanı izleme özelliğini hesaplamak için kullanılır, tüm etki alanı sınıflarına DefaultNamespace değerinin değiştiğini `ExampleModel` `ExampleElement` bildirecektir.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>İzilen özelliğin özellik işleyicisini değiştirmek için

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

## <a name="add-custom-code-for-the-tracking-property"></a>İzleme Özelliği için Özel Kod Ekleme

Etki alanı `CalculateNamespace` sınıfına bir `ExampleElement` yöntem ekleyin.

Bu yöntemin tanımlanması, CustomElements hesaplanan özelliğinin mantığını `ExampleModel` sağlar. Bu yöntem, kullanıcı durumuna göre güncelleştirilen ad alanı izleme özelliğine sahip etki alanı sınıflarının sayısını sayar ve bu s sayımı modelde toplam öğelerin oranı olarak temsil eden bir dize `ExampleElement` döndürür.

Ayrıca, etki alanı sınıfının Namespace özel depolama özelliğini almak ve ayarlamak için ve yöntemleri için depolama `ExampleElement` ekleyin.

> [!NOTE]
> DSL Araçlarının için oluşturulan kod get ve set yöntemlerini `ExampleModel` çağırabilir; ancak DSL Araçları, yöntemleri uygulayan kod oluşturmaz.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Özel tür tanımlayıcısının yöntemini eklemek için

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

## <a name="add-custom-code-to-support-serialization"></a>Serileştirmeyi Desteklemek için Özel Kod Ekleme

XML serileştirme için özel yükleme sonrası davranışını desteklemek üzere kod ekleyin.

> [!NOTE]
> DSL Araçları tarafından oluşturulan kod ve yöntemlerini `OnPostLoadModel` `OnPostLoadModelAndDiagram` çağırsa da, DSL Araçları bu yöntemleri uygulayan kod oluşturmaz.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Özel yükleme sonrası davranışını desteklemek üzere kod eklemek için

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

## <a name="test-the-language"></a>Dili Test Etmek

Sonraki adım, dsl tasarımcısını yeni bir örneğinde oluşturmak ve çalıştırmaktır; böylece izleme [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] özelliğinin düzgün çalıştığını doğrularsiniz.

1. Derleme menüsünde **Çözümü Yeniden** **Oluştur'a tıklayın.**

2. **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.

    deneysel [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] derlemesi, boş **bir** test dosyası içeren Hata Ayıklama çözümünü açar.

3. Bu **Çözüm Gezgini,** Test.trackingPropertyDsl dosyasına çift tıklar ve ardından tasarım yüzeyine tıklayın.

    Diyagramın Özellikler **penceresinde** Varsayılan Ad Alanı **özelliğinin** **DefaultNamespace,**  Özel Öğeler özelliğinin **ise 0/0** olduğunu unutmayın.

4. Araç **Kutusundan bir ExampleElement** **öğesini diyagram** yüzeyine sürükleyin.

5. Öğesinin **Özellikler** penceresinde Öğe Ad Alanı özelliğini **seçin** ve **DefaultNamespace** olan değeri **OtherNamespace olarak değiştirin.**

    Öğe Ad Alanı değerinin **artık kalın** olarak gösterildiğine dikkat olun.

6. Özellikler penceresinde **Öğe** Ad Alanı'ne sağ **tıklayın ve** ardından Sıfırla'ya **tıklayın.**

    özelliğinin değeri **DefaultNamespace** olarak değiştirilir ve değer normal bir yazı tipiyle gösterilir.

    Öğe Ad **Alanı'ne yeniden sağ** tıklayın. Özelliği şu anda izleme durumuna sahip olduğundan **Reset** komutu artık devre dışı bırakılmıştır.

7. Araç Kutusundan başka bir **ExampleElement** **öğesini** diyagram yüzeyine sürükleyin ve Öğe Ad **Alanı'nı** **OtherNamespace olarak değiştirme.**

8. Tasarım yüzeyine tıklayın.

    Diyagramın **Özellikler** penceresinde, Özel Öğeler'in **değeri artık** **1/2'dir.**

9. Diyagram **için Varsayılan Ad** Alanı'nın **DefaultNamespace'i NewNamespace** **olarak değiştirme.**

     İlk **öğenin** Ad Alanı **Varsayılan Ad** Alanı özelliğini izlerken, ikinci öğenin **Ad** Alanı, kullanıcı tarafından güncelleştirilen **OtherNamespace değerini korur.**

10. Çözümü kaydedin ve deneysel derlemeyi kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Birden fazla izleme özelliği kullanmayı veya izleme özelliklerini birden fazla DSL'de uygulamayı planlıyorsanız, her izleme özelliğini desteklemek için ortak kodu oluşturmak üzere bir metin şablonu oluşturabilirsiniz. Metin şablonları hakkında daha fazla bilgi için [bkz. Kod Oluşturma ve T4 Metin Şablonları.](../modeling/code-generation-and-t4-text-templates.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md)