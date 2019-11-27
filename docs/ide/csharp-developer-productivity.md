---
title: .NET geliştirme için üretkenliğinizi artırın
description: Daha iyi .NET kodu daha hızlı yazmanıza yardımcı olacak gezinti, kod analizi, birim testi ve diğer özelliklere genel bakış.
author: mikadumont
ms.author: tglee
manager: jillfra
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 5777ef318d557b85abddf35d2fbdf37a044b0ead
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491647"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Geliştiriciler için C# Visual Studio üretkenlik Kılavuzu

Visual Studio 'Nun geliştiricilerin her zamankinden daha üretken olmasını nasıl sağladığını öğrenin. Ön derlenmiş derlemelere gezinti, yazarken değişken adı önerileri, **Test+Gezgini**'nde bir hiyerarşi görünümü olan dosya/tür/üye/sembol bildirimleri, akıllı bir **özel durum Yardımcısı**, kod stili yapılandırmave zorlama ve birçok yeniden düzenlemeler ve kod düzeltmesi gibi performans ve üretkenlik geliştirmelerinden yararlanın.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Farklı bir düzenleyiciden klavye kısayolları için kullandım

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15,8 ' de yeni**

::: moniker-end

Başka bir IDE veya kodlama ortamından geliyorsanız, klavye düzeninizi *Visual Studio Code* veya *ReSharper (Visual Studio)* olarak değiştirebilirsiniz:

![Visual Studio 'da klavye şemaları](../ide/media/VS2017Guide-Keyboard.png)

Bazı uzantılar da klavye şemaları sunmaktadır:

- [Visual Studio için kısayol tuşları (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs öykünmesi](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Vsvım](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Popüler Visual Studio kısayollarından bazıları aşağıda verilmiştir:

| Kısayol (tüm profiller) | Komut | Açıklama |
|-|-|-|
| **Ctrl**+**t** | Tümüne git | Herhangi bir dosya, tür, üye veya sembol bildirimine gidin |
| **F12** (ayrıca **CTRL**+**tıklama**) | Tanıma Git | Simgenin tanımlandığı yere gitme |
| **Ctrl**+**F12** | Uygulamaya git | Temel bir türden veya Üyeden çeşitli uygulamalarına gitme |
| **Shıft**+**F12** | Tüm Başvuruları Bul | Tüm sembol veya değişmez başvuruları gör |
| **Alt**+**giriş** | Temele git | Devralma zincirinde gezin |
| **Ctrl**+ **.** (Ayrıca, C# **alt**+profile **yazın** ) | Hızlı Eylemler ve Yeniden Düzenlemeler | İmlecin konumunda veya kod seçiminde kod düzeltmelerinin, kod oluşturma eylemlerinin, yeniden düzenlemeler veya diğer hızlı eylemlerin kullanılabildiğini görün |
| **Ctrl**+**D** | Satırı Yinele | İmlecin bulunduğu kod satırını çoğaltır ( **Visual Studio 2017 sürüm 15,6** ve üzeri sürümlerde kullanılabilir) |
| **Shıft**+**Alt**+ **+** / **-** | Genişlet/sözleşme seçimi | Düzenleyicideki geçerli seçimi genişletir veya sözleşmelerini ( **Visual Studio 2017 sürüm 15,5** ve üzeri sürümlerde bulunur) |
| **Shıft** + **alt** +  **.** | Sonraki eşleşen giriş Işaretini Ekle | Geçerli seçimle eşleşen bir sonraki konuma bir seçim ve giriş işareti ekler ( **Visual Studio 2017 sürüm 15,8** ve üzeri sürümlerde kullanılabilir) |
| **Ctrl**+**Q** | Ara | Tüm Visual Studio ayarlarında ara |
| **F5** | Hata Ayıklamayı Başlat | Uygulamanızda hata ayıklamayı başlatma |
| **Ctrl**+**F5** | Hata ayıklama olmadan Çalıştır | Uygulamanızı hata ayıklama olmadan yerel olarak çalıştırma |
| **CTRL**+**K**,**d** (varsayılan profil) veya **CTRL**+**E**,**d** (C# profil) | Belgeyi Biçimlendir | Yeni satır, Aralık ve girintileme ayarlarınıza göre dosyanızdaki biçimlendirme ihlallerini temizler |
| **CTRL**+ **\\** ,**CTRL**+**E** (varsayılan profil) veya **CTRL**+**W**,**E** (C# profil) | Hata Listesi görüntüle | Belge, proje veya çözümünüzdeki tüm hataları görün |
| **Alt** + **PgUp/PgDn** | Sonraki/önceki soruna gidin | Belgenizde ( **Visual Studio 2017 sürüm 15,8** ve üzeri sürümlerde bulunur) önceki/sonraki hataya, uyarıya ve önerisine atlayın |
| **Ctrl**+**K**, **/** | Tek satır yorum/açıklama kaldır | Bu komut, seçiminizin zaten açıklama eklenmiş olmasına bağlı olarak tek satırlık yorum ekler veya kaldırır |
| **Ctrl**+**SHIFT**+ **/** | Değiştirme bloğu açıklaması/Açıklama | Bu komut, seçtiğiniz seçeneğe bağlı olarak blok açıklamalarını ekler veya kaldırır |

> [!NOTE]
> Bazı uzantılar varsayılan Visual Studio keybindings bağlantısını çözer. Yukarıdaki komutları kullanmak için, **araçlar** > **Içeri ve dışarı aktarma** > **tüm ayarları** ve **araçları** > **seçenekleri** > **klavye** > **sıfırlaması**' na giderek keybindings 'i Visual Studio 'nun varsayılan ayarlarına geri yükleyin.

Klavye kısayolları ve komutları hakkında daha fazla bilgi için bkz. [üretkenlik kısayolları](../ide/productivity-shortcuts.md) ve [popüler klavye kısayolları](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Dosyalara veya türlere hızlıca git

Visual Studio 'Nun **tümüne git** (**CTRL**+**t**) adlı bir özelliği vardır. **Tümüne git** , herhangi bir dosyaya, türe, üyeye veya sembol bildirimine hızlı bir şekilde gitmenizi sağlar.

- Bu arama çubuğunun konumunu değiştirin veya **dişli** simgesini kullanarak canlı gezinti önizlemeyi kapatın.
- `t mytype`gibi sözdizimi kullanarak sonuçları filtreleyin.
- Aramanızın kapsamını yalnızca geçerli belge olarak yapın.
- Camel büyük/küçük harf eşleştirme desteklenir.

![Visual Studio 'da tümüne git](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Kod stili kurallarını zorla

Kodlama kurallarını birlikte kullanmak ve kaynak ile seyahat etmek için bir EditorConfig dosyası kullanabilirsiniz.

![Visual Studio 'da kod stili zorlama](../ide/media/VSGuide_CodeStyle.png)

- Varsayılan bir veya ekleyin. > **Yeni öğe**Ekle ' ye tıklayarak, projenize net stil Editorconfig dosyası **ekleyin** . **Yeni öğe Ekle** iletişim kutusunda, "editorconfig" ifadesini aratın. **Editorconfig dosyası** öğe şablonlarından birini seçin ve ardından **Ekle**' yi seçin.

   ![Visual Studio 'da EditorConfig öğe şablonları](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- **Araçlar** > **seçeneklerinizde** kod stili ayarlarınıza göre otomatik olarak bir *. Editorconfig* dosyası oluşturun > **kod stili** **>** **C#** >.

   ![VS 2019 ' deki ayarlardan. editorconfig dosyası oluştur](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Visual Studio için ıntellicode 'un [kod çıkarımı özelliği](/visualstudio/intellicode/code-style-inference) , kod stillerinizi mevcut koddan algılar. Daha sonra, kod stili tercihleriniz zaten tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Bir kod stili kuralının önem düzeyini doğrudan düzenleyici aracılığıyla yapılandırın. Şu anda bir. editorconfig dosyanız yoksa, sizin için bir tane oluşturulur. İmlecinizi hata, uyarı veya öneriye yerleştirin ve **Ctrl**+yazın **.** Hızlı Eylemler ve yeniden düzenlemeler menüsünü açmak için. **Sorunları Yapılandır veya gizle**' yi seçin. Daha sonra kuralı seçin ve bu kural için yapılandırmak istediğiniz önem derecesini seçin. Bu, mevcut EditorConfig dosyanızı kuralın yeni önem derecesiyle güncelleştirir.

   ![Bir kod stili kuralının önem düzeyini doğrudan düzenleyicide yapılandırma](../ide/media/configure-severity-level.png)

[.Net kodlama kuralı seçenekleri](editorconfig-code-style-settings-reference.md) belgelerine göz atın ve bu da tüm editorconfig dosyasına bir örnek içerir.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Kod temizleme

Visual Studio kod **Temizleme** özelliği aracılığıyla kod stili tercihleri de dahil olmak üzere kod dosyanız için isteğe bağlı biçimlendirme sağlar. Kod temizlemeyi çalıştırmak için düzenleyicinin altındaki Broom simgesine tıklayın veya **ctrl**+**K**, **CTRL**+**E**tuşlarına basın.

![Visual Studio 2019 ' de kod temizleme düğmesi](media/execute-code-cleanup.png)

Ayrıca, tüm proje veya çözümünüz genelinde kod temizleme işlemini de çalıştırabilirsiniz. **Çözüm Gezgini**' de proje veya çözüm adına sağ tıklayın, **Çözümle ve kod temizleme**' yi seçin ve ardından **kod temizlemeyi Çalıştır**' ı seçin.

![Kod temizlemeyi tüm proje veya çözüm genelinde Çalıştır](media/run-code-cleanup-project-solution.png)

Dosyanızı boşluk, girintiler, et cetera için biçimlendirmeye ek olarak, **kod temizleme** de seçili kod stilleri uygular. Her kod stili için tercihleriniz, proje için bir tane varsa veya **Seçenekler** iletişim kutusundaki [kod stili ayarlarından](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) , [editorconfig dosyasından](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)okunurdur.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Yeniden düzenlemeler ve kod düzeltmeleri

Visual Studio çok sayıda yeniden düzenlemeler, kod oluşturma eylemi ve kod düzeltmesiyle birlikte gelir. Red dalgalı çizgiler hataları, yeşil dalgalı çizgiler uyarıları temsil eder ve üç gri noktayla kod önerilerini temsil eder. Ampul veya screwsürücü simgesine tıklayarak veya **Ctrl**+tuşlarına basarak kod düzeltmelere erişebilirsiniz **.** veya **Alt**+**girin**. Her bir onarım, düzeltmesinin nasıl çalıştığına ilişkin canlı bir kod farkı gösteren bir önizleme penceresiyle birlikte gelir.

Popüler hızlı düzeltmeler ve yeniden düzenlemeler şunları içerir:

- Yeniden adlandır
- Ayıklama Yöntemi
- Yöntem Imzasını Değiştir
- Oluşturucu oluştur
- Oluşturma yöntemi
- Türü dosyaya taşı
- Null denetimi Ekle
- Parametre Ekle
- Gereksiz kullanımları kaldır
- LINQ sorgusuna veya LINQ yöntemine foreach döngüsü
- Üyeleri çekme

Daha fazla bilgi için bkz. [kod oluşturma özellikleri](code-generation-in-visual-studio.md).

Kod sorunlarını işaretlemek için [FxCop çözümleyicileri yükleyebilirsiniz](../code-quality/install-fxcop-analyzers.md) . Ya da [Roslyn çözümleyicilerine](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix)sahip kendi yeniden düzenleme veya kod düzeltmesini yazın.

Birçok topluluk üyesi, ek kod İncelemeleri ekleyen ücretsiz uzantılar yazdı:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [Visual Studio için Sonarlınt](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [Stylecopçözümleyiciler](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Visual Studio 'da yeniden düzenlemeler](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Kullanımlar bulun, uygulamaya gidin ve derlenmiş derlemelere gidin

Visual Studio 'da, [kodunuzda gezinmenize ve gezinmenize](../ide/navigating-code.md)yardımcı olacak birçok özellik bulunur.

| Özellik | Kısayol | Ayrıntılar/geliştirmeler |
|- | - | -|
| Tüm Başvuruları Bul | **Shıft**+**F12**| Sonuçlar renklendirilir ve okuma veya yazma gibi proje, tanım ve başvuru türüne göre gruplanabilir. Ayrıca "kilitle" sonuçlarını da kullanabilirsiniz. |
| Uygulamaya git | **Ctrl**+**F12** | Geçersiz kılınan üyeye gitmek için `override` anahtar sözcüğüyle tanımına git ' i kullanabilirsiniz |
| Tanıma Git | **F12** veya **CTRL**+**tıklama**| Tanıma gitmek için tıklarken **CTRL** tuşuna basın |
| Tanıma göz at | **Alt**+**F12** | Bir tanım için satır içi görünüm |
| Yapı Görselleştirici | Köşeli ayraçlar arasında gri, noktalı çizgiler | Kod yapınızı görmek için üzerine gelin |
| Ayrıştırılmış derlemelere gezinti | **F12** veya **CTRL**+**tıklama** | Özelliği etkinleştirerek dış kaynak (ılspy ile derlenen) bölümüne gidin: **araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **C#**  > **Gelişmiş** > **ayrıştırılmış kaynaklara gezinmeyi etkinleştir**. |

![Tümüne git ve tüm başvuruları bul](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Geliştirilmiş IntelliSense

Yalnızca alfabetik bir liste yerine [bağlam kullanan kod tamamlamalar](/visualstudio/intellicode/intellicode-visual-studio) almak Için Visual Studio Için ıntellicode kullanın. Ayrıca, kendi etki alanına özgü kitaplıklarınızı temel alarak [özel bir IntelliSense modeli](/visualstudio/intellicode/custom-model-faq) de eğitebilirsiniz.

## <a name="unit-testing"></a>Birim testi

Visual Studio 2017 ' den başlayarak, test deneyiminde çok sayıda iyileştirme vardır. MSTest v1, MSTest v2, NUnit veya XUnit test çerçeveleri ile test edebilirsiniz.

- **Test Gezgini** test keşfi hızlıdır.

- Testleri **Test Gezgini** 'nde *hiyerarşik sıralamaya*göre düzenleyin.

   ![Visual Studio 'da metin Gezgini için hiyerarşi görünümü](../ide/media/VSGuide_Testing.png)

- [Canlı birim testi](../test/live-unit-testing.md) , kod değişikliklerinden etkilenen testleri sürekli çalıştırır ve testlerinizin durumunu bilmenizi sağlamak için satır içi düzenleyici simgelerini güncelleştirir. Canlı test kümesinden belirli testleri veya test projelerini dahil edin veya hariç tutun. (Yalnızca Visual Studio Enterprise Edition.)

## <a name="debugging"></a>Hata Ayıklama

Visual Studio 'dan bazılarının hata ayıklama özellikleri şunları içerir:

::: moniker range=">=vs-2019"

- **İzleme**, **oto**ve **Yerel öğeler** pencerelerinde dize arama özelliği.
- *' A tıklayarak*bir kod satırının yanına gelin, görüntülenen yeşil ' oynat ' simgesine basın ve bu satıra ulaşana kadar programınızı çalıştırın.
- En önemli bilgileri iletişim kutusunda en üst düzeyde (örneğin, `NullReferenceException``null` değişken) yerleştiren **özel durum Yardımcısı**.
- Önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın geçmişte bulunduğu durumu görüntülemenizi sağlayan [hata ayıklama işlemini geri](../debugger/view-historical-application-state.md)alabilirsiniz.
- Bir özel durum oluştuğunda canlı bir Web uygulamasının durumunu araştırmanıza olanak tanıyan [anlık görüntü hata ayıklaması](/azure/application-insights/app-insights-snapshot-debugger)(Azure 'da olmalıdır).

::: moniker-end

::: moniker range="vs-2017"

- *' A tıklayarak*bir kod satırının yanına gelin, görüntülenen yeşil ' oynat ' simgesine basın ve bu satıra ulaşana kadar programınızı çalıştırın.
- En önemli bilgileri iletişim kutusunda en üst düzeyde (örneğin, `NullReferenceException``null` değişken) yerleştiren **özel durum Yardımcısı**.
- Önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın geçmişte bulunduğu durumu görüntülemenizi sağlayan [hata ayıklama işlemini geri](../debugger/view-historical-application-state.md)alabilirsiniz.
- Bir özel durum oluştuğunda canlı bir Web uygulamasının durumunu araştırmanıza olanak tanıyan [anlık görüntü hata ayıklaması](/azure/application-insights/app-insights-snapshot-debugger)(Azure 'da olmalıdır).

::: moniker-end

![Visual Studio 'da özel durum Yardımcısı](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Sürüm denetimi

Visual Studio 'da kodunuzu depolamak ve güncelleştirmek için git veya TFVC kullanabilirsiniz.

::: moniker range=">=vs-2019"

- Visual Studio [Için çekme isteklerini](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) , Visual Studio 'dan çıkmadan çekme istekleri oluşturmak, gözden geçirmek, kullanıma almak ve çalıştırmak için yükler.

::: moniker-end

- [Takım Gezgini](reference/team-explorer-reference.md) 'de yerel değişikliklerinizi düzenleyin ve bekleyen işlemeler ve değişiklikleri izlemek için durum çubuğunu kullanın.

- Visual [Studio Için sürekli teslim araçları](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) uzantısı Ile Visual Studio 'nun içindeki ASP.net projeleriniz için sürekli tümleştirme ve dağıtım ayarlayın.

![Visual Studio 'da kaynak denetimi](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Ne öğrenmek gerekir?

Kod yazmayı daha verimli hale getirmek için düzenleyici ve üretkenlik özelliklerinin bir listesi aşağıda verilmiştir. Varsayılan olarak kapalı olduklarından bazı özelliklerin etkinleştirilmesi gerekebilir (bunlar makinenizde dizin oluşturabilir, controversıal veya şu anda deneysel).

| Özellik | Ayrıntılar | Nasıl etkinleştirilir |
|-|-|-|
| Dosyayı Çözüm Gezgini bul | **Çözüm Gezgini** 'de etkin dosyayı vurgular | **Araçlar** > **Seçenekler** > **Projeler ve çözümler** > **etkin öğeyi izleme Çözüm Gezgini** |
| Başvuru derlemelerindeki ve NuGet paketlerindeki türler için using 'ler ekleyin | Başvurulmayan bir tür için NuGet paketini yüklemek üzere kod düzeltmesinin bulunduğu bir hata ampul gösterir | **Araçlar** > **Seçenekler** > **metin düzenleyici** > **C#**  > **Gelişmiş** > , **başvuru derlemelerindeki türler için kullanımlar öner** ve **NuGet paketlerindeki türler için kullanımlar** öner |
| Tam çözüm analizini etkinleştirme | **Hata listesi** çözümünüzdeki tüm hataları görün | **Araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **C#**  > **Gelişmiş** > **tam çözüm analizini etkinleştir** |
| Derlenmekte olan kaynaklara gezinmeyi etkinleştir | Dış kaynaklardaki türlerde/üyelerde tanıma git 'e izin ver ve Yöntem gövdelerini göstermek için ılspy kaynak koda dönüştürücü kullanın | **Araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **C#**  > **Gelişmiş** > , **derlenen kaynaklara gezinmeyi etkinleştirir** |
| Tamamlama/öneri modu | IntelliSense 'de tamamlama davranışını değiştirir. IntelliJ arka planlarına sahip geliştiriciler burada varsayılan olmayan bir ayar kullanmaya eğilimlidir. | **Menü** > **düzenleme** > **IntelliSense** > **değiştirme moduna geç** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Düzenleyicide kod başvuru bilgilerini ve değişiklik geçmişini görüntüler. (Kaynak denetimi CodeLens göstergeleri Visual Studio Community Edition 'da kullanılamaz.) | **Araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **tüm diller** > **CodeLens** |
| [Kod parçacıkları](../ide/visual-csharp-code-snippets.md) | Ortak ortak kod saplamaya yardımcı olma | Bir kod parçacığı adı yazın ve **Tab** tuşuna iki kez basın. |
