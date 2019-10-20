---
title: Kodlanmış UI testlerini düzenleniyor
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 971b5d178a777b7a0021eda4bfccab06727981ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664995"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi 'Ni kullanarak kodlanmış UI testlerini düzenleme

Kodlanmış UI Testi Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. Kodlanmış UI test düzenleyicisini kullanarak, test yöntemlerinizin ve UI eylemlerinin özelliklerini bulabilir, görüntüleyebilir ve düzenleyebilirsiniz. Bunlara ek olarak, ilgili denetimlerini görüntülemek ve düzenlemek için UI denetim haritasını kullanabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="features-of-the-coded-ui-test-editor"></a>Kodlanmış UI test düzenleyicisinin özellikleri

Kodlanmış UI Test Düzenleyicisi 'nin kullanılması daha hızlı ve kod düzenleyicisini kullanarak kodlanmış UI test yöntemlerinizin kodunu düzenlemekten daha etkilidir. Kodlanmış UI Testi Düzenleyicisi ile, Kullanıcı Arabirimi eylemleri ve denetimleriyle ilişkili özellik değerlerini hızlı bir şekilde bulmak ve değiştirmek için araç çubuğu ve kısayol menülerini kullanabilirsiniz. Örneğin, kodlanmış UI Test Düzenleyicisi 'nin araç çubuğunu aşağıdaki komutları gerçekleştirmek için kullanabilirsiniz:

![UI Test Düzenleyicisi](../test/media/uitesteditor.png)

1. [Bul](../ide/finding-and-replacing-text.md) , Kullanıcı Arabirimi eylemlerini ve denetimleri bulmanıza yardımcı olur.

2. **Sil** , istenmeyen Kullanıcı Arabirimi eylemlerini kaldırır.

3. **Yeniden adlandırma** , test yöntemleri ve denetimlerinin adlarını değiştirir.

4. **Özellikler** seçili öğe için **Özellikler** penceresini açar.

5. **Yeni bir yönteme bölmek** , UI eylemlerini modüle etmenizi sağlar.

6. **Taşıma kodu** , test yöntemlerinize özel kod ekler.

7. Bir kullanıcı arabirimi eyleminden önce, milisaniye olarak belirtilen bir duraklama **eklemeden önce gecikme Ekle** .

8. Test edilen uygulamanın kullanıcı arabiriminde denetimin konumunu tanımlayan **UI denetimini bulun** .

9. **Tümünü Bul** özelliği, denetim özelliğini doğrulamanızı ve uygulamanın denetimlerinde önemli değişiklikler yapmanıza yardımcı olur.

Kodlanmış UI Testinizle bağlantılı *UIMap. UITest* dosyasını açtığınızda, kodlanmış UI testi kodlanmış UI testi **düzenleyicisinde**açılır. Aşağıdaki yordamlarda, test yöntemlerinizi bulma ve düzenleme, UI eylemlerinin özellikleri ve düzenleyicinin araç çubuğunu ve kısayol menülerini kullanarak denetimlerin nasıl yapılacağı açıklanır.

## <a name="open-a-coded-ui-test"></a>Kodlanmış UI testi açma

**KODLANMıŞ UI test düzenleyicisini**kullanarak, görsel C# ve Visual Basic tabanlı kodlanmış UI testinizi görüntüleyebilir ve düzenleyebilirsiniz.

![Bağlam menüsü kodlanmış UI Test Oluşturucusu Ile Düzenle](../test/media/editcodeduitest.png)

**Çözüm Gezgini**' de *UIMap. UITest* için kısayol menüsünü açın ve **Aç**' ı seçin. Kodlanmış UI testi, **KODLANMıŞ UI testi düzenleyicisinde**görüntülenir. Artık, kodlanmış UI testinde kayıtlı yöntemleri, eylemleri ve ilgili denetimleri görüntüleyebilir ve düzenleyebilirsiniz.

> [!TIP]
> **UI eylemleri** bölmesindeki bir yöntemde bulunan bir UI eylemi seçtiğinizde, karşılık gelen denetim vurgulanır. UI eylemini veya denetim özelliklerini de değiştirebilirsiniz.

## <a name="modify-ui-action-and-control-properties"></a>UI eylemini ve denetim özelliklerini değiştirme

Kodlanmış UI test düzenleyicisini kullanarak, test yöntemlerinizin tüm Kullanıcı Arabirimi eylemlerini hızlıca bulabilir ve görüntüleyebilirsiniz. Düzenleyicide Kullanıcı arabirimi eylemini seçtiğinizde, karşılık gelen denetim otomatik olarak vurgulanır. Benzer şekilde, bir denetimi seçerseniz, ilişkili Kullanıcı Arabirimi eylemleri vurgulanır. Bir UI eylemi veya bir denetim seçtiğinizde, bununla ilişkili özellikleri değiştirmek için **Özellikler** penceresini kullanmak kolaydır.

![UI eylemi özellikleri](../test/media/codeduiedituiaction.png)

Bir UI eyleminin özelliklerini değiştirmek için, **UI eylemi** bölmesinde, özelliklerini düzenlemek ISTEDIĞINIZ bir UI eylemi içeren test yöntemini genişletin, Kullanıcı arabirimi eylemini seçin ve ardından Özellikler penceresi kullanarak özellikleri değiştirin.

Örneğin, bir sunucu kullanılamaz durumdaysa ve Web tarayıcınızla ilişkili bir Kullanıcı Arabirimi eylemi varsa, **' <http://Contoso1/default.aspx> ' Web sayfasına gitiyorsa**, URL 'yi `'http://Contoso2/default.aspx'` olarak değiştirebilirsiniz.

![Denetim Özellikleri](../test/media/codeduitestcontrolprop.png)

Bir denetimin özelliklerini değiştirmek, UI eylemleriyle aynı şekilde yapılır. **UI denetim Haritası** bölmesinde, düzenlemek istediğiniz denetimi seçin ve **Özellikler penceresini kullanarak özelliklerini değiştirin** .

Örneğin, bir geliştirici, "ıdlogin" olarak test edilen uygulamanın kaynak kodundaki düğme denetimindeki **(ID)** özelliğini "ıdlogin" olarak değiştirmiş olabilir. Uygulamada **(ID)** özelliği değiştirildiğinde, kodlanmış UI testi düğme denetimini bulamaz ve başarısız olur. Bu durumda, sınayıcı **arama özellikleri** koleksiyonunu açabilir ve **kimlik** özelliğini, geliştirici uygulamada kullanılan yeni değerle eşleşecek şekilde değiştirebilir. Sınayıcı Ayrıca **kolay ad** özellik değerini "Gönder" Iken "Login" olarak değiştirebilir. Bu değişiklik yapıldığında, kodlanmış UI test düzenleyicisinde ilişkili Kullanıcı Arabirimi eylemi "' Gönder ' düğmesine", "' Login' düğmesini seçin."

Değişikliklerinizi tamamladıktan sonra, Visual Studio araç çubuğunda **Kaydet** ' i seçerek *UIMap. Designer* dosyasındaki değişiklikleri kaydedin.

### <a name="tips"></a>İpuçları

- **Özellikler** penceresi görüntülenmiyorsa, **ENTER**tuşuna basarak **alt** tuşunu basılı tutun veya **F4**tuşuna basın.

- Yaptığınız özellik değişikliklerini geri almak için, **Düzenle** menüsünden **geri al** ' ı seçin veya **CTRL** +**Z**' ye basın.

- Visual Studio 'da **Bul ve Değiştir** aracını açmak IÇIN kodlanmış UI Test Düzenleyicisi araç çubuğundaki **bul** düğmesini kullanabilirsiniz. Daha sonra, kodlanmış UI test düzenleyicisinde bir kullanıcı arabirimi eylemini bulmak için **bul** denetimini kullanabilirsiniz. Örneğin, "Click ' Login' düğmesini bulmayı deneyebilirsiniz." Bu, büyük testlerde yararlı olabilir. Kodlanmış UI test düzenleyicisinde **Bul ve Değiştir** aracında değiştirme işlevini kullanamazsınız. Daha fazla bilgi için bkz. [bulma ve değiştirme metin](../ide/finding-and-replacing-text.md)Içinde denetimi bulma.

- Bazen denetimlerin test edilen uygulamanın kullanıcı arabiriminde nerede olduğunu görselleştirmek zor olabilir. Kodlanmış UI testi düzenleyicisinin özelliklerinden biri, UI denetim haritasında listelenen bir denetimi seçebileceğiniz ve test edilen uygulamada konumunu görüntüleyebilin. Daha fazla bilgi için, bu makalede daha sonra bulunan [test altındaki uygulamada BIR UI denetimini bulma](#locate-a-ui-control-in-the-application-under-test) bölümüne bakın.

- Düzenlemek istediğiniz denetimi içeren kapsayıcı denetimini genişletmek gerekli olabilir. Daha fazla bilgi için, bu makalede daha [sonra bulunan bir denetimi ve alt öğelerini bulma](#locate-a-control-and-its-descendants) bölümüne bakın.

## <a name="delete-unwanted-ui-actions"></a>İstenmeyen UI eylemlerini silme

Kodlanmış UI testinizde, istenmeyen UI eylemlerini kolayca kaldırabilirsiniz.

![UI eylemini Sil](../test/media/codeduideleteuiaction.png)

**UI eylemi** bölmesinde, silmek istediğiniz kullanıcı arabirimi eylemini içeren test yöntemini genişletin. UI eyleminin kısayol menüsünü açın ve **Sil**' i seçin.

## <a name="split-a-test-method-into-two-separate-methods"></a>Test yöntemini iki ayrı yönteme bölme

UI eylemlerini daraltmak için bir test yöntemini bölebilir veya ayarlayabilirsiniz. Örneğin, testiniz iki kapsayıcı denetiminde UI eylemleriyle birlikte tek bir test yöntemine sahip olabilir. UI eylemleri, tek bir kapsayıcıya karşılık gelen iki yöntemde daha iyi modüler olabilir.

![Test yöntemini bölme](../test/media/codeduitestsplitmethod1.png)

![İki test yöntemi](../test/media/codeduitestsplitmethod2.png)

**UI eylemi** bölmesinde, iki ayrı yönteme bölmek istediğiniz test yöntemini genişletin ve yeni test yönteminin başlamasını istediğiniz kullanıcı arabirimi eylemini seçin. UI eylemi için kısayol menüsünü açın ve **Yeni bir yönteme Böl**' ü seçin veya kodlanmış UI Test Düzenleyicisi araç çubuğundaki **Yeni bir yönteme Böl** düğmesini seçin. Yeni test yöntemi, **UI eylemleri** bölmesinde görünür. Bölmeyi belirttiğiniz eylemden başlayarak Kullanıcı Arabirimi eylemlerini içerir.

Yöntemi bölmeyi tamamladıktan sonra, Visual Studio araç çubuğunda **Kaydet** ' i seçerek *UIMap. Designer* dosyasındaki değişiklikleri kaydedin.

> [!WARNING]
> Bir yöntemi bölemeseniz, mevcut yöntemi çağıran herhangi bir kodu değiştirmeniz gerekir, bu kullanıcı arabirimi eylemlerinin hala dahil edilmesini istiyorsanız oluşturmak üzere olduğunuz yeni yöntemi de çağırır. Bir yöntemi böldüğünüz zaman bir Microsoft Visual Studio iletişim kutusu görüntülenir. Ayrıca, oluşturmak üzere olduğunuz yeni yöntemi çağırmak için mevcut yöntemi çağıran herhangi bir kodu değiştirmeniz gerektiğini uyarır. **Evet**' i seçin.

### <a name="tips"></a>İpuçları

- Bölmeyi geri almak için, **Düzenle** menüsünden **geri al** ' ı seçin veya **CTRL** +**Z**' ye basın.

- Yeni yöntemi yeniden adlandırabilirsiniz. **UI eylemleri** bölmesinde seçin ve kodlanmış UI Test Düzenleyicisi araç çubuğundaki **Yeniden Adlandır** düğmesini seçin.

   veya

   Yeni test yönteminin kısayol menüsünü açın ve **Yeniden Adlandır**' ı seçin.

   Microsoft Visual Studio iletişim kutusu görüntülenir. Yönteme başvuran tüm kodları değiştirmeniz gerektiğini uyarır. **Evet**' i seçin.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Özelleştirmeyi kolaylaştırmak için bir test yöntemini UIMap dosyasına taşıyın

Kodlanmış UI testinizde test yöntemlerinizin birinin özel kod gerektirdiğini belirlerseniz, *UIMap.cs* veya *umap. vb* dosyasına taşımanız gerekir. Aksi takdirde, kodlanmış UI testi yeniden derlendiğinde kodunuzun üzerine yazılır. Yöntemi taşıyamazsınız, test her yeniden derlenilişinde özel kodunuzun üzerine yazılır.

**UI eylemi** bölmesinde, test kodu yeniden derlenme sırasında üzerine yazılmayacak özel kod işlevlerini kolaylaştırmak için *UIMap.cs* veya *umap. vb* dosyasına taşımak istediğiniz test yöntemini seçin. Sonra, kodlanmış UI Test Düzenleyicisi araç çubuğundaki **kodu taşı** düğmesini seçin veya test yönteminin kısayol menüsünü açın ve **kodu taşı**' yı seçin. Test yöntemi *UIMap. UITest* dosyasından kaldırılır ve artık **UI eylemleri** bölmesinde görüntülenmez. Taşıdığınız test dosyasını düzenlemek için, *UIMap.cs* veya *UIMap. vb* dosyasını **Çözüm Gezgini**açın.

Yöntemi taşımayı tamamladıktan sonra, Visual Studio araç çubuğunda **Kaydet** ' i seçerek *UIMap. Designer* dosyasına değişiklikleri kaydedin.

> [!WARNING]
> Bir yöntemi taşındıktan sonra, kodlanmış UI test düzenleyicisini kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız. Bir yöntemi taşıdığınızda bir Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemin *Umap. UITest* dosyasından *UIMap.cs* veya *umap. vb* dosyasına taşınacağını ve artık kodlanmış UI test düzenleyicisini kullanarak yöntemi düzenleyemeyeceksiniz. **Evet**' i seçin.

### <a name="tips"></a>İpuçları

Taşımayı geri almak için, **Düzenle** menüsünden **geri al** ' ı seçin veya **CTRL** +**Z**' ye basın. Ancak, kodu *UIMap.cs* veya *umap. vb* dosyasından el ile kaldırmanız gerekir.

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

Gecikmeyi eklemeyi tamamladıktan sonra, Visual Studio araç çubuğunda **Kaydet** ' i seçerek *UIMap. Designer* dosyasına değişiklikleri kaydedin.

Bir kullanıcı arabirimi eyleminden önce belirli bir denetimin kullanılabilir olduğundan emin olmanız gerekiyorsa, uygun UITestControl. WaitForControlXXX () yöntemini kullanarak test yönteminiz için özel kod eklemeyi göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz. [kayıttan yürütme sırasında belirli olaylar için KODLANMıŞ UI testlerini bekleme](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Ayrıca bkz.

- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Veri odaklı kodlanmış UI testi oluşturma](../test/creating-a-data-driven-coded-ui-test.md)
- [İzlenecek yol: kodlanmış bir UI testi oluşturma, düzenlememe ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)