---
title: Şekilleri ve bağlayıcıları modeli yansıtacak şekilde güncelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c31d54a87ff305504496eac6ae02900334c0966a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659451"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Modeli Yansıtacak Şekilleri ve Bağlayıcıları Güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 bir alana özgü dilde, bir şeklin görünümünün temel alınan modelin durumunu yansıtmasını sağlayabilirsiniz.

 Bu konudaki kod örnekleri, `Dsl` projenizdeki bir `.cs` dosyasına eklenmelidir. Her dosyada bu deyimlere ihtiyacınız olacaktır:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Bir dekoratörün görünürlüğünü denetlemek için şekil eşleme özelliklerini ayarlama
 Bir dekoratın görünürlüğünü, bir program kodu yazmadan denetleyebilir ve bu, DSL tanımındaki şekil ile alan sınıfı arasındaki eşlemeyi yapılandırarak kontrol edebilirsiniz. Daha fazla bilgi için aşağıdaki konulara bakın:

- [Nasıl yapılır: bir dekoratörün görünürlüğünü denetleme-yeniden yönlendirme](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Şeklin rengini ve stilini özellikler olarak kullanıma sunma
 DSL tanımında, şekil sınıfına sağ tıklayın, **gösterilen Ekle**' nin üzerine gelin ve ardından **Fill Color**gibi öğelerden birine tıklayın.

 Artık şekil, program kodunda veya Kullanıcı olarak ayarlayabileceğiniz bir etki alanı özelliğine sahiptir. Örneğin, bunu bir komutun veya kuralın program kodunda ayarlamak için şunu yazabilirsiniz:

 `shape.FillColor = System.Drawing.Color.Red;`

 Özellik değişkenini Kullanıcı tarafından değil yalnızca program denetimi altında yapmak istiyorsanız, DSL tanımı diyagramında **Fill Color** gibi yeni bir etki alanı özelliğini seçin. Sonra, Özellikler penceresi, `false` için **gözatılabilir** veya **Kullanıcı arabirimi salt okunur** `true` olarak ayarlanmıştır.

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Renk, stil veya konumun model öğesi özelliklerine bağımlı olması için değişiklik kurallarını tanımlayın
 Şeklin, modelin diğer bölümlerine bağımlı görünümünü güncelleştiren kurallar tanımlayabilirsiniz. Örneğin, model öğesinin özelliklerine bağımlı şeklin rengini güncelleştiren bir model öğesinde bir değişiklik kuralı tanımlayabilirsiniz. Değişiklik kuralları hakkında daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

 Geri Al komutu gerçekleştirildiğinde kurallar çağrılamadığından, yalnızca mağaza dahilinde tutulan özellikleri güncelleştirmek için kuralları kullanmanız gerekir. Bu, bir şeklin boyut ve görünürlüğü gibi bazı grafik özellikleri içermez. Bir şeklin bu özelliklerini güncelleştirmek için bkz. [depolama olmayan grafik özelliklerini güncelleştirme](#OnAssociatedProperty).

 Aşağıdaki örnek, önceki bölümde açıklandığı gibi `FillColor` bir etki alanı özelliği olarak kullanıma aldığını varsayar.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }

```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Şekil özelliklerini başlatmak için OnChildConfigured kullanın
 Bir şeklin özelliklerini ilk oluşturulduğunda ayarlamak için, geçersiz kılma `OnChildConfigured()` diyagram sınıfınızın kısmi tanımıdır. Diyagram sınıfı DSL tanımınızda belirtilir ve oluşturulan kod **Dsl\generated Code\Diagram.cs**' de bulunur. Örneğin:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}

```

 Bu yöntem, hem etki alanı özellikleri hem de depolama olmayan özellikler için kullanılabilir (örneğin, şeklin boyutu).

## <a name="OnAssociatedProperty"></a>Bir şeklin diğer özelliklerini güncelleştirmek için AssociateValueWith () kullanın
 Bir şeklin gölge veya bir bağlayıcının ok stili olup olmadığı gibi bazı özellikler için, özelliği etki alanı özelliği olarak gösterme yerleşik bir yöntemi yoktur.  Bu tür özelliklerde yapılan değişiklikler işlem sisteminin denetiminde değildir. Bu nedenle, Kullanıcı geri al komutunu gerçekleştirdiğinde kurallar çağrılmadığından kurallar kullanılarak güncelleştirilmesi uygun değildir.

 Bunun yerine, <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> kullanarak bu özellikleri güncelleştirebilirsiniz. Aşağıdaki örnekte, bağlayıcının ok stili, bağlayıcının gösterdiği ilişkide bir etki alanı özelliğinin değeri ile denetlenir:

```
public partial class ArrowConnector // My connector class.
{
   /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape’s built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }
    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}

```

 `AssociateValueWith()`, kaydetmek istediğiniz her bir etki alanı özelliği için bir kez çağrılmalıdır. Çağrıldıktan sonra, belirtilen özellikte yapılan herhangi bir değişiklik, özelliğin model öğesini sunan tüm şekillerde `OnAssociatedPropertyChanged()` çağırır.

 Her örnek için `AssociateValueWith()` çağırmak gerekli değildir. InitializeResources bir örnek yöntemi olsa da, her şekil sınıfı için yalnızca bir kez çağrılır.
