---
title: CodeLens ile kod değişikliklerini ve diğer geçmişi bulun | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8876a0a3c2b978443ee4bc74097dbc9fdd410b8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656009"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>CodeLens ile kod değişikliklerini ve diğer geçmişi bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyiciden çıkmadan kodunuzda ne olduğunu öğrenirken çalışmanıza odaklanmaya devam edin. Kodunuzda, bağlantılı hatalarda, çalışma öğelerinde, kod incelemelerinizde ve birim testlerinde başvuruları ve değişiklikleri bulun.

> [!NOTE]
> CodeLens yalnızca Visual Studio Enterprise ve Visual Studio Professional sürümlerinde kullanılabilir. Visual Studio Community Edition 'da kullanılamaz.

 Kodunuzdaki kodunuzun bağımsız bölümlerinin çözümünüzde nerede ve nasıl kullanıldığını görün:

 ![Kod düzenleyicisinde CodeLens göstergeleri](../ide/media/codelensoverview.png "CodeLensOverview")

 Düzenleyiciden çıkmadan kodunuzda değişiklikler hakkında ekibinize başvurun:

 ![CodeLens &#45; ekibinize başvurun](../ide/media/codelensovervew2.png "CodeLensOvervew2")

 Görmek istediğiniz göstergeleri seçmek veya CodeLens 'i kapatmak ve açmak için **Araçlar**, **Seçenekler**, **metin düzenleyici**, **tüm diller**, **CodeLens**' e gidin.

## <a name="find-references-to-your-code"></a><a name="FindReferences"></a> Kodunuza başvuruları bulma
 Şunlara ihtiyacınız var:

- Visual Studio Enterprise veya Visual Studio Professional

- Visual C# .NET veya Visual Basic .NET kodu

  **Başvurular** göstergesini seçin (**alt + 2**). **0 başvuru**görürseniz, Visual C# veya Visual Basic kodundan bir başvuruya sahip olursunuz. Bu, XAML ve ASPX dosyaları gibi diğer öğelerden başvuruları içermez.

  ![CodeLens &#45; başvuruları seçin göstergesi](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")

  Başvuru kodunu görüntülemek için farenizi başvurunun üzerine taşıyın.

  ![CodeLens &#45; Özeti başvurusu](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")

  Başvuruyu içeren dosyayı açmak için, başvuruya çift tıklayın.

  Bu kod ve başvuruları arasındaki ilişkileri görmek için [bir kod haritası oluşturun](../modeling/map-dependencies-across-your-solutions.md) ve kod Haritası kısayol menüsünde **tüm başvuruları göster** ' i seçin.

  ![Kod eşlemesinde CodeLens &#45; başvuruları](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")

## <a name="find-your-codes-history-and-linked-items"></a><a name="FindCodeHistory"></a> Kodunuzun geçmişini ve bağlantılı öğelerini bulun
 Kodunuzda ne olduğunu öğrenmek için kodunuzun geçmişini gözden geçirin. Ya da değişiklikleri kodunuzda birleştirilmeden önce gözden geçirin, böylece diğer dallardaki değişikliklerin kodunuzu nasıl etkileyebileceği hakkında daha iyi bir anlayışınız olabilir.

 Şunlara ihtiyacınız var:

- Visual Studio Enterprise veya Visual Studio Professional

- Team Foundation Server 2013 veya üzeri, Visual Studio Team Services veya git

- [Lync 2010 veya üzeri ya da Skype Kurumsal](https://technet.microsoft.com/lync), kod düzenleyicisinden ekibinizle iletişim kurmak için

  Visual C# .NET veya Team Foundation sürüm denetimi (TFVC) veya git ile depolanan Visual Basic .NET kodu için, sınıf ve yöntem düzeylerinde (*kod öğesi düzeyi* göstergeler) CodeLens ayrıntılarını alırsınız. Git deponuz TfGit 'te barındırılıyorsa TFS iş öğelerinin bağlantılarını da alırsınız.

  ![Kod öğesi&#45;düzeyi göstergeleri](../ide/media/codelenselementlevelindicators.png "Codelenselementlevelındicators")

  Visual Studio Düzenleyicisi 'nde açabileceğiniz tüm diğer dosya türleri için, pencerenin alt kısmında (*Dosya düzeyi* göstergeleri) bir yerde tüm dosyanın CodeLens ayrıntılarını alırsınız.

  ![Dosya&#45;düzeyi CodeLens göstergeleri](../ide/media/almcodelensfilelevelindicators.png "Almcodelensfilelevelındicators")

  Göstergeleri seçmek üzere klavyeyi kullanmak için, ilgili sayı anahtarlarını göstermek için **alt** tuşuna basın ve basılı tutun.

  ![Klavye erişim numaralarını görmek için ALT tuşuna basın](../ide/media/codelensaltkeyindicators.png "Codelensaltkeyındicators")

### <a name="find-changes-in-your-code"></a>Kodunuzda değişiklik bulun
 C# veya Visual Basic kodunuzu kimin değiştirdikleri ve kod öğesi düzeyinde göstergeler ' de yaptığı değişiklikleri bulun. Team Foundation Server veya Visual Studio Team Services içinde Team Foundation sürüm denetimi 'ni (TFVC) kullandığınızda gördüğünüz şeydir.

 ![CodeLens: TFVC 'de kodunuzun değişiklik geçmişini alın](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")

 Varsayılan süre, son 12 ay olur. Kodunuz Team Foundation Server depolanıyorsa, [CodeIndex komutuyla](../ide/codeindex-command.md) ve **/ındexgeçmişini** bayrağıyla [TFSConfig komutunu](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) çalıştırarak bunu değiştirebilirsiniz.

 Bir yıldan daha uzun bir süre önce dahil olmak üzere tüm değişikliklerin ayrıntılı geçmişini görmek için **tüm dosya değişikliklerini göster**' i seçin.

 ![Tüm kod değişikliklerini göster](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")

 Bu, değişiklik kümeleri için Geçmiş penceresini açar.

 ![Tüm kod değişiklikleri için geçmiş penceresi](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")

 Dosyalarınız bir git deposunda olduğunda ve kod öğesi düzeyinde değişiklikler göstergesini seçtiğinizde, bu durum sizin görebileceğinize göre belirlenir.

 ![CodeLens: git 'teki kodunuzun değişiklik geçmişini alın](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")

 Pencerenin alt kısmındaki dosya düzeyi göstergelerinde bir dosyanın tamamına (C# ve Visual Basic dosyaları hariç) ilişkin değişiklikleri bulur.

 ![CodeLens: kod dosyası ayrıntılarını al](../ide/media/codelensfilelevel.png "CodeLensFileLevel")

 Bir değişiklik hakkında daha fazla bilgi edinmek için bu öğeye sağ tıklayın. TFVC veya git kullanıyor olmanıza bağlı olarak, dosyanın sürümlerini karşılaştırmak, ayrıntıları görüntülemek ve değişiklik kümesini izlemek, dosyanın seçili sürümünü almak ve bu değişikliğin yazarından e-posta için bir dizi seçenek edinirsiniz. Bu ayrıntıların bazıları Takım Gezgini görüntülenir.

 Ayrıca, kodunuzun zaman içinde kimin tarafından değiştirildiğini de görebilirsiniz. Bu, takımınızın değişikliklerinde desenleri bulmanıza ve etkilerini değerlendirmenize yardımcı olabilir.

 ![CodeLens: grafik olarak kod değişikliği geçmişine bakın](../ide/media/codelens.png "CodeLens")

#### <a name="find-changes-in-your-current-branch"></a>Geçerli dalınızdaki değişiklikleri bulma
 Takımınızın bir ana dalı ve bir alt geliştirme olan birden çok dalı olduğunu varsayalım. kararlı kodun parçalara bölünmesi riskini azaltmak için:

 ![CodeLens: kodunuzun dallanmış olduğu zaman bulun](../ide/media/codelensfirstbranchconceptual.png "Codelensfirstbranchkavramsal")

 Kodunuzu kaç kişinin değiştirmiş olduğunu ve ana dalınızda kaç değişiklik yapıldığını (**alt + 6**) bulun:

 ![CodeLens: dalınızda kaç değişiklik olduğunu bulun](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")

#### <a name="find-when-your-code-was-branched"></a>Kodunuzun dallanmış olduğu zaman bulun
 Alt daldaki kodunuza (örneğin, geliştirme dalı) gidin. Değişiklik göstergesini seçin (**alt + 6**):

 ![CodeLens: kodunuzun dallanmış olduğu zaman bulun](../ide/media/codelensfirstbranchscreenshot.png "Codelensfirstbranchekran görüntüsü")

#### <a name="find-incoming-changes-from-other-branches"></a>Diğer dallardan gelen değişiklikleri bulma
 ![CodeLens: diğer dallardaki kod değişikliklerini bulma](../ide/media/codelensbranchchangecheckinconceptual.png "Codelensbranchchangecheckınkavramsal")

 ... Geliştirme dalında bu hata düzeltmesini beğendiniz:

 ![CodeLens: değişiklik başka bir dala iade edildi](../ide/media/codelensbranchchangedevscreenshot.png "Codelensbranchchangedevekran görüntüsü")

 Bu değişikliği geçerli dalınızı kapatmadan inceleyebilirsiniz (ana):

 ![CodeLens: başka bir daldan gelen değişikliğe bakın](../ide/media/codelensbranchchangemainscreenshot.png "Codelensbranchchangemainekran görüntüsü")

#### <a name="find-when-changes-got-merged"></a>Değişikliklerin ne zaman birleştirildiğini bul
 Bu nedenle, dalınızda hangi değişikliklerin yer aldığı hakkında bilgi alabilirsiniz:

 ![, Dallar arasındaki birleştirilmiş değişiklikleri &#45; CodeLens](../ide/media/codelensbranchmergedconceptual.png "Codelensbranchbirleştirilen kavramsal")

 Örneğin, Ana daldaki kodunuz artık geliştirici dalında hata düzeltmesine sahiptir:

 ![Şubelerle birleştirilmiş chagnes &#45; CodeLens](../ide/media/codelensbranchmergedscreenshot.png "Codelensbranchbirleştiriekran görüntüsü")

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Yerel sürümünüzle gelen bir değişikliği karşılaştırın (SHIFT + F10)
 ![CodeLens: gelen değişikliği yerel ile karşılaştırın](../ide/media/codelensbranchincomingchangemenu.png "Codelensbranchıncomingchangemenu")

 Değişiklik kümesine çift de tıklayabilirsiniz.

#### <a name="what-do-the-icons-mean"></a>Simgeler ne anlama geliyor?

|**Simg**|**Değişikliğin nereden geldiği**|
|--------------|-----------------------------------------|
|![CodeLens: geçerli dal simgesinden Değiştir simgesi](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Geçerli dal|
|![CodeLens &#45; üst dal simgesinden değişikliği](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Üst dal|
|![CodeLens: alt dal simgesinden değiştirme](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Bir alt dal|
|![CodeLens &#45; eş dalı simgesinden Değiştir simgesi](../ide/media/codelensbranchpeericon.png "Codelensbranchpeerıcon")|Bir eş dalı|
|![CodeLens &#45; dalından daha fazla değiştirme simgesi](../ide/media/codelensbranchfurtherawayicon.png "Codelensbranchmobilyatherawayıcon")|Üst, alt veya eşten daha fazla bir dal|
|![CodeLens: üst simge ile birleştirme](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Üst daldan alt dala birleştirme|
|![CodeLens: alt daldan birleştirme simgesi](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Alt dalından üst dala birleştirme|
|![CodeLens: ilişkisiz daldan birleştirme simgesi](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|İlişkisiz daldan birleştirme (baseless Merge)|

### <a name="find-linked-work-items"></a>Bağlantılı iş öğelerini bul
 ![CodeLens &#45; belirli kod için iş öğelerini bulma](../ide/media/codelensworkitems.png "Codelensworkıtems")

### <a name="find-linked-code-reviews"></a>Bağlantılı kod İncelemeleri bulun
 ![CodeLens &#45; görünüm kodu inceleme istekleri](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")

### <a name="find-linked-bugs"></a>Bağlantılı hataları bulma
 ![CodeLens &#45; değişiklik kümelerine bağlı hataları bul](../ide/media/codelensbugschangesets.png "Codelensbugsdeğişiklik kümeleri")

### <a name="contact-the-owner-of-an-item"></a>Bir öğenin sahibine başvurun
 ![Bir öğenin sahibine başvurun](../ide/media/codelenscontactitemowner.png "Codelensınant Titemowner")

 İletişim seçeneklerini görmek için bir öğenin kısayol menüsünü açın. Lync veya Skype Kurumsal yüklüyse, şu seçenekleri görürsünüz:

 ![Öğe için iletişim seçenekleri](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")

## <a name="find-unit-tests-for-your-code"></a><a name="FindRunUnitTests"></a> Kodunuz için birim testlerini bulma
 Test Gezgini 'ni açmadan kodunuz için var olan birim testleri hakkında daha fazla bilgi edinin. Şunlara ihtiyacınız var:

- Visual Studio Enterprise veya Visual Studio Professional

- Visual C# .NET veya Visual Basic .NET kodu

- Uygulama kodunuz için birim testlerine sahip bir [birim testi projesi](../test/unit-test-your-code.md)

1. Birim testlerini içeren uygulama koduna gidin.

2. Bu kod için testleri gözden geçirin (**alt + 3**).

     ![CodeLens &#45; kod düzenleyicisinde test durumunu seçin](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")

3. Bir uyarı simgesi görürseniz ![&#45; birim testleri henüz uyarı çalıştırmadıysa](../ide/media/codelenstestwarningicon.png "Codelenstestwarningıcon"), testleri çalıştırın.

     ![CodeLens &#45; görünüm birimi testleri henüz çalıştırılmadı](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")

4. Bir testin tanımını gözden geçirmek için CodeLens gösterge penceresindeki test öğesine çift tıklayarak kod dosyasını düzenleyicide açın.

     ![CodeLens &#45; birim testi tanımına git](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")

5. Test sonuçlarını gözden geçirin Test durumu göstergesini seçin (![codelens &#45; birim testi başarısız simgesi](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") veya ![CodeLens &#45; birim testi geçti simgesi](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")) veya **alt + 1**tuşlarına basın.

     ![CodeLens &#45; bkz. birim test sonucu](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")

6. Bu testi değiştiren, bu testi değiştiren veya bu testte kaç tane değişiklik yapıldığını görmek için [kodunuzun geçmişini ve bağlantılı öğelerini bulun](#FindCodeHistory).

## <a name="q--a"></a><a name="QA"></a> SORU-CEVAP &

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a><a name="ChangeOrTurnOff"></a> S: CodeLens 'i Nasıl yaparım? açın mi? Ya da hangi göstergeleri görmek istediğinizi seçin
 Y **:**  Başvurular göstergesi dışında, göstergeleri kapalı veya açık olarak açabilirsiniz. **Araçlar**, **Seçenekler**, **metin düzenleyici**, **tüm diller**, **CodeLens**öğesine gidin.

 Göstergeler açıldığında, göstergelerden CodeLens seçeneklerini de açabilirsiniz.

 ![CodeLens &#45; göstergeyi kapatma veya açma](../ide/media/codelensturnoffonindicatorsfromcode.png "Codelensturnoffonındicatorsfromcode")

 Düzenleyici penceresinin alt köşeli ayraç simgelerini kullanarak CodeLens dosya düzeyi göstergelerini açın ve kapatın.

 ![Dosya&#45;düzeyi göstergelerini aç ve Kapat](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")

### <a name="q-where-is-codelens"></a><a name="NoIndicators"></a> S: CodeLens nerede?
 Y **:** CodeLens, Visual C# .NET içinde ve yöntem, sınıf, Dizin Oluşturucu ve özellik düzeyinde .NET kodu Visual Basic görünür. CodeLens, diğer tüm dosya türleri için dosya düzeyinde görünür.

- CodeLens 'in açık olduğundan emin olun. **Araçlar**, **Seçenekler**, **metin düzenleyici**, **tüm diller**, **CodeLens**öğesine gidin.

- Kodunuz TFS 'de depolanıyorsa, [TFS Config komutuyla](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) [CodeIndex komutunu](../ide/codeindex-command.md) kullanarak kod dizin oluşturma özelliğinin açık olduğundan emin olun.

- TFS ilişkili göstergeler yalnızca iş öğeleri koda bağlandığında ve bağlantılı iş öğelerini açmak için izniniz olduğunda görünür. [Ekip üyesi izinleriniz olduğunu doğrulayın.](/azure/devops/organizations/security/view-permissions)

- Birim testi göstergeleri, uygulama kodu birim testlerine sahip olmadığında görünmez. Test durumu göstergeleri test projesinde otomatik olarak görüntülenir. Uygulama kodunuzun birim testleri olduğunu biliyorsanız, ancak test göstergeleri görünmüyorsa, çözümü oluşturmayı deneyin (**Ctrl + Shift + B**).

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>S: bir kayıt için iş öğesi ayrıntılarını neden görmüyorum?
 Y **:** CodeLens TFS 'de iş öğelerini bulamadığı için bu durum oluşabilir. Bu iş öğelerini içeren takım projesine bağlı olduğunuzdan ve bu iş öğelerini görme izniniz olduğundan emin olun. Bu durum, kayıt açıklamasında TFS 'deki iş öğesi kimlikleri hakkında yanlış bilgiler varsa de oluşabilir.

### <a name="q-why-dont-i-see-the-lync-or-skype-indicators"></a><a name="NoLync"></a> S: Lync veya Skype göstergelerini neden görmüyorum?
 Y **:** Lync veya Skype Kurumsal oturumu açmadıysanız, bunlardan biri yüklü değilse veya desteklenen bir yapılandırmaya sahip değilseniz görünmez. Ancak yine de posta gönderebilirsiniz:

 ![CodeLens &#45; kişi değişiklik kümesi sahibine posta](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")

 **Hangi Lync ve Skype yapılandırması desteklenir?**

- Skype Kurumsal (32-bit veya 64-bit)

- Lync 2010 veya sonraki bir sürümü (32-bit veya 64-bit), Windows 8.1 ile Lync temel 2013 değil

  CodeLens, farklı Lync veya Skype sürümünün yüklü olmasını desteklemez. Visual Studio 'nun tüm yerelleştirilmiş sürümleri için yerelleştirilmiş olmayabilir.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>S: Nasıl yaparım? CodeLens 'in yazı tipini ve rengini değiştirmek istiyor musunuz?
 Y **:** **Araçlar**, **Seçenekler**, **ortam**, **yazı tipleri ve renkler**'e gidin.

 ![CodeLens &#45; yazı tipi ve renk ayarlarını değiştir](../ide/media/codelensoptionsfontscolorssettings.png "Codelensoptions Fontscolorssettings")

 Klavyeyi kullanmak için:

1. **Seçenekler** kutusunu açmak için **Alt + T + O** tuşlarına basın.

2. **Ortam** düğümüne gitmek Için **yukarı ok** veya **aşağı ok** tuşuna basın ve ardından düğümü genişletmek için **sol ok** tuşuna basın.

3. **Yazı tipleri ve renkler '** e gitmek Için **aşağı ok** tuşuna basın.

4. **Ayarları göster** listesine gitmek için **Tab** tuşuna basın ve ardından **CodeLens**' i seçmek için **aşağı ok** tuşuna basın.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>S: CodeLens ekran göstergesi görüntüsünü taşıyabilir miyim?
 Y **:** Evet, CodeLens 'i pencere olarak yerleştirmek için ![bir pencere olarak codelens &#45; yerleştir](../ide/media/codelensdockwindow.png "CodeLensDockWindow") ' i seçin.

 ![CodeLens gösterge penceresini yerleştir](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")

 ![Sabitlenmiş CodeLens başvuruları penceresi](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")

### <a name="q-how-do-i-refresh-the-indicators"></a>S: Göstergeleri nasıl yenileyebilirim?
 Y **:** Bu gösterge şunlara bağlıdır:

- **Başvurular**: Bu gösterge, kod değiştiğinde otomatik olarak güncelleştirilir. Bu göstergeyi ayrı bir pencere olarak yuvalandıysanız, göstergeyi burada el ile yenileyin:

     ![CodeLens &#45; pencere olarak Yerleştir](../ide/media/codelensviewreferencesdocked.png "Codelensviewreferencesyerleştirildi")

- **Takım**: Bu göstergeleri burada el ile yenileyin:

     ![CodeLens &#45; yenileme göstergeleri](../ide/media/codelensrefreshindicatorsfromcode.png "Codelensrefreshındicatorsfromcode")

- **Test**: Bu göstergeyi yenilemek için [kodunuzun birim testlerini bulun](#FindRunUnitTests) .

### <a name="q-whats-local-version"></a><a name="LocalVersion"></a> S: "Yerel sürüm" nedir?
 Y **:** **Yerel sürüm** oku, bu dosyanın yerel sürümünüzde en son değişiklik kümesine işaret eder. Sunucuda daha yeni değişiklik kümeleri olduğunda, değişiklik kümelerini sıralamak için kullanılan sıralamaya bağlı olarak **Yerel sürüm** okunun üstünde veya altında görünürler.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>S: CodeLens 'in geçmişi ve bağlantılı öğeleri göstermek için kodu nasıl işlediğinde yönetebilir miyim?
 Y **:** Evet, kodunuz TFS 'de ise, [TFS Config komutuyla](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) [CodeIndex komutunu](../ide/codeindex-command.md) kullanın.
