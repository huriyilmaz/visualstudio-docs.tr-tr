---
title: Düzenleme Kodlu UI Testleri
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8df6d1ea44cb9737c39653366c7b35823051d5f6
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445044"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi'ni kullanarak kodlanmış UI testlerini edin

Kodlanmış UI Test Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenizi sağlar. Kodlanmış UI Test Düzenleyicisi'ni kullanarak test yöntemlerinizin ve UI eylemlerinizin özelliklerini bulabilir, görüntüleyebilir ve değiştirebilirsiniz. Buna ek olarak, karşılık gelen denetimlerini görüntülemek ve bunları sağlamak için UI denetim eşlemi kullanabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="features-of-the-coded-ui-test-editor"></a>Kodlu UI Test Düzenleyicisinin Özellikleri

Kodlu UI Test Düzenleyicisi'ni kullanmak, Kod Düzenleyicisi'ni kullanarak kodlu UI test yöntemlerinizdeki kodu düzenlemeden daha hızlı ve etkilidir. Kodlanmış UI Test Düzenleyicisi ile, Araç Arabirimi eylemleri ve denetimleriyle ilişkili özellik değerlerini hızla bulmak ve değiştirmek için araç çubuğunu ve kısayol menülerini kullanabilirsiniz. Örneğin, aşağıdaki komutları gerçekleştirmek için Kodlanmış UI Test Düzenleyicisi araç çubuğunu kullanabilirsiniz:

![UI Test Düzenleyicisi](../test/media/uitesteditor.png)

1. [Bulun,](../ide/finding-and-replacing-text.md) UI eylemlerini ve denetimlerini bulmanıza yardımcı olur.

2. **Delete** istenmeyen Kullanıcı Bira eylemlerini kaldırır.

3. **Yeniden adlandırma,** test yöntemleri ve denetimleri için adları değiştirir.

4. **Özellikler** seçili öğe için **Özellikler** penceresini açar.

5. **Yeni bir yönteme bölme,** UI eylemlerini modüle etmenizi sağlar.

6. **Move Code,** test yöntemlerinize özel kod ekler.

7. **Gecikmeyi Ekleme Önce,** milisaniye cinsinden belirtilen bir Arama Ara birimi eyleminden önce bir duraklama ekleyin.

8. **Kullanıcı Aracı Denetimi'ni bulun,** test altındaki uygulamanın Kullanıcı Aracı'ndaki denetimin konumunu tanımlar.

9. **Tüm'ü Bul,** denetim özelliğini ve uygulama denetimlerinde önemli değişiklikleri doğrulamanıza yardımcı olur.

Kodlanmış UI testinizle bağlı *UIMap.uitest* dosyasını açtığınızda, kodlanmış UI **testi Kodlu UI Test**Düzenleyicisi'nde açılır. Aşağıdaki yordamlar, test yöntemlerinizi ve UI eylemlerinin özelliklerini nasıl bulabileceğinizi ve bunları nasıl düzeltebileceğinizi ve düzenleyicinin araç çubuğu ve kısayol menülerini kullanarak denetimleri açıklar.

## <a name="open-a-coded-ui-test"></a>Kodlanmış bir UI testi açma

**Kodlu UI Test Düzenleyicisini**kullanarak Visual C# ve Visual Basic tabanlı kodlu ui testinizi görüntüleyebilir ve edinebilirsiniz.

![Kodlu UI Test Oluşturucu suyla Bağlam menüsü Edit](../test/media/editcodeduitest.png)

**Solution**Explorer'da, *UIMap.uitest* için kısayol menüsünü açın ve **Aç'ı**seçin. Kodlanmış UI testi **Kodlanmış UI Test**Düzenleyicisi'nde görüntülenir. Artık kodlanmış UI testinde kaydedilen yöntemleri, eylemleri ve ilgili denetimleri görüntüleyebilir ve edinebilirsiniz.

> [!TIP]
> **UI Eylemleri** bölmesinde bir yöntemde bulunan bir UI eylem seçtiğinizde, karşılık gelen denetim vurgulanır. Ayrıca, UI eylemini veya denetim özelliklerini de değiştirebilirsiniz.

## <a name="modify-ui-action-and-control-properties"></a>UI eylem ve denetim özelliklerini değiştirme

Kodlanmış UI Test Düzenleyicisi'ni kullanarak, test yöntemlerinizdeki tüm UI eylemlerini hızlı bir şekilde bulabilir ve görüntüleyebilirsiniz. Düzenleyicide UI eylemini seçtiğinizde, karşılık gelen denetim otomatik olarak vurgulanır. Aynı şekilde, bir denetim seçerseniz, ilişkili UI eylemleri vurgulanır. Bir UI eylemi veya denetim seçtiğinizde, onunla karşılık gelen özellikleri değiştirmek için **Özellikler** penceresini kullanmak kolaydır.

![UI eylem özellikleri](../test/media/codeduiedituiaction.png)

**UI Eylem** bölmesinde bir UI eylem özellikleri değiştirmek için, özellikleri için değiştirmek istediğiniz bir UI eylem içeren test yöntemini genişletin, UI eylem seçin ve sonra Özellikler penceresi kullanarak özellikleri değiştirin.

Örneğin, bir sunucu kullanılamıyorsa ve web tarayıcınızla ilişkili bir kullanıcı arabirimi eyleminiz varsa **web tarayıcınıza http http'e\/gidin: /Contoso1/default.aspx**, URL'yi . `http://Contoso2/default.aspx`

![Denetim özellikleri](../test/media/codeduitestcontrolprop.png)

Denetim için özellikleri değiştirme, UI eylemleri yle aynı şekilde yapılır. **UI Denetim Haritası** bölmesinde, özellikler **penceresini** kullanarak değiştirmek istediğiniz denetimi seçin.

Örneğin, bir geliştirici, "idSubmit"den "idLogin" olarak sınanan uygulamanın kaynak kodundaki bir düğme denetimindeki **(ID)** özelliğini değiştirmiş olabilir. Uygulamada **(ID)** özelliği nin değiştirilmesiyle, kodlanmış Kullanıcı Bira testi düğme denetimini bulamayacak ve başarısız olur. Bu durumda, sınayıcı **Arama Özellikleri** koleksiyonunu açabilir ve **Geliştiricinin** uygulamada kullandığı yeni değerle eşleşecek şekilde Id özelliğini değiştirebilir. Test eden, Friendly **Name** özellik değerini "Gönder"den "Giriş" olarak da değiştirebilir. Bu değişikliği yaparak, Kodlanmış UI Test Düzenleyicisi'ndeki ilişkili UI eylemi "'Gönder' düğmesinden "Giriş'i seç" düğmesine güncelleştirilir.

Değişikliklerinizi tamamladıktan sonra, Visual Studio araç çubuğunda **Kaydet'i** seçerek *değişiklikleri UIMap.Designer* dosyasına kaydedin.

### <a name="tips"></a>İpuçları

- **Özellikler** penceresi görüntülenmiyorsa Enter tuşuna **basarken** **Alt** tuşuna basın veya **F4**tuşuna basın.

- Yaptığınız özellik değişikliklerini geri almak **için, Edit** menüsünden **Geri Al'ı** seçin veya **Ctrl**+**Z**tuşuna basın.

- Visual Studio'da **Bul ve Değiştir** aracını açmak için Kodlanmış UI Test düzenleyicisi araç çubuğundaki **Bul** düğmesini kullanabilirsiniz. Daha sonra Kodlanmış UI Test düzenleyicisinde bir UI eylemini bulmak için **Bul** denetimini kullanabilirsiniz. Örneğin, "'Giriş' düğmesini tıklatmayı" bulabilirsiniz. Bu büyük testlerde yararlı olabilir. Kodlanmış UI Test Düzenleyicisi'ndeki **Bul ve Değiştir** aracındaki değiştir işlevini kullanamazsınız. Daha fazla bilgi için [Find and replace text](../ide/finding-and-replacing-text.md)bkz.

- Bazen, denetimlerin test altında uygulamanın Kullanıcı Arabirimi'nde nerede bulunduğunu görselleştirmek zor olabilir. Kodlanmış Kullanıcı Arabirimi Test Düzenleyicisi'nin özelliklerinden biri, Kullanıcı Arabirimi denetim haritasında listelenen bir denetim seçip test altındaki uygulamada konumunu görüntüleyebiliyor olabilirsiniz. Daha fazla bilgi için, bu makalede daha aşağıda bulunan [test altında uygulamada bir Kullanıcı Arabirimi denetimi bulun](#locate-a-ui-control-in-the-application-under-test) bakın.

- Denetlemek istediğiniz denetimi içeren kapsayıcı denetimini genişletmek gerekebilir. Daha fazla bilgi için bkz: Bu makalede daha aşağıda bulunan [bir denetimi ve torunlarını bulun.](#locate-a-control-and-its-descendants)

## <a name="delete-unwanted-ui-actions"></a>İstenmeyen Kullanıcı Durumu hareketlerini silme

Kodlanmış UI testinizde istenmeyen UI eylemlerini kolayca kaldırabilirsiniz.

![Kullanıcı Bira Sıtkı eylemini silme](../test/media/codeduideleteuiaction.png)

Kullanıcı **Bire-ü Hareketi** bölmesinde, silmek istediğiniz Kullanıcı Bira eylemini içeren test yöntemini genişletin. Kullanıcı Arabirimi eylemi için kısayol menüsünü açın ve **Sil'i**seçin.

## <a name="split-a-test-method-into-two-separate-methods"></a>Test yöntemini iki ayrı yönteme bölme

UI eylemlerini hassaslaştırmak veya modüle etmek için bir test yöntemini bölebilirsiniz. Örneğin, testinizin iki kapsayıcı denetiminde UI eylemleri içeren tek bir test yöntemi olabilir. UI eylemleri, bir kapsayıcıyla karşılık gelen iki yöntemde daha iyi modüle edilebilir.

![Test yöntemini bölme](../test/media/codeduitestsplitmethod1.png)

![İki test yöntemi](../test/media/codeduitestsplitmethod2.png)

**UI Eylem** bölmesinde, iki ayrı yönteme bölmek istediğiniz test yöntemini genişletin ve yeni test yönteminin başlamasını istediğiniz u-ui eylemini seçin. UI eylemi için kısayol menüsünü açın ve ardından **Yeni bir yönteme Böl'ü**seçin veya Kodlanmış UI Test Düzenleyicisi araç çubuğunda **yeni bir yöntem düğmesine Bölün'ü** seçin. Yeni test yöntemi **UI Eylemleri** bölmesinde görünür. Bölmeyi belirttiğiniz eylemden başlayarak u-u uy eylemleri içerir.

Yöntemi bölmeyi bitirdikten sonra, Visual Studio araç çubuğunda **Kaydet'i** seçerek değişiklikleri *UIMap.Designer* dosyasına kaydedin.

> [!WARNING]
> Bir yöntemi bölerseniz, bu Ara birimi eylemlerinin dahil olmasını istiyorsanız, oluşturmak üzere olduğunuz yeni yöntemi de çağırmak için varolan yöntemi çağıran tüm kodları değiştirmeniz gerekir. Bir yöntemi böldüğünüzde, bir Microsoft Visual Studio iletişim kutusu görüntülenir. Oluşturmak üzere olduğunuz yeni yöntemi de aramak için varolan yöntemi çağıran herhangi bir kodu değiştirmeniz gerektiği konusunda sizi uyarır. **Evet'i**seçin.

### <a name="tips"></a>İpuçları

- Bölmeyi geri almak **için, Edit** menüsünden **Geri Al'ı** seçin veya **Ctrl**+**Z**tuşuna basın.

- Yeni yöntemi yeniden adlandırabilirsiniz. **Kullanıcı Arabirimi Eylemleri** bölmesinde seçin ve Kodlanmış Kullanıcı Arabirimi Test Düzenleyicisi araç çubuğundaki **Yeniden Adlandır** düğmesini seçin.

   -veya-

   Yeni test yöntemi için kısayol menüsünü açın ve **Yeniden Adlandır'ı**seçin.

   Microsoft Visual Studio iletişim kutusu görüntülenir. Yönteme başvuran herhangi bir kodu değiştirmeniz gerektiği konusunda sizi uyarır. **Evet'i**seçin.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Özelleştirmeyi kolaylaştırmak için bir test yöntemini UIMap dosyasına taşıma

Kodlanmış Kullanıcı Bira testinizdeki test yöntemlerinizden birinin özel kod gerektirdiğini belirlerseniz, bunu *UIMap.cs* veya *UIMap.vb* dosyasına taşımanız gerekir. Aksi takdirde, kodlanmış UI testi yeniden derlendiğinde kodunuz üzerine yazılır. Yöntemi taşımazsanız, test her kez yeniden derleniş olduğunda özel kodunuz üzerine yazılır.

Kullanıcı **Bire-posta İşlemi** bölmesinde, test kodu yeniden derlendiğinde üzerine yazılmayan özel kod işlevselliğini kolaylaştırmak için *UIMap.cs* veya *UIMap.vb* dosyasına taşımak istediğiniz test yöntemini seçin. Ardından, Kodlanmış UI Test Düzenleyicisi araç çubuğundaki **Kodu Taşı** düğmesini seçin veya test yöntemi için kısayol menüsünü açın ve **Kodu Taşı'yı**seçin. Test yöntemi *UIMap.uitest* dosyasından kaldırılır ve artık **UI Eylemleri** bölmesinde görüntülenmez. Taşıdığınız test dosyasını yeniden yapmak **için, Solution Explorer'dan** *UIMap.cs* veya *UIMap.vb* dosyasını açın.

Yöntemi taşımayı bitirdikten sonra, Visual Studio araç çubuğunda **Kaydet'i** seçerek değişiklikleri *UIMap.Designer* dosyasına kaydedin.

> [!WARNING]
> Bir yöntemi taşıdıktan sonra, Kodlu UI Test Düzenleyicisi'ni kullanarak artık bu yöntemi değiştiremezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız. Bir yöntemi taşıdığınızda, bir Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemin *UIMap.uitest* dosyasından *UIMap.cs* veya *UIMap.vb* dosyasına taşınacağı ve artık kodlanmış UI Test Düzenleyicisi'ni kullanarak yöntemi değiştiremeyeceğiniz konusunda sizi uyarır. **Evet'i**seçin.

### <a name="tips"></a>İpuçları

Hareketi geri almak **için, Edit** menüsünden **Geri Al'ı** seçin veya **Ctrl**+**Z**tuşuna basın. Ancak, daha sonra kodu *UIMap.cs* veya *UIMap.vb* dosyasından el ile kaldırmanız gerekir.

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Test altında uygulamada bir Kullanıcı Aracı denetimi bulun

Bazen, denetimlerin test altında uygulamanın Kullanıcı Arabirimi'nde nerede bulunduğunu görselleştirmek zor olabilir. Kodlanmış Kullanıcı Arabirimi Test Düzenleyicisi'nin özelliklerinden biri, Kullanıcı Arabirimi denetim haritasında listelenen bir denetim seçip test altındaki uygulamada konumunu görüntüleyebiliyor olabilirsiniz. Test altındaki uygulamada **Kullanıcı Arasını Denetimi'ni bul** özelliğini kullanmak, denetimde yaptığınız arama özelliği değişikliklerini doğrulamak için de kullanılabilir.

![UI denetimini bulma](../test/media/codeduilocatecontrol.png)

![Test kapsamında uygulamada bulunan kontrol](../test/media/codeduilocatecontrol2.png)

Kullanıcı **Birbiri Aracı Denetim Haritası** bölmesinde, testle ilişkili uygulamada bulmak istediğiniz denetimi seçin. Ardından, denetim için kısayol menüsünü açın ve ardından **UI Denetimini Bul'u**seçin. Test edilen uygulamada, denetim mavi kenarlıkile belirlenir.

> [!NOTE]
> Kullanıcı Aracı denetimini bulmadan önce, testle ilişkili uygulamanın çalıştığını doğrulayın.

### <a name="tips"></a>İpuçları

Kapsayıcı altındaki tüm denetimlerin doğru şekilde bulunabileceğini doğrulamak için **Tümlerini Bul** seçeneğini kullanabilirsiniz. Bu seçenek sonraki bölümde açıklanmıştır.

## <a name="locate-a-control-and-its-descendants"></a>Bir kontrol ve onun torunları bulun

Bir kapsayıcının altındaki tüm denetimlerin test altındaki uygulamanın Kullanıcı Birliğini doğru şekilde bulunabileceğini doğrulayabilirsiniz. Bu, kapsayıcıda yapmış olabileceğiniz arama özelliği değişikliklerini doğrulamada yararlı olabilir. Ayrıca, test altındaki uygulamanın Kullanıcı Arabirimi'nde önemli değişiklikler olduysa, varolan denetim arama özelliklerinin hala doğru olduğunu doğrulayabilirsiniz.

![Tüm soyundan gelen denetimleri bulma](../test/media/codeduilocateall.png)

![Bulunan tüm denetimler](../test/media/codeduilocateall2.png)

**UI Denetim Haritası** bölmesinde, bulmak istediğiniz kapsayıcı denetimini seçin ve tüm torunları görüntüleyin. Ardından, denetim için kısayol menüsünü açın ve **Tümlerini Bul'u**seçin. Kapsayıcı denetimi ve tüm soyundan gelen denetimler, kodlanmış u-posta testi düzenleyicisinde yeşil onay işareti veya kırmızı 'X' ile işaretlenir. Bu işaretler, denetimlerin test altındaki uygulamada başarıyla bulunup bulunmadığınızı size bildirin.

> [!NOTE]
> Kullanıcı Bulma Birimi denetimlerini bulmadan önce, testle ilişkili uygulamanın çalıştığını doğrulayın.

## <a name="insert-a-delay-before-a-ui-action"></a>Bir UI eyleminden önce gecikme ekleme

Bazen, bir pencerenin görünmesi, ilerleme çubuğunun kaybolması gibi belirli olayların oluşması için sınama beklemesini isteyebilirsiniz. Kodlanmış UI Test Düzenleyicisi'ni kullanarak, bir UI eyleminden önce bir gecikme ekleyerek bunu başarabilirsiniz. Gecikmenin kaç saniye olmasını istediğinizi belirtebilirsiniz.

![Bir UI eyleminden önce gecikme ekleme](../test/media/codeduidelay.png)

![Gecikme 5 saniye ile eklendi](../test/media/codeduidealy2.png)

**UI Eylem** bölmesinde, önce bir gecikme eklemek istediğiniz UI eylemini içeren test yöntemini genişletin. UI eylemini seçin. Ardından, UI eylemi için kısayol menüsünü açın ve **Önce Gecikme ekle'yi**seçin. Aşağıdaki metinle seçili Kullanıcı Arabirimi eyleminden önce bir gecikme eklenir ve vurgulanır: **Eylemler arasında kullanıcı gecikmesi için 1 saniye bekleyin.** **Özellikler** penceresinde, **Gecikme** özelliğinin değerini istenen milisaniye sayısıyla değiştirin.

Gecikmeyi eklemeyi bitirdikten sonra, Visual Studio araç çubuğunda **Kaydet'i** seçerek değişiklikleri *UIMap.Designer* dosyasına kaydedin.

Kullanıcı Arabirimi eyleminden önce belirli bir denetimin kullanılabilir olduğundan emin olmanız gerekiyorsa, uygun UITestControl.WaitForControlXXX() yöntemini kullanarak test yönteminize özel kod eklemeyi düşünmelisiniz. Daha fazla bilgi için bkz. [Kodlu Kullanıcı Arabirimi testleri oynatma sırasında belirli olayları beklemesini](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)sağlama.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Veri tabanlı kodlu ui testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md)
- [Walkthrough: Kodlanmış bir UI testi oluşturma, düzenleme ve bakım](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
