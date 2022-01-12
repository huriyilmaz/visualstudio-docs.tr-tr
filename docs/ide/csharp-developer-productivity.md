---
title: .NET geliştirmesi için üretkenliğinizi artırın
description: Daha hızlı .NET kodu yazmanıza yardımcı olmak için gezinti, kod analizi, birim testi ve diğer özelliklere genel bakış.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.date: 02/24/2021
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: b1ef2f5c9280f6c58f60f8ebdda0cd0de6b8a7d9
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135533902"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Visual Studio C# geliştiricileri için üretkenlik kılavuzu

Geliştiricilerin Visual Studio daha üretken hale nasıl getirir? Dosya/tür/üye/sembol bildirimlerine gitmek için, akıllı bir Özel Durum Yardımcısı, kod stili yapılandırma ve zorlama, birçok yeniden düzenleme ve kod düzeltmesi için, kod stili önerileri, **Test** Gezgini'nde hiyerarşi-görünümü , Tüme Git **(Ctrl** + **T)** gibi performans ve üretkenlik geliştirmelerinden faydalanın. 

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Farklı bir düzenleyiciden klavye kısayollarına alışabilirsiniz

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15.8'de yeni**

::: moniker-end

Başka bir IDE veya kodlama ortamından geliyorsanız, klavye  düzeninizi Visual Studio Code *veya ReSharper (Visual Studio) olarak değiştirebilirsiniz:*

![Visual Studio'de Klavye Düzenleri](../ide/media/VS2017Guide-Keyboard.png)

Bazı uzantılar da klavye düzenleri sağlar:

- [Visual Studio için HotKeys (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs Öykünmesi](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Aşağıdakiler popüler Visual Studio kısayollardır:

| Kısayol (Tüm Profiller) | Komut | Açıklama |
|-|-|-|
| **Ctrl** + **T** | Tamam'a git | Herhangi bir dosyaya, türe, üyeye veya sembol bildirimine gidin |
| **F12** **(ayrıca Ctrl** + **tuşuna basın)** | Tanıma Git | Sembolün tanımlandığı yere gidin |
| **Ctrl** + **F12** | Uygulamaya Git | Temel tür veya üyeden çeşitli uygulamalarına gidin |
| **Üstkrkt** + **F12** | Tüm Başvuruları Bul | Tüm simge veya değişmez başvurulara bakın |
| **Alt** + **Ev** | Temele Git | Devralma zincirinde gezinme |
| **Ctrl** + **.** (ayrıca **Alt** +  C# Profili'ne girin) | Hızlı Eylemler ve Yeniden Düzenlemeler | İmleç konumunuz veya kod seçiminiz üzerinde hangi kod düzeltmelerini, kod oluşturma eylemlerini, yeniden düzenlemelerini veya diğer hızlı eylemlerin kullanılabilir olduğunu görme |
| **Ctrl** + **D** | Yinelenen satır | İmlecin içinde olduğu kod satırı yineler **(Visual Studio 2017 sürüm 15.6** ve sonraki sürümlerde kullanılabilir) |
| **Üstkrkt** + **Alt**+**+**/**-** | Genişlet/Sözleşme seçimi | Düzenleyicide geçerli seçimi genişleter veya sözleşmeler **(Visual Studio 2017 sürüm 15.5** ve sonraki sürümlerde kullanılabilir) |
| **Üstkrkt**  +  **Alt**  +  **.** | Sonraki Eşleşen Caret Ekle | Geçerli seçimle eşleşen bir sonraki konuma bir seçim ve dikkat Visual Studio **2017 sürüm 15.8** ve sonraki sürümlerde kullanılabilir) |
| **Ctrl** + **S** | Arayın | Tüm Visual Studio ara |
| **F5** | Hata Ayıklamayı Başlat | Uygulamanıza hata ayıklamaya başlama |
| **Ctrl** + **F5** | Hata Ayıklama olmadan çalıştırma | Hata ayıklama olmadan yerel olarak uygulama çalıştırma |
| **Ctrl** + **K,****D** (Varsayılan Profil) veya **Ctrl** + **E**,**D** (C# Profili) | Belgeyi Biçimlendir | Dosyanız için yeni satır, aralık ve girinti ayarlarına göre biçimlendirme ihlallerini temizler |
| **Ctrl** + **\\** ,**Ctrl** + **E** (Varsayılan Profil) veya **Ctrl** + **W**,**E** (C# Profili) | Hata Listesini Görüntüleme | Belgeniz, projeniz veya çözümünüzle ilgili tüm hataları görme |
| **Alt**  +  **PgUp/PgDn** | Sonraki/Önceki Soruna Git | Belgenizin önceki/sonraki hata, uyarı ve öneriye atlayın **(Visual Studio 2017 sürüm 15.8** ve sonraki sürümlerde kullanılabilir) |
| **Ctrl** + **K**,**/** | Tek satırlı açıklamayı açıp/açıklamayı geri alma | Bu komut, seçiminize zaten açıklama ekli olup olmadığınıza bağlı olarak tek satırlık bir açıklama ekler veya kaldırır |
| **Ctrl** + **Üstkrkt**+**/** | Blok açıklamalarını açıp kapat/açıklamayı geri alma | Bu komut, seçtiğinize bağlı olarak blok açıklamalarını ekler veya kaldırır |

> [!NOTE]
> Bazı uzantılar varsayılan anahtar bağlamalarını Visual Studio bağlamayı geri aldı. Yukarıdaki komutları kullanmak için Araçlar İçeri ve Dışarı Aktarma Visual Studio'a gidip tuş bağlamalarınızı varsayılan ayarlarınıza geri Ayarlar Tüm ayarları sıfırla veya Araçlar Seçenekleri Klavye Sıfırlama'ya  >    >     >    >    >  **gidin.**

Klavye kısayolları ve komutları hakkında daha fazla bilgi için [bkz. Üretkenlik kısayolları ve](../ide/productivity-shortcuts.md) [Popüler klavye kısayolları.](default-keyboard-shortcuts-in-visual-studio.md)

## <a name="navigate-quickly-to-files-or-types"></a>Dosyalara veya türlere hızla gidin

Visual Studio Git **(** **Ctrl** T ) adlı bir özelliği + **vardır.** **Tüm Sayfalara Git** özelliği herhangi bir dosyaya, türe, üyeye veya sembol bildirimine hızlıca atlamanız için olanak sağlar.

- Dişli simgesini kullanarak bu arama çubuğunun konumunu değiştirebilir veya canlı gezinti önizlemesini **kapatabilirsiniz.**
- Gibi söz dizimi kullanarak sonuçları `t mytype` filtrele.
- Aramanızı yalnızca geçerli belgeyle kapsamına ekleyin.
- Büyük/büyük harf eşleştirmesi de destekler.

![Visual Studio'de Tüm'e Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Kod stili kurallarını zorlama

Kodlama kurallarınızı kodlamak ve kaynakla birlikte yolculuk yapmak için editorConfig dosyasını kullanabilirsiniz.

![Visual Studio'de kod stili zorlama](../ide/media/VSGuide_CodeStyle.png)

- Varsayılan veya ekleyin. Yeni Öğe Ekle'yi seçerek NET stili EditorConfig **dosyasını**  >  **projenize ekleyin.** Yeni Öğe **Ekle iletişim** kutusunda "editorconfig" araması yazın. editorconfig Dosya öğesi **şablonlarından birini** ve ardından Ekle'yi **seçin.**

   ![Visual Studio'de EditorConfig öğe şablonları](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Araçlar Seçenekler Metin Düzenleyici  C# Kod Stili'nde kod stili ayarlarınıza göre otomatik olarak bir *.editorconfig* dosyası >  >  >  > **oluşturun.**

   ![VS 2019'da ayarlardan .editorconfig dosyası oluşturma](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- [IntelliCode'daki kod](/visualstudio/intellicode/code-style-inference) çıkarma özelliği Visual Studio kod stillerinizi mevcut koddan çıkartır. Ardından kod stili tercihleriniz önceden tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Bir kod stili kuralının önem derecelerini doğrudan düzenleyici aracılığıyla yapılandırma. Şu anda bir .editorconfig dosyanız yoksa sizin için bir tane oluşturulur. İmlecinizi hata, uyarı veya öneri üzerine yerleştirerek **Ctrl tuşlarına** + **basın.** hızlı eylemler ve yeniden düzenleme menüsünü açın. Sorunları **Yapılandır veya Bastır'ı seçin.** Daha sonra kuralı seçin ve bu kural için yapılandırmak istediğiniz önem derecesini seçin. Bu, mevcut EditorConfig dosyanızı kuralın yeni önem derecesiyle güncelleştirir.

   ![Doğrudan düzenleyicide bir kod stili kuralının önem derecelerini yapılandırma](../ide/media/configure-severity-level.png)

Tam bir [EditorConfig dosyası örneği de içeren .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options) kodlama kuralı seçenekleri belgelerine göz atabilirsiniz.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Kod Temizleme

Visual Studio, Kod Temizleme özelliği aracılığıyla kod stili tercihleri de dahil olmak üzere kod dosyanız için isteğe **bağlı biçimlendirme** sağlar. Kod Temizleme'yi çalıştırmak için düzenleyicinin alt kısmında bulunan süpürge simgesine tıklayın veya **Ctrl** + **K**, **Ctrl** + **E tuşlarına basın.**

![Visual Studio 2019'da Kod Temizleme düğmesi](media/execute-code-cleanup.png)

Ayrıca tüm projeniz veya çözümünüz genelinde kod temizleme de çalıştırabilirsiniz. Çözüm Gezgini proje veya çözüm adına **sağ tıklayın, Analiz ve Kod Temizleme'yi** **seçin** ve ardından Kod Temizlemeyi **Çalıştır'ı seçin.**

![Kod Temizlemeyi Tüm Project Çözümü Çalıştırma](media/run-code-cleanup-project-solution.png)

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

Kod sorunlarını [bayrakla belirlemek için FxCop](../code-quality/install-net-analyzers.md) çözümleyicilerini yükleyebilirsiniz. Veya Roslyn çözümleyicileri ile kendi yeniden düzenleme [veya kod düzeltmenizi yazın.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md)

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

![Visual Studio'de yeniden Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Kullanımları Bulma, Uygulamaya Gitme ve Koda Bağlı Derlemelere Gitme

Visual Studio aramanıza ve kodunda gezinmenize yardımcı olacak [birçok özellik vardır.](../ide/navigating-code.md)

| Özellik | Kısayol | Ayrıntılar/Geliştirmeler |
|- | - | -|
| Tüm Başvuruları Bul | **Üstkrkt** + **F12**| Sonuçlar renklendirmelidir ve okuma veya yazma gibi projeye, tanıma ve başvuru türüne göre gruplandırabilir. Ayrıca sonuçları "kilitler"siniz. |
| Uygulamaya Git | **Ctrl** + **F12** | Geçersiz kılınan üyeye gitmek için `override` anahtar sözcüğü üzerinde Tanıma Git'i kullanabilirsiniz |
| Tanıma Git | **F12 veya** **Ctrl Tıklama** + | Tanıma **gitmek için tıklarken Ctrl** tuşuna basın |
| Tanıma Göz At | **Alt** + **F12** | Tanımın satır içi görünümü |
| Yapı Görselleştirici | Küme ayraçları arasında gri, noktalı çizgiler | Kod yapınızı görmek için üzerine gelin |
| Koda bağlı derlemelere gezinti | **F12 veya** **Ctrl Tıklama** +  | Özelliği etkinleştirerek dış kaynak (ILSpy ile kaynak koda alınan) gidin: **Araçlar** Seçenekler Metin Düzenleyici C# Gelişmiş Kaynak koda sahip  >    >    >    >    >  **kaynaklara gezinmeyi etkinleştirin.** |

![Tüm Başvurulara Git ve Tüm Başvuruları Bul](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Geliştirilmiş IntelliSense

Yalnızca alfabetik bir Visual Studio yerine [bağlam kullanan kod](/visualstudio/intellicode/intellicode-visual-studio) tamamlamaları almak için IntelliCode kullanın. Ayrıca, etki alanına özgü kitaplıklarınızı temel alan özel bir [IntelliSense](/visualstudio/intellicode/custom-model-faq) modeli de eğitebilirsiniz.

## <a name="unit-testing"></a>Birim testi

2017'Visual Studio başlayarak, test deneyiminde çok sayıda geliştirme vardır. MSTest v1, MSTest v2, NUnit veya XUnit test çerçeveleriyle test etmek için.

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

Git veya TFVC kullanarak kodunuzu depolar ve güncelleştirebilirsiniz Visual Studio.

::: moniker range=">=vs-2019"

- Çekme isteklerini [oluşturmak, gözden geçirmek, Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) ve çalışmadan çalıştırmak için çekme isteklerini Visual Studio.

::: moniker-end

- Yerel değişikliklerinizi yerel [Takım Gezgini](reference/team-explorer-reference.md) ve bekleyen işlemeleri ve değişiklikleri izlemek için durum çubuğunu kullanın.

- ASP.NET uzantısı için Sürekli teslim araçlarıyla Visual Studio projeleriniz için [sürekli tümleştirme ve teslim Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) ayarlayın.

![Visual Studio'de kaynak denetimi](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Hangi diğer özellikler hakkında bilgim olmalı?

Burada, kod yazmayı daha verimli hale getirirken düzenleyici ve üretkenlik özelliklerinin bir listesi ve ardından yer almaktadır. Bazı özelliklerin varsayılan olarak kapalı olması (makinenize göre dizin oluşturması, tartışmalı olması veya şu anda deneysel olması) nedeniyle etkinleştirilmesi gerekir.

| Özellik | Ayrıntılar | Etkinleştirme |
|-|-|-|
| dosyalarda dosya Çözüm Gezgini | Dosyanın içinde etkin dosyayı **Çözüm Gezgini** | **Araçları**  >  **Seçenekler**  >  **Projeler ve Çözümler**  >  **Etkin Öğeyi Çözüm Gezgini** |
| Başvuru derlemelerinde ve uygulama paketlerinde türler için NuGet ekleme | Bir hata ampulü ve kod düzeltmesi ile bir NuGet türü için bir paket yüklemesini gösterir | **Araçları**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Başvuru derlemelerinde türler için kullanma önerin ve** **Paketlerde türler için NuGet önerin** |
| Tam çözüm analizini etkinleştirme | Hata Listesinde çözümünüzle ilgili tüm **hataları görme** | **Araçları**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Tam çözüm analizini etkinleştirme** |
| Kaynaklarda gezinmeyi etkinleştirme | Dış kaynaklardan gelen türlerde/üyelerde Tanıma Git'e izin verme ve yöntem gövdelerini göstermek için ILSpy decompiler kullanma | **Araçları**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Kaynaklarda gezinmeyi etkinleştirme** |
| Tamamlama/Öneri Modu | IntelliSense'te tamamlanma davranışını değiştirir. IntelliJ arka plan bilgilerine sahip geliştiriciler burada varsayılan olmayan bir ayar kullanma eğilimindedir. | **Menü**  >  **Düzenle**  >  **Intellisense**  >  **Tamamlama Modunu Değiştir** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Düzenleyicide kod başvuru bilgilerini ve değişiklik geçmişini görüntüler. (CodeLens kaynak denetimi göstergeleri, kod Visual Studio Community kullanılamaz.) | **Araçları**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **Tüm Diller**  >  **CodeLens** |
| [Kod parçacıkları](../ide/visual-csharp-code-snippets.md) | Ortak ortak kodun saplama yardımı | Bir kod parçacığı adı yazın ve Sekme **tuşuna iki kez** basın. |
