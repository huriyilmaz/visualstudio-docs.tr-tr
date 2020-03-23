---
title: 'Adım 9: Kodunuzu gözden geçirin, yorumlayın ve test edin'
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b31532bf6c26512e471ee787dc7219620e6db62
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579751"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Adım 9: Kodunuzu gözden geçirin, yorumlayın ve test edin

Daha sonra kodunuza bir yorum ekleyebilirsiniz. Yorum, uygulamanın nasıl bir şekilde değiştiğini değiştirmeyen bir notdur. Kodunuzu okuyan birinin ne işe yyaptığını anlamasını kolaylaştırır. Kodunuza yorum eklemek girmek için iyi bir alışkanlıktır.

C#'da, iki ileri eğreşme (//) satırı yorum olarak işaretler. Visual Basic'te, bir satırı yorum olarak işaretlemek için tek bir tırnak işareti (') kullanılır. Bir yorum ekledikten sonra, uygulamanızı test esiniz. Projeleriniz üzerinde çalışırken kodunuzu sık sık çalıştırmak ve test etmek iyi bir uygulamadır, böylece kod daha karmaşık hale gelmeden önce herhangi bir sorunu erkenden yakalayıp çözebilirsiniz. Buna *yinelemeli test*denir.

Sadece çalışan bir şey inşa, ve henüz bitmiş olmasına rağmen, zaten bir resim yükleyebilirsiniz. Kodunuza bir yorum eklemeden ve test etmeden önce, bu kavramları sık sık kullanacağınız için kod kavramlarını gözden geçirmek için zaman ayırın:

- **Windows Forms Designer'da** **resim göster** düğmesini çift tıklattığınızda, IDE otomatik olarak programınızın koduna bir *yöntem* ekledi.

- Yöntemler, kodunuzu nasıl düzenlediğinizdir: Kodunuzu birlikte gruplandırma yöntemidir.

- Çoğu zaman, bir yöntem (veya) `showButton_Click()` `ShowButton_Click()`yönteminizin bir iletişim kutusunu nasıl gösterdiği ve ardından bir resim yüklemesi gibi belirli bir sırada az sayıda şey yapar.

- Yöntem, kod *deyimlerinden*veya kod satırlarından oluşur. Kod deyimlerini bir araya getirmek için bir yöntem düşünün.

- Bir yöntem yürütüldüğünde *called*veya çağrıldığında, yöntemdeki ifadeler ilkinden başlayarak birbiri ardına sırayla yürütülür.

   Aşağıda bir deyim örneği verilmiştir.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   İfadeler, programlarınızın bir şeyler yapmasını sağlamakta. C#'da bir deyim her zaman yarı kolonda biter. Visual Basic'te, bir satırın sonu bir deyimin sonudur. (Visual Basic'te yarım kolon gerekmez.) Önceki deyim, kullanıcının <xref:System.Windows.Forms.PictureBox> **OpenFileDialog** bileşeniile seçtiği dosyayı yüklemesini sağlar.

## <a name="to-add-comments"></a>Yorum eklemek için

1. Kodunuza aşağıdaki yorumu ekleyin.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    **showButton** düğmenizin <xref:System.Windows.Forms.Control.Click> olay işleyicisi artık tamamlandı ve çalışıyor. Bir `if` deyimle başlayarak kod yazmaya başladınız. Bir `if` deyim, uygulamanıza "Bu tek şeyi kontrol edin ve doğruysa, bu eylemleri yapın" şeklinde ifade edeyim. Bu durumda, uygulamanıza **Dosya aç** iletişim kutusunu açmasını söylersiniz ve kullanıcı bir dosya seçip **Tamam** düğmesini seçerse, bu dosyayı **PictureBox'a**yükleyin.

    > [!TIP]
    > IDE kod yazmanızı kolaylaştırmak için oluşturulmuşve *kod parçacıkları* bunu yapmanın bir yoludur. Parçacık, küçük bir kod bloğuna genişletilen bir kısayoldur.
    >
    >  Mevcut tüm parçacıkları görebilirsiniz. Menü çubuğunda, **Araçlar** > **Kodu Parçacıkları Yöneticisi'ni**seçin. C# için `if` parçacık **Visual C#** 'dadır. `if` Visual Basic için, parçacıklar Kod **Desenleri** > **Koşullu lar ve Döngüler**bulunmaktadır. Bu yöneticiyi, varolan parçacıklara göz atmak veya kendi parçacıklarınızı eklemek için kullanabilirsiniz.
    >
    >  Kod yazarken bir parçacığı etkinleştirmek için yazın ve **Sekme** anahtarını seçin. **IntelliSense** penceresinde birçok parçacık görünür, bu nedenle **Sekme** anahtarını iki kez seçersiniz: önce **IntelliSense** penceresinden parçacığı seçmek ve sonra IDE'ye parçacığı kullanmasını söylemek. (IntelliSense `if` parçacığı destekler, ancak `ifelse` parçacık değil.)

1. Uygulamanızı çalıştırmadan önce, aşağıdaki ekran görüntüsüne benzer olması gereken Tümaraç Çubuğunu **Kaydet** düğmesini seçerek uygulamanızı kaydedin.

     ![Tüm araç çubuğu düğmesini kaydet](../ide/media/express_iconsaveall.png)<br>
***Tümlerini Kaydet*** *düğmesi*

     Alternatif olarak, uygulamanızı kaydetmek için menü çubuğundan > **Dosya Yı Kaydet'i** **seçin**(veya **Ctrl**+**Shift**+**S**tuşuna basın). Erken ve sık kaydetmek için en iyi uygulama.

     Çalışırken, programınız aşağıdaki resim gibi görünmelidir.

     ![Resim Görüntüleyici](../ide/media/express_pictureviewerdonerun.png)<br>***Resim Görüntüleyici***

## <a name="to-test-your-app"></a>Uygulamanızı test etmek için

1. **F5** tuşunu seçin veya **Hata Ayıklama** araç çubuğunu başlat'ı seçin.

1. Az önce yazdığınız kodu çalıştırmak için **resim göster** düğmesini seçin. İlk olarak, uygulama Dosya **aç** iletişim kutusunu açar. Filtrelerinizin iletişim kutusunun altındaki tür açılır listesindeki **Dosyalar'da** göründüğünü doğrulayın. Ardından bir resme gidin ve açın. Genellikle Belgelerim klasöründe, *Resimlerim\Örnek Resimler* klasöründe, Windows işletim sistemiyle birlikte gönderi yapan örnek resimleri *Belgelerim* klasöründe bulabilirsiniz.

    > [!TIP]
    > **Resim dosyası** seç iletişim kutusunda herhangi bir resim görmüyorsanız, iletişim kutusunun sağ alt tarafındaki açılan listede Tüm **dosyalar (*.\*) filtresinin** seçildiğinden emin olun.

1. Resmi yükleyin ve PictureBox'ınızda görünür. Ardından, kenarlıklarını sürükleyerek formunuzu yeniden boyutlandırmayı deneyin. PictureBox'ınızı, formun içine sabitlenmiş bir TableLayoutPanel'in içine sabitlediği için, resim alanınız kendisini biçim kadar geniş olacak şekilde yeniden boyutlandıracak ve formun en üst yüzde 90'ını doldurur. Bu nedenle <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.FlowLayoutPanel> kapsayıcıları kullandınız: Kullanıcı yeniden boyutlandırıldığında formunuzu doğru boyutta tutarlar.

     Şu anda, daha büyük resimler resim görüntüleyenizin sınırlarının ötesine geçer. Bir sonraki adımda, resimleri pencereye sığdırmak için kod eklersiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[Bkz. Adım 10: Ek düğmeler ve onay kutusu için kod yazın.](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**

- Önceki öğretici adıma dönmek için bkz: [Adım 8: Resim düğmesi olay işleyicisi için kod yazın.](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
