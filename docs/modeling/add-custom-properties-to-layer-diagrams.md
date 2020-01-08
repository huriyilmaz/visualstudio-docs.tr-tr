---
title: Bağımlılık diyagramlarına özel özellikler ekleme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3623a0c2380188cbb16f6186bddc3f3f2f0c3bd7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590598"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Bağımlılık diyagramlarına özel özellikler ekleme

Bağımlılık diyagramları için uzantı kodu yazdığınızda, değerleri bir bağımlılık diyagramında herhangi bir öğe ile saklayabilirsiniz. Diyagram kaydedilip yeniden açıldığında değerler kalır. Ayrıca, kullanıcıların bunları görebilmesi ve düzenleyebilmeleri için **Özellikler** penceresinde bu özelliklerin görünmesini sağlayabilirsiniz. Örneğin, kullanıcıların her katman için bir normal ifade belirtmesini ve her katmandaki sınıfların adlarının Kullanıcı tarafından belirtilen düzene uygun olduğunu doğrulamak için doğrulama kodu yazabilmesini sağlayabilirsiniz.

## <a name="non-visible-properties"></a>Görünür olmayan özellikler

Yalnızca kodunuzun bir bağımlılık diyagramında herhangi bir öğeye değer iliştirmek istiyorsanız, MEF bileşeni tanımlamanız gerekmez. [ILayerElement](/previous-versions/ff644511(v=vs.140))içinde `Properties` adlı bir sözlük var. Yalnızca herhangi bir katman öğesinin sözlüğüne sıralanabilecek değerleri eklemeniz yeterlidir. Bu, bağımlılık diyagramının bir parçası olarak kaydedilir.

## <a name="editable-properties"></a>Düzenlenebilir özellikler

**İlk hazırlık**

> [!IMPORTANT]
> Özellikleri açmak için, katman özelliklerinin görünmesini istediğiniz her bilgisayarda aşağıdaki değişikliği yapın:
>
> 1. **Yönetici olarak çalıştır**'ı kullanarak not defteri 'ni çalıştırın. *%ProgramFiles%\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*öğesini açın.
> 2. **İçerik** öğesinin içinde şunu ekleyin:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. Visual Studio uygulama Başlat menüsünün **Visual Studio Araçları** bölümünde **Geliştirici komut istemi**' i açın. Girin:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Visual Studio'yu yeniden başlatın.

**Kodunuzun bir VSıX projesinde olduğundan emin olun**

Eğer özelliği bir komutun, hareketin veya doğrulama projesinin parçasıysa, herhangi bir şey eklemeniz gerekmez. Özel özellik kodu, MEF bileşeni olarak tanımlanmış bir Visual Studio genişletilebilirlik projesinde tanımlanmalıdır. Daha fazla bilgi için bkz. [bağımlılık diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md) veya [bağımlılık diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

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

- `ILayerModel`-model

- `ILayer`-her katman

- `ILayerDependencyLink`-Katmanlar arasındaki bağlantılar

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Örnek

Aşağıdaki kod tipik bir özel özellik tanımlayıcısıdır. Katman modelinde (`ILayerModel`), kullanıcının özel doğrulama yöntemi için değer sağlamasına imkan tanıyan bir Boole özelliği tanımlar.

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
