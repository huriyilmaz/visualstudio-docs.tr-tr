---
title: 'Adım 11: Resim görüntüleyici uygulamanızı çalıştırın ve diğer özellikleri deneyin'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579896"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Adım 11: Resim görüntüleyici uygulamanızı çalıştırın ve diğer özellikleri deneyin

Resim görüntüleyici uygulamanız tamamlandı ve çalışmaya hazır. Uygulamanızı çalıştırabilir ve arka plan <xref:System.Windows.Forms.PictureBox>rengini ayarlayabilirsiniz. Daha fazla bilgi edinmek için, formun rengini değiştirerek, düğmeleri ve onay kutusunu özelleştirerek ve formun özelliklerini değiştirerek uygulamayı geliştirmeye çalışın.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Uygulamanızı çalıştırma ve arka plan rengini ayarlama

1. **F5'i**veya menü çubuğunda **Hata** > **Ayıklama Başlat'ı**seçin.

1. Resmi açmadan önce **arka plan renk düğmesini ayarla'yı** seçin. **Renk** iletişim kutusu açılır.

     ![Renk iletişim kutusu](../ide/media/express_colordialog.png)<br/>
***Renk*** *iletişim kutusu*

1. PictureBox arka plan rengini ayarlamak için bir renk seçin. Nasıl çalıştığını anlamak `backgroundButton_Click()` için `BackgroundButton_Click()`(veya, ) yöntemine yakından bakın.

    > [!NOTE]
    > URL'sini **Dosya Aç** iletişim kutusuna yapıştırarak internetten resim yükleyebilirsiniz. Saydam arka plana sahip bir görüntü bulmaya çalışın, böylece arka plan renginiz gösterir.

1. Temizolduğundan emin olmak için **resmi temizle** düğmesini seçin. Ardından **Kapat** düğmesini seçerek uygulamadan çıkın.

## <a name="try-other-features"></a>Diğer özellikleri deneme

* **BackColor** özelliğini kullanarak formun rengini ve düğmeleri değiştirin.

* **Yazı Tipi** ve **ForeColor** özelliklerini kullanarak düğmelerinizi ve onay kutunuzu özelleştirin.

* Formunuzun **FormBorderStyle** ve **ControlBox** özelliklerini değiştirin.

* Kullanıcı **Enter** veya **Esc** tuşunu seçtiğinde düğmelerin otomatik olarak seçilmesi için formunuzun **AcceptButton** ve **CancelButton** özelliklerini kullanın. Kullanıcı Esc'i seçtiğinde uygulamayı **Dosya** aç **Enter** iletişim kutusunu aç ve **kutuyu**kapat' ı seçin.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici 2: Zamanlanmış matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md)

Önceki öğretici adıma dönmek için [Bkz. Adım 10: Ek düğmeler ve onay kutusu için kod yazın.](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# eğitimleri](/visualstudio/get-started/csharp/)
* [Daha Fazla Visual Basic öğreticileri](/visualstudio/get-started/visual-basic/)
* [C++ eğitimi](/cpp/get-started/tutorial-console-cpp)
