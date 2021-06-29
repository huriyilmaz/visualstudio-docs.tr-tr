---
title: .NET geliştirme için üretkenliğinizi artırın
description: Daha iyi .NET kodu daha hızlı yazmanıza yardımcı olacak gezinti, kod analizi, birim testi ve diğer özelliklere genel bakış.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 09a33db9df8e1309792cd6a3722bb82333348d84
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038661"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>C# geliştiricileri için Visual Studio üretkenlik Kılavuzu

Visual Studio 'Nun geliştiricilerin her zamankinden daha üretken olmasını nasıl sağladığını öğrenin. Ön derlenmiş derlemelere gezinti, yazarken değişken adı önerileri, **Test Gezgini**'nde bir hiyerarşi görünümü, + bir akıllı **özel durum Yardımcısı**, kod stili yapılandırma ve zorlama ve birçok yeniden düzenlemeler ve kod düzeltmesi gibi performans ve üretkenlik geliştirmelerinden yararlanın...

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
| **CTRL** + **T** | Tümüne git | Herhangi bir dosya, tür, üye veya sembol bildirimine gidin |
| **F12** (Ayrıca **CTRL**+ + **tıklama**) | Tanıma Git | Simgenin tanımlandığı yere gitme |
| **CTRL** + **F12** | Uygulamaya git | Temel bir türden veya Üyeden çeşitli uygulamalarına gitme |
| **SHIFT** + **F12** | Tüm Başvuruları Bul | Tüm sembol veya değişmez başvuruları gör |
| **Alt** + **Giriş sayfası** | Temele Git | Devralma zincirinde gezin |
| **CTRL** + **.** (Ayrıca **alt** + C# profilinde **girin** ) | Hızlı Eylemler ve Yeniden Düzenlemeler | İmlecin konumunda veya kod seçiminde kod düzeltmelerinin, kod oluşturma eylemlerinin, yeniden düzenlemeler veya diğer hızlı eylemlerin kullanılabildiğini görün |
| **CTRL** + **D** | Yinelenen satır | İmlecin bulunduğu kod satırını çoğaltır ( **Visual Studio 2017 sürüm 15,6** ve üzeri sürümlerde kullanılabilir) |
| **SHIFT** + **Alt**+**+**/**-** | Genişlet/sözleşme seçimi | Düzenleyicideki geçerli seçimi genişletir veya sözleşmelerini ( **Visual Studio 2017 sürüm 15,5** ve üzeri sürümlerde bulunur) |
| **SHIFT**  +  **Alt**  +  **.** | Sonraki eşleşen giriş Işaretini Ekle | Geçerli seçimle eşleşen bir sonraki konuma bir seçim ve giriş işareti ekler ( **Visual Studio 2017 sürüm 15,8** ve üzeri sürümlerde kullanılabilir) |
| **CTRL** + **Soru-cevap** | Arayın | Tüm Visual Studio ayarlarında ara |
| **F5** | Hata ayıklamayı Başlat | Uygulamanızda hata ayıklamayı başlatma |
| **CTRL** + **F5** | Hata ayıklama olmadan Çalıştır | Uygulamanızı hata ayıklama olmadan yerel olarak çalıştırma |
| **CTRL** + **K**,**d** (varsayılan profil) veya **CTRL** + **E**,**D** (C# profili) | Belgeyi Biçimlendir | Yeni satır, Aralık ve girintileme ayarlarınıza göre dosyanızdaki biçimlendirme ihlallerini temizler |
| **CTRL** + **\\** ,**CTRL** + **E** (varsayılan profil) veya **CTRL** + **W**,**E** (C# profili) | Hata Listesi görüntüle | Belge, proje veya çözümünüzdeki tüm hataları görün |
| **Alt**  +  **PgUp/PgDn** | Sonraki/önceki soruna git | Belgenizde ( **Visual Studio 2017 sürüm 15,8** ve üzeri sürümlerde bulunur) önceki/sonraki hataya, uyarıya ve önerisine atlayın |
| **CTRL** + **K**,**/** | Tek satır yorum/açıklama kaldır | Bu komut, seçiminizin zaten açıklama eklenmiş olmasına bağlı olarak tek satırlık yorum ekler veya kaldırır |
| **CTRL** + **SHIFT**+**/** | Değiştirme bloğu açıklaması/Açıklama | Bu komut, seçtiğiniz seçeneğe bağlı olarak blok açıklamalarını ekler veya kaldırır |

> [!NOTE]
> Bazı uzantılar varsayılan Visual Studio keybindings bağlantısını çözer. Yukarıdaki komutları kullanmak için, **Araçlar**  >  **içeri ve dışarı aktarma ayarları**  >  **sıfırlama tüm ayarları** veya **araç**  >  **seçenekleri**  >  **klavye**  >  **sıfırlaması**' na giderek keybindings 'i Visual Studio 'nun varsayılan ayarlarına geri yükleyin.

Klavye kısayolları ve komutları hakkında daha fazla bilgi için bkz. [üretkenlik kısayolları](../ide/productivity-shortcuts.md) ve [popüler klavye kısayolları](default-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Dosyalara veya türlere hızlıca git

Visual Studio 'nun **tümüne git** (**CTRL** + **T**) adlı bir özelliği vardır. **Tümüne git** , herhangi bir dosyaya, türe, üyeye veya sembol bildirimine hızlı bir şekilde gitmenizi sağlar.

- Bu arama çubuğunun konumunu değiştirin veya **dişli** simgesini kullanarak canlı gezinti önizlemeyi kapatın.
- Sonuçları gibi sözdizimi kullanarak filtreleyin `t mytype` .
- Aramanızın kapsamını yalnızca geçerli belge olarak yapın.
- Camel büyük/küçük harf eşleştirme desteklenir.

![Visual Studio 'da tümüne git](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Kod stili kurallarını zorla

Kodlama kurallarını birlikte kullanmak ve kaynak ile seyahat etmek için bir EditorConfig dosyası kullanabilirsiniz.

![Visual Studio 'da kod stili zorlama](../ide/media/VSGuide_CodeStyle.png)

- Varsayılan bir veya ekleyin. Yeni öğe Ekle seçeneğini belirleyerek projenize net stil editorconfig dosyası **ekleyin**  >  . **Yeni öğe Ekle** iletişim kutusunda, "editorconfig" ifadesini aratın. **Editorconfig dosyası** öğe şablonlarından birini seçin ve ardından **Ekle**' yi seçin.

   ![Visual Studio 'da EditorConfig öğe şablonları](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- **Araçlar** Seçenekler  >  > **metin Düzenleyicisi** > **C#** > **kod stili** içindeki kod stili ayarlarınıza göre otomatik olarak bir. editorconfig dosyası oluşturun.

   ![VS 2019 ' deki ayarlardan. editorconfig dosyası oluştur](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Visual Studio için ıntellicode 'un [kod çıkarımı özelliği](/visualstudio/intellicode/code-style-inference) , kod stillerinizi mevcut koddan algılar. Daha sonra, kod stili tercihleriniz zaten tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Bir kod stili kuralının önem düzeyini doğrudan düzenleyici aracılığıyla yapılandırın. Şu anda bir. editorconfig dosyanız yoksa, sizin için bir tane oluşturulur. İmlecinizi hata, uyarı veya öneriye yerleştirin ve **CTRL** yazın + **.** Hızlı Eylemler ve yeniden düzenlemeler menüsünü açmak için. **Sorunları Yapılandır veya gizle**' yi seçin. Daha sonra kuralı seçin ve bu kural için yapılandırmak istediğiniz önem derecesini seçin. Bu, mevcut EditorConfig dosyanızı kuralın yeni önem derecesiyle güncelleştirir.

   ![Bir kod stili kuralının önem düzeyini doğrudan düzenleyicide yapılandırma](../ide/media/configure-severity-level.png)

[.Net kodlama kuralı seçenekleri](/dotnet/fundamentals/code-analysis/code-style-rule-options) belgelerine göz atın ve bu da tüm editorconfig dosyasına bir örnek içerir.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Kod Temizleme

Visual Studio, Kod Temizleme özelliği aracılığıyla kod stili tercihleri de dahil olmak üzere kod dosyanız için isteğe **bağlı biçimlendirme** sağlar. Kod Temizleme'yi çalıştırmak için düzenleyicinin alt kısmında bulunan süpürge simgesine tıklayın veya **Ctrl** + **K**, **Ctrl** + **E tuşlarına basın.**

![Visual Studio 2019'da Kod Temizleme düğmesi](media/execute-code-cleanup.png)

Ayrıca tüm projeniz veya çözümünüz genelinde kod temizleme de çalıştırabilirsiniz. projesinde proje veya çözüm adına sağ **tıklayın, Çözüm Gezgini** ve Kod Temizleme'yi **seçin** ve ardından Kod Temizlemeyi **Çalıştır'ı seçin.**

![Proje veya Çözümün Tamamına Kod Temizleme Çalıştırma](media/run-code-cleanup-project-solution.png)

Kod Temizleme, dosyanızı boşluklar, girintiler ve cetera için biçimlendirmeye ek **olarak** seçili kod stillerini de uygular. Her kod stiline yönelik tercihleriniz [EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)dosyasından , proje için varsa [](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) veya Seçenekler iletişim kutusundaki kod stili **ayarlarından** okunur.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Yeniden düzenleme ve kod düzeltmeleri

Visual Studio çok sayıda yeniden düzenleme, kod oluşturma eylemi ve kod düzeltmeleri ile birlikte gelir. Kırmızı geçişler hataları, yeşil geçişler uyarıları, üç gri nokta ise kod önerilerini temsil eder. Ampule veya tornavida simgesine tıklayarak veya Ctrl tuşlarına basarak kod **düzeltmelerine erişebilirsiniz.** +  veya **Alt** + **Enter.** Her düzeltme, düzeltmenin nasıl çalıştığını gösteren bir canlı kod farkını gösteren bir önizleme penceresiyle birlikte gelir.

Popüler hızlı düzeltmeler ve yeniden düzenlemelerde şunlar yer almaktadır:

- Rename
- Ayıklama Yöntemi
- Yöntem İmzasını Değiştirme
- Oluşturucu Oluşturma
- Generate Metodu
- Türü Dosyaya Taşıma
- Yeni Null-Check
- Parametre Ekle
- Gereksiz Kullanımı Kaldırma
- LINQ Sorgusuna veya LINQ yöntemine Foreach Döngüsü
- Üyeleri Yukarı Çekme

Daha fazla bilgi için [bkz. kod oluşturma özellikleri.](code-generation-in-visual-studio.md)

Kod sorunlarını [bayrakla belirlemek için FxCop](../code-quality/install-fxcop-analyzers.md) çözümleyicilerini yükleyebilirsiniz. Veya Roslyn çözümleyicileri ile kendi yeniden düzenleme [veya kod düzeltmenizi yazın.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md)

Topluluk üyelerinden birkaçı ek kod incelemeleri ek olarak ücretsiz uzantılar yazdı:

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [Visual Studio için SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [Visual Studio için SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Visual Studio'da yeniden düzenleme](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Kullanımları Bulma, Uygulamaya Gitme ve Koda Bağlı Derlemelere Gitme

Visual Studio aramanıza ve kodunda gezinmenize yardımcı olacak [birçok özellik vardır.](../ide/navigating-code.md)

| Özellik | Kısayol | Ayrıntılar/Geliştirmeler |
|- | - | -|
| Tüm Başvuruları Bul | **Shift ile kaydırma** + **F12**| Sonuçlar renklendirmelidir ve okuma veya yazma gibi projeye, tanıma ve başvuru türüne göre gruplandırabilir. Ayrıca sonuçları "kilitleyip" de kilitlersiniz. |
| Uygulamaya Git | **Ctrl tuşunu basılı tutarak** + **F12** | Geçersiz kılınan üyeye gitmek için `override` anahtar sözcüğü üzerinde Tanıma Git'i kullanabilirsiniz |
| Tanıma Git | **F12 veya** **Ctrl Tıklama** + | Tanıma **gitmek için tıklarken Ctrl** tuşuna basın |
| Tanıma Göz At | **Alt** + **F12** | Tanımın satır içi görünümü |
| Yapı Görselleştirici | Küme ayraçları arasında gri, noktalı çizgiler | Kod yapınızı görmek için üzerine gelin |
| Koda bağlı derlemelere gezinti | **F12 veya** **Ctrl Tıklama** +  | Özelliği etkinleştirerek dış kaynak (ILSpy ile kaynak koda alınan) gidin: **Araçlar** Seçenekler Metin Düzenleyici C# Gelişmiş Kaynak koda sahip  >    >    >    >    >  **kaynaklara gezinmeyi etkinleştirin.** |

![Tüm Başvurulara Git ve Tüm Başvuruları Bul](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Geliştirilmiş IntelliSense

Yalnızca alfabetik bir Visual Studio yerine [bağlam kullanan kod tamamlamaları](/visualstudio/intellicode/intellicode-visual-studio) almak üzere intelliCode kullanın. Ayrıca, etki alanına özgü kitaplıklarınızı temel alan özel bir [IntelliSense](/visualstudio/intellicode/custom-model-faq) modeli de eğitebilirsiniz.

## <a name="unit-testing"></a>Birim testi

2017'Visual Studio başlayarak test deneyiminde çok sayıda geliştirmeler var. MSTest v1, MSTest v2, NUnit veya XUnit test çerçeveleriyle test etmek için.

- **Test Gezgini** test bulma hızlıdır.

- Test **Gezgini'nde testlerinizi** *hiyerarşik sıralama ile düzenleme.*

   ![Visual Studio'de Metin Gezgini için hiyerarşi görünümü](../ide/media/VSGuide_Testing.png)

- [Canlı birim testi,](../test/live-unit-testing.md) kod değişikliklerinizin etkisinde olan testleri sürekli çalıştırır ve testlerin durumunu size haber verme amacıyla satır içi düzenleyici simgelerini günceller. Belirli testleri veya test projelerini canlı test kümenize dahil etmek veya hariç tutmak. (Visual Studio Enterprise sürümü.)

## <a name="debugging"></a>Hata Ayıklama

Bir Visual Studio hata ayıklama özelliği şunlardır:

::: moniker range=">=vs-2019"

- İzleme, Otomatikler ve Yereller **pencerelerinde bir** dize **arama** özelliği.
- *bir kod satırına* gelmenize olanak sağlayan 'play' simgesine tıklamak için çalıştırın, görüntülenen yeşil 'oynat' simgesine tıklayın ve programınızı bu satıra ulaşana kadar çalıştırın.
- en **önemli bilgileri** iletişim kutusuna en üst düzeye (örneğin, hangi değişkenin içinde olduğunu) koyan Özel Durum `null` `NullReferenceException` Yardımcısı.
- [Önceki kesme noktalarına](../debugger/view-historical-application-state.md)veya adımlara geri dönmenizi ve uygulamanın geçmişte olduğu gibi durumunu görüntülemenizi sağlayan hata ayıklamayı geri adımlama.
- [Bir özel durumun](/azure/application-insights/app-insights-snapshot-debugger)(Azure'da olması gerekir) atıldığı anda canlı bir web uygulamasının durumunu araştırmanız için anlık görüntü hata ayıklama.

::: moniker-end

::: moniker range="vs-2017"

- *bir kod satırına* gelmenize olanak sağlayan 'play' simgesine tıklamak için çalıştırın, görüntülenen yeşil 'oynat' simgesine tıklayın ve programınızı bu satıra ulaşana kadar çalıştırın.
- en **önemli bilgileri** iletişim kutusuna en üst düzeye (örneğin, hangi değişkenin içinde olduğunu) koyan Özel Durum `null` `NullReferenceException` Yardımcısı.
- [Önceki kesme noktalarına](../debugger/view-historical-application-state.md)veya adımlara geri dönmenizi ve uygulamanın geçmişte olduğu gibi durumunu görüntülemenizi sağlayan hata ayıklamayı geri adımlama.
- [Bir özel durumun](/azure/application-insights/app-insights-snapshot-debugger)(Azure'da olması gerekir) atıldığı anda canlı bir web uygulamasının durumunu araştırmanız için anlık görüntü hata ayıklama.

::: moniker-end

![Visual Studio'de Özel Durum Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Sürüm denetimi

Git veya TFVC kullanarak kodunuzu depolar ve güncellerken Visual Studio.

::: moniker range=">=vs-2019"

- Çekme isteklerini [oluşturmak, gözden geçirmek Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) ve çalışmadan çalıştırmak için çekme isteklerini Visual Studio.

::: moniker-end

- Yerel değişikliklerinizi yerel [Takım Gezgini](reference/team-explorer-reference.md) ve bekleyen işlemeleri ve değişiklikleri izlemek için durum çubuğunu kullanın.

- ASP.NET uzantısı için Sürekli teslim araçlarıyla Visual Studio projeleriniz için sürekli tümleştirme [ve teslim Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) ayarlayın.

![Visual Studio'da kaynak denetimi](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Hangi diğer özellikler hakkında bilgim olmalı?

Burada, kod yazmayı daha verimli hale getirirken düzenleyici ve üretkenlik özelliklerinin bir listesi ve ardından yer almaktadır. Bazı özelliklerin varsayılan olarak kapalı olması (makinenize göre dizin oluşturması, tartışmalı olması veya şu anda deneysel olması) nedeniyle etkinleştirilmesi gerekir.

| Özellik | Ayrıntılar | Etkinleştirme |
|-|-|-|
| dosyalarda dosya Çözüm Gezgini | Dosyanın içinde etkin dosyayı **Çözüm Gezgini** | **Araçlar**  >  **Seçenekler**  >  **Projeler ve Çözümler**  >  **Etkin Öğeyi Çözüm Gezgini** |
| Başvuru derlemeleri ve NuGet paketlerinde türler için usings ekleme | Bir nuGet paketi yükleme kod düzeltmesi içeren bir hata ampulü gösterir. | **Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Başvuru derlemelerinde türler için kullanma önerin** ve **NuGet paketlerinde türler için kullanma önerin** |
| Tam çözüm analizini etkinleştirme | Hata Listesinde çözümünüzle ilgili tüm **hataları görme** | **Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Tam çözüm analizini etkinleştirme** |
| Kaynaklarda gezinmeyi etkinleştirme | Dış kaynaklardan gelen türlerde/üyelerde Tanıma Git'e izin verme ve yöntem gövdelerini göstermek için ILSpy decompiler kullanma | **Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Kaynaklarda gezinmeyi etkinleştirme** |
| Tamamlama/Öneri Modu | IntelliSense'te tamamlanma davranışını değiştirir. IntelliJ arka plan bilgilerine sahip geliştiriciler burada varsayılan olmayan bir ayar kullanma eğilimindedir. | **Menü**  >  **Düzenle**  >  **IntelliSense**  >  **Tamamlama Modunu Değiştir** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Düzenleyicide kod başvuru bilgilerini ve değişiklik geçmişini görüntüler. (CodeLens kaynak denetimi göstergeleri, kod Visual Studio Community kullanılamaz.) | **Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **Tüm Diller**  >  **CodeLens** |
| [Kod parçacıkları](../ide/visual-csharp-code-snippets.md) | Ortak ortak kodun saplama yardımı | Bir kod parçacığı adı yazın ve Sekme **tuşuna iki kez** basın. |
