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
ms.openlocfilehash: 54054e39a9211bf63d6c187a250a47dcb1ed751c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094535"
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
|![CodeLens: alt daldan birleştirme simgesi](../ide/media/codelensbranchmergefromchildicon.png)|Alt dalından üst dala birleştirme|
|![CodeLens: ilişkisiz daldan birleştirme simgesi](../ide/media/codelensbranchmergefromunrelatedicon.png)|İlişkisiz daldan birleştirme (baseless Merge)|

## <a name="linked-work-items"></a>Bağlantılı iş öğeleri

**İş öğeleri** göstergesini seçerek veya **alt** 8 tuşlarına basarak bağlantılı iş öğelerini bulun + .

![CodeLens-belirli bir kod için iş öğelerini bul](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Bağlantılı kod İncelemeleri

**İncelemeler** göstergesini seçerek bağlantılı kod İncelemeleri bulun. Klavyeyi kullanmak için, **alt** tuşunu basılı tutarak gösterge seçeneklerinde gezinmek için **sol ok** veya **sağ ok** tuşuna basın.

![CodeLens-kod inceleme isteklerini görüntüle](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Bağlantılı hatalar

**Hata** göstergesini seçerek veya **alt** 7 tuşlarına basarak bağlantılı hataları bulun + .

![CodeLens-değişiklik kümelerine bağlı hataları bul](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Bir öğenin sahibine başvurun

**Yazarların** göstergesini seçerek veya **alt** 5 tuşlarına basarak bir öğenin yazarını bulun + .

![Bir öğenin sahibine başvurun](../ide/media/codelens-contact-item-owner.png)

İletişim seçeneklerini görmek için bir öğenin kısayol menüsünü açın. Lync veya Skype Kurumsal yüklüyse, şu seçenekleri görürsünüz:

![Öğe için iletişim seçenekleri](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>İlişkili birim testleri

C# veya Visual Basic kodunuz için var olan birim testlerini **Test gezgini**'ni açmadan keşfedebilirsiniz.

1. İlişkili [birim test koduna](../test/unit-test-your-code.md)sahip uygulama koduna gidin.

2. Henüz yapmadıysanız CodeLens test göstergelerini yüklemek için uygulamanızı derleyin.

3. Alt 3 tuşlarına basarak kodun testlerini gözden geçirin  + .

     ![CodeLens-kod düzenleyicisinde test durumu seçme](../ide/media/codelens-choose-test-indicator.png)

4. Bir uyarı simgesi görürseniz ![uyarı simgesi](../ide/media/codelenstestwarningicon.png), testler henüz çalıştırılmadı, bu nedenle onları çalıştırın.

     ![CodeLens-görünüm birimi testleri henüz çalıştırılmadı](../ide/media/codelens-tests-not-yet-run.png)

5. Bir testin tanımını gözden geçirmek için CodeLens gösterge penceresindeki test öğesine çift tıklayarak kod dosyasını düzenleyicide açın.

     ![CodeLens-birim testi tanımına git](../ide/media/codelens-unit-test-definition.png)

6. Testin sonuçlarını gözden geçirmek için, test durumu göstergesini seçin ( ![ test başarısız simgesi ](../ide/media/codelenstestfailedicon.png) veya ![ Test geçilen simge ](../ide/media/codelenstestpassedicon.png) ) veya **alt** + **1**' e basın.

     ![CodeLens-bkz. birim test sonucu](../ide/media/codelens-unit-test-result.png)

7. Bu testi değiştiren, bu testi değiştiren veya bu testte kaç tane değişiklik yapıldığını görmek için [kodunuzun geçmişini](#find-changes-in-your-code) ve bağlantılı öğelerini bulun.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Göstergeleri seçmek için klavyeyi kullanmak üzere, ilgili sayı tuşlarını göstermek için **alt** tuşuna basın ve basılı tutun, ardından seçmek istediğiniz göstergeye karşılık gelen sayıya basın.

![Klavye erişim numaraları](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> **İncelemeler** göstergesini seçmek için, sol ve sağ ok tuşlarını kullanırken gezinmek için **alt** tuşunu basılı tutun.

## <a name="q--a"></a>Soru-Cevap

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>S: CodeLens 'i kapatmak veya açmak Nasıl yaparım? veya hangi göstergeleri görmek istediğinizi seçin.

Y **:**  Başvurular göstergesi dışında, göstergeleri kapalı veya açık olarak açabilirsiniz. **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **tüm diller**  >  **CodeLens** bölümüne gidin.

Göstergeler açıldığında, göstergelerden CodeLens seçeneklerini de açabilirsiniz.

![CodeLens-göstergeleri kapatma veya açma](../ide/media/codelensturnoffonindicatorsfromcode.png)

Düzenleyici penceresinin alt köşeli ayraç simgelerini kullanarak CodeLens dosya düzeyi göstergelerini açın ve kapatın.

![Dosya düzeyi göstergelerini açma ve kapatma](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>S: CodeLens nerede?

Y **:** codelens, C# ve yöntem, sınıf, dizin oluşturucu ve özellik düzeyinde kod Visual Basic görüntülenir. CodeLens, diğer tüm dosya türleri için dosya düzeyinde görünür.

- CodeLens 'in açık olduğundan emin olun. **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **tüm diller**  >  **CodeLens** bölümüne gidin.

- Kodunuz TFS 'de depolanıyorsa, [TFS Config komutuyla](/azure/devops/server/command-line/tfsconfig-cmd) [CodeIndex komutunu](../ide/codeindex-command.md) kullanarak kod dizin oluşturma özelliğinin açık olduğundan emin olun.

- DevOps ilgili göstergeler yalnızca iş öğeleri koda bağlandığında ve bağlantılı iş öğelerini açmak için izinleriniz olduğunda görüntülenir. [Ekip üyesi izinleriniz](/azure/devops/organizations/security/view-permissions?view=vsts&preserve-view=true)olduğunu doğrulayın.

- Birim testi göstergeleri, uygulama kodu birim testlerine sahip olmadığında görünmez. Test durumu göstergeleri test projesinde otomatik olarak görüntülenir. Uygulama kodunuzun birim testleri olduğunu biliyorsanız, ancak test göstergeleri görünmüyorsa, çözümü oluşturmayı deneyin (**CTRL** + **vardiyası** + **B**).

::: moniker range=">=vs-2019"

> [!TIP]
> codelens Visual Studio Community sürümünde kullanılabilir, ancak *kaynak denetim* göstergeleri bu sürümde kullanılamaz.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> codelens Visual Studio Community sürümünde kullanılamaz.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>S: bir kayıt için iş öğesi ayrıntılarını neden görmüyorum?

Y **:** codelens Azure Boards veya TFS 'de iş öğelerini bulamadığı için bu durum oluşabilir. Bu iş öğelerinin bulunduğu projeye bağlı olduğunuzu ve bu iş öğelerini görme izinlerinizin olduğunu denetleyin. çalışma öğesi ayrıntıları, Azure Boards veya TFS 'de iş öğesi kimlikleri hakkında yanlış bilgiler içeriyorsa de görüntülenmeyebilir.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>s: Skype göstergelerini neden görmüyorum?

**A:** Skype Kurumsal oturum açmadıysanız, yüklü değilse veya desteklenen bir yapılandırmaya sahip değilseniz Skype göstergeleri görünmez. Bununla birlikte, yine de e-posta gönderebilirsiniz:

![CodeLens-posta ile kişi değişiklik kümesi sahibi](../ide/media/codelenscodesendmailchangesetnolync1.png)

**hangi Skype ve Lync yapılandırması desteklenir?**

- Skype Kurumsal (32-bit veya 64-bit)

- Lync 2010 veya sonraki bir sürümü (32-bit veya 64-bit), Windows 8.1 ile Lync temel 2013 değil

codelens, farklı Lync veya Skype sürümünün yüklü olmasını desteklemez. Visual Studio tüm yerelleştirilmiş sürümleri için yerelleştirilmemiş olabilir.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>S: Nasıl yaparım? CodeLens 'in yazı tipini ve rengini değiştirmek istiyor musunuz?

Y **:** **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **yazı tipleri ve renkler** bölümüne gidin.

![CodeLens-yazı tipi ve renk ayarlarını değiştir](../ide/media/codelensoptionsfontscolorssettings.png)

Klavyeyi kullanmak için:

1.  +  + **Seçenekler** iletişim kutusunu açmak için alt T **O** tuşlarına basın.

2. **Ortam** düğümüne gitmek Için **yukarı ok** veya **aşağı ok** tuşuna basın ve ardından düğümü genişletmek için **sol ok** tuşuna basın.

3. **Yazı tipleri ve renkler '** e gitmek Için **aşağı ok** tuşuna basın.

4. **Ayarları göster** listesine gitmek için **Tab** tuşuna basın ve ardından **CodeLens**' i seçmek için **aşağı ok** tuşuna basın.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>S: CodeLens ekran göstergesi görüntüsünü taşıyabilir miyim?

Y **:** Evet, ![ ](../ide/media/codelensdockwindow.png) CodeLens 'i pencere olarak yerleştirmek için Yerleştir simgesini seçin.

![CodeLens gösterge penceresinde Dock düğmesi](../ide/media/codelensselectdockwindow.png)

![Sabitlenmiş CodeLens başvuruları penceresi](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>S: Göstergeleri nasıl yenileyebilirim?

Y **:** Bu gösterge şunlara bağlıdır:

- **Başvurular**: Bu gösterge, kod değiştiğinde otomatik olarak güncelleştirilir. **Başvurular** göstergesi ayrı bir pencere olarak yerleştirilmişse, **Yenile**' yi seçerek göstergeyi yenileyin:

   ![CodeLens başvurularında Yenile düğmesi](../ide/media/codelensviewreferencesdocked.png)

- **Takım**: sağ tıklama menüsünde **CodeLens takım göstergelerini Yenile** ' yi seçerek bu göstergeleri yenileyin:

   ![CodeLens takım göstergeleri menü öğesini Yenile](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: **Test** göstergesini yenilemek için [kodunuzun birim testlerini bulun](#associated-unit-tests) .

### <a name="q-whats-local-version"></a>S: "Yerel sürüm" nedir?

Y **:** **Yerel sürüm** oku, bir dosyanın yerel sürümünüzde en son değişiklik kümesine işaret eder. Sunucuda daha yeni değişiklik kümeleri olduğunda, değişiklik kümelerini sıralamak için kullanılan sıralamaya bağlı olarak **Yerel sürüm** okunun üstünde veya altında görünürler.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>S: CodeLens 'in geçmişi ve bağlantılı öğeleri göstermek için kodu nasıl işlediğinde yönetebilir miyim?

**Y:** Evet. Kodunuz TFS 'de ise, [TFS Config komutuyla](/azure/devops/server/command-line/tfsconfig-cmd) [CodeIndex komutunu](../ide/codeindex-command.md) kullanın.

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>S: çözümmi ilk kez açtığımda CodeLens test göstergeleri artık dosyada görünmüyor. Bunları nasıl yükleyebilirim?

Y **:** Dosyanıza yüklenecek CodeLens test göstergeleri almak için projenizi yeniden derleyin. performansı artırmak için, kod dosyaları yüklendiğinde test göstergeleri için kaynak bilgileri artık Visual Studio. Test göstergeleri, bir derlemeden sonra yüklenir veya test **Gezgini**'nde çift tıklayarak teste gidebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
