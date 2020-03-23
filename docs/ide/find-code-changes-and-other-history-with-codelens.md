---
title: CodeLens ile kod değişikliklerini ve diğer geçmişi bulma
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9859366f6e4b9a0d1c219adc2080e6415b1e44a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588661"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>CodeLens ile kod değişikliklerini ve diğer geçmişi bulma

CodeLens, editörden ayrılmadan kodunuza&ndash;ne olduğunu öğrenirken işinize odaklanmanızı sağlar. Bir kod parçasına, kodunuzdaki değişikliklere, bağlantılı hatalara, çalışma öğelerine, kod incelemelerine ve birim testlerine başvurular bulabilirsiniz.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens Visual Studio Community sürümünde mevcuttur, *ancak, kaynak kontrol* göstergeleri bu baskıda mevcut değildir.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens yalnızca Visual Studio Enterprise ve Professional sürümlerinde kullanılabilir. Visual Studio Community sürümünde kullanılamaz.

::: moniker-end

Kodunuzu tek tek parçalarının çözümünde nerede ve nasıl kullanıldığını görün:

![Kod düzenleyicisinde CodeLens göstergeleri](../ide/media/codelens-overview.png)

Düzenleyiciden ayrılmadan kodunuzda yapılan değişiklikler hakkında ekibinize başvurun:

![CodeLens - Ekibinizle iletişim kurun](../ide/media/codelens-contact-info.png)

Görmek istediğiniz göstergeleri seçmek veya CodeLens'i kapatıp açmak için **Araçlar** > **Seçenekleri** > **Metin Editörü** > **Tüm Diller** > **KoduLens'e**gidin.

## <a name="find-references-to-your-code"></a>Kodunuza yapılan başvuruları bulma

C# veya Visual Basic kodunda referanslar bulabilirsiniz.

1. **Referanslar** göstergesini seçin veya **Alt**+**2'ye**basın.

   ![CodeLens referansları](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Gösterge0 **referansları**gösteriyorsa, C# veya Visual Basic kodundan referansyok. Ancak, *.xaml* ve *.aspx* dosyaları gibi diğer öğelerde başvurular olabilir.

2. Başvuru kodunu görüntülemek için, listedeki başvurunun üzerinde fare.

   ![CodeLens - Peek referans](../ide/media/codelens-peek-reference.png)

3. Başvuruyu içeren dosyayı açmak için başvuruyu çift tıklatın.

### <a name="code-maps"></a>Kod haritaları

Kod ve başvuruları arasındaki ilişkileri görmek için [bir kod eşlemi oluşturun.](../modeling/map-dependencies-across-your-solutions.md) Kod eşlemi kısayol menüsünde **Tüm Başvuruları Göster'i**seçin.

![CodeLens - Kod haritasında referanslar](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Kodunuzdaki değişiklikleri bulma

Kodunuza ne olduğunu öğrenmek için kodunuzu inceleyin. Veya, diğer dallardaki değişikliklerin kodunuzu nasıl etkileyebileceğini daha iyi anlamak için değişiklikleri kodunuzla birleştirilmeden önce gözden geçirin.

Gerekenler:

- Visual Studio Enterprise veya Professional sürümü

- Azure DevOps Hizmetleri, Team Foundation Server 2013 veya sonraki veya Daha sonra

- [Skype for Business,](/skypeforbusiness/) kod düzenleyicisinden ekibinizle iletişim kurmak için

Team Foundation Sürüm Kontrolü (TFVC) veya Git ile depolanan C# veya Visual Basic kodu için, sınıf ve yöntem düzeylerinde *(kod öğesi düzeyi* göstergeleri) CodeLens ayrıntılarını alırsınız. Git deponuz TfGit'te barındırılırsa, TFS iş öğelerine bağlantılar da alabilirsiniz.

![Kod öğesi düzeyi göstergeleri](../ide/media/codelens-element-level-indicators.png)

*.cs* veya *.vb*dışındaki dosya türleri için, pencerenin alt kısmında ki tek bir yerde *(dosya düzeyi* göstergeleri) tüm dosyaiçin CodeLens ayrıntılarını alırsınız.

![Dosya düzeyinde CodeLens göstergeleri](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Kod öğesi düzeyi göstergeleri

Kod öğesi düzeyi göstergeleri, kodunuzu kimin değiştirdiğini ve hangi değişiklikleri yaptıklarını görmenizi sağlar. C# ve Visual Basic kodu için kod öğesi düzeyi göstergeleri kullanılabilir.

Team Foundation Server veya Azure DevOps Hizmetlerinde Team Foundation Sürüm Denetimi'ni (TFVC) kullandığınızda şunları görürsünüz:

![CodeLens: TFVC'de kodunuz için değişiklik geçmişini alın](../ide/media/codelens-code-changes.png)

Varsayılan zaman dilimi son 12 aydır. Kodunuz Team Foundation Server'da depolanırsa, [CodeIndex komutu](../ide/codeindex-command.md) ve **/indexHistoryPeriod** bayrağıyla [TFSConfig komutunu](/azure/devops/server/command-line/tfsconfig-cmd) çalıştırarak süreyi değiştirebilirsiniz.

Bir yıldan uzun bir süre öncesine ait olanlar da dahil olmak üzere tüm değişikliklerin ayrıntılı geçmişini görmek için **tüm dosya değişikliklerini göster'i**seçin:

![Tüm kod değişikliklerini göster](../ide/media/codelens-show-all-file-changes.png)

**Geçmiş** penceresi açılır:

![Tüm kod değişiklikleri için geçmiş penceresi](../ide/media/codelenscodechangeshistory.png)

Dosyalarınız Git deposundayken ve kod öğesi düzeyindeki değişiklikleri göstergesini seçtiğinizde, şunları görüyorsunuz:

![CodeLens: Git'de kodunuz için değişiklik geçmişini alın](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Dosya düzeyi göstergeleri

Pencerenin altındaki dosya düzeyi göstergelerinde dosyanın tamamının değişikliklerini bulun:

![CodeLens: Kod dosyası ayrıntılarını alın](../ide/media/codelens-file-level.png)

> [!NOTE]
> C# ve Visual Basic dosyaları için dosya düzeyinde göstergeler kullanılamaz.

Değişiklik hakkında daha fazla bilgi almak için bu öğeyi sağ tıklatın. TFVC veya Git kullanıp kullanmadığınıza bağlı olarak, dosyanın sürümlerini karşılaştırmak, ayrıntıları görüntülemek ve değiştiriyi izlemek, dosyanın seçili sürümünü almak ve bu değişikliğin yazarına e-posta göndere bilmek için seçenekler vardır. Bu ayrıntıların bazıları **Takım Gezgini'nde**görünür.

Zaman içinde kodunuzu kimin değiştirdiğini de görebilirsiniz. Bu, ekibinizin değişikliklerindeki desenleri bulmanıza ve etkilerini değerlendirmenize yardımcı olabilir.

![CodeLens: Grafik olarak kod değişiklikleri geçmişini görün](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Geçerli dalınızdaki değişiklikleri bulma

Ekibinizin kararlı kodu kırma riskini azaltmak için bir ana dal ve bir alt geliştirme dalı gibi birden çok dalı olabilir.

![CodeLens: Kodunuzu dallanmış zaman bulun](../ide/media/codelensfirstbranchconceptual.png)

**Alt**+**6**tuşuna basarak kodunuzu kaç kişinin değiştirdiğini ve ana dalda kaç değişiklik yapıldığını öğrenebilirsiniz:

![CodeLens: Şubenizde kaç değişiklik olduğunu bulma](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Kodunuzu dallandırınca bulma

Kodunuzu dallandırıldığında bulmak için alt daldaki kodunuza gidin. Ardından, **değişiklik** göstergesini seçin veya **Alt**+**6'ya**basın:

![CodeLens: Kodunuzu dallanmış zaman bulun](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Diğer şubelerden gelen değişiklikleri bulma

![CodeLens: Diğer dallarda kod değişiklikleri bulma](../ide/media/codelensbranchchangecheckinconceptual.png)

Gelen değişiklikleri görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde, "Dev" dalında bir hata düzeltmesi yapıldı:

![CodeLens: Değişiklik başka bir dala giriş yaptı](../ide/media/codelens-branch-changes-dev.png)

Geçerli şubenizden ("Main") çıkmadan değişikliği gözden geçirebilirsiniz:

![CodeLens: Başka bir şubeden gelen değişikliği görün](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Değişikliklerin birleştirildiğinde bulma

Değişikliklerin ne zaman birleştirildiğine göre, dalınızda hangi değişikliklerin yer aldığını belirleyebilirsiniz:

![CodeLens - Dallar arasındaki birleştirilmiş değişiklikler](../ide/media/codelensbranchmergedconceptual.png)

Örneğin, Ana daldaki kodunuz artık "Dev" dalından hata düzeltmesi ne şr

![CodeLens - Dallar arasındaki birleştirilmiş değişiklikler](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Gelen değişikliği yerel sürümünüzle karşılaştırın

**Shift**+**F10**tuşuna basarak veya değiştirkümesini çift tıklatarak gelen değişikliği yerel sürümünüzle karşılaştırın.

![CodeLens: Gelen değişikliği yerel ile karşılaştırın](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Şube simgeleri

**Şube** sütunundaki simge, şubenin çalıştığınız şubeyle nasıl ilişkili olduğunu gösterir.

|**Simge**|**Değişiklik geldi:**|
|--------------| - |
|![CodeLens: Geçerli şube simgesinden değiştirme](../ide/media/codelensbranchcurrenticon.png)|Geçerli dal|
|![CodeLens: Üst dal simgesinden değiştirme](../ide/media/codelensbranchparenticon.png)|Üst dal|
|![CodeLens: Alt dal simgesinden değiştirme](../ide/media/codelensbranchchildicon.png)|Bir alt dal|
|![CodeLens: Eş dal simgesinden değiştirme](../ide/media/codelensbranchpeericon.png)|Eş dalı|
|![CodeLens: Şubeden daha uzaktaki simgesini değiştir](../ide/media/codelensbranchfurtherawayicon.png)|Bir ebeveyn, çocuk veya eşten daha uzakta bir dal|
|![CodeLens: Üst simgeden birleştirme](../ide/media/codelensbranchmergefromparenticon.png)|Üst daldan alt dala birleştirme|
|![CodeLens: Alt dal simgesinden birleştirme](../ide/media/codelensbranchmergefromchildicon.png)|Alt daldan üst dala birleştirme|
|![CodeLens: Alakasız şube simgesinden birleştirme](../ide/media/codelensbranchmergefromunrelatedicon.png)|İlişkisiz bir daldan birleştirme (temelsiz birleştirme)|

## <a name="linked-work-items"></a>Bağlantılı iş öğeleri

**İş kalemleri** göstergesini seçerek veya **Alt**+**8**tuşuna basarak bağlantılı iş öğelerini bulun.

![CodeLens - Belirli kodiçin iş öğeleri bulun](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Bağlantılı kod incelemeleri

**İncelemeler** göstergesini seçerek bağlantılı kod incelemelerini bulun. Klavyeyi kullanmak için **Alt** tuşunu basılı tutun ve gösterge seçeneklerinde gezinmek için **Sol ok** veya **Sağ ok** tuşuna basın.

![CodeLens - Kod gözden geçirme isteklerini görüntüleyin](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Bağlantılı hatalar

**Hata** göstergesini seçerek veya **Alt**+**7**tuşuna basarak bağlantılı hataları bulun.

![CodeLens - Değişiklik kümelerine bağlı hataları bulma](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Bir öğenin sahibiyle iletişim kurun

**Yazar** göstergesini seçerek veya **Alt**+**5**tuşuna basarak bir öğenin yazarını bulun.

![Bir öğenin sahibiyle iletişim kurun](../ide/media/codelens-contact-item-owner.png)

Kişi seçeneklerini görmek için bir öğenin kısayol menüsünü açın. Lync veya Skype for Business yüklüyseniz, şu seçenekleri görürsünüz:

![Bir öğeiçin kişi seçenekleri](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>İlişkili birim testleri

**Test**Gezgini'ni açmadan C# veya Visual Basic kodunuz için var olan birim testlerini keşfedebilirsiniz.

1. [İlişkili birim test koduna](../test/unit-test-your-code.md)sahip uygulama koduna gidin.

2. Zaten yapmadıysanız, CodeLens test göstergelerini yüklemek için uygulamanızı oluşturun. 

3. **Alt**+**3**tuşuna basarak kod için testleri gözden geçirin.

     ![CodeLens - Kod düzenleyicisinde test durumunu seçin](../ide/media/codelens-choose-test-indicator.png)

4. Bir uyarı simgesi görürseniz ![uyarı simgesi](../ide/media/codelenstestwarningicon.png), testler henüz çalışmadı, bu yüzden çalıştırın.

     ![CodeLens - Görüntü birim testleri henüz çalışmadı](../ide/media/codelens-tests-not-yet-run.png)

5. Bir testin tanımını gözden geçirmek için, düzenleyicideki kod dosyasını açmak için CodeLens göstergesi penceresindeki test öğesini çift tıklatın.

     ![CodeLens - Birim test tanımına git](../ide/media/codelens-unit-test-definition.png)

6. Test sonuçlarını gözden geçirmek için, test durum![göstergesini](../ide/media/codelenstestfailedicon.png) ![(test](../ide/media/codelenstestpassedicon.png)başarısız simgesi veya test geçti simgesi) seçin veya **Alt**+**1**tuşuna basın.

     ![CodeLens - Birim test sonucuna bakın](../ide/media/codelens-unit-test-result.png)

7. Bu testi kaç kişinin değiştirdiğini, bu testi kimlerin değiştirdiğini veya bu testte kaç değişiklik yapıldığını görmek için [kodunuzu geçmişve](#find-changes-in-your-code) bağlantılı öğeleri bulun.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Göstergeleri seçmek için klavyeyi kullanmak için, ilgili sayı tuşlarını görüntülemek için **Alt** tuşuna basın ve basılı tutun, ardından seçmek istediğiniz göstergeye karşılık gelen numaraya basın.

![Klavye erişim numaraları](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> **İncelemeler** göstergesini seçmek için, gezinmek için sol ve sağ ok tuşlarını kullanırken **Alt'ı** basılı tutun.

## <a name="q--a"></a>Soru-Cevap

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>S: CodeLens'i nasıl kapatırım veya açabilirim veya hangi göstergeleri göreceğimi seçerim?

**A:**  Referanslar göstergesi dışında göstergeleri kapatabilir veya açabilirsiniz. **Araçlar** > **Seçenekleri** > **Metin Editörü** > **Tüm Diller** > **CodeLens**gidin.

Göstergeler açıldığında, göstergelerden CodeLens seçeneklerini de açabilirsiniz.

![CodeLens - Göstergeleri kapatın veya açın](../ide/media/codelensturnoffonindicatorsfromcode.png)

CodeLens dosya düzeyindeki göstergeleri düzenleyici penceresinin altındaki köşeli sembolleri kullanarak açıp kapatın.

![Dosya düzeyindeki göstergeleri açma ve kapatma](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>S: CodeLens nerede?

**A:** CodeLens yöntem, sınıf, dizinleyici ve özellik düzeyinde C# ve Visual Basic kodunda görünür. CodeLens, diğer tüm dosya türleri için dosya düzeyinde görünür.

- CodeLens'in açık olduğundan emin olun. **Araçlar** > **Seçenekleri** > **Metin Editörü** > **Tüm Diller** > **CodeLens**gidin.

- Kodunuz TFS'de depolanırsa, [TFS Config komutu](/azure/devops/server/command-line/tfsconfig-cmd)ile [CodeIndex komutunu](../ide/codeindex-command.md) kullanarak kod dizini oluşturmanın açık olduğundan emin olun.

- DevOps ile ilgili göstergeler yalnızca iş öğeleri koda bağlandığında ve bağlantılı çalışma öğelerini açma izniniz olduğunda görünür. Ekip üyesi [izinlerine](/azure/devops/organizations/security/view-permissions?view=vsts)sahip olduğunuzu onaylayın.

- Uygulama kodunda birim testleri olmadığında birim test göstergeleri görünmez. Test durumu göstergeleri test projesinde otomatik olarak görüntülenir. Uygulama kodunuzda birim testleri olduğunu, ancak test göstergelerinin görünmediğini biliyorsanız, çözümü oluşturmayı deneyin **(Ctrl**+**Shift**+**B).**

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens Visual Studio Community sürümünde mevcuttur, *ancak, kaynak kontrol* göstergeleri bu baskıda mevcut değildir.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens Visual Studio Community sürümünde kullanılamaz.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>S: Bir taahhüt için iş öğesi ayrıntılarını neden göremiyorum?

**A:** CodeLens iş öğelerini Azure Panoları'nda veya TFS'de bulamadığı için bu durum olabilir. Bu çalışma öğelerine sahip projeye bağlı olup olmadığınızı ve bu çalışma öğelerini görmek için izinlere sahip olduğunuzu denetleyin. İş öğesi ayrıntıları, azure panolarında veya TFS'deki iş öğesi iyelikleri hakkında yanlış bilgilere sahipse, iş öğesi ayrıntıları da gösterilmeyebilir.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>S: Skype göstergelerini neden göremiyorum?

**A:** Skype kurumsal olarak oturum açmış değilseniz, yüklü değilseniz veya desteklenen bir yapılandırmanız yoksa Skype göstergeleri görünmez. Ancak, yine de e-posta gönderebilirsiniz:

![CodeLens - Posta ile changeset sahibi ne başvurun](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Hangi Skype ve Lync yapılandırmaları desteklenir?**

- Skype kurumsal (32 bit veya 64 bit)

- Lync 2010 veya daha sonra tek başına (32-bit veya 64-bit), ama Windows 8.1 ile Lync Basic 2013

CodeLens, Lync veya Skype'ın farklı sürümlerinin yüklenmesini desteklemez. Visual Studio'nun tüm yerelleştirilmiş sürümleri için yerelleştirilemeyebilirler.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>S: CodeLens'in yazı tipini ve rengini nasıl değiştirebilirim?

**A:** **Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkleri'ne**gidin.

![CodeLens - Yazı tipini ve renk ayarlarını değiştir](../ide/media/codelensoptionsfontscolorssettings.png)

Klavyeyi kullanmak için:

1. **Seçenekler** iletişim kutusunu açmak için **Alt**+**T**+**O** tuşuna basın.

2. **Çevre** düğümüne gitmek için **Yukarı Ok** veya **Aşağı Ok'a** basın, ardından düğümü genişletmek için **Sol Ok'a** basın.

3. Yazı Tipleri ve **Renkler'e**gitmek için **Aşağı Ok** tuşuna basın.

4. Liste için Göster **ayarlarına** gitmek için **Sekme'ye** basın ve ardından **CodeLens'i**seçmek için **Aşağı Ok'a** basın.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>S: CodeLens ekran göstergesi görüntüsünü taşıyabilir miyim?

**A:** Evet, ![CodeLens'i pencere olarak sabitlemek için Dock simgesini](../ide/media/codelensdockwindow.png) seçin.

![CodeLens gösterge penceresinde Dock düğmesi](../ide/media/codelensselectdockwindow.png)

![Docked CodeLens Referanslar penceresi](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>S: Göstergeleri nasıl yenileyebilirim?

**A:** Bu göstergeye bağlıdır:

- **Referanslar**: Bu gösterge, kod değiştiğinde otomatik olarak güncellenir. **Referanslar** göstergesi ayrı bir pencere olarak sabitlenirse, Yenile seçeneğini seçerek göstergeyi **yenileyin:**

   ![CodeLens Referanslarında Yenile düğmesi](../ide/media/codelensviewreferencesdocked.png)

- **Takım**: Sağ tıklama menüsünden **CodeLens Takım Göstergelerini Yenile** seçeneğini seçerek bu göstergeleri yenileyin:

   ![CodeLens Takım Göstergelerini Yenile menü öğesi](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: **Test** göstergesini yenilemek [için kodunuz için birim testlerini bulun.](#associated-unit-tests)

### <a name="q-whats-local-version"></a>S: "Yerel Sürüm" nedir?

**A:** **Yerel Sürüm** ok noktaları, bir dosyanın yerel sürümündeki en son değişiklik kümesini işaret eder. Sunucunun daha yeni değişiklik kümeleri olduğunda, değiştirim kümelerini sıralamak için kullanılan sıraya bağlı olarak **Yerel Sürüm** oku üstünde veya altında görünürler.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>S: CodeLens'in geçmişi ve bağlantılı öğeleri göstermek için kodu nasıl işlediğini yönetebilir miyim?

**Y:** Evet. Kodunuz TFS'deyse, [TFS Config komutuyla](/azure/devops/server/command-line/tfsconfig-cmd) [CodeIndex komutunu](../ide/codeindex-command.md) kullanın.

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>S: Çözümmü ilk açtığımda CodeLens test göstergelerim artık dosyamda görünmüyor. Nasıl yükleyebilirim?

**A:** CodeLens test göstergelerinin dosyanıza yüklenmesini sağlamak için projenizi yeniden oluşturun. Performansı artırmak için Visual Studio, kod dosyaları yüklendiğinde test göstergeleri için kaynak bilgilerini artık getirmez. Test göstergeleri bir yapıdan sonra veya **Test Gezgini'nde**çift tıklayarak bir teste gittikten sonra yüklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
