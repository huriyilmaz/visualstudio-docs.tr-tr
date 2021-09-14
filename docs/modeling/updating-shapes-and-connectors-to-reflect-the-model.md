---
title: Modeli Yansıtacak Şekilleri ve Bağlayıcıları Güncelleştirme
description: Visual Studio bir alana özgü dilde, bir şeklin görünümünün temel alınan modelin durumunu yansıttığından emin olun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0f667821a9940603f887850a9b26fc1d8ca2f073
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637270"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Şekilleri ve Bağlayıcıları Modeli Yansıtacak Şekilde Güncelleştirin

Visual Studio bir alana özgü dilde, bir şeklin görünümünün temel alınan modelin durumunu yansıtmasını sağlayabilirsiniz.

Bu konudaki kod örnekleri `.cs` projenizdeki bir dosyaya eklenmelidir `Dsl` . Her bir dosyada bu yönergelere ihtiyacınız vardır:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Bir dekoratörün görünürlüğünü denetlemek için şekil eşleme özelliklerini ayarlama

Bir dekoratın görünürlüğünü, bir program kodu yazmadan denetleyebilir ve bu, DSL tanımındaki şekil ile alan sınıfı arasındaki eşlemeyi yapılandırarak kontrol edebilirsiniz. Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Şeklin rengini ve stilini özellikler olarak kullanıma sunma

DSL tanımında, şekil sınıfına sağ tıklayın, **gösterilen Ekle**' nin üzerine gelin ve ardından **Fill Color** gibi öğelerden birine tıklayın.

Artık şekil, program kodunda veya Kullanıcı olarak ayarlayabileceğiniz bir etki alanı özelliğine sahiptir. Örneğin, bunu bir komutun veya kuralın program kodunda ayarlamak için şunu yazabilirsiniz:

`shape.FillColor = System.Drawing.Color.Red;`

Özellik değişkenini Kullanıcı tarafından değil yalnızca program denetimi altında yapmak istiyorsanız, DSL tanımı diyagramında **Fill Color** gibi yeni bir etki alanı özelliğini seçin. Daha sonra, Özellikler penceresi, set olarak **gözatılabilir** `false` veya **Kullanıcı arabirimi salt okunur** olarak ayarlanır `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Model öğe özelliklerine göre renk, stil veya konum sağlamak için değişiklik kurallarını tanımlayın
 Şeklin, modelin diğer bölümlerine bağımlı görünümünü güncelleştiren kurallar tanımlayabilirsiniz. Örneğin, model öğesinin özelliklerine bağımlı şeklin rengini güncelleştiren bir model öğesinde bir değişiklik kuralı tanımlayabilirsiniz. Değişiklik kuralları hakkında daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

 Geri Al komutu gerçekleştirildiğinde kurallar çağrılamadığından, yalnızca mağaza dahilinde tutulan özellikleri güncelleştirmek için kuralları kullanmanız gerekir. Bu, bir şeklin boyut ve görünürlüğü gibi bazı grafik özellikleri içermez. Bir şeklin bu özelliklerini güncelleştirmek için bkz. [depolama olmayan grafik özelliklerini güncelleştirme](#OnAssociatedProperty).

 Aşağıdaki örnek, `FillColor` önceki bölümde açıklandığı gibi bir etki alanı özelliği olarak kullanıma sunulacak olduğunu varsayar.

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

Bir şeklin özelliklerini ilk oluşturulduğunda ayarlamak için, `OnChildConfigured()` Diyagram sınıfınızın kısmi tanımında geçersiz kılma. Diyagram sınıfı DSL tanımınızda belirtilir ve oluşturulan kod **Dsl\generated Code\Diagram.cs**' de bulunur. Örnek:

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

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Bir şeklin diğer özelliklerini güncelleştirmek için AssociateValueWith () kullanın

Bir şeklin gölge veya bir bağlayıcının ok stili olup olmadığı gibi bazı özellikler için, özelliği etki alanı özelliği olarak gösterme yerleşik bir yöntemi yoktur.  Bu tür özelliklerde yapılan değişiklikler işlem sisteminin denetiminde değildir. Bu nedenle, Kullanıcı geri al komutunu gerçekleştirdiğinde kurallar çağrılmadığından kurallar kullanılarak güncelleştirilmesi uygun değildir.

Bunun yerine, kullanarak bu özellikleri güncelleştirebilirsiniz <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . Aşağıdaki örnekte, bağlayıcının ok stili, bağlayıcının gösterdiği ilişkide bir etki alanı özelliğinin değeri ile denetlenir:

```csharp
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
        { // Update the shape's built-in Decorator feature:
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

`AssociateValueWith()` kaydetmek istediğiniz her bir etki alanı özelliği için bir kez çağrılmalıdır. Çağrıldıktan sonra, belirtilen özellikte yapılan herhangi bir değişiklik, `OnAssociatedPropertyChanged()` özelliğin model öğesini sunan herhangi bir şekle çağrı yapılır.

Her örnek için çağrı yapılması gerekli değildir `AssociateValueWith()` . InitializeResources bir örnek yöntemi olsa da, her şekil sınıfı için yalnızca bir kez çağrılır.
