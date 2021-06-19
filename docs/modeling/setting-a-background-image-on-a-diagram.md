---
title: Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama
description: Visual Studio Ve Modelleme SDK'sı'nda özel kod kullanarak oluşturulan bir tasarımcının arka plan görüntüsünü ayarlayabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9304117932b92408f12a23747253de66dfd767d1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385675"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama
Görselleştirme Visual Studio Modelleme SDK'sı içinde, özel kod kullanarak oluşturulan bir tasarımcının arka plan görüntüsünü oluşturabilirsiniz.

## <a name="setting-the-background-image"></a>Arka plan görüntüsünü ayarlama

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Oluşturulan tasarımcı için arka plan görüntüsü ayarlamak için

1. Diyagramın arka planı olarak kullanmak istediğiniz görüntü dosyasını geçerli projenin Dsl\Resources dizinine kopyalayın.

2. Bu **Çözüm Gezgini** Dsl\Resources klasörüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Mevcut Öğe'ye **tıklayın.**

3. Var Olan **Öğeyi Ekle iletişim** kutusunda Dsl\Resources klasörüne gidin.

4. Türe **göre dosyalar listesinde** Görüntü Dosyaları'ya **tıklayın.**

5. Dizinine kopyalanan görüntü dosyasına ve ardından Ekle'ye **tıklayın.**

6. Dsl'ye sağ tıklayın ve **Özellikler'e** tıklar ve Dsl projesinin özelliklerini açın.

7. Kaynaklar **sekmesinde Bu** proje **bir varsayılan kaynak dosyası içermedi'ye tıklayın. Oluşturmak için buraya tıklayın.**

8. Resim dosyasını kaynak dosyadan kaynaklar penceresine **sürükleyerek Çözüm Gezgini** dosyasına ekleyin.

9. Dosya menüsünü açın ve proje özelliklerini kaydetmek için seçeneğine tıklayın.

10. Dsl\Properties\Resources.resx dosyasının mevcut olduğunu ve altında Resources.Designer.cs dosyasının olduğunu doğrulayın.

11. Resources.Designer.cs eksikse, dosyasındaki Resources.resx **dosyasına Çözüm Gezgini.**

12. Özellikler **penceresinde** özelliğini olarak `Custom Tool` `ResXFileCodeGenerator` ayarlayın.

13. Bu **Çözüm Gezgini** Dsl projesine sağ tıklayın, Ekle'nin üzerine **gelin** ve Yeni Klasör'e **tıklayın.**

14. Klasöre Özel **adını girin.**

15. Özel klasörüne sağ tıklayın, Ekle'nin **üzerine gelin ve** Yeni **Öğe'ye tıklayın.**

16. Yeni **Öğe Ekle iletişim** kutusundaki Şablonlar listesinde **Kod Dosyası'nın** **üzerine tıklayın.**

17. Ad **kutusuna yazın** ve `BackgroundImage.cs` Ekle'ye **tıklayın.**

18. Ad alanını, diyagram sınıf adını ve görüntü dosyası kaynak adını ayarlayarak aşağıdaki kodu BackgroundImage.cs dosyasına kopyalayın.

     "MyDiagramClass" ifadesini Dsl\GeneratedCode\Diagrams.cs içinde tanımlanan diyagram kısmi sınıfının adıyla değiştirin. Dsl\GeneratedCode\Diagrams.cs dosyasından doğru ad alanını da edinebilirsiniz.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Modeli program koduyla özelleştirme hakkında daha fazla bilgi için bkz. Program Kodunda [Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Şekiller ve Bağlayıcıları Tanımlama](../modeling/defining-shapes-and-connectors.md)
- [Metin ve Görüntü Alanlarını Özelleştirme](../modeling/customizing-text-and-image-fields.md)
- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
