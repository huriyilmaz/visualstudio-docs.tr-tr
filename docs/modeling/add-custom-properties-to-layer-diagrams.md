---
title: Bağımlılık diyagramlarına özel özellikler ekleme
description: Bağımlılık diyagramları için uzantı kodu yazdığınızda bir bağımlılık diyagramında herhangi bir öğeyle değerleri nasıl depolayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: e67ccec3405dfb0cf50f914ff9e91fbec2d8d604
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157741"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Bağımlılık diyagramlarına özel özellikler ekleme

Bağımlılık diyagramları için uzantı kodu yazdığınızda, değerleri bir bağımlılık diyagramında herhangi bir öğe ile saklayabilirsiniz. Diyagram kaydedilip yeniden açıldığında değerler kalır. Ayrıca, kullanıcıların bunları görebilmesi ve düzenleyebilmeleri için **Özellikler** penceresinde bu özelliklerin görünmesini sağlayabilirsiniz. Örneğin, kullanıcıların her katman için bir normal ifade belirtmesini ve her katmandaki sınıfların adlarının Kullanıcı tarafından belirtilen düzene uygun olduğunu doğrulamak için doğrulama kodu yazabilmesini sağlayabilirsiniz.

## <a name="non-visible-properties"></a>Görünür olmayan özellikler

Yalnızca kodunuzun bir bağımlılık diyagramında herhangi bir öğeye değer iliştirmek istiyorsanız, MEF bileşeni tanımlamanız gerekmez. `Properties` [ILayerElement](/previous-versions/ff644511(v=vs.140))içinde adlı bir sözlük var. Yalnızca herhangi bir katman öğesinin sözlüğüne sıralanabilecek değerleri eklemeniz yeterlidir. Bu, bağımlılık diyagramının bir parçası olarak kaydedilir.

## <a name="editable-properties"></a>Düzenlenebilir özellikler

**İlk hazırlık**

> [!IMPORTANT]
> Özellikleri açmak için, katman özelliklerinin görünmesini istediğiniz her bilgisayarda aşağıdaki değişikliği yapın:
>
> 1. **yönetici olarak çalıştır**'ı kullanarak Not Defteri çalıştırın. *% ProgramFiles% \ Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest* öğesini açın.
> 2. **İçerik** öğesinin içinde şunu ekleyin:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. Visual Studio uygulama başlat menüsünün **Visual Studio Araçları** bölümü altında **Geliştirici Komut İstemi**' yı açın. Şunları girin:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Visual Studio’yu yeniden başlatın.

**Kodunuzun bir VSıX projesinde olduğundan emin olun**

Eğer özelliği bir komutun, hareketin veya doğrulama projesinin parçasıysa, herhangi bir şey eklemeniz gerekmez. özel özellik kodu, MEF bileşeni olarak tanımlanan bir Visual Studio genişletilebilirlik projesinde tanımlanmalıdır. Daha fazla bilgi için bkz. [bağımlılık diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md) veya [bağımlılık diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Özel özelliği tanımlayın**

Özel bir özellik oluşturmak için aşağıdaki gibi bir sınıf tanımlayın:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

[ILayerElement](/previous-versions/ff644511(v=vs.140)) veya türetilmiş sınıflarından herhangi birini içeren özellikleri tanımlayabilirsiniz:

- `ILayerModel` -Model

- `ILayer` -Her katman

- `ILayerDependencyLink` -Katmanlar arasındaki bağlantılar

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Örnek

Aşağıdaki kod tipik bir özel özellik tanımlayıcısıdır. `ILayerModel`Kullanıcının özel bir doğrulama yöntemi için değer sağlamasına imkan tanıyan katman modelinde () bir Boole özelliği tanımlar.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)
