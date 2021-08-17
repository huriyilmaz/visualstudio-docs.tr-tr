---
title: Resim görüntüleyicisi uygulamasını çalıştırma ve diğer özellikleri deneme
description: Resim görüntüleyicisi uygulamanızı çalıştırın ve resim görüntüleyici oluşturma öğreticisinde diğer özellikleri deneyin.
ms.date: 09/11/2019
ms.custom: SEO-VS-2020
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 39bd1f97408f81b486a7c5f4128c71dca686608f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078121"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>11. Adım: Resim görüntüleyicisi uygulamanızı çalıştırma ve diğer özellikleri deneme

Resim görüntüleyicisi uygulamanız tamamlandı ve çalıştırmaya hazır. Uygulamalarınızı çalıştırabilirsiniz ve arka plan rengini <xref:System.Windows.Forms.PictureBox> ayarlayın. Daha fazla bilgi edinmek için formun rengini değiştirerek, düğmeleri ve onay kutusunu özelleştirerek ve formun özelliklerini değiştirerek uygulamayı geliştirmeye çalışabilirsiniz.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Uygulama çalıştırma ve arka plan rengini ayarlama

1. **F5'i** seçin veya menü çubuğunda Hata Ayıklama Başlat **Hata**  >  **Ayıklama'ya tıklayın.**

1. Bir resmi açmadan önce Arka plan **rengini ayarla düğmesini** seçin. Renk **iletişim** kutusu açılır.

     ![Renk iletişim kutusu](../ide/media/express_colordialog.png)<br/>
***Renk** _ _dialog kutusu*

1. PictureBox arka plan rengini ayarlamak için bir renk seçin. Nasıl çalıştığını anlamak `backgroundButton_Click()` için (veya `BackgroundButton_Click()` ) yöntemine yakından bakın.

    > [!NOTE]
    > Url'sini Dosya Aç iletişim kutusuna yapıştırarak İnternet'e **bir resim** abilirsiniz. Arka plan renginizin olması için saydam arka plana sahip bir görüntü bulmaya çalışabilirsiniz.

1. Temiz **olduğundan emin olmak** için Resmi temizle düğmesini seçin. Ardından Kapat düğmesini seçerek **uygulamadan çıkın.**

## <a name="try-other-features"></a>Diğer özellikleri deneme

* **BackColor** özelliğini kullanarak formun rengini ve düğmeleri değiştirme.

* Font ve ForeColor özelliklerini kullanarak **düğmelerinizi** **ve onay kutularınızı özelleştirin.**

* Form'nizin **FormBorderStyle ve** **ControlBox özelliklerini** değiştirin.

* Kullanıcı Enter veya Esc tuşuna bassa düğmelerin otomatik olarak seçilecek  şekilde form'nizin AcceptButton ve **CancelButton** **özelliklerini** kullanın.  Kullanıcı Enter tuşuna **basınca** uygulamayı Dosya Aç iletişim **kutusunu** açın ve kullanıcı Esc'yi seçerken kutuyu **kapatın.**

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici 2: Zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md)

Önceki öğretici adımına dönmek için [bkz. 10. Adım: Ek](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)düğmeler için kod yazma ve onay kutusu.

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Diğer Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticisi](/cpp/get-started/tutorial-console-cpp)