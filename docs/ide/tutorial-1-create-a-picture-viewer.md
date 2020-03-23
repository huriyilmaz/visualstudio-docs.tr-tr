---
title: 'Öğretici 1: Resim görüntüleyicisi oluşturma'
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f1431d56516c749004cef1b35ada482a6c53446
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579715"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Öğretici 1: Resim görüntüleyicisi oluşturma

Bu öğreticide, bir dosyadan resim yükleyen ve bir pencerede görüntüleyen bir uygulama oluşturursunuz. Düğmeler ve resim kutuları gibi denetimleri formunuzun üzerine sürüklemek, özelliklerini ayarlamak ve formu sorunsuz bir şekilde yeniden boyutlandırmak için kapsayıcıları kullanmak için **Windows Forms Designer'ı** kullanmayı öğrenirsiniz. Ayrıca kod yazmaya başlarsınız.

> [!NOTE]
> Bu öğretici hem C# hem de Visual Basic'i kapsar, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.

Bu öğretici aşağıdaki görevleri size yol sağlar:

* Yeni bir proje oluşturma.

* Bir uygulamayı test edin (hata ayıklama).

* Bir forma onay kutuları ve düğmeler gibi temel denetimler ekleyin.

* Düzenleri kullanarak form üzerindeki konum denetimleri.

* Bir forma **Dosya aç** ve **renk** iletişim kutularını ekleyin.

* IntelliSense ve kod parçacıklarını kullanarak kod yazın.

* Olay işleyicisi yöntemlerini yazın.

İşlemi tamamladığınızda, uygulamanız aşağıdaki resme benzer olmalıdır:

![Bu öğreticide oluşturduğunuz Resim Görüntüleyici uygulaması](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Öğretici bağlantılar

|Başlık|Açıklama|
|-----------|-----------------|
|[Adım 1: Windows Forms App projesi oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)|Bir Windows Forms App projesi oluşturarak başlayın.|
|[Adım 2: Resim görüntüleyici uygulamanızı çalıştırın](../ide/step-2-run-your-program.md)|Önceki adımda oluşturduğunuz Windows Forms App projesini çalıştırın.|
|[Adım 3: Form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md)|**Özellikler** penceresini kullanarak formunuzun görünüm şeklini değiştirin.|
|[Adım 4: TabloDüzeniPanel denetimi ile formunuzu düzene sürün](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Formunuza `TableLayoutPanel` bir denetim ekleyin.|
|[Adım 5: Formunuza denetim ekleme](../ide/step-5-add-controls-to-your-form.md)|Formunuza `PictureBox` denetim ve `CheckBox` denetim gibi denetimler ekleyin. Formunuza düğmeler ekleyin.|
|[Adım 6: Düğme denetimlerinizi adlandırın](../ide/step-6-name-your-button-controls.md)|Düğmelerinizi daha anlamlı bir şeye yeniden adlandırın.|
|[Adım 7: Formunuza iletişim bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md)|Formunuza `OpenFileDialog` bir `ColorDialog` bileşen ve bileşen ekleyin.|
|[Adım 8: Resim düğmesi olay işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense aracını kullanarak kod yazın.|
|[Adım 9: Kodunuzu gözden geçirin, yorumlayın ve test edin](../ide/step-9-review-comment-and-test-your-code.md)|Kodunuzu gözden geçirin ve test edin. Gerektiği gibi yorum ekleyin.|
|[Adım 10: Ek düğmeler ve onay kutusu için kod yazın](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|IntelliSense'i kullanarak diğer düğmeleri ve onay kutusunu n için kod yazın.|
|[Adım 11: Uygulamanızı çalıştırın ve diğer özellikleri deneyin](../ide/step-11-run-your-program-and-try-other-features.md)|Uygulamanızı çalıştırın ve arka plan rengini ayarlayın. Renkleri, yazı tiplerini ve kenarlıkları değiştirme gibi diğer özellikleri deneyin.|

Ayrıca büyük, ücretsiz video öğrenme kaynakları sizin için kullanılabilir. C#'da programlama hakkında daha fazla bilgi edinmek [için C# temellerine bakın: Yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Visual Basic'te programlama hakkında daha fazla bilgi edinmek [için Visual Basic temellerine bakın: Mutlak yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için Adım 1 ile **[başlayın: Windows Forms uygulama projesi oluşturun.](../ide/step-1-create-a-windows-forms-application-project.md)**

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# eğitimleri](/visualstudio/get-started/csharp/)
* [Visual Basic eğitimleri](/visualstudio/get-started/visual-basic/)
* [C++ eğitimleri](/cpp/get-started/tutorial-console-cpp)
