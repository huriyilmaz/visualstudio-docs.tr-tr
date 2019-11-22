---
title: '11. Adım: programınızı çalıştırın ve diğer özellikleri deneyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d79bf8205e4233a89effcd04196b18f9c11df26
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295763"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>11. Adım: Programınızı Çalıştırma ve Diğer Özellikleri Deneme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programınız tamamlandı ve çalıştırılmaya hazırlanıyor. Programınızı çalıştırabilir ve PictureBox 'ın arka plan rengini ayarlayabilirsiniz. Daha fazla bilgi edinmek için, formun rengini değiştirerek, düğmeleri ve onay kutusunu özelleştirerek ve formun özelliklerini değiştirerek programı geliştirmeyi deneyin.

 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 5](https://go.microsoft.com/fwlink/?LinkId=205216) veya [öğretici 1: video üzerinde C# bir resim görüntüleyici oluşturma 5](https://go.microsoft.com/fwlink/?LinkId=205206). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-run-your-program-and-set-the-background-color"></a>Programınızı çalıştırmak ve arka plan rengini ayarlamak için

1. F5 ' i seçin veya menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat**' ı seçin.

2. Bir resmi açmadan önce, **arka plan rengini ayarla** düğmesini seçin. **Renk** iletişim kutusu açılır.

     ![Renk iletişim kutusu](../ide/media/express-colordialog.png "Express_ColorDialog") Renk iletişim kutusu

3. PictureBox arka plan rengini ayarlamak için bir renk seçin. Nasıl çalıştığını anlamak için `backgroundButton_Click()` yöntemine yakından bakın.

    > [!NOTE]
    > URL 'sini **Dosya Aç** iletişim kutusuna yapıştırarak Internet 'ten bir resim yükleyebilirsiniz. Arka plan renginiz görünür olduğundan, saydam bir arka plana sahip bir görüntü bulmaya çalışın.

4. Temizlendiğinden emin olmak için **Resmi Temizle** düğmesini seçin. Sonra, **Kapat** düğmesini seçerek programdan çıkın.

### <a name="to-try-other-features"></a>Diğer özellikleri denemek için

- **BackColor** özelliğini kullanarak formun ve düğmelerin rengini değiştirin.

- **Yazı tipi** ve **ForeColor** özelliklerini kullanarak düğmelerinizi ve onay kutusunu özelleştirin.

- Formunuzun **FormBorderStyle** ve **ControlBox** özelliklerini değiştirin.

- Kullanıcı ENTER veya ESC tuşunu seçtiğinde düğmelerin otomatik olarak seçilmesi için formunuzun **AcceptButton** ve **CancelButton** özelliklerini kullanın. Kullanıcı ENTER ' a tıkladığında **dosyayı aç** iletişim kutusunu açar ve Kullanıcı ESC ' i seçtiğinde kutuyu kapatır.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Visual Studio 'da programlama hakkında daha fazla bilgi edinmek için bkz. [programlama kavramları](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).

- Visual Basic hakkında daha fazla bilgi edinmek için bkz. [Visual Basic uygulamalar geliştirme](https://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).

- Görsel C#hakkında daha fazla bilgi edinmek için bkz. [ C# dile giriş ve .NET Framework](https://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).

- Sonraki öğreticiye gitmek için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

- Önceki öğretici adımına dönmek için bkz. [adım 10: ek düğmeler ve onay kutusu Için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
