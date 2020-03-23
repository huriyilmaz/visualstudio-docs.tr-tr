---
title: .NET geliştirme için üretkenliğinizi artırın
description: Daha iyi .NET kodunu daha hızlı yazmanıza yardımcı olacak gezinti, kod analizi, birim testi ve diğer özelliklere genel bakış.
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 0aa8e19f2be78671587dd1d9bc6254306c82a78c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567508"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>C# geliştiricileri için Visual Studio üretkenlik kılavuzu

Visual Studio'nun geliştiricileri her zamankinden daha üretken hale nasıl kdığını öğrenin. Derlenmiş derlemelere gezinme, yazarken değişken ad önerileri, **Test Explorer'da**bir hiyerarşi görünümü , Dosya/tür/üye/sembol bildirimleri, akıllı Bir **Özel Durum Yardımcısı,** kod stili yapılandırma ve zorlama ve birçok refactoring ve kod düzeltmelerine gitmek için Tümüne Git (**Ctrl**+**T**) gibi performans ve üretkenlik iyileştirmelerimizden yararlanın.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Farklı bir editörden klavye kısayolları için kullanılır

::: moniker range="vs-2017"

**Visual Studio 2017 sürümünde yeni sürüm 15.8**

::: moniker-end

Başka bir IDE veya kodlama ortamından geliyorsanız, klavye düzeninizi *Visual Studio Code* veya *ReSharper (Visual Studio)* olarak değiştirebilirsiniz:

![Visual Studio'da Klavye Şemaları](../ide/media/VS2017Guide-Keyboard.png)

Bazı uzantılar klavye şemaları da sunar:

- [Visual Studio için HotKeys (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs Öykünme](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Popüler Visual Studio kısayolları şunlardır:

| Kısayol (Tüm Profiller) | Komut | Açıklama |
|-|-|-|
| **Ctrl**+**T** | Tümüne Git | Herhangi bir dosyaya, türe, üyeye veya sembol bildirimine gidin |
| **F12** (ayrıca **Ctrl**+**Tıklayın)** | Tanıma Git | Sembolün tanımlandığı yere gidin |
| **Ctrl**+**F12** | Uygulamaya Git | Bir taban türünden veya üyeden çeşitli uygulamalarına gidin |
| **Shift**+**F12** | Tüm Başvuruları Bul | Tüm simge veya gerçek referansları görün |
| **Alt**+**Ana Sayfa** | Temele Git | Devralma zincirinde gezinme |
| **Ctrl**+**.** (ayrıca **Alt**+C# Profiline**Girin)** | Hızlı Eylemler ve Yeniden Düzenlemeler | İmleç konumunuzda veya kod seçiminizde hangi kod düzeltmelerinin, kod oluşturma eylemlerinin, yeniden faktörlerin veya diğer hızlı eylemlerin kullanılabilenleri görün |
| **Ctrl**+**D** | Yinelenen satır | İmlecin içinde bulunduğu kod satırını yineler **(Visual Studio 2017 sürüm 15.6** ve sonraki sürümde kullanılabilir) |
| **Vardiya**+**Alt**+**+**/**-** | Genişletme/Sözleşme seçimi | Editördeki mevcut seçimi genişletir veya sözleşmeler **(Visual Studio 2017 sürüm 15.5** ve sonrası sürümde mevcuttur) |
| **Shift** + **Alt** + **.** | Sonraki Eşleşen Caret ekle | Geçerli seçimle eşleşen bir sonraki konuma bir seçim ve bakım ekler **(Visual Studio 2017 sürüm 15.8** ve sonraki sürümde mevcuttur) |
| **Ctrl**+**Q** | Search | Tüm Visual Studio ayarlarını ara |
| **F5** | Hata Ayıklama'yı Başlatma | Uygulamanızın hata ayıklama başlatma |
| **Ctrl**+**F5** | Hata Ayıklama olmadan çalıştırın | Hata ayıklama yapmadan uygulamanızı yerel olarak çalıştırın |
| **Ctrl**+**K**,**D** (Varsayılan Profil) veya **Ctrl**+**E**,**D** (C# Profili) | Belgeyi Biçimlendir | Yeni hattınız, boşluk ve girintinasyon ayarlarınıza göre dosyanızdaki biçimlendirme ihlallerini temizler |
| **Ctrl**+**\\**,**Ctrl**+**E** (Varsayılan Profil) veya **Ctrl**+**W**,**E** (C# Profili) | Hata Listesini Görüntüle | Belge, proje veya çözümünüzdeki tüm hataları görme |
| **Alt** + **PgUp/PgDn** | Sonraki/Önceki Sayıya Git | Belgenizdeki önceki/sonraki hataya, uyarıya, öneriye atlayın **(Visual Studio 2017 sürüm 15.8** ve sonraki sürümde mevcuttur) |
| **Ctrl**+**K**,**/** | Tek satırlı yorumu/yorum suz'u değiştirme | Bu komut, seçiminizin zaten yorumlanıp yorumlanmayacağına bağlı olarak tek bir satır yorumu ekler veya kaldırır |
| **Ctrl**+**Kaydırma**+**/** | Engelleme açıklama/yorum değiştirme değiştirme | Bu komut, seçtiğiniz şeye bağlı olarak blok açıklamaları ekler veya kaldırır |

> [!NOTE]
> Bazı uzantılar varsayılan Visual Studio anahtar bağlamalarını unbind. Yukarıdaki komutları kullanmak için, **Araçlar** > **Alma ve Dışa Aktarma Ayarları'na** > giderek tuş bağlaçlarınızı Visual Studio'nun varsayılanlarına geri yükleyin tüm ayarları veya **Araç** > **Seçenekleri** > **Klavye** > **Sıfırlama'yı****sıfırlayın.**

Klavye kısayolları ve komutları hakkında daha fazla bilgi için [Üretkenlik kısayolları](../ide/productivity-shortcuts.md) ve [Popüler klavye kısayolları'na](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)bakın.

## <a name="navigate-quickly-to-files-or-types"></a>Dosyalara veya türlere hızla gidin

Visual Studio'nun **Go To All** **(Ctrl**+**T)** adlı bir özelliği vardır. **Tüme Git,** herhangi bir dosyaya, yazıya, üyeye veya sembol bildirimine hızla atlamanızı sağlar.

- Bu arama çubuğunun konumunu değiştirin veya **vites** simgesini kullanarak canlı gezinme önizlemesini kapatın.
- Sonuçları ' gibi `t mytype`sözdizimi kullanarak filtreleyin.
- Aramanızı yalnızca geçerli belgeye göre kapsamda tarayın.
- Deve kılıfı eşleştirmesi desteklenir.

![Visual Studio'da Herkese Git](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Kod stili kurallarını zorlama

Kodlama kurallarını kodlamak ve kaynağınızla birlikte seyahat etmelerini sağlamak için bir EditorConfig dosyası kullanabilirsiniz.

![Visual Studio'da kod stili uygulaması](../ide/media/VSGuide_CodeStyle.png)

- Varsayılan veya . Net tarzı EditorConfig dosyasını yeni**öğe**ekle'yi seçerek projenize **ekleyin.** >  Yeni **Öğe Ekle** iletişim kutusunda "editorconfig" araması yapın. **Editorconfig Dosya** öğesi şablonlarından birini seçin ve sonra **Ekle'yi**seçin.

   ![Visual Studio'da EditorConfig öğe şablonları](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- > **Araçlar** > > **Code Style** **Options** **Text Editor** *.editorconfig* > Seçenekleri Metin **Düzenleyicisi C#** Kod Stili'nde kod stili ayarlarınızı temel alan bir .editorconfig dosyası otomatik olarak oluşturun.

   ![VS 2019'daki ayarlardan .editorconfig dosyası oluşturma](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- IntelliCode for Visual Studio'nun [kod çıkarım özelliği,](/visualstudio/intellicode/code-style-inference) kod stillerinizi varolan koddan çıkarır. Daha sonra zaten tanımlanmış kod stili tercihleri ile boş olmayan bir EditorConfig dosyası oluşturur.

- Kod stili kuralının önem düzeyini doğrudan düzenleyici aracılığıyla yapılandırın. Şu anda bir .editorconfig dosyanız yoksa, sizin için bir dosya oluşturulur. İmlecinizi hata, uyarı veya öneri üzerine yerleştirin ve **Ctrl**+**yazın.** Hızlı Eylemler ve Refactorings menüsünü açmak için. **Sorunları Yapılandır veya Bastır'ı**seçin. Daha sonra kuralı seçin ve bu kural için yapılandırmak istediğiniz önem derecesini seçin. Bu, mevcut EditorConfig dosyanızı kuralın yeni önem derecesiyle güncelleştirir.

   ![Kod stili kuralının önem düzeyini doğrudan düzenleyicide yapılandırma](../ide/media/configure-severity-level.png)

Tam bir EditorConfig dosyasının örneğini de içeren [.NET kodlama kuralı seçenekleri](editorconfig-code-style-settings-reference.md) belgelerine göz atın.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Kod Temizleme

Visual Studio, **Kod Temizleme** özelliği aracılığıyla kod stili tercihleri de dahil olmak üzere kod dosyanızın isteğe bağlı biçimlendirmesini sağlar. Kod Temizleme'yi çalıştırmak için, düzenleyicinin altındaki süpürge simgesine tıklayın veya **Ctrl**+**K**, **Ctrl**+**E**tuşuna basın.

![Visual Studio 2019'da Kod Temizleme düğmesi](media/execute-code-cleanup.png)

Ayrıca tüm projeveya çözüm genelinde kod temizleme çalıştırabilirsiniz. **Çözüm Gezgini'nde**proje veya çözüm adına sağ tıklayın, **Analiz ve Kod Temizleme'yi**seçin ve ardından Kodu **Temizlemeyi Çalıştır'ı**seçin.

![Tüm Proje veya Çözüm De Kod Temizleme Çalıştır](media/run-code-cleanup-project-solution.png)

Dosyanızı boşluklar, girintiler ve saire için biçimlendirmenin yanı **sıra, Kod Temizleme** de seçili kod stilleri uygular. Her kod stili için tercihleriniz [EditorConfig dosyasından](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), proje için varsa veya **Seçenekler** iletişim kutusundaki kod [stili ayarlarından](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) okunur.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refactorings ve kod düzeltmeleri

Visual Studio çok sayıda refactorings, kod oluşturma eylemleri ve kod düzeltmeleri ile birlikte gelir. Kırmızı dalgalı hatalar hataları, yeşil dalgalı geçişler uyarıları temsil eder ve üç gri nokta kod önerilerini temsil eder. Ampul veya tornavida simgesine tıklayarak veya **Ctrl**+tuşuna basarak kod düzeltmeleri erişebilirsiniz.**.** veya **Alt**+**Girin.** Her düzeltme, düzeltmenin nasıl çalıştığını gösteren bir önizleme penceresiyle birlikte gelir.

Popüler hızlı düzeltmeler ve refactorings şunlardır:

- Yeniden Adlandır
- Ayıklama Yöntemi
- Metot İmzasını Değiştirme
- Yapıcı Oluştur
- Yöntem Oluştur
- Türü Dosyaya Taşı
- Null-Check ekle
- Parametre Ekle
- Gereksiz Usings'i kaldırma
- Foreach Loop'dan LINQ Sorgusuna veya LINQ yöntemine
- Üyeleri Yukarı Çek

Daha fazla bilgi için [kod oluşturma özelliklerine](code-generation-in-visual-studio.md)bakın.

Kod sorunlarını işaretlemek için [FxCop çözümleyicilerini yükleyebilirsiniz.](../code-quality/install-fxcop-analyzers.md) Veya, [Roslyn analizörleri](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix)ile kendi refactoring veya kod düzeltme yazın.

Birkaç topluluk üyesi ek kod denetimleri eklemek ücretsiz uzantıları yazdım:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [Görsel Stüdyo için SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Visual Studio'da Yeniden Düzenleme](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Kullanımları Bul, Uygulamaya Git ve Derlenmiş Derlemelere Git

Visual Studio arama ve kod [gezinmek](../ide/navigating-code.md)yardımcı olmak için birçok özelliğe sahiptir.

| Özellik | Kısayol | Ayrıntılar / Geliştirmeler |
|- | - | -|
| Tüm Başvuruları Bul | **Shift**+**F12**| Sonuçlar renklendirilmiştir ve okuma veya yazma gibi proje, tanım ve başvuru türüne göre gruplandırılabilir. Ayrıca sonuçları "kilitleyebilirsiniz". |
| Uygulamaya Git | **Ctrl**+**F12** | Geçersiz kılınan üyeye `override` gitmek için anahtar kelimede Tanıma Git'i kullanabilirsiniz |
| Tanıma Git | **F12** veya **Ctrl**+**Tıklayın**| Tanıma gitmek için tıklatırken **Ctrl** tuşuna basın |
| Tanıma Göz At | **Alt**+**F12** | Tanımın satır satır görünümü |
| Yapı Görselleştiricisi | Ayraçlar arasında gri, noktalı çizgiler | Kod yapınızı görmek için gezinme |
| Derlenmiş derlemelere gezinme | **F12** veya **Ctrl**+**Tıklayın** | Özelliği etkinleştirerek harici kaynağa (ILSpy ile derlenmiş) gidin: **Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **C#** > **Gelişmiş** > **Decompiled kaynaklara navigasyon etkinleştirin.** |

![Tüme Git ve Tüm Referansları Bul](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Geliştirilmiş IntelliSense

Sadece alfabetik bir liste yerine [içeriğe duyarlı kod tamamlamaları](/visualstudio/intellicode/intellicode-visual-studio) almak için Visual Studio için IntelliCode'u kullanın. Ayrıca, kendi etki alanınıza özel kitaplıklarınıza dayalı özel bir [IntelliSense modeli](/visualstudio/intellicode/custom-model-faq) de eğitebilirsiniz.

## <a name="unit-testing"></a>Birim testi

Visual Studio 2017'den itibaren test deneyiminde çok sayıda gelişme vardır. MSTest v1, MSTest v2, NUnit veya XUnit test çerçeveleri ile test edebilirsiniz.

- **Test Explorer** test bulma hızlıdır.

- Hiyerarşik sıralama ile **Test Gezgini'nde** testlerinizi *düzenleyin.*

   ![Visual Studio'da Metin Gezgini için hiyerarşi görünümü](../ide/media/VSGuide_Testing.png)

- [Canlı birim testi,](../test/live-unit-testing.md) testlerinizin durumunu bilmenizi sağlamak için kod değişiklikleriniz ve güncelleştirmeleri satır başı düzenleyici simgelerinizden etkilenen testleri sürekli olarak çalıştırıyor. Canlı test setinizden belirli testleri veya test projelerini ekleyin veya hariç tayın. (Yalnızca Visual Studio Enterprise sürümü.)

## <a name="debugging"></a>Hata ayıklama

Visual Studio'nun hata ayıklama özelliklerinden bazıları şunlardır:

::: moniker range=">=vs-2019"

- **Watch,** **Autos**ve **Locals** pencerelerinde bir dize arama yeteneği.
- Bir kod satırının yanında gezinmenizi, görünen yeşil 'oynatma' simgesine basmanızı ve programınızı bu *satıra*ulaşana kadar çalıştırmanızı sağlayan tıklatmak için çalıştırın.
- **Özel Durum Yardımcısı**, iletişim kutusunda en önemli bilgileri en üst düzeye koyar, örneğin, hangi değişken `null` bir `NullReferenceException`.
- Önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın durumunu geçmişte olduğu gibi görüntülemenizi sağlayan hata ayıklama yı [adım atın.](../debugger/view-historical-application-state.md)
- [Anlık hata ayıklama,](/azure/application-insights/app-insights-snapshot-debugger)bir özel durum atıldığı anda canlı bir web uygulamasının durumunu araştırmanızı sağlayan (Azure'da olmalıdır).

::: moniker-end

::: moniker range="vs-2017"

- Bir kod satırının yanında gezinmenizi, görünen yeşil 'oynatma' simgesine basmanızı ve programınızı bu *satıra*ulaşana kadar çalıştırmanızı sağlayan tıklatmak için çalıştırın.
- **Özel Durum Yardımcısı**, iletişim kutusunda en önemli bilgileri en üst düzeye koyar, örneğin, hangi değişken `null` bir `NullReferenceException`.
- Önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın durumunu geçmişte olduğu gibi görüntülemenizi sağlayan hata ayıklama yı [adım atın.](../debugger/view-historical-application-state.md)
- [Anlık hata ayıklama,](/azure/application-insights/app-insights-snapshot-debugger)bir özel durum atıldığı anda canlı bir web uygulamasının durumunu araştırmanızı sağlayan (Azure'da olmalıdır).

::: moniker-end

![Visual Studio'da Özel Durum Yardımcısı](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Sürüm denetimi

Visual Studio'da kodunuzu depolamak ve güncellemek için git veya TFVC'yi kullanabilirsiniz.

::: moniker range=">=vs-2019"

- Visual Studio'dan ayrılmadan çekme isteklerini oluşturmak, gözden geçirmek, kullanıma almak ve çalıştırmak [için Visual Studio için Çekme isteklerini](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) yükleyin.

::: moniker-end

- Yerel değişikliklerinizi [Team Explorer'da](reference/team-explorer-reference.md) düzenleyin ve bekleyen taahhütleri ve değişiklikleri izlemek için durum çubuğunu kullanın.

- Visual Studio uzantısı için [Sürekli teslimat araçları](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) ile Visual Studio içinde ASP.NET projeleriniz için sürekli entegrasyon ve teslimat ayarlayın.

![Visual Studio'da kaynak kontrolü](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Başka hangi özellikler hakkında bilmem gerekir?

Burada kod yazmayı daha verimli hale getirmek için editör ve verimlilik özelliklerinin bir listesi. Bazı özelliklerin etkinleştirilmesi gerekebilir, çünkü varsayılan olarak kapalıdırlar (makinenizdeki şeyleri dizine ekleyebilirler, tartışmalıdırlar veya şu anda deneyseldirler).

| Özellik | Ayrıntılar | Nasıl etkinleştirilir? |
|-|-|-|
| Çözüm Gezgini'nde Dosyayı Bul | **Solution Explorer'daki** etkin dosyayı vurgular | **Araç** > **Seçenekleri** > **Projeler ve Çözümler** > **Çözüm Gezgini'nde Etkin Öğeyi Takip Eder** |
| Referans derlemeleri ve NuGet paketlerindeki türler için usingekleme | Başvuruedilmeyen bir tür için NuGet paketini yüklemek için kod düzeltmesi olan bir hata ampulü gösterir | **Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **C#** > **Advanced** > **Referans derlemelerinde türleri için kullanır** öner ve **NuGet paketlerindeki türler için kullanma öner** |
| Tam çözüm analizini etkinleştirme | **Hata Listesinde** çözümünüzdeki tüm hataları görün | **Araçlar** > **Seçenekleri** > Metin**Düzenleyicic#** > **Text Editor** > **Gelişmiş** > **Tam çözüm analizini etkinleştir** |
| Decompiled kaynakları için gezinmeyi etkinleştirme | Dış kaynaklardan türleri / üyeleri üzerinde Tanım git ve yöntem gövdeleri göstermek için ILSpy decompiler kullanın | **Araçlar** > **Seçenekleri** > Metin**Düzenleyicic#** > **Text Editor** > **Gelişmiş** > **Decompiled kaynaklara navigasyon etkinleştirme** |
| Tamamlama/Öneri Modu | IntelliSense'de tamamlama davranışını değiştirir. IntelliJ arka plana sahip geliştiriciler burada varsayılan olmayan bir ayar kullanma eğilimindedir. | **Menü** > **Dele** > **IntelliSense** > Geçiş Tamamlama**Modu** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Editörde kod başvuru bilgilerini görüntüler ve geçmişi değiştirir. (Kaynak kontrol CodeLens göstergeleri Visual Studio Community sürümünde kullanılamaz.) | **Araçlar** > **Seçenekleri** > **Metin Editörü** > **Tüm Diller** > **CodeLens** |
| [Kod parçacıkları](../ide/visual-csharp-code-snippets.md) | Ortak ortak plaka kodunun saplatın | Bir parçacık adı yazın ve **Sekme'ye** iki kez basın. |
