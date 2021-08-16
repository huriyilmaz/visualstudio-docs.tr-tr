---
title: CodeLens ile kod değişikliklerini ve diğer geçmişi bulma
description: CodeLens hakkında bilgi edinin ve nasıl kullanılacağı, düzenleyiciden çıkmak zorunda kalmadan kodunuzun geçmişini keşfedebilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8c909a89cbd8268fa133bc761d7b74d335dbdfdc310304a9cbff1480082a28c6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121274403"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>CodeLens ile kod değişikliklerini ve diğer geçmişi bulma

CodeLens, Düzenleyiciden çıkmadan kodunuzda ne olduğunu öğrenirken çalışmanıza odaklanmanızı sağlar &ndash; . Kod parçasına, kodunuzda değişikliklere, bağlantılı hatalara, iş öğelerine, kod incelemelerine ve birim testlerine yönelik başvuruları bulabilirsiniz.

::: moniker range=">=vs-2019"

> [!NOTE]
> codelens Visual Studio Community sürümünde kullanılabilir, ancak *kaynak denetim* göstergeleri bu sürümde kullanılamaz.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> codelens yalnızca Visual Studio Enterprise ve Professional sürümlerinde kullanılabilir. Visual Studio Community sürümünde kullanılamaz.

::: moniker-end

Kodunuzdaki kodunuzun bağımsız bölümlerinin çözümünüzde nerede ve nasıl kullanıldığını görün:

![Kod düzenleyicisinde CodeLens göstergeleri](../ide/media/codelens-overview.png)

Düzenleyiciden çıkmadan kodunuzda değişiklikler hakkında ekibinize başvurun:

![CodeLens-ekibinize başvurun](../ide/media/codelens-contact-info.png)

Görmek istediğiniz göstergeleri seçmek veya CodeLens 'i kapatmak ve açmak için, **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **tüm diller**  >  **CodeLens** bölümüne gidin.

## <a name="find-references-to-your-code"></a>Kodunuza başvuruları bulma

başvuruları C# veya Visual Basic kodunda bulabilirsiniz.

1. **Başvurular** göstergesini seçin veya **alt** + **2**' ye basın.

   ![CodeLens başvuruları](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > gösterge **0 başvuru** gösteriyorsa, C# veya Visual Basic kodundan bir başvuruya sahip olursunuz. Ancak, *. xaml* ve *. aspx* dosyaları gibi diğer öğelerde başvurular olabilir.

2. Başvuruda bulunan kodu, listede başvuru üzerinde görüntülemek için.

   ![CodeLens-Özeti başvurusu](../ide/media/codelens-peek-reference.png)

3. Başvuruyu içeren dosyayı açmak için, başvuruya çift tıklayın.

### <a name="code-maps"></a>Kod eşlemeleri

Kod ve başvuruları arasındaki ilişkileri görmek için [bir kod haritası oluşturun](../modeling/map-dependencies-across-your-solutions.md). Kod Haritası kısayol menüsünde **tüm başvuruları göster**' i seçin.

![CodeLens-kod eşlemesindeki başvurular](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Kodunuzda değişiklik bulun

Kodunuzda ne olduğunu öğrenmek için kodunuzun geçmişini inceleyin. Ya da değişiklikleri kodunuzda birleştirilmeden önce gözden geçirin, böylece diğer dallardaki değişikliklerin kodunuzu nasıl etkileyebileceği hakkında daha iyi bir anlayışınız olabilir.

Gerekenler:

- Visual Studio Enterprise veya Professional sürümü

- Azure DevOps Services, Team Foundation Server 2013 veya üzeri ya da Git

- kod düzenleyicisinden ekibinizle iletişim kurmak için [Skype Kurumsal](/skypeforbusiness/)

C# veya Team Foundation Sürüm Denetimi (tfvc) veya Git ile depolanan Visual Basic kod için sınıf ve yöntem düzeylerinde (*kod öğesi düzeyi* göstergeler) codelens ayrıntılarını alırsınız. Git deponuz TfGit 'te barındırılıyorsa TFS iş öğelerinin bağlantılarını da alırsınız.

![Kod öğesi düzeyi göstergeleri](../ide/media/codelens-element-level-indicators.png)

*. Cs* veya *. vb* dışındaki dosya türleri için, pencerenin alt kısmındaki (*Dosya düzeyi* göstergeleri) bir yerde tüm dosyanın CodeLens ayrıntılarını alırsınız.

![Dosya düzeyi CodeLens göstergeleri](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Kod öğesi düzeyi göstergeleri

Kod öğesi düzeyi göstergeleri, kodunuzun kim tarafından değiştirildiğini ve ne değişiklikleri yaptığını görmenizi sağlar. kod öğesi düzeyindeki göstergeler C# ve Visual Basic kodu için kullanılabilir.

bu, Team Foundation Server veya Azure DevOps Services Team Foundation Sürüm Denetimi (tfvc) kullandığınızda gördüğünüz şeydir:

![CodeLens: TFVC 'de kodunuzun değişiklik geçmişini alın](../ide/media/codelens-code-changes.png)

Varsayılan süre, son 12 ay olur. kodunuz Team Foundation Server depolanıyorsa, [codeındex komutuyla](../ide/codeindex-command.md) ve **/ındexgeçmişini** bayrağıyla [TFSConfig komutunu](/azure/devops/server/command-line/tfsconfig-cmd) çalıştırarak zaman aralığını değiştirebilirsiniz.

Bir yıldan daha uzun bir süre önce dahil olmak üzere tüm değişikliklerin ayrıntılı geçmişini görmek için **tüm dosya değişikliklerini göster**' i seçin:

![Tüm kod değişikliklerini göster](../ide/media/codelens-show-all-file-changes.png)

**Geçmiş** penceresi açılır:

![Tüm kod değişiklikleri için geçmiş penceresi](../ide/media/codelenscodechangeshistory.png)

Dosyalarınız bir git deponuz olduğunda ve kod öğesi düzeyi değişiklikler göstergesini seçerseniz, bu durum aşağıdaki gibi olur:

![CodeLens: git 'teki kodunuzun değişiklik geçmişini alın](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Dosya düzeyi göstergeleri

Pencerenin alt kısmındaki dosya düzeyi göstergelerinde bir dosyanın tamamına yönelik değişiklikleri bulur:

![CodeLens: kod dosyası ayrıntılarını al](../ide/media/codelens-file-level.png)

> [!NOTE]
> dosya düzeyi göstergeleri, C# ve Visual Basic dosyaları için kullanılamaz.

Bir değişiklik hakkında daha fazla bilgi edinmek için bu öğeye sağ tıklayın. TFVC veya git kullanıyor olmanıza bağlı olarak, dosyanın sürümlerini karşılaştırma, ayrıntıları görüntüleme ve değişiklik kümesini izleme, dosyanın seçili sürümünü edinme ve bu değişikliğin yazarından e-posta ile ilgili seçenekler vardır. Bu ayrıntıların bazıları **Takım Gezgini** görüntülenir.

Ayrıca, kodunuzun zaman içinde kimin tarafından değiştirildiğini de görebilirsiniz. Bu, takımınızın değişikliklerinde desenleri bulmanıza ve etkilerini değerlendirmenize yardımcı olabilir.

![CodeLens: grafik olarak kod değişikliği geçmişine bakın](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Geçerli dalınızdaki değişiklikleri bulma

Takımınız, sabit kodu parçalara ayırma riskini azaltmak için birden çok dala (örneğin, bir ana dal ve bir alt geliştirme dalı) sahip olabilir.

![CodeLens: geçerli dalınızdaki değişiklikleri bulma](../ide/media/codelensfirstbranchconceptual.png)

Kodunuzu kaç kişinin değiştirmiş olduğunu ve ana dalda **alt** 6 tuşlarına basarak kaç değişiklik yapıldığını öğrenebilirsiniz + :

![CodeLens: dalınızda kaç değişiklik olduğunu bulun](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Kodunuzun dallanmış olduğu zaman bulun

Kodunuzun dallanmış olduğunu bulmak için alt dalda kodunuza gidin. Ardından, **değişiklikler** göstergesini seçin veya **alt** + **6** tuşlarına basın:

![CodeLens: kodunuzun dallanmış olduğu zaman bulun](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Diğer dallardan gelen değişiklikleri bulma

![CodeLens: diğer dallardaki kod değişikliklerini bulma](../ide/media/codelensbranchchangecheckinconceptual.png)

Gelen değişiklikleri görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde, "dev" dalında bir hata düzeltilme yapılmıştır:

![CodeLens: değişiklik başka bir dala iade edildi](../ide/media/codelens-branch-changes-dev.png)

Değişikliği geçerli dalından çıkmadan gözden geçirebilirsiniz ("ana"):

![CodeLens: başka bir daldan gelen değişikliğe bakın](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Değişikliklerin ne zaman birleştirildiğini bul

Değişikliklerin ne zaman birleştirildiğini görebilirsiniz, böylece dalınıza hangi değişikliklerin ekleneceğini belirleyebilirsiniz:

![CodeLens-değişikliklerin ne zaman birleştirildiğini bul](../ide/media/codelensbranchmergedconceptual.png)

Örneğin, Ana daldaki kodunuz artık "dev" dalındaki hata düzeltmesine sahiptir:

![Kod lens-dallar arasındaki değişiklikleri birleştirildi](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Yerel sürümünüzle gelen bir değişikliği karşılaştırın

**SHIFT** + **F10** tuşlarına basarak veya değişiklik kümesine çift tıklayarak gelen bir değişikliği yerel sürümünüzle karşılaştırın.

![CodeLens: gelen değişikliği yerel ile karşılaştırın](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Dal simgeleri

**Dal** sütunundaki simge, dalın çalıştığınız Dalla nasıl ilişkili olduğunu söyler.

|**Simge**|**Değişikliğin geldiği yer:**|
|--------------| - |
|![CodeLens: geçerli dal simgesinden Değiştir simgesi](../ide/media/codelensbranchcurrenticon.png)|Geçerli dal|
|![CodeLens: üst dal simgesinden değiştirme](../ide/media/codelensbranchparenticon.png)|Üst dal|
|![CodeLens: alt dal simgesinden değiştirme](../ide/media/codelensbranchchildicon.png)|Bir alt dal|
|![CodeLens: eş dalı simgesini değiştirme](../ide/media/codelensbranchpeericon.png)|Bir eş dalı|
|![CodeLens: daldan uzağa geçiş simgesi](../ide/media/codelensbranchfurtherawayicon.png)|Üst, alt veya eşten daha fazla bir dal|
|![CodeLens: üst simge ile birleştirme](../ide/media/codelensbranchmergefromparenticon.png)|Üst daldan alt dala birleştirme|
|![CodeLens: Alt daldan birleştir simgesi](../ide/media/codelensbranchmergefromchildicon.png)|Alt daldan üst dala birleştirme|
|![CodeLens: Ilgisiz daldan birleştirme simgesi](../ide/media/codelensbranchmergefromunrelatedicon.png)|Ilgisiz daldan birleştirme (temelsiz birleştirme)|

## <a name="linked-work-items"></a>Bağlantılı iş öğeleri

İş öğeleri göstergesini seçerek veya Alt 8 tuşuna basarak bağlı **iş** öğelerini  + **bulun.**

![CodeLens - Belirli bir kod için iş öğelerini bulma](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Bağlantılı kod incelemeleri

İnceleme göstergesini seçerek bağlı kod **incelemelerini** bulun. Klavyeyi kullanmak için Alt tuşunu **basılı** tutun ve ardından Gösterge **seçeneklerine gitmek için** Sol ok **veya** Sağ ok tuşlarına basın.

![CodeLens - Kod inceleme isteklerini görüntüleme](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Bağlantılı hatalar

Hata göstergesini seçerek veya **Alt** 7 **tuşuna** basarak bağlantılı + **hataları bulun.**

![CodeLens - Değişiklik kümeleri ile bağlantılı hataları bulma](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Bir öğenin sahibine ulaşın

Yazar göstergesini seçerek veya Alt 5 **tuşuna** basarak bir **öğenin** + **yazarını bulun.**

![Bir öğenin sahibine ulaşın](../ide/media/codelens-contact-item-owner.png)

Kişi seçeneklerini görmek için bir öğenin kısayol menüsünü açın. Lync veya Skype Kurumsal yüklüyse şu seçenekleri görüyorsanız:

![Bir öğe için iletişim seçenekleri](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>İlişkili birim testleri

Test Gezgini'ni açmadan C# veya Visual Basic birim **testlerini keşfedebilirsiniz.**

1. İlişkili birim testi kodunun olduğu [uygulama koduna gidin.](../test/unit-test-your-code.md)

2. Henüz oluşturmadısanız, CodeLens test göstergelerini yüklemek için uygulamanızı derlemeniz gerekir.

3. Alt 3 tuşuna basarak **kodun** + **testlerini gözden geçirme.**

     ![CodeLens - Kod düzenleyicisinde test durumunu seçme](../ide/media/codelens-choose-test-indicator.png)

4. Uyarı simgesi görüyorsanız ![uyarı simgesi](../ide/media/codelenstestwarningicon.png), testleri henüz çalıştırmadı, bu nedenle çalıştırın.

     ![CodeLens - Birim testlerini görüntüleme henüz çalıştırlanmadı](../ide/media/codelens-tests-not-yet-run.png)

5. Bir testin tanımını gözden geçirmek için CodeLens gösterge penceresinde test öğesini çift tıklatın ve kod dosyasını düzenleyicide açın.

     ![CodeLens - Birim testi tanımına gidin](../ide/media/codelens-unit-test-definition.png)

6. Testin sonuçlarını gözden geçirmek için test durumu göstergesini (test başarısız oldu simgesi veya test başarılı simgesi ) seçin ![ ](../ide/media/codelenstestfailedicon.png) veya Alt ![ ](../ide/media/codelenstestpassedicon.png)  + **1'e basın.**

     ![CodeLens - Birim testi sonucuna bakın](../ide/media/codelens-unit-test-result.png)

7. Bu testi kaç kişinin değiştirdiğini, bu testi kimin değiştirdiğini veya bu testte kaç değişiklik yapılmış olduğunu görmek için kodunuzun geçmişini [ve bağlantılı](#find-changes-in-your-code) öğelerini bulun.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Klavyeyi kullanarak göstergeleri seçmek için **Alt** tuşuna basın ve basılı tutun. İlgili sayı tuşlarını görüntülemek için, ardından seçmek istediğiniz göstergeye karşılık gelen sayıya basın.

![Klavye erişim numaraları](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> İnceleme göstergesini **seçmek** için sol ve **sağ** ok tuşlarını kullanarak Alt tuşunu basılı tutun.

## <a name="q--a"></a>Soru-Cevap

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>S: Nasıl yaparım? CodeLens'i kapatıyor veya açıyor veya hangi göstergelerin göreceğini seçiyor?

**A:**  Başvuru göstergesi dışında göstergeleri kapatarak veya açarak açabileceksiniz. Araçlar Seçenekler **Metin**  >    >  **Düzenleyici Tüm Diller**  >  **CodeLens**  >  **'e gidin.**

Göstergeler açık olduğunda, göstergelerden CodeLens seçeneklerini de açabilirsiniz.

![CodeLens - Göstergeleri kapatma veya açma](../ide/media/codelensturnoffonindicatorsfromcode.png)

Düzenleyici penceresinin altındaki köşeli çift ayraç simgelerini kullanarak CodeLens dosya düzeyi göstergelerini açın ve kapatın.

![Dosya düzeyi göstergelerini açma ve kapatma](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>S: CodeLens nerede?

**A:** CodeLens C# içinde görünür ve Visual Basic, sınıf, dizin ve özellik düzeyinde kod kullanır. CodeLens, diğer tüm dosya türleri için dosya düzeyinde görünür.

- CodeLens'in açık olduğundan emin olun. Araçlar Seçenekler **Metin**  >    >  **Düzenleyici Tüm Diller**  >  **CodeLens**  >  **'e gidin.**

- Kodunuz TFS'de depolanıyorsa, TFS Config komutuyla [CodeIndex](../ide/codeindex-command.md) komutu kullanılarak kod dizininin açık [olduğundan emin olun.](/azure/devops/server/command-line/tfsconfig-cmd)

- DevOps ilgili göstergeler yalnızca iş öğeleri koda bağlı olduğunda ve bağlantılı iş öğelerini açma izinlerine sahip olduğunda görünür. Takım üyesi izinlerine [sahip olduğunu onaylayın.](/azure/devops/organizations/security/view-permissions?view=vsts&preserve-view=true)

- Uygulama kodunda birim testi olmayan birim testi göstergeleri görünmez. Test durumu göstergeleri test projesinde otomatik olarak görüntülenir. Uygulama kodunuzun birim testleri olduğunu biliyorsanız ancak test göstergeleri görünmüyorsa, çözümü (**Ctrl Shift** B ) + **oluşturmak için bunu** + **deneyin.**

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens, Visual Studio Community sürümde kullanılabilir, ancak  kaynak denetim göstergeleri bu sürümde kullanılamaz.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens, Visual Studio Community kullanılamaz.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>S: Bir işlemenin iş öğesi ayrıntılarını neden göremiyorum?

**A:** CodeLens, TFS'de veya TFS'de iş Azure Boards olabilir. Bu iş öğelerine sahip projeye bağlı olduğunuzdan ve bu iş öğelerini görme izinlerine sahip olduğunuzdan emin olun. İş öğesi ayrıntıları, işleme açıklamasında TFS veya TFS'de iş öğesi kimlikleri hakkında yanlış Azure Boards gösternemebilirsiniz.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>S: Neden Skype göremiyorum?

**A:** Skype oturum Skype Kurumsal yüklü değil veya desteklenen bir yapılandırmanız yoksa bu göstergeler görünmez. Ancak yine de e-posta gönderebilirsiniz:

![CodeLens - Değişiklik kümesi sahibiyle e-postaya göre iletişim kurma](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Hangi Skype ve Lync yapılandırmaları de destekler?**

- Skype Kurumsal (32 bit veya 64 bit)

- Lync 2010 veya sonraki bir tek başına (32 bit veya 64 bit), ancak lync basic 2013 Windows 8.1

CodeLens, Lync veya Skype sürümlerinin yüklü Skype desteklemez. Bu sürümler tüm yerelleştirilmiş sürümler için yerelleştirilmiş Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>S: Nasıl yaparım? codeLens için yazı tipini ve rengini nasıl değiştirebilirsiniz?

**A:** Araçlar Seçenekler **Ortam**  >  **Yazı Tipleri**  >  **ve**  >  **Renkler'e gidin.**

![CodeLens - Yazı tipi ve renk ayarlarını değiştirme](../ide/media/codelensoptionsfontscolorssettings.png)

Klavyeyi kullanmak için:

1. Seçenekler **iletişim** kutusunu açmak için Alt + **T** + **O** **tuşuna** basın.

2. Ortam **düğümüne** gitmek **için Yukarı** Ok'a veya Aşağı Ok'a basın, sonra düğümü genişletmek için Sol **Ok'a** basın. 

3. Yazı **Tipleri ve Renkler'e** gitmek için Aşağı **Ok tuşuna basın.**

4. Sekme **tuşuna** basarak **Listenin ayarlarını göster'e** gidin ve ardından CodeLens'i **seçmek için** Aşağı Ok **tuşuna basın.**

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>S: CodeLens ekran göstergesi görüntüsünü taşıyabilir miyim?

**A:** Evet, ![ ](../ide/media/codelensdockwindow.png) CodeLens'i pencere olarak yerleştirmek için Dock simgesi seçin.

![CodeLens gösterge penceresindeki Dock düğmesi](../ide/media/codelensselectdockwindow.png)

![Yerleştirildi CodeLens Başvuruları penceresi](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>S: Göstergeleri nasıl yenileyebilirim?

**A:** Bu göstergeye bağlıdır:

- **Başvurular:** Kod değişirken bu gösterge otomatik olarak ler. Başvurular **göstergesi** ayrı bir pencere olarak yerleştirildi ise Yenile'yi seçerek göstergeyi **yenileyin:**

   ![Yenile düğmesi CodeLens Başvurularında](../ide/media/codelensviewreferencesdocked.png)

- **Takım:** Sağ tıklama menüsünden **CodeLens Takım** Göstergelerini Yenile'yi seçerek bu göstergeleri yenileyin:

   ![CodeLens Takım Göstergeleri menü öğesini yenileme](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test:** [Test göstergesini yenilemek için kodunuz](#associated-unit-tests) için birim **testleri** bulun.

### <a name="q-whats-local-version"></a>S: "Yerel Sürüm" nedir?

**A:** Yerel **Sürüm oku,** bir dosyanın yerel sürümündeki en son değişiklik kümesine bakarak. Sunucuda daha yeni değişiklik kümeleri olduğunda, değişiklik  kümeleri sıralamak için kullanılan sıraya bağlı olarak Yerel Sürüm okunda veya altında görünürler.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>S: CodeLens'in geçmişi ve bağlantılı öğeleri göstermek için kodu nasıl işleyeni yönetmesine izin verilsin mi?

**Y:** Evet. Kodunuz TFS'de ise, TFS Config [komutuyla CodeIndex](../ide/codeindex-command.md) [komutunu kullanın.](/azure/devops/server/command-line/tfsconfig-cmd)

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>S: Çözümüm ilk kez açılırken CodeLens test göstergelerim artık dosyamda görünmüyor. Bunları nasıl yükleyim?

**A:** CodeLens test göstergelerini dosyanıza yüklemek için projenizi yeniden oluşturma. Performansı artırmak Visual Studio artık kod dosyaları yüklendiğinde test göstergelerinin kaynak bilgilerini getirmez. Test göstergeleri bir derlemeden sonra veya Test Gezgini'nde üzerine çift tıklayarak bir teste **gidildikten sonra yüklenir.**

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
