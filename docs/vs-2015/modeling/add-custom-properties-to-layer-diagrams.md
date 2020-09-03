---
title: Katman diyagramlarına özel özellikler ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec1c7c94c8a0e6aa233cf21f9b57e093cc430d48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655296"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Katman diyagramlarına özel özellikler ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman diyagramları için uzantı kodu yazdığınızda, değerleri katman diyagramında herhangi bir öğe ile saklayabilirsiniz. Diyagram kaydedilip yeniden açıldığında değerler kalır. Ayrıca, kullanıcıların bunları görebilmesi ve düzenleyebilmeleri için **Özellikler** penceresinde bu özelliklerin görünmesini sağlayabilirsiniz. Örneğin, kullanıcıların her katman için bir normal ifade belirtmesini ve her katmandaki sınıfların adlarının Kullanıcı tarafından belirtilen düzene uygun olduğunu doğrulamak için doğrulama kodu yazabilmesini sağlayabilirsiniz.

## <a name="properties-not-visible-to-the-user"></a>Kullanıcıya görünmeyen Özellikler
 Yalnızca kodunuzun katman diyagramındaki herhangi bir öğeye değer iliştirmek istiyorsanız, MEF bileşeni tanımlamanız gerekmez. `Properties` [ILayerElement](/previous-versions/ff644511(v=vs.140))içinde adlı bir sözlük var. Yalnızca herhangi bir katman öğesinin sözlüğüne sıralanabilecek değerleri eklemeniz yeterlidir. Katman diyagramının bir parçası olarak kaydedilir. Daha fazla bilgi için bkz. [Program kodundaki katman modellerini gezinme ve güncelleştirme](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="properties-that-the-user-can-edit"></a>Kullanıcının düzenleyebilmesi için Özellikler
 **İlk hazırlık**

> [!IMPORTANT]
> Özellikleri görünmesi için, katman özelliklerinin görünür olmasını istediğiniz her bilgisayarda aşağıdaki değişikliği yapmanız gerekir.
>
>  1. **Yönetici olarak çalıştır**'ı kullanarak not defteri 'ni çalıştırın. Açın `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`
>
>  2. Öğesinin içinde `Content` şunu ekleyin:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
>  3. Visual Studio uygulama Başlat menüsünün **Visual Studio Araçları** bölümünde **Geliştirici komut istemi**' i açın.
>
>     Şunları girin:
>
>     `devenv /rootSuffix /updateConfiguration`
>
>     `devenv /rootSuffix Exp /updateConfiguration`
>
>  4. Visual Studio’yu yeniden başlatın.

 **Kodunuzun bir VSıX projesinde olduğundan emin olun**

 Eğer özelliği bir komutun, hareketin veya doğrulama projesinin parçasıysa, herhangi bir şey eklemeniz gerekmez. Özel özellik kodu, MEF bileşeni olarak tanımlanmış bir Visual Studio genişletilebilirlik projesinde tanımlanmalıdır. Daha fazla bilgi için bkz. [Katman diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md) veya [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 **Özel özelliği tanımlayın**

 Özel bir özellik oluşturmak için aşağıdaki gibi bir sınıf tanımlayın:

```
[Export(typeof(IPropertyExtension))]
public class MyProperty
      : PropertyExtension<ILayerElement>
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

```
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

## <a name="see-also"></a>Ayrıca Bkz.
 [Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)
