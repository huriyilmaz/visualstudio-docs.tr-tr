---
title: Kodlanmış UI Testlerini Düzenleme
description: Test yöntemlerinizi ve UI eylemlerinizi bulmak, görüntülemek ve düzenlemek için Kodlanmış UI Test Düzenleyicisi'ni kullanmayı öğrenin. İlgili denetimleri görüntülemek ve düzenlemek için kullanıcı arabirimi denetim eşlemesi kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 6be42c91936da9a02c735ea8759e6ccba918b4f12f7dc52a3cfdd9036fa793ff
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441485"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi'ni kullanarak kodlanmış UI testlerini düzenleme

Kodlanmış UI Test Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. Kodlanmış UI Test Düzenleyicisi'ni kullanarak test yöntemlerinizin ve UI eylemlerinizin özelliklerini bulup görüntüleyemez ve düzenleyebilirsiniz. Ayrıca, ilgili denetimleri görüntülemek ve düzenlemek için kullanıcı arabirimi denetim haritasını kullanabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="features-of-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi'nin Özellikleri

Kodlanmış UI Test Düzenleyicisi'ni kullanmak, Kod Düzenleyicisi'ni kullanarak kodlanmış UI test yöntemlerinizin kodu düzenlemeye göre daha hızlı ve daha verimlidir. Kodlanmış UI Test Düzenleyicisi ile araç çubuğunu ve kısayol menülerini kullanarak UI eylemleri ve denetimleriyle ilişkili özellik değerlerini hızla bulup değiştirebilirsiniz. Örneğin, aşağıdaki komutları gerçekleştirmek için Kodlanmış UI Test Düzenleyicisi'nin araç çubuğunu kullanabilirsiniz:

![UI Test Düzenleyicisi](../test/media/uitesteditor.png)

1. [Bul,](../ide/finding-and-replacing-text.md) kullanıcı arabirimi eylemlerini ve denetimlerini bulmanıza yardımcı olur.

2. **Silme,** istenmeyen kullanıcı arabirimi eylemlerini kaldırır.

3. **Yeniden** adlandırma, test yöntemleri ve denetimlerinin adlarını değiştirir.

4. **Özellikler,** **seçili öğenin** Özellikler penceresini açar.

5. **Yeni bir yönteme bölmek,** kullanıcı arabirimi eylemlerini modüler hale geliştirmenizi sağlar.

6. **Move Code,** test yöntemlerinize özel kod ekler.

7. **Gecikme EklemeDen** Önce, milisaniye cinsinden belirtilen kullanıcı arabirimi eylemden önce bir duraklama ekler.

8. **KULLANıCı Arabirimi Denetimi'nin,** test altındaki uygulamanın kullanıcı arabiriminde denetimin konumunu belirlemesi.

9. **Tüm'leri** bul, denetim özelliğini ve uygulamanın denetimlerde yapılan önemli değişiklikleri doğrulamanıza yardımcı olur.

Kodlanmış UI testinize bağlı *UIMap.uitest* dosyasını açtığınız zaman, kodlanmış UI testi Kodlanmış **UI Test Düzenleyicisi'nde açılır.** Aşağıdaki yordamlarda, düzenleyicinin araç çubuğunu ve kısayol menülerini kullanarak test yöntemlerinizi ve kullanıcı arabirimi eylemlerine ilişkin özellikleri ve denetimleri nasıl bulup düzenleyebilirsiniz?

## <a name="open-a-coded-ui-test"></a>Kodlanmış ui testini açma

Kodlanmış UI Test Düzenleyicisi'ni kullanarak Visual C# Visual Basic kodlanmış UI testini **görüntüleyemez ve düzenleyebilirsiniz.**

![Bağlam menüsü Kodlanmış UI Test Oluşturucusu ile Düzenle](../test/media/editcodeduitest.png)

Bu **Çözüm Gezgini** *UIMap.uitest* kısayol menüsünü açın ve Aç'ı **seçin.** Kodlanmış UI testi, Kodlanmış UI **Test Düzenleyicisi'nde görüntülenir.** Artık kodlanmış UI testinde kayıtlı yöntemleri, eylemleri ve karşılık gelen denetimleri görüntüleyemez ve düzenleyebilirsiniz.

> [!TIP]
> UI Eylemleri bölmesindeki bir yöntemde bulunan kullanıcı arabirimi **eylemlerini** seçerek ilgili denetim vurgulanır. Kullanıcı arabirimi eylemlerini veya denetim özelliklerini de değiştirebilirsiniz.

## <a name="modify-ui-action-and-control-properties"></a>UI eylem ve denetim özelliklerini değiştirme

Kodlanmış UI Test Düzenleyicisi'ni kullanarak test yöntemlerinizin tüm UI eylemlerini hızla bulup görüntüebilirsiniz. Düzenleyicide kullanıcı arabirimi eylemlerini seçerek ilgili denetim otomatik olarak vurgulanır. Benzer şekilde, bir denetim seçersiniz, ilişkili kullanıcı arabirimi eylemleri vurgulanır. Kullanıcı arabirimi eylemlerini veya denetimlerini seçerek Özellikler penceresini  kullanarak buna karşılık gelen özellikleri kolayca değiştirebilirsiniz.

![UI eylem özellikleri](../test/media/codeduiedituiaction.png)

Bir UI eyleminin özelliklerini değiştirmek için, **UI** Eylemi bölmesinde, özelliklerini düzenlemek istediğiniz ui eylemini içeren test yöntemini genişletin, kullanıcı arabirimi eylemini seçin ve ardından kullanıcı arabirimini kullanarak Özellikler penceresi.

Örneğin, bir sunucu kullanılamıyorsa ve web tarayıcınızla ilişkilendirilmiş **http: \/ /Contoso1/default.aspx Web** sayfasına git adlı bir kullanıcı arabirimi eyleminiz varsa URL'yi olarak değiştirebilirsiniz. `http://Contoso2/default.aspx`

![Denetim özellikleri](../test/media/codeduitestcontrolprop.png)

Bir denetimin özelliklerini değiştirmek ui eylemleriyle aynı şekilde yapılır. Kullanıcı **Arabirimi Denetim Eşlemesi** bölmesinde, Özellikler penceresini kullanarak özelliklerini düzenlemek ve değiştirmek istediğiniz **denetimi** seçin.

Örneğin bir geliştirici, "idSubmit" olan test edilen uygulamanın kaynak kodundaki bir düğme denetiminde **(ID)** özelliğini "idLogin" olarak değiştirmiş olabilir. Uygulamada **(ID)** özelliği değiştirıldığında, kodlanmış UI testi düğme denetimi bulamaz ve başarısız olur. Bu durumda, test sahibi Arama  Özellikleri koleksiyonunu açabilir ve **Id** özelliğini geliştiricinin uygulamada kullandığı yeni değerle eşleyecek şekilde değiştirebilir. Test etmek için "Submit" olan **Kolay Ad** özellik değerini de "Login" olarak değiştirebilir. Bu değişikliği yaparak, Kodlanmış UI Test Düzenleyicisi'nde ilişkili kullanıcı arabirimi eylemi "'Gönder' düğmesini seç" seçeneğinden "Oturum Aç' düğmesini seç" olarak güncelleştirilir.

Değişikliklerinizi tamamladıktan sonra, kullanıcı arabirimi araç çubuğunda Kaydet'i seçerek *DEĞIŞIKLIKLERI UIMap.Designer* Visual Studio kaydedin. 

### <a name="tips"></a>İpuçları

- Özellikler penceresi **görüntülenmezse,** Enter tuşuna basırken **Alt** tuşuna basın ve **basılı** tutun veya **F4 tuşuna basın.**

- Yaptığınız özellik değişikliklerini geri almak için Düzenle **menüsünden Geri Al'ı** **seçin** veya **Ctrl** + **Z tuşlarına basın.**

- Kodlanmış UI **Testi düzenleyicisi** araç çubuğundaki Bul düğmesini  kullanarak Bul ve Değiştir aracını Visual Studio. Daha sonra **Kodlanmış** UI Testi düzenleyicisinde ui eylemini bulmak için Bul denetimi kullanabilirsiniz. Örneğin, "'Oturum Aç' düğmesine tıklayın"ı bulmaya çalışabilirsiniz. Bu, büyük testlerde yararlı olabilir. Kodlanmış UI Test Düzenleyicisi'nde **Bul ve Değiştir aracında** değiştirme işlevini kullanılamaz. Daha fazla bilgi için Bkz. Metin bulma [ve değiştirme içinde denetimi bulma.](../ide/finding-and-replacing-text.md)

- Bazen denetimlerin test altındaki uygulama kullanıcı arabiriminde bulunduğu yeri görselleştirmek zor olabilir. Kodlanmış UI Test Düzenleyicisi'nin özelliklerinden biri, kullanıcı arabirimi denetim haritasında listelenen bir denetimi seçerek uygulamanın test altındaki konumunu görüntüleyabilmektir. Daha fazla bilgi için bu [makalenin altında yer alan test altındaki uygulamada](#locate-a-ui-control-in-the-application-under-test) kullanıcı arabirimi denetimi bulma makalesine bakın.

- Düzenlemek istediğiniz denetimi içeren kapsayıcı denetimi genişletmek gerekebilir. Daha fazla bilgi için bu [makalenin daha altında yer alan](#locate-a-control-and-its-descendants) Denetimi ve alt altlarını bulma makalesine bakın.

## <a name="delete-unwanted-ui-actions"></a>İstenmeyen kullanıcı arabirimi eylemlerini silme

Kodlanmış UI testinde istenmeyen UI eylemlerini kolayca kaldırabilirsiniz.

![Kullanıcı arabirimini silme eylemi](../test/media/codeduideleteuiaction.png)

UI **Eylemi bölmesinde,** silmek istediğiniz kullanıcı arabirimi eylemini içeren test yöntemini genişletin. Kullanıcı arabirimi eyleminin kısayol menüsünü açın ve Sil'i **seçin.**

## <a name="split-a-test-method-into-two-separate-methods"></a>Test yöntemini iki ayrı yönteme bölme

Ui eylemlerini iyileştirmek veya modüler hale etmek için bir test yöntemini bölebilirsiniz. Örneğin, testinde iki kapsayıcı denetiminde kullanıcı arabirimi eylemlerine sahip tek bir test yöntemi olabilir. UI eylemleri, bir kapsayıcıya karşılık gelen iki yöntemde daha iyi modüler hale getirildi.

![Test yöntemini bölme](../test/media/codeduitestsplitmethod1.png)

![İki test yöntemi](../test/media/codeduitestsplitmethod2.png)

UI **Eylemi bölmesinde,** iki ayrı yönteme bölmek istediğiniz test yöntemini genişletin ve yeni test yönteminin başlamalarını istediğiniz kullanıcı arabirimi eylemini seçin. Kullanıcı arabirimi eyleminin kısayol menüsünü açın ve ardından Yeni yönteme  bölün'ü seçin veya Kodlanmış UI Test Düzenleyicisi araç çubuğunda Yeni yönteme bölün düğmesini seçin. Yeni test yöntemi KULLANıCı Arabirimi Eylemleri **bölmesinde** görünür. Bölmeyi belirttiğiniz eylemden başlayan kullanıcı arabirimi eylemlerini içerir.

Yöntemi bölmeyi bitirdikten sonra, kullanıcı arabirimi araç çubuğunda Kaydet'i seçerek *UIMap.Designer* **dosyasına** Visual Studio kaydedin.

> [!WARNING]
> Bir yöntemi bölersiniz, mevcut yöntemi çağıran herhangi bir kodu değiştirerek bu ui eylemlerini yine de dahil etmek istediğiniz yeni yöntemi de çağırabilirsiniz. Bir yöntemi bölüştüşt Microsoft Visual Studio iletişim kutusu görüntülenir. Oluşturmakta olduğunu yeni yöntemi de çağıran mevcut yöntemi çağıran herhangi bir kodu değiştirmeniz gerektiğini sizi uyarıyor. **Evet'i seçin.**

### <a name="tips"></a>İpuçları

- Bölme işlemini geri almak için Düzenle **menüsünden** Geri **Al'ı** seçin veya **Ctrl** + **Z tuşlarına basın.**

- Yeni yöntemi yeniden adlandırebilirsiniz. Kullanıcı Arabirimi Eylemleri **bölmesinde bunu seçin** ve Kodlanmış UI Test Düzenleyicisi araç çubuğunda Yeniden Adlandır düğmesini seçin. 

   -veya-

   Yeni test yönteminin kısayol menüsünü açın ve Yeniden Adlandır'ı **seçin.**

   Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemine başvurulan herhangi bir kodu değiştirmeniz gerektiğini belirtir. **Evet'i seçin.**

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Özelleştirmeyi kolaylaştırmak için test yöntemini UIMap dosyasına taşıma

Kodlanmış UI testinde test yöntemlerinden birinin özel kod gerektirdiğini belirlerse, bunu *UIMap.cs* veya *UIMap.vb* dosyasına taşımanız gerekir. Aksi takdirde, kodlanmış UI testi her yeniden derlemede kodunuz üzerine yazılır. Yöntemi taşısanız, test her yeniden derlemede özel kodunuzun üzerine yazılır.

Ui **Eylemi** bölmesinde, test kodu yeniden derlemesi olduğunda üzerine yazılmayan özel kod işlevselliğini kolaylaştırmak için *UIMap.cs* veya *UIMap.vb* dosyasına taşımak istediğiniz test yöntemini seçin. Ardından, **Kodlanmış UI** Test Düzenleyicisi araç çubuğunda Kodu Taşı düğmesini seçin veya test yönteminin kısayol menüsünü açıp Kodu **Taşı'yı seçin.** Test yöntemi *UIMap.uitest dosyasından* kaldırılır ve artık UI Eylemleri **bölmesinde görüntülenmez.** Taşındığınız test dosyasını düzenlemek için, dosyasından *UIMap.cs* veya *UIMap.vb* **dosyasını Çözüm Gezgini.**

Yöntemi taşımayı bitirdikten sonra, araç çubuğunda Kaydet'i seçerek *UIMap.Designer* **dosyasına** Visual Studio kaydedin.

> [!WARNING]
> Bir yöntemi taşıdıktan sonra, artık Kodlanmış UI Test Düzenleyicisi'ni kullanarak düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız. Bir yöntemi taşıyıcıda, Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemin *UIMap.uitest* dosyasından *UIMap.cs* veya *UIMap.vb* dosyasına taşınacağını ve artık Kodlanmış UI Test Düzenleyicisi'ni kullanarak yöntemi düzenleyemezsiniz konusunda sizi uyarır. **Evet'i seçin.**

### <a name="tips"></a>İpuçları

Taşıma işlemini geri almak için Düzenle **menüsünden** Geri **Al'ı** seçin veya **Ctrl** + **Z tuşlarına basın.** Ancak daha sonra kodu *UIMap.cs* veya *UIMap.vb* dosyasından el ile kaldırmanız gerekir.

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Test altındaki uygulamada kullanıcı arabirimi denetimi bulma

Bazen denetimlerin test altındaki uygulama kullanıcı arabiriminde bulunduğu yeri görselleştirmek zor olabilir. Kodlanmış UI Test Düzenleyicisi'nin özelliklerinden biri, kullanıcı arabirimi denetim haritasında listelenen bir denetimi seçerek uygulamanın test altındaki konumunu görüntüleyabilmektir. Test **kapsamındaki uygulamada Kullanıcı** Arabirimi Denetimi Bul özelliğini kullanmak, denetimde yapılan arama özelliği değişikliklerini doğrulamak için de kullanılabilir.

![UI denetimi bulma](../test/media/codeduilocatecontrol.png)

![Uygulamada test altında bulunan denetim](../test/media/codeduilocatecontrol2.png)

Kullanıcı **Arabirimi Denetim Eşlemesi** bölmesinde, testle ilişkili uygulamada bulmak istediğiniz denetimi seçin. Ardından denetimin kısayol menüsünü açın ve Ui Denetimi **bul'u seçin.** Test edilen uygulamada denetim mavi kenarlıkla belirlenmiştir.

> [!NOTE]
> Kullanıcı arabirimi denetimi bulmadan önce testle ilişkili uygulamanın çalıştığını doğrulayın.

### <a name="tips"></a>İpuçları

Bir kapsayıcı altındaki **tüm denetimlerin** doğru şekilde buluna olduğunu doğrulamak için Hepsini Bul seçeneğini kullanabilirsiniz. Bu seçenek sonraki bölümde açıklanmıştır.

## <a name="locate-a-control-and-its-descendants"></a>Denetimi ve altlarını bulma

Kapsayıcı altındaki tüm denetimlerin test altındaki uygulama kullanıcı arabiriminde doğru şekilde yer alanın. Bu, kapsayıcıda yapmış olabilir arama özelliği değişikliklerini doğrulamaya yardımcı olabilir. Ayrıca, test kapsamındaki uygulamanın kullanıcı arabiriminde önemli değişiklikler olduysa, mevcut denetim arama özelliklerinin hala doğru olduğunu doğruabilirsiniz.

![Tüm alt denetimleri bulma](../test/media/codeduilocateall.png)

![Bulunan tüm denetimler](../test/media/codeduilocateall2.png)

UI **Denetim Eşlemesi** bölmesinde, bulmak ve tüm alt öğeleri görüntülemek istediğiniz kapsayıcı denetimi seçin. Ardından denetimin kısayol menüsünü açın ve Tüm Öğeleri **Bul'a tıklayın.** Kapsayıcı denetimi ve tüm alt denetimleri, Kodlanmış UI Test Düzenleyicisi'nde yeşil onay işareti veya kırmızı 'X' ile işaretlenir. Bu işaretler, denetimlerin test kapsamındaki uygulamada başarıyla bulunuyor olup olamay olduğunu size gösterir.

> [!NOTE]
> Kullanıcı arabirimi denetimlerini bulmadan önce testle ilişkili uygulamanın çalıştığını doğrulayın.

## <a name="insert-a-delay-before-a-ui-action"></a>Ui eylemden önce gecikme ekleme

Bazen testin gerçekleşmesi için bir pencere, ilerleme çubuğunun kaybolması gibi belirli olayların gerçekleşmesini beklemesini sebilirsiniz. Kodlanmış UI Test Düzenleyicisi'ni kullanarak, bunu ui eylemini önce bir gecikme olarak ekerek gerçekleştirebilirsiniz. Gecikmenin kaç saniye olacağını belirterek.

![Kullanıcı arabirimi eylemden önce gecikme ekleme](../test/media/codeduidelay.png)

![5 saniyelik gecikme eklendi](../test/media/codeduidealy2.png)

UI **Eylemi bölmesinde,** daha önce gecikme eklemek istediğiniz UI eylemini içeren test yöntemini genişletin. Kullanıcı arabirimi eylemlerini seçin. Ardından kullanıcı arabirimi eyleminin kısayol menüsünü açın ve Öncesinde Gecikme **Ekle'yi seçin.** Seçilen kullanıcı arabirimi eylemden önce şu metinle bir gecikme eklenir ve vurgulanır: Eylemler arasında kullanıcı gecikmesi için **1 saniye bekleyin.** Özellikler **penceresinde** Delay özelliğinin **değerini** istenen milisaniye sayısıyla değiştirin.

Gecikmeyi ekledikten sonra, kullanıcı arabirimi araç çubuğunda Kaydet'i seçerek *UIMap.Designer* **dosyasına** Visual Studio kaydedin.

Ui eylemden önce belirli bir denetimin kullanılabilir olduğundan emin olmak için uygun UITestControl.WaitForControlXXX() yöntemini kullanarak test yönteminize özel kod eklemeyi göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. Kayıttan yürütme sırasında kodlanmış UI testlerinin belirli olayları beklemesi.](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Veri odaklı kodlanmış UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md)
- [Adım adım kılavuz: Kodlanmış ui testi oluşturma, düzenleme ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
