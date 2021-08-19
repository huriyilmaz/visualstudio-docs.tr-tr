---
title: '9. Adım: Kodunuzu gözden geçirme, açıklama ve test etme'
description: Kodunuza nasıl açıklama ekleneceğini ve uygulamanızı test etme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b2f285893e32d1067c67ec8d76fe41c5958f9766
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116922"
---
# <a name="step-9-review-comment-and-test-your-code"></a>9. Adım: Kodunuzu gözden geçirme, açıklama ve test etme

Daha sonra kodunuza bir açıklama eklersiniz. Yorum, uygulamanın davranış biçimini değiştirmeyen bir notdur. Kodunuzu okuyan birisinin ne yaptığını öğrenmesini kolaylaştırır. Kodunuza açıklama eklemek için iyi bir önleminizi alarak vardır.

C# dilinde iki eğik çizgi (//) bir satırı açıklama olarak işaretler. Visual Basic, bir satırı açıklama olarak işaretlemek için tek tırnak işareti (') kullanılır. Bir açıklama ekledikten sonra uygulamanızı test edersiniz. Projeniz üzerinde çalışırken kodunuzu sık çalıştırmak ve test etmek iyi bir uygulamadır. bu sayede, kod daha karmaşık hale gelmeden önce sorunları önceden yakalayabilir ve çözebilirsiniz. Buna *yinelemeli test* denir.

Yalnızca bir şey oluşturmuş olabilirsiniz ve henüz yapılmasa da, bir resmi yükleyebilir. Kodunuza bir açıklama eklemeden ve test etmeden önce, bu kavramları sık kullandığınız için kod kavramlarını gözden geçirmek için zaman alın:

- **Windows Form Tasarımcısı** **resim göster** düğmesine çift tıkladığınızda, ıde programınızın koduna otomatik olarak bir *yöntem* ekledi.

- Yöntemler, kodunuzun nasıl düzenlenme yöntemleridir: kodunuz birlikte gruplandırılır.

- Çoğu zaman, `showButton_Click()` (veya `ShowButton_Click()` ) yönteminizin bir iletişim kutusu gösterdiği ve sonra bir resmi yükleyen gibi belirli bir sırada çok sayıda şey yapmaz.

- Yöntem kod *deyimlerinden* veya kod satırlarından oluşur. Bir yöntemi kod deyimlerini birlikte paketetmenin bir yolu olarak düşünün.

- Bir yöntem yürütüldüğünde veya *çağrıldığında*, yöntem içindeki deyimler sırayla yürütülür ve ilki birinci bir ile başlar.

   Aşağıda bir deyimin örneği verilmiştir.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Deyimler, programlarınızın şeyleri yapabilecekleri şeydir. C# ' de, bir ifade her zaman noktalı virgül ile biter. Visual Basic, satırın sonu deyimin sonu olur. (Visual Basic noktalı virgül gerekmez.) Yukarıdaki ifade, <xref:System.Windows.Forms.PictureBox> Denetiinizde **OpenFileDialog** bileşeni ile kullanıcının seçtiği dosyayı yüklemesini söyler.

## <a name="to-add-comments"></a>Açıklama eklemek için

1. Aşağıdaki yorumu kodunuza ekleyin.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet1":::

    **ShowButton** düğinizin <xref:System.Windows.Forms.Control.Click> olay işleyicisi artık tamamlandı ve çalışıyor. Bir deyimden başlayarak kod yazmaya başladıysanız `if` . Bir `if` ifade, uygulamanıza "Bunu nasıl denetleyeceğinizi, ister doğru olursa, bu eylemleri gerçekleştirirsiniz." Bu durumda, uygulamanıza **Dosya Aç** iletişim kutusunu açmasını söylersiniz ve Kullanıcı bir dosya seçip **Tamam** düğmesini seçerse, bu dosyayı **PictureBox**'a yükleyin.

    > [!TIP]
    > IDE, kod yazmanızı kolaylaştıracak şekilde oluşturulmuştur ve *kod parçacıkları* bunu yapmanın bir yoludur. Kod parçacığı, küçük bir kod bloğuna genişletilmiş bir kısayoldur.
    >
    >  Kullanılabilir tüm parçacıkları görebilirsiniz. Menü çubuğunda **Araçlar**  >  **kod parçacıkları Yöneticisi**' ni seçin. C# için, `if` kod parçacığı **Visual C#** ' de bulunur. Visual Basic için, `if` kod parçacıkları, **kod desenleri**  >  **conditionals ve döngülerinde** bulunur. Bu yöneticiyi, mevcut parçacıkları taramak veya kendi kod parçacıklarınızı eklemek için kullanabilirsiniz.
    >
    >  Kodu yazarken bir kod parçacığını etkinleştirmek için yazın ve **sekme** tuşunu seçin. Birçok parçacık, **IntelliSense** penceresinde görünür. bu **nedenle,** **IntelliSense** PENCERESINDE kod parçacığını seçmek ve sonra IDE 'nin kod parçacığını kullanmasını söylemek için. (IntelliSense parçacığı destekler `if` , ancak `ifelse` kod parçacığını destekler.)

1. Uygulamanızı çalıştırmadan önce, aşağıdaki ekran görüntüsüne benzer şekilde görünmesi gereken **Tümünü Kaydet** araç çubuğu düğmesini seçerek uygulamanızı kaydedin.

     ![Tümünü Kaydet araç çubuğu düğmesi](../ide/media/express_iconsaveall.png)<br>
***Tümünü Kaydet** _ _button *

     Alternatif olarak, uygulamanızı kaydetmek için, **Dosya**  >  **Tümünü** menü çubuğundan Kaydet ' i seçin (veya **CTRL** + **+ Shift** + **S** tuşlarına basın). Bu, erken ve sık tasarrufu sağlamak için en iyi uygulamadır.

     Çalıştığında, programınız aşağıdaki görüntüye benzer şekilde görünmelidir.

     ![Resim görüntüleyici](../ide/media/express_pictureviewerdonerun.png)<br>***Resim görüntüleyici***

## <a name="to-test-your-app"></a>Uygulamanızı test etmek için

1. **F5** tuşunu seçin veya **hata ayıklamayı Başlat** araç çubuğu düğmesini seçin.

1. Yeni yazdığınız kodu çalıştırmak için **bir resim göster** düğmesini seçin. Uygulama ilk olarak bir **Dosya Aç** iletişim kutusu açar. Filtrelerinizin, iletişim kutusunun alt kısmındaki **dosya türü** açılan listesinde göründüğünü doğrulayın. Ardından bir resme gidin ve açın. genellikle *belgelerim klasörünüzdeki Windows* işletim sistemiyle birlikte gelen örnek resimleri, *resimlerim \ örnek resimler* klasörü içinde bulabilirsiniz.

    > [!TIP]
    > **Resim dosyası seç** iletişim kutusunda herhangi bir görüntü görmüyorsanız, iletişim kutusunun sağ alt tarafındaki aşağı açılan listede **tüm dosyalar (*. \* )** filtresinin seçili olduğundan emin olun.

1. Bir resim yükleyin ve PictureBox 'da görünür. Ardından, kenarlıklarını sürükleyerek formunuzu yeniden boyutlandırmayı deneyin. PictureBox 'ın, kendisini formun içine yerleştirilmiş bir TableLayoutPanel içinde yerleştiğinden, resim alanı kendini form kadar geniş olacak şekilde yeniden boyutlandırır ve formun en üstteki %90 ' unu dolduracaktır. Ve kapsayıcılarını şu şekilde kullandığınıza <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.FlowLayoutPanel> göre: Kullanıcı yeniden boyutlandırdığında formunuzu doğru boyutlandırırlar.

     Şimdi, daha büyük resimler resim görüntüleyicinizin kenarlıklarının ötesine geçer. Sonraki adımda, resimlerin pencereye sığması için kod ekleyeceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. **[adım 10: ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**.

- Önceki öğretici adımına dönmek için bkz. [8. Adım: resim göster düğmesi olay işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
