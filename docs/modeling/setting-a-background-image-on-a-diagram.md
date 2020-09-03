---
title: Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7701bf0ba1467b481f6da64d3c2e229be77a7fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542590"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama
Visual Studio görselleştirme ve modelleme SDK 'da, özel kod kullanarak oluşturulan tasarımcı için arka plan resmini ayarlayabilirsiniz.

## <a name="setting-the-background-image"></a>Arka plan görüntüsünü ayarlama

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Oluşturulmuş bir tasarımcı için arka plan görüntüsü ayarlamak için

1. Diyagramın arka planı olarak kullanmak istediğiniz resim dosyasını geçerli proje için Dsl\Resources dizinine kopyalayın.

2. **Çözüm Gezgini**, Dsl\Resources klasörüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın.

3. **Varolan öğe Ekle** iletişim kutusunda Dsl\Resources klasörüne göz atın.

4. **Dosya türü** listesinde, **görüntü dosyaları**' na tıklayın.

5. Dizine kopyaladığınız görüntü dosyasına tıklayın ve ardından **Ekle**' ye tıklayın.

6. DSL ' ye sağ tıklayın ve **Özellikler** ' e tıklayarak DSL projesinin özelliklerini açın.

7. **Kaynaklar** sekmesinde, **Bu proje varsayılan bir kaynak dosyası içermez öğesine tıklayın. Bir tane oluşturmak için buraya tıklayın.**

8. Resmi **Çözüm Gezgini** kaynak dosyasına sürükleyerek, resim dosyasını kaynak dosyasına ekleyin.

9. Dosya menüsünü açın ve proje özelliklerini kaydetmek için seçeneğe tıklayın.

10. Dsl\Properties\Resources.resx dosyasının var olduğunu ve Resources.Designer.cs dosyasına sahip olduğunu doğrulayın.

11. Resources.Designer.cs eksikse **Çözüm Gezgini**' de resources. resx dosyasına tıklayın.

12. **Özellikler** penceresinde, `Custom Tool` özelliğini olarak ayarlayın `ResXFileCodeGenerator` .

13. **Çözüm Gezgini**, DSL projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' e tıklayın.

14. Klasörü **özel**olarak adlandırın.

15. Özel klasöre sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni öğe**' ye tıklayın.

16. **Yeni öğe Ekle** iletişim kutusunda, **Şablonlar** listesinde, **kod dosyası**' na tıklayın.

17. **Ad** kutusuna yazın `BackgroundImage.cs` ve **Ekle**' ye tıklayın.

18. Aşağıdaki kodu BackgroundImage.cs dosyasına kopyalayın, ad alanı, diyagram sınıf adı ve görüntü dosyası kaynak adı ' nı ayarlama.

     "MyDiagramClass" ifadesini, Dsl\GeneratedCode\Diagrams.cs. içinde tanımlanan diyagram parçalı sınıfının adıyla değiştirin Ayrıca, Dsl\GeneratedCode\Diagrams.cs. dosyasından doğru ad alanını alabilirsiniz

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

     Modeli program kodu ile özelleştirme hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Şekiller ve Bağlayıcıları Tanımlama](../modeling/defining-shapes-and-connectors.md)
- [Metin ve Görüntü Alanlarını Özelleştirme](../modeling/customizing-text-and-image-fields.md)
- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
