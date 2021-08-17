---
title: 'Öğretici 1: Resim görüntüleyici oluşturma'
description: Bir dosyadan resim yüken ve pencerede görüntüleyen bir uygulama derlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a232ce7297aee8e2682bbadf3340f0014de7e0492a3a364d17035750abff63e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121444470"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Öğretici 1: Resim görüntüleyici oluşturma

Bu öğreticide, bir dosyadan resim yüken ve pencerede görüntüleyen bir uygulama derlemeniz gerekir. Düğme ve resim kutuları **gibi denetimleri form Windows,** özelliklerini ayarlamak ve kapsayıcıları kullanarak formu sorunsuz bir şekilde yeniden boyutlandırmak için Windows Forms Tasarımcısı'nın nasıl kullanılacazını öğrenirsiniz. Ayrıca kod yazmaya da başladın.

> [!NOTE]
> Bu öğreticide hem C# hem de Visual Basic, bu nedenle kullanmakta olan programlama diline özgü bilgilere odaklanın.

Bu öğretici, aşağıdaki görevlerde size yol gösterir:

* Yeni bir proje oluşturma.

* Bir uygulamayı test (hata ayıklama).

* Forma onay kutuları ve düğmeler gibi temel denetimler ekleyin.

* Düzenleri kullanarak bir formda denetimleri konumlandırma.

* Forma **Dosya** ve **Renk** Aç iletişim kutuları ekleyin.

* IntelliSense ve kod parçacıkları kullanarak kod yazma.

* Olay işleyicisi yöntemleri yazma.

Tamamlasanız, uygulama aşağıdaki görüntüye benzer şekilde görüntüye benzer:

![Bu öğreticide oluştursanız da Resim Görüntüleyicisi uygulaması](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Windows Forms Uygulaması projesi oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)|Başlangıç olarak bir Windows Forms Uygulaması projesi oluşturma.|
|[2. Adım: Resim görüntüleyicisi uygulamanızı çalıştırma](../ide/step-2-run-your-program.md)|Önceki Windows oluşturduğunuz Windows Forms Uygulaması projesini çalıştırın.|
|[3. Adım: Form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md)|Özellikler penceresini kullanarak form'nizin nasıl **göründüğünü** değiştirin.|
|[4. Adım: TableLayoutPanel denetimi ile formunuzu düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Formnize `TableLayoutPanel` bir denetim ekleyin.|
|[5. Adım: Formunuza denetimler ekleme](../ide/step-5-add-controls-to-your-form.md)|Formnize denetim `PictureBox` ve denetim `CheckBox` gibi denetimler ekleyin. Formnize düğme ekleyin.|
|[6. Adım: Düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md)|Düğmelerinizi daha anlamlı bir adla yeniden adlandırabilirsiniz.|
|[7. Adım: Formunuza iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md)|Formnize `OpenFileDialog` bir `ColorDialog` bileşen ve bileşen ekleyin.|
|[8. Adım: Resim göster düğmesi olay işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense aracını kullanarak kod yazma.|
|[9. Adım: Kodunuzu gözden geçirme, açıklama ve test etme](../ide/step-9-review-comment-and-test-your-code.md)|Kodunuzu gözden geçirme ve test etmek. Gerektiğinde açıklama ekleyin.|
|[10. Adım: Ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|IntelliSense kullanarak diğer düğmelerin ve onay kutusunun çalışması için kod yazın.|
|[11. Adım: Uygulamanızı çalıştırma ve diğer özellikleri deneme](../ide/step-11-run-your-program-and-try-other-features.md)|Uygulamalarınızı çalıştırın ve arka plan rengini ayarlayın. Renkleri, yazı tiplerini ve kenarlıkları değiştirme gibi diğer özellikleri deneyin.|

Ayrıca size harika, ücretsiz video öğrenme kaynakları da sunulmaktadır. C# dilinde programlama hakkında daha fazla bilgi edinmek için [bkz. C# temelleri: Mutlak yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Programlama hakkında daha fazla bilgi edinmek Visual Basic için [bkz. Visual Basic temelleri: Mutlak yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için **[1. Adım: Windows Forms uygulama projesi oluşturun.](../ide/step-1-create-a-windows-forms-application-project.md)**

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)