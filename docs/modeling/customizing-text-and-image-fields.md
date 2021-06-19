---
title: Metin ve Görüntü Alanlarını Özelleştirme
description: Metin ve resim dosyalarını özelleştirme hakkında bilgi edinin. Ayrıca bir şekildeki metin dekoratörü tanımladığınızda, TextField tarafından temsil edilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52c4deda5b934a9b55c5ecfeec95ca633edf15e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389273"
---
# <a name="customizing-text-and-image-fields"></a>Metin ve Görüntü Alanlarını Özelleştirme
Bir şekildeki metin dekoratörü tanımladığınızda, bir TextField tarafından temsil edilir. TextFields ve diğer şekil alanlarının başlatılmasının örnekleri için DSL çözümünüzdeki Dsl\GeneratedCode\Shapes.cs inceleyin.

 TextField, bir şeklin içindeki bir alanı, etikete atanan boşluk gibi yöneten bir nesnedir. Bir TextField örneği aynı sınıfın birçok şekli arasında paylaşılır. TextField örneği, etiketin metnini her örnek için ayrı olarak depolamaz: bunun yerine, `GetDisplayText(ShapeElement)` yöntemi şekli bir parametre olarak alır ve bu metni, şeklin ve model öğesinin geçerli durumuna bağlı olarak arayabilir.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Bir metin alanının görünümü nasıl belirlenir
 `DoPaint()`Yöntemi, ekranda alanı görüntülenecek şekilde çağrılır. Varsayılanı geçersiz kılabilir `DoPaint(),` ya da çağrı yaptığı yöntemlerin bazılarını geçersiz kılabilirsiniz. Varsayılan yöntemlerin aşağıdaki Basitleştirilmiş sürümü, varsayılan davranışı nasıl geçersiz kılacağınızı anlamanıza yardımcı olabilir:

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Gibi birkaç farklı `Get` Yöntem ve özellik çifti vardır `Default` `DefaultMultipleLine/GetMultipleLine()` . Şekil alanının tüm örnekleri için değeri değiştirmek üzere varsayılan özelliğe bir değer atayabilirsiniz. Değeri bir şekil örneğinden diğerine, ya da şeklin ya da model öğesinin durumuna bağlı yapmak için yöntemini geçersiz kılın `Get` .

## <a name="static-customizations"></a>Statik özelleştirmeler
 Bu şekil alanının her örneğini değiştirmek istiyorsanız, önce DSL tanımında özelliği ayarlayıp ayarlayamayacağını öğrenin. Örneğin, Özellikler penceresi yazı tipi boyutunu ve stilini ayarlayabilirsiniz.

 Aksi takdirde, `InitializeShapeFields` Şekil sınıfınızın yöntemini geçersiz kılın ve metin alanının uygun özelliğine bir değer atayın `Default...` .

> [!WARNING]
> Geçersiz kılmak için `InitializeShapeFields()` , şekil sınıfının **Double TÜRETILMIŞ** özelliğini dsl tanımında öğesine ayarlamanız gerekir `true` .

 Bu örnekte, bir şeklin Kullanıcı açıklamaları için kullanılacak bir metin alanı vardır. Standart açıklama yazı tipini kullanmak istiyoruz. Stil kümesinden standart bir yazı tipi olduğundan, varsayılan yazı tipi kimliğini ayarlayabiliriz:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Dinamik özelleştirmeler
 Görünümün, bir şeklin veya model öğesinin durumuna bağlı olarak değişmesini sağlamak için kendi alt sınıfını türetirsiniz `TextField` ve bir veya daha fazla yöntemi geçersiz kılın `Get...` . Ayrıca, şeklinizin ınitialeshapefields yöntemini geçersiz kılmanız ve TextField öğesinin örneğini kendi sınıfınızın bir örneğiyle değiştirmeniz gerekir.

 Aşağıdaki örnek, bir metin alanının yazı tipini şeklin model öğesinin bir Boolean etki alanı özelliğinin durumuna bağımlı hale getirir.

 Bu örnek kodu çalıştırmak için, en az dil şablonunu kullanarak yeni bir DSL çözümü oluşturun. `AlternateState`ExampleElement etki alanı sınıfına bir Boole alanı özelliği ekleyin. ExampleShape sınıfına bir simge dekoratör ekleyin ve görüntüsünü bir bit eşlem dosyası olarak ayarlayın. **Tüm Şablonları Dönüştür**' e tıklayın. DSL projesine yeni bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin.

 Kodu test etmek için F5 tuşuna basın ve hata ayıklama çözümünde örnek bir diyagram açın. Simgenin varsayılan durumu görünmelidir. Şekli seçin ve Özellikler penceresi **AlternateState** özelliğinin değerini değiştirin. Öğe adının yazı tipi değişmelidir.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Stil kümeleri
 Yukarıdaki örnek, metin alanını kullanılabilen herhangi bir yazı tipiyle nasıl değiştirekullanabileceğinizi gösterir. Bununla birlikte, tercih edilen bir yöntem, şekli şekille veya uygulamayla ilişkili bir stil kümesinden biriyle değiştirmek olur. Bunu yapmak için, <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> veya Gettextbrühıd () öğesini geçersiz kılın.

 Alternatif olarak, geçersiz kılarak şekillerinizin Stil kümesini değiştirmeyi göz önünde bulundurun <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Bu, tüm şekil alanları için yazı tiplerini ve fırçaları değiştirme etkisine sahiptir.

## <a name="customizing-image-fields"></a>Görüntü alanlarını özelleştirme
 Bir şekildeki görüntü dekoratörü tanımladığınızda ve bir resim şekli tanımladığınızda, şeklin görüntülendiği alan bir ImageField tarafından yönetilir. ImageFields ve diğer şekil alanlarının başlatılmasının örnekleri için DSL çözümünüzdeki Dsl\GeneratedCode\Shapes.cs inceleyin.

 ImageField, bir dekorata atanmış alan gibi bir şekil içindeki alanı yöneten bir nesnedir. Tek bir ImageField örneği, aynı şekil sınıfının birçok şekli arasında paylaşılır. ImageField örneği her şekil için ayrı bir görüntü depolamaz: bunun yerine, `GetDisplayImage(ShapeElement)` yöntemi şekli bir parametre olarak alır ve resmin geçerli durumuna ve model öğesine bağlı olarak görüntüyü arayabilir.

 Değişken görüntü gibi özel davranışları isterseniz, ImageField 'dan türetilmiş kendi sınıfınızı oluşturabilirsiniz.

#### <a name="to-create-a-subclass-of-imagefield"></a>ImageField öğesinin bir alt sınıfını oluşturmak için

1. DSL tanımınızda üst Şekil sınıfının **Double türetilmiş** özelliğini oluştur ' u ayarlayın.

2. `InitializeShapeFields`Şekil sınıfınızın yöntemini geçersiz kılın.

    - DSL projesinde yeni bir kod dosyası oluşturun ve şekil sınıfı için kısmi bir sınıf tanımı yazın. Burada yöntem tanımını geçersiz kılın.

3. DSL\GeneratedCode\Shapes.cs. içindeki kodu inceleyin `InitializeShapeFields`

     Geçersiz kılma yönteminde, temel yöntemi çağırın ve ardından kendi görüntü alanı sınıfınızın bir örneğini oluşturun. Listedeki normal görüntü alanını değiştirmek için bunu kullanın `shapeFields` .

## <a name="dynamic-icons"></a>Dinamik simgeler
 Bu örnek, bir simge değişikliğini şeklin model öğesinin durumuna bağımlı hale getirir.

> [!WARNING]
> Bu örnek, dinamik görüntü dekoratörü yapmayı gösterir. Ancak, bir model değişkeninin durumuna bağlı olarak yalnızca bir veya iki görüntü arasında geçiş yapmak istiyorsanız, birkaç görüntü dekoratlayıcısı oluşturmak, şekildeki aynı konumda bulmak ve sonra görünürlük filtresini model değişkeninin belirli değerlerine göre ayarlamak daha basittir. Bu filtreyi ayarlamak için DSL tanımında şekil eşlemesini seçin, DSL ayrıntıları penceresini açın ve dekoratörler sekmesine tıklayın.

 Bu örnek kodu çalıştırmak için, en az dil şablonunu kullanarak yeni bir DSL çözümü oluşturun. `AlternateState`ExampleElement etki alanı sınıfına bir Boole alanı özelliği ekleyin. ExampleShape sınıfına bir simge dekoratör ekleyin ve görüntüsünü bir bit eşlem dosyası olarak ayarlayın. **Tüm Şablonları Dönüştür**' e tıklayın. DSL projesine yeni bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin.

 Kodu test etmek için F5 tuşuna basın ve hata ayıklama çözümünde örnek bir diyagram açın. Simgenin varsayılan durumu görünmelidir. Şekli seçin ve Özellikler penceresi **AlternateState** özelliğinin değerini değiştirin. Bu durumda, simgenin bu şekle göre 90 derece döndürüldüğü gösterilmelidir.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Şekiller ve Bağlayıcıları Tanımlama](../modeling/defining-shapes-and-connectors.md)
- [Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)