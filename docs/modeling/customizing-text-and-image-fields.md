---
title: Metin ve Görüntü Alanlarını Özelleştirme
description: Metin ve görüntü dosyalarını özelleştirme hakkında bilgi öğrenin. Ayrıca, bir metin dekoratörü bir şekilde tanımladığınız zaman, bunun textField ile temsil edilen olduğunu da öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8f56c67a16b59b17de5a4bd95ad9a074203b097224844f541adc8b658d60edea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386062"
---
# <a name="customizing-text-and-image-fields"></a>Metin ve Görüntü Alanlarını Özelleştirme
Bir metin dekoratörü şekilde tanımladığınız zaman, metin dekoratörü bir TextField ile temsil edilen. TextFields ve diğer ShapeFields başlatma örnekleri için DSL çözümde Dsl\GeneratedCode\Shapes.cs'yi inceleyin.

 TextField, bir etikete atanan alan gibi bir şekil içindeki alanı yöneten bir nesnedir. Bir TextField örneği aynı sınıfın birçok şekli arasında paylaşılır. TextField örneği etiketin metnini her örnek için ayrı depolamaz: bunun yerine yöntemi şekli parametre olarak alır ve şeklin ve model öğesinin geçerli durumuna bağlı olarak metni `GetDisplayText(ShapeElement)` indirebilirsiniz.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Metin alanı görünümü nasıl belirlenir?
 `DoPaint()`yöntemini çağırarak alanı ekranda görüntüler. Varsayılanı geçersiz `DoPaint(),` kılarak veya çağıran bazı yöntemleri geçersiz kılarak. Varsayılan yöntemlerin aşağıdaki basitleştirilmiş sürümü, varsayılan davranışı geçersiz kılmayı anlamanıza yardımcı olabilir:

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

 gibi birkaç yöntem ve `Get` özellik `Default` çifti daha `DefaultMultipleLine/GetMultipleLine()` vardır. Şeklin tüm örneklerinin değerini değiştirmek için Default özelliğine bir değer atabilirsiniz. Değerin bir şekil örneğinden diğerine değişiklik gösterebiliyor veya şeklin veya model öğesinin durumuna bağlı olarak yöntemini geçersiz `Get` kılın.

## <a name="static-customizations"></a>Statik özelleştirmeler
 Bu şekil alanı örneklerini değiştirmek için önce DSL Tanımı'nın özelliğini ayar olup olmadığı hakkında bir karara varabilirsiniz. Örneğin, yazı tipi boyutunu ve stilini Özellikler penceresi.

 Yoksa, şekil sınıfınıza ait yöntemi geçersiz kılın ve `InitializeShapeFields` metin alanı için uygun `Default...` özellik için bir değer attayabilirsiniz.

> [!WARNING]
> 'i geçersiz kılmak için DSL Tanımında şekil sınıfının Çift Türetilmiş `InitializeShapeFields()` özelliğini olarak  `true` ayarlayabilirsiniz.

 Bu örnekte, şeklin kullanıcı yorumları için kullanılacak bir metin alanı vardır. Standart açıklama yazı tipini kullanmak istiyorum. Stil kümesinden standart bir yazı tipi olduğundan varsayılan yazı tipi kimliğini de değiştirebiliriz:

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
 Görünümün şeklin veya model öğesinin durumuna bağlı olarak değişiklik göstersin, kendi alt sınıfını türetin ve bir veya daha fazla `TextField` yöntemi `Get...` geçersiz kılın. Ayrıca şeklinizin InitializeShapeFields yöntemini geçersiz kılmanız ve TextField örneğini kendi sınıfınıza ait bir örnekle değiştirmeniz gerekir.

 Aşağıdaki örnek, metin alanının yazı tipini şeklin model öğesinin Boole etki alanı özelliğinin durumuna bağımlı hale gelir.

 Bu örnek kodu çalıştırmak için Minimum Dil şablonunu kullanarak yeni bir DSL çözümü oluşturun. ExampleElement etki alanı sınıfına bir Boole `AlternateState` etki alanı özelliği ekleyin. ExampleShape sınıfına bir simge dekoratör ekleyin ve görüntüsünü bit eşlem dosyasına ayarlayın. Tüm **Şablonları Dönüştür'e tıklayın.** DSL projesine yeni bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin.

 Kodu test etmek için F5 tuşuna basın ve hata ayıklama çözümünde bir örnek diyagram açın. Simgenin varsayılan durumu görüntü gerekir. Şekli seçin ve Özellikler penceresi **AlternateState** özelliğinin değerini değiştirme. Öğe adının yazı tipi değişsin.

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
 Yukarıdaki örnekte, metin alanını kullanılabilen herhangi bir yazı tipiyle nasıl değiştirebilirsiniz? Ancak tercih edilen yöntem, şekliyle veya uygulamayla ilişkilendirilmiş bir stil kümesiyle değiştirmektir. Bunu yapmak için veya <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> GetTextBrushId() geçersiz kılın.

 Alternatif olarak, geçersiz karak şeklinizin stil kümesini değiştirmeyi <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> düşünün. Bu, tüm şekil alanları için yazı tiplerini ve fırçaları değiştirme etkisine sahiptir.

## <a name="customizing-image-fields"></a>Görüntü Alanlarını Özelleştirme
 Bir şekil içinde görüntü dekoratör tanımladığınız zaman ve görüntü şeklini tanımladığınız zaman şeklin görüntü olduğu alan bir ImageField tarafından yönetilir. ImageFields ve diğer ShapeFields başlatma örnekleri için DSL çözümde Dsl\GeneratedCode\Shapes.cs'yi inceleyin.

 ImageField, bir dekoratöre atanan alan gibi bir şekil içindeki alanı yöneten bir nesnedir. Bir ImageField örneği, aynı şekil sınıfının birçok şekli arasında paylaşılır. ImageField örneği her şekil için ayrı bir görüntü depolamaz: bunun yerine yöntemi şekli parametre olarak alır ve şeklin geçerli durumuna ve model öğesinin durumuna bağlı olarak görüntüyü bu şekilde `GetDisplayImage(ShapeElement)` indirebilirsiniz.

 Değişken görüntü gibi özel bir davranışa sahip olmak için ImageField'den türetilen kendi sınıfınızı oluşturabilirsiniz.

#### <a name="to-create-a-subclass-of-imagefield"></a>ImageField alt sınıfı oluşturmak için

1. DSL **Tanımınız içinde üst** şekil sınıfının İki Kez Türetilen Özelliğini Üretir özelliğini ayarlayın.

2. Şekil `InitializeShapeFields` sınıfınıza göre yöntemini geçersiz kılın.

    - DSL projesinde yeni bir kod dosyası oluşturun ve şekil sınıfı için kısmi bir sınıf tanımı yazın. Burada yöntem tanımını geçersiz kılın.

3. `InitializeShapeFields`DSL\GeneratedCode\Shapes.cs içinde kodunu inceleyin.

     Geçersiz kılma yönteminde temel yönteminizi çağırarak kendi görüntü alanı sınıfı örneğinizi oluşturun. Listede normal görüntü alanını değiştirmek için bunu `shapeFields` kullanın.

## <a name="dynamic-icons"></a>Dinamik simgeler
 Bu örnek, şeklin model öğesinin durumuna bağlı olarak bir simge değişikliği yapar.

> [!WARNING]
> Bu örnekte, dinamik görüntü dekoratörü yapma hakkında bilgi ve içerikler yer almaktadır. Ancak model değişkeninin durumuna bağlı olarak yalnızca bir veya iki görüntü arasında geçiş yapmak için birkaç görüntü dekoratör oluşturmak, bunları şekilde aynı konumda bulmak ve ardından Görünürlük filtresini model değişkeninin belirli değerlerine bağlı olarak ayarlamak daha kolaydır. Bu filtreyi ayarlamak için DSL Tanımı'nın şekil haritasını seçin, DSL Ayrıntıları penceresini açın ve Dekoratörler sekmesine tıklayın.

 Bu örnek kodu çalıştırmak için Minimum Dil şablonunu kullanarak yeni bir DSL çözümü oluşturun. ExampleElement etki alanı sınıfına bir Boole `AlternateState` etki alanı özelliği ekleyin. ExampleShape sınıfına bir simge dekoratör ekleyin ve görüntüsünü bit eşlem dosyasına ayarlayın. Tüm **Şablonları Dönüştür'e tıklayın.** DSL projesine yeni bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin.

 Kodu test etmek için F5 tuşuna basın ve hata ayıklama çözümünde bir örnek diyagram açın. Simgenin varsayılan durumu görüntü gerekir. Şekli seçin ve Özellikler penceresi **AlternateState** özelliğinin değerini değiştirme. Simge daha sonra bu şekilde 90 dereceye kadar döndürülmüş olarak görünerek görünür.

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