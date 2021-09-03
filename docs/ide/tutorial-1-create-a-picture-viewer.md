---
title: 'Öğretici 1: resim görüntüleyici oluşturma'
description: Bir dosyadan resim yükleyen ve bir pencerede görüntüleyen bir uygulama oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e19a66adaf2123879e07f784bfbc6b953956001d
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397700"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Öğretici 1: resim görüntüleyici oluşturma

Bu öğreticide, bir dosyadan resim yükleyen ve onu bir pencerede görüntüleyen bir uygulama oluşturacaksınız. formunuza düğmeler ve resim kutuları gibi denetimleri sürüklemek, özelliklerini ayarlamak ve formu düzgün şekilde yeniden boyutlandırmak için kapsayıcıları kullanmak üzere **Windows Form Tasarımcısı** kullanmayı öğreneceksiniz. Ayrıca kod yazmaya başlayın.

> [!NOTE]
> bu öğretici hem C# hem de Visual Basic yanı sıra, kullanmakta olduğunuz programlama diline özgü bilgilere de odaklanırsınız.

Bu öğretici aşağıdaki görevlerde size kılavuzluk eder:

* Yeni bir proje oluşturma.

* Bir uygulamayı test etme (hata ayıklama).

* Bir forma onay kutuları ve düğmeler gibi temel denetimleri ekleyin.

* Düzenleri kullanarak bir formdaki denetimleri konumlandırın.

* Bir forma **Açık dosya** ve **renk** iletişim kutuları ekleyin.

* IntelliSense ve kod parçacıkları kullanarak kod yazın.

* Olay işleyicisi yöntemlerini yazın.

Bitirdiğinizde, uygulamanız aşağıdaki görüntüye benzer görünmelidir:

![Bu öğreticide oluşturduğunuz resim görüntüleyici uygulaması](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Windows Forms Uygulaması projesi oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)|Windows Forms bir uygulama projesi oluşturarak başlayın.|
|[2. Adım: resim görüntüleyici uygulamanızı çalıştırma](../ide/step-2-run-your-program.md)|önceki adımda oluşturduğunuz Windows Forms uygulama projesini çalıştırın.|
|[3. Adım: Form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md)|**Özellikler** penceresini kullanarak formunuzun görünme şeklini değiştirin.|
|[4. Adım: TableLayoutPanel denetimi ile formunuzu düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Formunuza bir `TableLayoutPanel` denetim ekleyin.|
|[5. Adım: Formunuza denetimler ekleme](../ide/step-5-add-controls-to-your-form.md)|`PictureBox`Formunuza denetim ve denetim gibi denetimler ekleyin `CheckBox` . Formunuza düğmeler ekleyin.|
|[6. Adım: Düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md)|Düğmelerinizi daha anlamlı bir şekilde yeniden adlandırın.|
|[7. Adım: Formunuza iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md)|Formunuza bir `OpenFileDialog` bileşen ve `ColorDialog` bileşen ekleyin.|
|[8. Adım: resim göster düğmesi olay işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense aracını kullanarak kod yazın.|
|[9. Adım: Kodunuzu gözden geçirme, açıklama ve test etme](../ide/step-9-review-comment-and-test-your-code.md)|Kodunuzu gözden geçirin ve test edin. Gerektiğinde Yorumlar ekleyin.|
|[10. Adım: Ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|IntelliSense kullanarak diğer düğmeleri ve onay kutusunu çalışacak şekilde kod yazın.|
|[11. Adım: Uygulamanızı çalıştırma ve diğer özellikleri deneme](../ide/step-11-run-your-program-and-try-other-features.md)|Uygulamanızı çalıştırın ve arka plan rengini ayarlayın. Renkleri, yazı tiplerini ve kenarlıkları değiştirme gibi diğer özellikleri deneyin.|

Ayrıca harika, ücretsiz video öğrenimi kaynakları da mevcuttur. C# dilinde programlama hakkında daha fazla bilgi edinmek için bkz. [C# temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Sonraki adımlar

öğreticiye başlamak için, 1. **[adım: Windows Forms uygulama projesi oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)** ile başlayın.

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)