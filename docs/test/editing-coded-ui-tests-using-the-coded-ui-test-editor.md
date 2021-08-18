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

Kodlanmış UI Test Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. Kodlanmış UI Test Düzenleyicisi'ni kullanarak test yöntemlerinizin ve UI eylemlerinizin özelliklerini bulup görüntüleyemez ve düzenleyebilirsiniz. Buna ek olarak, ilgili denetimleri görüntülemek ve düzenlemek için kullanıcı arabirimi denetim haritasını kullanabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="features-of-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi'nin Özellikleri

Kodlanmış UI Test Düzenleyicisi'ni kullanmak, Kod Düzenleyicisi'ni kullanarak kodlanmış UI test yöntemlerinizin kodu düzenlemeye göre daha hızlı ve daha verimlidir. Kodlanmış UI Test Düzenleyicisi ile, kullanıcı arabirimi eylemleri ve denetimleriyle ilişkili özellik değerlerini hızla bulmak ve değiştirmek için araç çubuğunu ve kısayol menülerini kullanabilirsiniz. Örneğin, aşağıdaki komutları gerçekleştirmek için Kodlanmış UI Test Düzenleyicisi'nin araç çubuğunu kullanabilirsiniz:

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

Örneğin geliştirici, "idSubmit" olan test edilen uygulamanın kaynak kodundaki bir düğme denetiminde **(ID)** özelliğini "idLogin" olarak değiştirmiş olabilir. Uygulamada **(ID)** özelliği değiştirıldığında, kodlanmış UI testi düğme denetimi bulamaz ve başarısız olur. Bu durumda, test sahibi Arama  Özellikleri koleksiyonunu açabilir ve **Id** özelliğini geliştiricinin uygulamada kullandığı yeni değerle eşleyecek şekilde değiştirebilir. Test etmek için "Submit" olan **Kolay Ad** özellik değerini de "Login" olarak değiştirebilir. Bu değişiklik yapıldığında, Kodlanmış UI Test Düzenleyicisi'nde ilişkili kullanıcı arabirimi eylemi "'Gönder' düğmesini seç" seçeneğinden "Oturum Aç' düğmesini seç" olarak güncelleştirilir.

Değişikliklerinizi tamamladıktan sonra, kullanıcı arabirimi araç çubuğunda Kaydet'i seçerek *DEĞIŞIKLIKLERI UIMap.Designer* Visual Studio kaydedin. 

### <a name="tips"></a>İpuçları

- Özellikler penceresi **görüntülenmezse,** Enter tuşuna basırken **Alt** tuşuna basın ve **basılı** tutun veya **F4 tuşuna basın.**

- Yaptığınız özellik değişikliklerini geri almak için Düzenle **menüsünden Geri Al'ı** **seçin** veya **Ctrl** + **Z tuşlarına basın.**

- Kodlanmış UI **Testi düzenleyicisi** araç çubuğundaki Bul düğmesini  kullanarak Bul ve Değiştir aracını Visual Studio. Daha sonra **Kodlanmış** UI Testi düzenleyicisinde bir UI eylemini bulmak için Bul denetimi kullanabilirsiniz. Örneğin, "'Oturum Aç' düğmesine tıklayın"ı bulmaya çalışabilirsiniz. Bu, büyük testlerde yararlı olabilir. Kodlanmış UI Test Düzenleyicisi'nde **Bul ve Değiştir aracında** değiştirme işlevini kullanılamaz. Daha fazla bilgi için Bkz. Metin bulma [ve değiştirme içinde denetimi bulma.](../ide/finding-and-replacing-text.md)

- Bazen denetimlerin test altındaki uygulama kullanıcı arabiriminde bulunduğu yeri görselleştirmek zor olabilir. Kodlanmış UI Test Düzenleyicisi'nin özelliklerinden biri, kullanıcı arabirimi denetim haritasında listelenen bir denetimi seçerek uygulamanın test altındaki konumunu görüntüleyabilmektir. Daha fazla bilgi için bu [makalenin daha altında yer alan test altındaki uygulamada](#locate-a-ui-control-in-the-application-under-test) kullanıcı arabirimi denetimi bulma makalesine bakın.

- Düzenlemek istediğiniz denetimi içeren kapsayıcı denetimi genişletmek gerekebilir. Daha fazla bilgi için bu [makalenin daha altında yer alan](#locate-a-control-and-its-descendants) Denetimi ve alt altlarını bulma makalesine bakın.

## <a name="delete-unwanted-ui-actions"></a>İstenmeyen kullanıcı arabirimi eylemlerini silme

Kodlanmış UI testinde istenmeyen UI eylemlerini kolayca kaldırabilirsiniz.

![Kullanıcı arabirimini silme eylemi](../test/media/codeduideleteuiaction.png)

UI **Eylemi bölmesinde,** silmek istediğiniz ui eylemini içeren test yöntemini genişletin. Kullanıcı arabirimi eyleminin kısayol menüsünü açın ve Sil'i **seçin.**

## <a name="split-a-test-method-into-two-separate-methods"></a>Test yöntemini iki ayrı yönteme bölme

Ui eylemlerini iyileştirmek veya modüler hale etmek için bir test yöntemini bölebilirsiniz. Örneğin, testinde iki kapsayıcı denetiminde kullanıcı arabirimi eylemleri olan tek bir test yöntemi olabilir. UI eylemleri, bir kapsayıcıya karşılık gelen iki yöntemde daha iyi modüler hale getirildi.

![Test yöntemini bölme](../test/media/codeduitestsplitmethod1.png)

![İki test yöntemi](../test/media/codeduitestsplitmethod2.png)

UI **Eylemi bölmesinde,** iki ayrı yönteme bölmek istediğiniz test yöntemini genişletin ve yeni test yönteminin başlamalarını istediğiniz kullanıcı arabirimi eylemini seçin. Kullanıcı arabirimi eyleminin kısayol menüsünü açın ve ardından Yeni yönteme  bölün'ü seçin veya Kodlanmış UI Test Düzenleyicisi araç çubuğunda Yeni yönteme bölün düğmesini seçin. Yeni test yöntemi KULLANıCı Arabirimi Eylemleri **bölmesinde** görünür. Bölmeyi belirttiğiniz eylemden başlayarak kullanıcı arabirimi eylemlerini içerir.

Yöntemi bölmeyi bitirdikten sonra, kullanıcı arabirimi araç çubuğunda Kaydet'i seçerek *UIMap.Designer* **dosyasına** Visual Studio kaydedin.

> [!WARNING]
> Bir yöntemi bölersiniz, mevcut yöntemi çağıran herhangi bir kodu değiştirerek bu ui eylemlerini yine de dahil etmek istediğiniz yeni yöntemi de çağırabilirsiniz. Bir yöntemi bölüşt Microsoft Visual Studio iletişim kutusu görüntülenir. Oluşturmakta olduğunu yeni yöntemi de çağıran mevcut yöntemi çağıran herhangi bir kodu değiştirmeniz gerektiğini sizi uyarıyor. **Evet'i seçin.**

### <a name="tips"></a>İpuçları

- Bölme işlemini geri almak için Düzenle **menüsünden** Geri **Al'ı** seçin veya **Ctrl** + **Z tuşlarına basın.**

- Yeni yöntemi yeniden adlandırebilirsiniz. Kullanıcı Arabirimi Eylemleri **bölmesinde bunu seçin** ve Kodlanmış UI Test Düzenleyicisi araç çubuğunda Yeniden Adlandır düğmesini seçin. 

   -veya-

   Yeni test yönteminin kısayol menüsünü açın ve Yeniden Adlandır'ı **seçin.**

   Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemine başvurulan herhangi bir kodu değiştirmeniz gerektiğini belirtir. **Evet'i seçin.**

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Özelleştirmeyi kolaylaştırmak için test yöntemini UIMap dosyasına taşıma

Kodlanmış UI testinde test yöntemlerinden birinin özel kod gerektirdiğini belirlerse, bunu *UIMap.cs* veya *UIMap.vb* dosyasına taşımanız gerekir. Aksi takdirde, kodlanmış UI testi her yeniden derlemede kodunuz üzerine yazılır. Yöntemi taşısanız, test her yeniden derlemede özel kodunuzun üzerine yazılır.

Ui **Eylemi** bölmesinde, test kodu yeniden derlemesi olduğunda üzerine yazılmayan özel kod işlevselliğini kolaylaştırmak için *UIMap.cs* veya *UIMap.vb* dosyasına taşımak istediğiniz test yöntemini seçin. Ardından, **Kodlanmış UI** Test Düzenleyicisi araç çubuğunda Kodu Taşı düğmesini seçin veya test yönteminin kısayol menüsünü açıp Kodu **Taşı'yı seçin.** Test yöntemi *UIMap. UITest* dosyasından kaldırılır ve artık **UI eylemleri** bölmesinde görüntülenmez. Taşıdığınız test dosyasını düzenlemek için, **Çözüm Gezgini**' den *UIMap. cs* veya *UIMap. vb* dosyasını açın.

yöntemi taşımayı tamamladıktan sonra, Visual Studio araç çubuğunda **kaydet** ' i seçerek *uımap. Designer* dosyasındaki değişiklikleri kaydedin.

> [!WARNING]
> Bir yöntemi taşındıktan sonra, kodlanmış UI test düzenleyicisini kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız. bir yöntemi taşıdığınızda bir Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemin *umap. UITest* dosyasından *UIMap. cs* veya *UIMap. vb* dosyasına taşınacağını ve artık kodlanmış UI test düzenleyicisini kullanarak yöntemi düzenleyemeyeceksiniz. **Evet**' i seçin.

### <a name="tips"></a>İpuçları

Taşımayı geri almak için, **Düzenle** menüsünden **geri al** ' ı seçin veya **CTRL** + **Z** tuşuna basın. Ancak, kodu *UIMap. cs* veya *umap. vb* dosyasından el ile kaldırmanız gerekir.

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Test edilen uygulamada bir UI denetimini bulma

Bazen denetimlerin test edilen uygulamanın kullanıcı arabiriminde nerede olduğunu görselleştirmek zor olabilir. Kodlanmış UI testi düzenleyicisinin özelliklerinden biri, UI denetim haritasında listelenen bir denetimi seçebileceğiniz ve test edilen uygulamada konumunu görüntüleyebilin. Test edilen uygulamada **UI denetimini bul** özelliğinin kullanılması, bir denetimde yaptığınız arama özelliği değişikliklerini doğrulamak için de kullanılabilir.

![UI denetimini bul](../test/media/codeduilocatecontrol.png)

![Test edilen uygulamada bulunan denetim](../test/media/codeduilocatecontrol2.png)

**UI denetim eşlemesi** bölmesinde, test ile ilişkili uygulamada bulmak istediğiniz denetimi seçin. Sonra, denetimin kısayol menüsünü açın ve ardından **UI denetimini bul**' u seçin. Test edilmekte olan uygulamada, denetim mavi bir kenarlıkla atanır.

> [!NOTE]
> Bir UI denetimini bulmadan önce, test ile ilişkili uygulamanın çalıştığını doğrulayın.

### <a name="tips"></a>İpuçları

Bir kapsayıcı altındaki tüm denetimlerin doğru bir şekilde konumlandırılabilir olduğunu doğrulamak için **Tümünü Bul** seçeneğini kullanabilirsiniz. Bu seçenek, sonraki bölümde açıklanmaktadır.

## <a name="locate-a-control-and-its-descendants"></a>Bir denetimi ve alt öğelerini bulma

Bir kapsayıcı altındaki tüm denetimlerin test edilen uygulamanın kullanıcı arabiriminde doğru şekilde konumlandırılabilecek olduğunu doğrulayabilirsiniz. Bu, kapsayıcıda yapmış olduğunuz arama özelliği değişikliklerinin doğrulanması için yararlı olabilir. Ayrıca, test edilen uygulamanın kullanıcı arabiriminde önemli değişiklikler varsa, var olan denetim arama özelliklerinin hala doğru olduğunu doğrulayabilirsiniz.

![Tüm alt denetimleri bul](../test/media/codeduilocateall.png)

![Bulunan tüm denetimler](../test/media/codeduilocateall2.png)

**UI denetim eşlemesi** bölmesinde, bulmak istediğiniz kapsayıcı denetimini seçin ve tüm alt öğelerini görüntüleyin. Sonra, denetimin kısayol menüsünü açın ve **Tümünü Bul**' u seçin. Kapsayıcı denetimi ve tüm alt denetimleri, kodlanmış UI test düzenleyicisinde yeşil onay işaretiyle veya kırmızı bir ' X ' ile işaretlenir. Bu işaretler, denetimlerin test edilen uygulamada başarılı bir şekilde konumlandırılmasını bilmenizi sağlar.

> [!NOTE]
> UI denetimlerini konumlandırmadan önce, test ile ilişkili uygulamanın çalıştığını doğrulayın.

## <a name="insert-a-delay-before-a-ui-action"></a>Kullanıcı arabirimi eyleminden önce bir gecikme ekleyin

Bazen, bir pencere görüntülenecek bir pencere, ilerleme çubuğunun kaybolması gibi belirli olayların gerçekleşmesini beklemek isteyebilirsiniz. Kodlanmış UI test düzenleyicisini kullanarak, bir kullanıcı arabirimi eyleminden önce bir gecikme ekleyerek bunu yapabilirsiniz. Gecikmenin kaç saniye olmasını istediğinizi belirtebilirsiniz.

![Kullanıcı arabirimi eyleminden önce gecikme Ekle](../test/media/codeduidelay.png)

![5 saniyeye eklenen gecikme](../test/media/codeduidealy2.png)

**UI eylemi** bölmesinde, daha önce gecikme eklemek istediğiniz UI eylemini içeren test yöntemini genişletin. UI eylemini seçin. Sonra, Kullanıcı Arabirimi eyleminin kısayol menüsünü açın ve **önce gecikme Ekle**' yi seçin. Şu metinle seçili kullanıcı arabirimi eyleminden önce bir gecikme eklenir ve vurgulanır: **Eylemler arasındaki kullanıcı gecikmesi için 1 saniye bekleyin**. **Özellikler** penceresinde, **Delay** özelliğinin değerini istenen milisaniye sayısıyla değiştirin.

gecikmeyi eklemeyi bitirdikten sonra, Visual Studio araç çubuğunda **kaydet** ' i seçerek *umap. Designer* dosyasındaki değişiklikleri kaydedin.

Bir kullanıcı arabirimi eyleminden önce belirli bir denetimin kullanılabilir olduğundan emin olmanız gerekiyorsa, uygun UITestControl. WaitForControlXXX () yöntemini kullanarak test yönteminiz için özel kod eklemeyi göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz. [kayıttan yürütme sırasında belirli olaylar için KODLANMıŞ UI testlerini bekleme](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Veri odaklı kodlanmış UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md)
- [İzlenecek yol: kodlanmış bir UI testi oluşturma, düzenlememe ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
