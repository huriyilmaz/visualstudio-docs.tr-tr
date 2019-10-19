---
title: '9\. Adım: kodunuzu gözden geçirme, açıklama ve test etme'
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39be6feffb70dd43823af2af0fce719daafc6f78
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572477"
---
# <a name="step-9-review-comment-and-test-your-code"></a>9\. Adım: kodunuzu gözden geçirme, açıklama ve test etme

Daha sonra kodunuza bir açıklama eklersiniz. Yorum, uygulamanın davranış biçimini değiştirmeyen bir notdur. Kodunuzu okuyan birisinin ne yaptığını öğrenmesini kolaylaştırır. Kodunuza açıklama eklemek için iyi bir önleminizi alarak vardır.

İçinde C#, iki eğik çizgi (//) bir satırı açıklama olarak işaretler. Visual Basic, bir satırı açıklama olarak işaretlemek için tek tırnak işareti (') kullanılır. Bir açıklama ekledikten sonra uygulamanızı test edersiniz. Projeniz üzerinde çalışırken kodunuzu sık çalıştırmak ve test etmek iyi bir uygulamadır. bu sayede, kod daha karmaşık hale gelmeden önce sorunları önceden yakalayabilir ve çözebilirsiniz. Buna *yinelemeli test*denir.

Yalnızca bir şey oluşturmuş olabilirsiniz ve henüz yapılmasa da, bir resmi yükleyebilir. Kodunuza bir açıklama eklemeden ve test etmeden önce, bu kavramları sık kullandığınız için kod kavramlarını gözden geçirmek için zaman alın:

- **Windows form tasarımcısı** **resim göster** DÜĞMESINE çift tıkladığınızda, IDE programınızın koduna otomatik olarak bir *Yöntem* ekledi.

- Yöntemler, kodunuzun nasıl düzenlenme yöntemleridir: kodunuz birlikte gruplandırılır.

- Çoğu zaman, `showButton_Click()` (veya `ShowButton_Click()`) yönteminizin bir iletişim kutusunu nasıl gösterdiği ve sonra bir resmi yükleyen gibi belirli bir sırada çok sayıda şey yapar.

- Yöntem kod *deyimlerinden*veya kod satırlarından oluşur. Bir yöntemi kod deyimlerini birlikte paketetmenin bir yolu olarak düşünün.

- Bir yöntem yürütüldüğünde veya *çağrıldığında*, yöntem içindeki deyimler sırayla yürütülür ve ilki birinci bir ile başlar.

   Aşağıda bir deyimin örneği verilmiştir.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Deyimler, programlarınızın şeyleri yapabilecekleri şeydir. İçinde C#, bir ifade her zaman noktalı virgül ile biter. Visual Basic, satırın sonu deyimin sonu olur. (Visual Basic noktalı virgül gerekmez.) Yukarıdaki ifade, <xref:System.Windows.Forms.PictureBox> denetimine kullanıcının seçtiği dosyayı **OpenFileDialog** bileşeniyle yüklemesini söyler.

## <a name="to-add-comments"></a>Açıklama eklemek için

1. Aşağıdaki yorumu kodunuza ekleyin.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    **ShowButton** düğinizin <xref:System.Windows.Forms.Control.Click> olay işleyicisi artık tamamlanmıştır ve işe yarar. Bir `if` ifadesiyle başlayarak kod yazmaya başladıysanız. @No__t_0 bir ifade, uygulamanıza "Bunu nasıl denetleyeceğinizi, ister doğru olursa, bu eylemleri gerçekleştirirsiniz." Bu durumda, uygulamanıza **Dosya Aç** iletişim kutusunu açmasını söylersiniz ve Kullanıcı bir dosya seçip **Tamam** düğmesini seçerse, bu dosyayı **PictureBox**'a yükleyin.

    > [!TIP]
    > IDE, kod yazmanızı kolaylaştıracak şekilde oluşturulmuştur ve *kod parçacıkları* bunu yapmanın bir yoludur. Kod parçacığı, küçük bir kod bloğuna genişletilmiş bir kısayoldur.
    >
    >  Kullanılabilir tüm parçacıkları görebilirsiniz. Menü çubuğunda **araçlar**  > **kod parçacıkları Yöneticisi**' ni seçin. İçin C#`if` parçacığı **görseldir C#**  . Visual Basic için, `if` parçacıkları  > **conditionals ve Döngülerde** **kod desenlerinde** bulunur. Bu yöneticiyi, mevcut parçacıkları taramak veya kendi kod parçacıklarınızı eklemek için kullanabilirsiniz.
    >
    >  Kodu yazarken bir kod parçacığını etkinleştirmek için yazın ve **sekme** tuşunu seçin. Birçok parçacık, **IntelliSense** penceresinde görünür. bu **nedenle,** **IntelliSense** PENCERESINDE kod parçacığını seçmek ve sonra IDE 'nin kod parçacığını kullanmasını söylemek için. (IntelliSense, `if` parçacığı destekler, ancak `ifelse` parçacığı değil.)

1. Uygulamanızı çalıştırmadan önce, aşağıdaki ekran görüntüsüne benzer şekilde görünmesi gereken **Tümünü Kaydet** araç çubuğu düğmesini seçerek uygulamanızı kaydedin.

     Tüm araç çubuğu düğmesini ![Save ](../ide/media/express_iconsaveall.png)<br>
***Tümünü Kaydet*** *düğmesi*

     Alternatif olarak, uygulamanızı kaydetmek için, **dosya**  > **Tümünü** menü çubuğundan Kaydet ' i seçin (veya **CTRL** +**SHIFT** +**S**' e basın). Bu, erken ve sık tasarrufu sağlamak için en iyi uygulamadır.

     Çalıştığında, programınız aşağıdaki görüntüye benzer şekilde görünmelidir.

     ![Picture Görüntüleyici ](../ide/media/express_pictureviewerdonerun.png)<br>***Resim görüntüleyici***

## <a name="to-test-your-app"></a>Uygulamanızı test etmek için

1. **F5** tuşunu seçin veya **hata ayıklamayı Başlat** araç çubuğu düğmesini seçin.

1. Yeni yazdığınız kodu çalıştırmak için **bir resim göster** düğmesini seçin. Uygulama ilk olarak bir **Dosya Aç** iletişim kutusu açar. Filtrelerinizin, iletişim kutusunun alt kısmındaki **dosya türü** açılan listesinde göründüğünü doğrulayın. Ardından bir resme gidin ve açın. Genellikle *Belgelerim klasörünüzdeki Windows* işletim sistemiyle birlikte gelen örnek resimleri, *Resimlerim \ örnek resimler* klasörü içinde bulabilirsiniz.

    > [!TIP]
    > **Resim dosyası seç** iletişim kutusunda herhangi bir görüntü görmüyorsanız, iletişim kutusunun sağ alt tarafındaki aşağı açılan listede **tüm dosyalar (*. \*)** filtresinin seçili olduğundan emin olun.

1. Bir resim yükleyin ve PictureBox 'da görünür. Ardından, kenarlıklarını sürükleyerek formunuzu yeniden boyutlandırmayı deneyin. PictureBox 'ın, kendisini formun içine yerleştirilmiş bir TableLayoutPanel içinde yerleştiğinden, resim alanı kendini form kadar geniş olacak şekilde yeniden boyutlandırır ve formun en üstteki %90 ' unu dolduracaktır. Bu nedenle <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.FlowLayoutPanel> kapsayıcıları kullandınız: Kullanıcı yeniden boyutlandırdığında formunuzu doğru boyutlandırırlar.

     Şimdi, daha büyük resimler resim görüntüleyicinizin kenarlıklarının ötesine geçer. Sonraki adımda, resimlerin pencereye sığması için kod ekleyeceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. **[adım 10: ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)** .

- Önceki öğretici adımına dönmek için bkz. [8. Adım: resim göster düğmesi olay işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
