---
title: '9. Adım: Kodunuzu gözden geçirme, açıklama ve test etme'
description: Kodunuza açıklama ekleme ve uygulamayı test etmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
dev_langs:
- CSharp
- VB
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 70db7188d16d3a878ecec50f734946cdb93d8f3c
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397357"
---
# <a name="step-9-review-comment-and-test-your-code"></a>9. Adım: Kodunuzu gözden geçirme, açıklama ve test etme

Daha sonra kodunuz için bir açıklama eksersiniz. Açıklama, uygulamanın davranışlarını değiştirmeyen bir nottur. Bu, kodunuzu okuyan birinin ne yaptığını an yazması için daha kolay hale getirir. Kodunuza açıklama eklemek iyi bir alışkanlıktır.

C# içinde, iki eğik çizgi (//) bir satırı açıklama olarak işaret ediyor. Bu Visual Basic, bir satırı açıklama olarak işaretlemek için tek bir tırnak işareti (') kullanılır. Bir açıklama ekledikten sonra, uygulamanızı test etmek için. Projeleriniz üzerinde çalışırken kodunuzu sık sık çalıştırmak ve test etmek iyi bir uygulamadır. Böylece kod daha karmaşık hale gelmeden önce sorunları erkenden yakalayabilir ve düzeltebilirsiniz. Buna, *test etme adı verilen bir testtir.*

Yalnızca işe yarar bir şey inşa ettiniz ve henüz yapılmamış olsa da bir resim yükleyemediniz. Kodunuzla yorum eklemeden ve testmeden önce, kod kavramlarını gözden geçirmek için zaman geçirin çünkü bu kavramları sık sık kullanıcaz:

- Form Tasarımcısı'nda Resim  göster düğmesine **çift Windows** IDE, program kodunuz  için otomatik olarak bir yöntem ekledi.

- Yöntemler kodunuzu düzenleme yöntemidir: Kodunuzun birlikte nasıl gruplandıklarıdır.

- Çoğu zaman yöntem, (veya ) yönteminizin iletişim kutusunu nasıl gösterip resim yüklemesi gibi belirli bir sırada az sayıda `showButton_Click()` `ShowButton_Click()` şey yapar.

- Yöntem, kod deyimlerini *veya kod* satırlarını içerir. Bir yöntemi, kod deyimlerini birlikte paketlenin bir yolu olarak düşünebilirsiniz.

- Bir yöntem yürütülürken veya çağrıldıktan sonra, yönteminde deyimleri sırayla, sırayla yürütülür ve ilki ile başlayarak.

   Aşağıda bir deyimi örneği ve ardından ve bir örnek ve ardından ve bir deyimi ve daha sonra yer alan bir deyim ve daha fazla bilgi ve daha fazla bilgi

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Deyimler, programlarınızı bir şeyler yapmaya zorlar. C# içinde deyimi her zaman noktalı virgülle biter. Bu Visual Basic, bir satırın sonu bir deyimin sonu. (Visual Basic.) Yukarıdaki deyim, <xref:System.Windows.Forms.PictureBox> denetiminize kullanıcının **OpenFileDialog** bileşeniyle birlikte seçmiş olduğu dosyayı yüklemelerini söyler.

## <a name="to-add-comments"></a>Açıklama eklemek için

1. Kodunuz için aşağıdaki açıklamayı ekleyin.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet1":::

    **showButton düğmenizin** olay <xref:System.Windows.Forms.Control.Click> işleyicisi artık tamamlandı ve çalışıyor. Deyimiyle başlayarak kod yazmaya `if` başladın. Deyimi, uygulamanıza "Bunu kontrol edin ve doğruysa bu eylemleri `if` gerçekleştirin" şeklinde ifade etmektir. Bu durumda, uygulamanıza Dosya Aç  iletişim kutusunu açmalarını söylersiniz ve kullanıcı bir  dosya seçer ve Tamam düğmesini seçerse bu dosyayı **PictureBox'a yükleyebilirsiniz.**

    > [!TIP]
    > IDE, kod yazmayı kolaylaştıracak şekilde hazır hale geldi ve kod parçacıkları *bunu* yapma yollarından biri. Kod parçacığı, küçük bir kod bloğuna genişletilen bir kısayoldur.
    >
    >  Kullanılabilir tüm kod parçacıklarını görebilir. Menü çubuğunda Araçlar Kod Parçacıkları  >  **Yöneticisi'ni seçin.** C# için kod `if` parçacığı **Visual C# içindedir.** Daha Visual Basic kod parçacıkları Kod Desenleri Koşullu `if` **Ve**  >  **Döngüler içindedir.** Mevcut kod parçacıklarına göz atmak veya kendi kod parçacıklarınızı eklemek için bu yöneticiyi kullanabilirsiniz.
    >
    >  Kod yazarken kod parçacığını etkinleştirmek için yazın ve Sekme **tuşuna** basın. **IntelliSense** penceresinde birçok kod parçacığı görünür. Bu  nedenle Sekme tuşuna iki kez basın: önce **IntelliSense** penceresinden kod parçacığını seçmek ve ardından IDE'ye kod parçacığını kullanmalarını söylemek. (IntelliSense kod `if` parçacığını destekler, ancak kod parçacığını `ifelse` desteklemez.)

1. Uygulamayı çalıştırmadan önce, aşağıdaki ekran  görüntüsüne benzer şekilde olması gereken Tüm Araç Çubuğunu Kaydet düğmesini seçerek uygulamalarınızı kaydedin.

     ![Tüm araç çubuğunu kaydet düğmesi](../ide/media/express_iconsaveall.png)<br>
***Hepsini Kaydet** _ _button*

     Alternatif olarak, uygulamanızı kaydetmek için menü **çubuğundan Dosya**  >  **Tamamını Kaydet'i** seçin (veya **Ctrl Shift** S + **tuşlarına** + **basın).** Erken ve sık tasarruf etmek en iyi yöntemdir.

     Çalışma zaman, programınız aşağıdaki görüntü gibi görüntüye benzin.

     ![Resim Görüntüleyici](../ide/media/express_pictureviewerdonerun.png)<br>***Resim Görüntüleyici***

## <a name="to-test-your-app"></a>Uygulamanızı test etmek için

1. **F5 tuşuna** basın veya Hata **Ayıklamayı Başlat araç çubuğu** düğmesini seçin.

1. Az önce **yazdığını kodu** çalıştırmak için Resim göster düğmesini seçin. İlk olarak, uygulama bir Dosya **Aç iletişim** kutusu açar. İletişim kutusunun alt kısmında yer **alan Türe ait** dosyalar açılan listesinde filtrenizin görüntü olduğunu doğrulayın. Ardından bir resme gidin ve açın. Genellikle Belgelerim klasörünüzdeki Windows ile birlikte gönderilen  örnek resimleri Resimlerim\Örnek Resimler *klasörünün içinde* bulabilirsiniz.

    > [!TIP]
    > Resim dosyası seçin iletişim kutusunda  görüntü görmüyorsanız, iletişim kutusunun sağ alt tarafındaki açılan listede Tüm dosyalar **(*. \* ) filtresinin** seçili olduğundan emin olun.

1. Bir resim yüklensin ve resim PictureBox' ta görünür. Ardından kenarlıklarını sürükleyerek formlarınızı yeniden boyutlandırmayı deneyin. PictureBox'ını formun içine yerleştirmiş bir TableLayoutPanel içine yerleştirmiş olduğunuz için resim alanınız form kadar geniş olacak şekilde yeniden boyutlandırılır ve formun ilk yüzde 90'ını doldurur. ve kapsayıcılarını bu nedenle kullandınız: Kullanıcı yeniden boyutlandırılırken <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.FlowLayoutPanel> formuz doğru boyutlandırılır.

     Şu anda büyük resimler resim görüntüleyicinizin kenarlıklarının ötesine geçmaktadır. Sonraki adımda, resimlerin pencereye sığmalarını için kod eksersiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 10. Adım: Ek](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)** düğmeler için kod yazma ve onay kutusu.

- Önceki öğretici adımına dönmek için [bkz. 8. Adım: Resim göster düğmesi olay işleyicisi için kod yazma.](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
