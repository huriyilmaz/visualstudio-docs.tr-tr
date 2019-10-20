---
title: Diyagram üzerinde arka plan görüntüsü ayarlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b7d206852101a1d99a08eac710d88e93afe4a04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671200"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirme ve modelleme SDK [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], özel kod kullanarak oluşturulan tasarımcı için arka plan görüntüsünü ayarlayabilirsiniz.

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

12. **Özellikler** penceresinde `Custom Tool` özelliğini `ResXFileCodeGenerator` olarak ayarlayın.

13. **Çözüm Gezgini**, DSL projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' e tıklayın.

14. Klasörü **özel**olarak adlandırın.

15. Özel klasöre sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni öğe**' ye tıklayın.

16. **Yeni öğe Ekle** iletişim kutusunda, **Şablonlar** listesinde, **kod dosyası**' na tıklayın.

17. **Ad** kutusuna `BackgroundImage.cs` yazın ve **Ekle**' ye tıklayın.

18. Aşağıdaki kodu BackgroundImage.cs dosyasına kopyalayın, ad alanı, diyagram sınıf adı ve görüntü dosyası kaynak adı ' nı ayarlama.

     "MyDiagramClass" ifadesini, Dsl\GeneratedCode\Diagrams.cs. içinde tanımlanan diyagram parçalı sınıfının adıyla değiştirin Ayrıca, Dsl\GeneratedCode\Diagrams.cs. dosyasından doğru ad alanını alabilirsiniz

    ```
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

## <a name="see-also"></a>Ayrıca Bkz.
 [Şekilleri ve bağlayıcıları tanımlama](../modeling/defining-shapes-and-connectors.md) [metin ve görüntü alanlarını özelleştirme](../modeling/customizing-text-and-image-fields.md) [Program kodu](../modeling/navigating-and-updating-a-model-in-program-code.md) [yazma kodu, etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
