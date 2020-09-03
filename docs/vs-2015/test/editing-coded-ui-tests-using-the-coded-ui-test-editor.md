---
title: Kodlanmış UI Test Düzenleyicisi 'Ni kullanarak kodlanmış UI testlerini düzenleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c070f1bafb157e3979eb9c1f49b317b17807f1e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82587005"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi'ni Kullanarak Kodlanmış UI Testlerini Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI Testi Düzenleyicisi, kodlanmış UI testlerinizi kolayca değiştirmenize olanak sağlar. Kodlanmış UI test düzenleyicisini kullanarak, test yöntemlerinizin ve UI eylemlerinin özelliklerini bulabilir, görüntüleyebilir ve düzenleyebilirsiniz. Bunlara ek olarak, ilgili denetimlerini görüntülemek ve düzenlemek için UI denetim haritasını kullanabilirsiniz.

 **Gereksinimler**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Neden bunu yapmam gerekir?
 Kodlanmış UI Test Düzenleyicisi 'nin kullanılması daha hızlı ve kod düzenleyicisini kullanarak kodlanmış UI test yöntemlerinizin kodunu düzenlemekten daha etkilidir. Kodlanmış UI Testi Düzenleyicisi ile, Kullanıcı Arabirimi eylemleri ve denetimleriyle ilişkili özellik değerlerini hızlı bir şekilde bulmak ve değiştirmek için araç çubuğu ve kısayol menülerini kullanabilirsiniz. Örneğin, kodlanmış UI Test Düzenleyicisi 'nin araç çubuğunu aşağıdaki komutları gerçekleştirmek için kullanabilirsiniz:

 ![UI test edito](../test/media/uitesteditor.png "Uıısteditor")

1. [Bul](../ide/finding-and-replacing-text.md) , Kullanıcı Arabirimi eylemlerini ve denetimleri bulmanıza yardımcı olur.

2. [Sil](#CodedUITestEditor_DeleteUIActions) , istenmeyen Kullanıcı Arabirimi eylemlerini kaldırır.

3. **Yeniden adlandırma** , test yöntemleri ve denetimlerinin adlarını değiştirir.

4. **Özellikler** seçili öğe Için Özellikler penceresini açar.

5. [Yeni bir yönteme bölmek](#CodedUITestEditor_SplitMethods) , UI eylemlerini modüle etmenizi sağlar.

6. [Taşıma kodu](#CodedUITestEditor_MoveMethods) , test yöntemlerinize özel kod ekler.

7. Bir kullanıcı arabirimi eyleminden önce, milisaniye olarak belirtilen bir duraklama [eklemeden önce gecikme Ekle](#CodedUITestEditor_InsertDelay) .

8. Test edilen uygulamanın kullanıcı arabiriminde denetimin konumunu tanımlayan [UI denetimini bulun](#CodedUITestEditor_LocateUIControl) .

9. [Tümünü Bul](#CodedUITestEditor_LocateDecendants) özelliği, denetim özelliğini doğrulamanızı ve uygulamanın denetimlerinde önemli değişiklikler yapmanıza yardımcı olur.

## <a name="how-do-i-do-this"></a>Bunu nasıl yapabilirim?
 ' De, kodlanmış UI test projenizde kodlanmış UI [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] testinizle bağlantılı UIMap. UITest dosyasını açmak, kodlanmış UI testi düzenleyicisinde KODLANMıŞ UI testini otomatik olarak görüntüler. Aşağıdaki yordamlarda, test yöntemlerinizi bulma ve düzenleme, UI eylemlerinin özellikleri ve düzenleyicinin araç çubuğunu ve kısayol menülerini kullanarak denetimlerin nasıl yapılacağı açıklanır.

## <a name="open-a-coded-ui-test"></a>Kodlanmış UI testi açma
 Kodlanmış UI test düzenleyicisini kullanarak, Visual C# ve Visual Basic tabanlı kodlanmış UI testinizi görüntüleyebilir ve düzenleyebilirsiniz.

 ![Bağlam menüsü kodlanmış UI Test Oluşturucusu Ile Düzenle](../test/media/editcodeduitest.png "EditCodedUITest")

 Çözüm Gezgini ' de **UIMap. UITest** için kısayol menüsünü açın ve **Aç**' ı seçin. Kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde görüntülenir. Artık, kodlanmış UI testinde kayıtlı yöntemleri, eylemleri ve ilgili denetimleri görüntüleyebilir ve düzenleyebilirsiniz.

> [!TIP]
> **UI eylemleri** bölmesindeki bir yöntemde bulunan bir UI eylemi seçtiğinizde, karşılık gelen denetim vurgulanır. UI eylemini veya denetim özelliklerini de değiştirebilirsiniz.

 Kodlanmış UI test düzenleyicisini *görmüyorum* .
2012 ' dan önceki Visual Studio Enterprise sürümünü kullanıyor olabilirsiniz. Kodlanmış UI Test Düzenleyicisi, Visual Studio 2010 Feature Pack 2 ' de bir MSDN aboneliği ile de kullanıma sunulmuştur. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 özellik paketi 2](https://msdn.microsoft.com/library/gg269474.aspx).

## <a name="modify-ui-action-properties-and-their-corresponding-control-properties"></a><a name="CodedUITestEditor_EditActionAndControlProperties"></a> UI eylemi özelliklerini ve bunlara karşılık gelen denetim özelliklerini değiştirme
 Kodlanmış UI test düzenleyicisini kullanarak, test yöntemlerinizin tüm Kullanıcı Arabirimi eylemlerini hızlıca bulabilir ve görüntüleyebilirsiniz. Düzenleyicide Kullanıcı arabirimi eylemini seçtiğinizde, karşılık gelen denetim otomatik olarak vurgulanır. Benzer şekilde, bir denetimi seçerseniz, ilişkili Kullanıcı Arabirimi eylemleri vurgulanır. Bir UI eylemi veya bir denetim seçtiğinizde, buna karşılık gelen özellikleri değiştirmek için Özellikler penceresi kullanmak kolaydır.

 ![UI eylemi özellikleri](../test/media/codeduiedituiaction.png "CodedUIEditUIAction") UI eylemi özelliklerini Düzenle

 Bir UI eyleminin özelliklerini değiştirmek için, **UI eylemi** bölmesinde, özelliklerini düzenlemek ISTEDIĞINIZ bir UI eylemi içeren test yöntemini genişletin, Kullanıcı arabirimi eylemini seçin ve ardından Özellikler penceresi kullanarak özellikleri değiştirin.

 Örneğin, bir sunucu kullanılamaz durumdaysa ve Web tarayıcınızla ilişkili, Web **sayfasına git ' <http://Contoso1/default.aspx’> e**ait bir kullanıcı arabirimi EYLEMI varsa, URL 'yi olarak değiştirebilirsiniz `‘http://Contoso2/default.aspx’` .

 ![Denetim özellikleri](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp") Denetim özelliklerini Düzenle

 Bir denetimin özelliklerini değiştirmek, UI eylemleriyle aynı şekilde yapılır. **UI denetim eşlemesi** bölmesinde, düzenlemek istediğiniz denetimi seçin ve Özellikler penceresi kullanarak özelliklerini değiştirin.

 Örneğin, bir geliştirici, "ıdlogin" olarak test edilen uygulamanın kaynak kodundaki düğme denetimindeki **(ID)** özelliğini "ıdlogin" olarak değiştirmiş olabilir. Uygulamada **(ID)** özelliği değiştirildiğinde, kodlanmış UI testi düğme denetimini bulamaz ve başarısız olur. Bu durumda, sınayıcı **arama özellikleri** koleksiyonunu açabilir ve **kimlik** özelliğini, geliştirici uygulamada kullanılan yeni değerle eşleşecek şekilde değiştirebilir. Sınayıcı Ayrıca **kolay ad** özellik değerini "Gönder" Iken "Login" olarak değiştirebilir. Bu değişiklik yapıldığında, kodlanmış UI test düzenleyicisinde ilişkili Kullanıcı Arabirimi eylemi "' Gönder ' düğmesine", "' Login' düğmesini seçin."

 Değişikliklerinizi tamamladıktan sonra, araç çubuğunda **Kaydet** ' i seçerek UIMap. Designer dosyasındaki değişiklikleri kaydedin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 *Başka ne bilmem gerekir?*
 **Uçları**

- ![İpucu](../test/media/tip.png "İpucu") Özellikler penceresi görüntülenmiyorsa, **ENTER**tuşuna basarak **alt** tuşunu basılı tutun veya alternatif olarak **F4**tuşuna basın.

- ![İpucu](../test/media/tip.png "İpucu") Yaptığınız özellik değişikliklerini geri almak için, **Düzenle** menüsünden **geri al** ' ı seçin veya CTRL + Z tuşlarına basın.

- ![İpucu](../test/media/tip.png "İpucu") Visual Studio 'da bul ve Değiştir aracını açmak için kodlanmış UI Test Düzenleyicisi araç çubuğundaki **bul** düğmesini kullanabilirsiniz. Daha sonra, kodlanmış UI test düzenleyicisinde bir kullanıcı arabirimi eylemini bulmak için bul denetimini kullanabilirsiniz. Örneğin, "Click ' Login' düğmesini bulmayı deneyebilirsiniz." Bu, büyük testlerde yararlı olabilir. Kodlanmış UI test düzenleyicisinde bul ve Değiştir aracında değiştirme işlevini kullanmayacağınızı unutmayın. Daha fazla bilgi için bkz. [metni bulma ve değiştirme](../ide/finding-and-replacing-text.md)Içindeki denetimi bulma.

- ![İpucu](../test/media/tip.png "İpucu") Bazen denetimlerin test edilen uygulamanın kullanıcı arabiriminde nerede olduğunu görselleştirmek zor olabilir. Kodlanmış UI testi düzenleyicisinin özelliklerinden biri, UI denetim haritasında listelenen bir denetimi seçebileceğiniz ve test edilen uygulamada konumunu görüntüleyebilin. [!INCLUDE[crdefault](../includes/crdefault-md.md)]Bu konuda aşağıda yer alan [test altında bulunan uygulamada BIR UI denetimini bulma](#CodedUITestEditor_LocateUIControl) .

- ![İpucu](../test/media/tip.png "İpucu") Düzenlemek istediğiniz denetimi içeren kapsayıcı denetimini genişletmek gerekli olabilir. [!INCLUDE[crdefault](../includes/crdefault-md.md)]Bu konuda daha ayrıntılı [bir denetim ve alt öğeleri bulunuyor](#CodedUITestEditor_LocateDecendants) .

## <a name="delete-unwanted-ui-actions"></a><a name="CodedUITestEditor_DeleteUIActions"></a> İstenmeyen UI eylemlerini silme
 Kodlanmış UI testinizde, istenmeyen UI eylemlerini kolayca kaldırabilirsiniz.

 ![UI eylemini Sil](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")

 **UI eylemi** bölmesinde, silmek istediğiniz kullanıcı arabirimi eylemini içeren test yöntemini genişletin. UI eyleminin kısayol menüsünü açın ve **Sil**' i seçin.

## <a name="split-a-test-method-into-two-separate-methods"></a><a name="CodedUITestEditor_SplitMethods"></a> Test yöntemini iki ayrı yönteme bölme
 UI eylemlerini daraltmak için bir test yöntemini bölebilir veya ayarlayabilirsiniz. Örneğin, testiniz iki kapsayıcı denetiminde UI eylemleriyle birlikte tek bir test yöntemine sahip olabilir. UI eylemleri, tek bir kapsayıcıya karşılık gelen iki yöntemde daha iyi modüler olabilir.

 ![SPLT a test yöntemi](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")

 ![İki test yöntemi](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")

 **UI eylemi** bölmesinde, iki ayrı yönteme bölmek istediğiniz test yöntemini genişletin ve yeni test yönteminin başlamasını istediğiniz kullanıcı arabirimi eylemini seçin. UI eylemi için kısayol menüsünü açın ve **Yeni bir yönteme Böl**' ü seçin veya kodlanmış UI Test Düzenleyicisi araç çubuğundaki **Yeni bir yönteme Böl** düğmesini seçin. Yeni test yöntemi, UI eylemleri bölmesinde görünür. Bölmeyi belirttiğiniz eylemden başlayarak Kullanıcı Arabirimi eylemlerini içerir.

 Yöntemi bölmeyi tamamladıktan sonra, araç çubuğunda **Kaydet** ' i seçerek UIMap. Designer dosyasındaki değişiklikleri kaydedin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 *Başka ne bilmem gerekir?*
 **Önemli sorunlar**

- ![Uyarı simgesi](../test/media/caution.gif "dikkatli") **uyarısı:** bir yöntemi bölemeseniz, mevcut yöntemi çağıran herhangi bir kodu değiştirmeniz gerekir, bu kullanıcı Arabirimi eylemlerini hala eklemek istiyorsanız, oluşturmak üzere olduğunuz yeni yöntemi de çağırabilirsiniz. Bir yöntemi böldüğünüz zaman bir Microsoft Visual Studio iletişim kutusu görüntülenir. Ayrıca, oluşturmak üzere olduğunuz yeni yöntemi çağırmak için mevcut yöntemi çağıran herhangi bir kodu değiştirmeniz gerektiğini uyarır. **Evet**' i seçin.

  **Uçları**

- ![İpucu](../test/media/tip.png "İpucu") Bölmeyi geri almak için, **Düzenle** menüsünden **geri al** ' ı seçin veya CTRL + Z tuşlarına basın.

- ![İpucu](../test/media/tip.png "İpucu") Yeni yöntemi yeniden adlandırabilirsiniz. UI eylemleri bölmesinde seçin ve kodlanmış UI Test Düzenleyicisi araç çubuğundaki **Yeniden Adlandır** düğmesini seçin.

   -veya-

   Yeni test yönteminin kısayol menüsünü açın ve **Yeniden Adlandır**' ı seçin.

   Microsoft Visual Studio iletişim kutusu görüntülenir. Yönteme başvuran tüm kodları değiştirmeniz gerektiğini uyarır. **Evet**' i seçin.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a><a name="CodedUITestEditor_MoveMethods"></a> Özelleştirmeyi kolaylaştırmak için bir test yöntemini UIMap dosyasına taşıyın
 Kodlanmış UI testinizde test yöntemlerinizin birinin özel kod gerektirdiğini belirlerseniz, UIMap.cs veya Umap. vb dosyasına taşımanız gerekir. Aksi takdirde, kodlanmış UI testi yeniden derlendiğinde kodunuzun üzerine yazılır. Yöntemi taşıyamazsınız, test her yeniden derlenilişinde özel kodunuzun üzerine yazılır.

 **UI eylemi** bölmesinde, test kodu yeniden derlenme sırasında üzerine yazılmayacak özel kod işlevlerini kolaylaştırmak için UIMap.cs veya umap. vb dosyasına taşımak istediğiniz test yöntemini seçin. Sonra, kodlanmış UI Test Düzenleyicisi araç çubuğundaki **kodu taşı** düğmesini seçin veya test yönteminin kısayol menüsünü açın ve **kodu taşı**' yı seçin. Test yöntemi UIMap.uitest dosyasından kaldırılır ve artık UI Eylemler bölmesinde görüntülenmez. Taşıdığınız test dosyasını düzenlemek için, UIMap.cs veya UIMap. vb dosyasını Çözüm Gezgini açın.

 Yöntemi taşımayı tamamladıktan sonra, araç çubuğunda **Kaydet** ' i seçerek UIMap. Designer dosyasındaki değişiklikleri kaydedin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 *Başka ne bilmem gerekir?*
 **Önemli sorunlar**

- ![Uyarı simgesi](../test/media/caution.gif "dikkatli") **uyarısı:** bir yöntemi taşıdıktan sonra, kodlanmış UI test düzenleyicisini kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız. Bir yöntemi taşıdığınızda bir Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemin Umap. UITest dosyasından UIMap.cs veya Umap. vb dosyasına taşınacağını ve artık kodlanmış UI test düzenleyicisini kullanarak yöntemi düzenleyemeyeceksiniz. **Evet**' i seçin.

  **Uçları**

- ![İpucu](../test/media/tip.png "İpucu") Taşımayı geri almak için, **Düzenle** menüsünden **geri al** ' ı seçin veya CTRL + Z tuşlarına basın. Ancak, kodu UIMap.cs veya Umap. vb dosyasından el ile kaldırmanız gerekir.

## <a name="locating-a-ui-control-in-the-application-under-test"></a><a name="CodedUITestEditor_LocateUIControl"></a> Test edilen uygulamada bir UI denetimini bulma
 Bazen denetimlerin test edilen uygulamanın kullanıcı arabiriminde nerede olduğunu görselleştirmek zor olabilir. Kodlanmış UI testi düzenleyicisinin özelliklerinden biri, UI denetim haritasında listelenen bir denetimi seçebileceğiniz ve test edilen uygulamada konumunu görüntüleyebilin. Test edilen uygulamada **UI denetimini bul** özelliğinin kullanılması, bir denetimde yaptığınız arama özelliği değişikliklerini doğrulamak için de kullanılabilir.

 ![UI denetimini bul](../test/media/codeduilocatecontrol.png "CodedUILocateControl")

 ![Test edilen uygulamada bulunan denetim](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")

 **UI denetim eşlemesi** bölmesinde, test ile ilişkili uygulamada bulmak istediğiniz denetimi seçin. Sonra, denetimin kısayol menüsünü açın ve ardından **UI denetimini bul**' u seçin. Test edilmekte olan uygulamada, denetim mavi bir kenarlıkla atanır.

 *Başka ne bilmem gerekir?*
 **Önemli sorunlar**

- ![Uyarı simgesi](../test/media/caution.gif "dikkatli") **uyarısı:** bir UI denetimini bulmadan önce, test ile ilişkili uygulamanın çalıştığını doğrulayın.

  **Uçları**

- ![İpucu](../test/media/tip.png "İpucu") Alternatif olarak, bir kapsayıcı altındaki tüm denetimlerin doğru bir şekilde konumlandırılabilecek olduğunu doğrulamak için **Tümünü Bul** seçeneğini de kullanabilirsiniz. Bu seçenek, sonraki bölümde açıklanmaktadır.

## <a name="locating-a-control-and-its-descendants"></a><a name="CodedUITestEditor_LocateDecendants"></a> Bir denetimi ve alt öğelerini bulma
 Bir kapsayıcı altındaki tüm denetimlerin test edilen uygulamanın kullanıcı arabiriminde doğru şekilde konumlandırılabilecek olduğunu doğrulayabilirsiniz. Bu, kapsayıcıda yapmış olduğunuz arama özelliği değişikliklerinin doğrulanması için yararlı olabilir. Ayrıca, test edilen uygulamanın kullanıcı arabiriminde önemli değişiklikler varsa, var olan denetim arama özelliklerinin hala doğru olduğunu doğrulayabilirsiniz.

 ![Tüm alt denetimleri bul](../test/media/codeduilocateall.png "CodedUILocateAll")

 ![Bulunan tüm denetimler](../test/media/codeduilocateall2.png "CodedUILocateAll2")

 **UI denetim eşlemesi** bölmesinde, bulmak istediğiniz kapsayıcı denetimini seçin ve tüm alt öğelerini görüntüleyin. Sonra, denetimin kısayol menüsünü açın ve **Tümünü Bul**' u seçin. Kapsayıcı denetimi ve tüm alt denetimleri, kodlanmış UI test düzenleyicisinde yeşil onay işaretiyle veya kırmızı bir ' X ' ile işaretlenir. Bu işaretler, denetimlerin test edilen uygulamada başarılı bir şekilde konumlandırılmasını bilmenizi sağlar.

 *Başka ne bilmem gerekir?*
 **Önemli sorunlar**

- ![Uyarı simgesi](../test/media/caution.gif "dikkatli") **uyarısı:** UI denetimlerini konumlandırmadan önce, test ile ilişkili uygulamanın çalıştığını doğrulayın.

## <a name="inserting-a-delay-before-a-ui-action"></a><a name="CodedUITestEditor_InsertDelay"></a> Kullanıcı arabirimi eyleminden önce gecikme ekleme
 Bazen, bir pencere görüntülenecek bir pencere, ilerleme çubuğunun kaybolması gibi belirli olayların gerçekleşmesini beklemek isteyebilirsiniz. Kodlanmış UI test düzenleyicisini kullanarak, bir kullanıcı arabirimi eyleminden önce bir gecikme ekleyerek bunu yapabilirsiniz. Gecikmenin kaç saniye olmasını istediğinizi belirtebilirsiniz.

 ![Kullanıcı arabirimi eyleminden önce gecikme Ekle](../test/media/codeduidelay.png "CodedUIDelay")

 ![5 saniyeye eklenen gecikme](../test/media/codeduidealy2.png "CodedUIDealy2")

 **UI eylemi** bölmesinde, daha önce gecikme eklemek istediğiniz UI eylemini içeren test yöntemini genişletin. UI eylemini seçin. Sonra, Kullanıcı Arabirimi eyleminin kısayol menüsünü açın ve **önce gecikme Ekle**' yi seçin. Şu metinle seçili kullanıcı arabirimi eyleminden önce bir gecikme eklenir ve vurgulanır: **Eylemler arasındaki kullanıcı gecikmesi için 1 saniye bekleyin**. Özellikler penceresi, **Delay** özelliğinin değerini istenen milisaniye sayısıyla değiştirin.

 Gecikmeyi eklemeyi bitirdikten sonra, araç çubuğunda **Kaydet** ' i seçerek Umap. Designer dosyasındaki değişiklikleri kaydedin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 *Başka ne bilmem gerekir?*
 **Notlar**

- ![Prerequsite](../test/media/prereq.png "Önkoşul") Bir kullanıcı arabirimi eyleminden önce belirli bir denetimin kullanılabilir olduğundan emin olmanız gerekiyorsa, uygun UITestControl. WaitForControlXXX () yöntemini kullanarak test yönteminiz için özel kod eklemeyi göz önünde bulundurmanız gerekir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Kayıttan yürütme sırasında belirli olaylar Için KODLANMıŞ UI testlerini bekleme](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

  **Uçları**

- ![İpucu](../test/media/tip.png "İpucu") Özellikler penceresi görüntülenmiyorsa, ENTER tuşuna basarak alt tuşunu basılı tutun veya alternatif olarak F4 tuşuna basın.

## <a name="external-resources"></a>Dış kaynaklar

### <a name="guidance"></a>Rehber
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="faq"></a>SSS
 [Kodlanmış UI testleri SSS-1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Kodlanmış UI testleri SSS-2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
 [Visual Studio UI Otomasyon testi (CodedUI içerir)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Ayrıca Bkz.
 [Kodunuzu test etmek IÇIN UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md) [kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) BIR [veri odaklı kodlanmış UI testi](../test/creating-a-data-driven-coded-ui-test.md) oluşturma bir [mevcut eylem kaydından kodlanmış](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) UI testi oluşturma [Izlenecek yol: kodlanmış bir UI testi oluşturma, düzenlemeyle ve sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
