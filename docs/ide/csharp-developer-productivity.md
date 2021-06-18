---
title: .NET geliştirme için üretkenliğinizi artırın
description: Daha hızlı .NET kodu yazmanıza yardımcı olmak için gezinti, kod analizi, birim testi ve diğer özelliklere genel bakış.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 6de31ed1b649f226ac47161fdadfe44d434289b9
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308525"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Visual Studio C# geliştiricileri için üretkenlik kılavuzu

Geliştiricilerin Visual Studio daha üretken hale nasıl getirir? Dosya/tür/üye/sembol bildirimlerine gitmek için, akıllı bir Özel Durum Yardımcısı, kod stili yapılandırma ve zorlama, birçok yeniden düzenleme ve kod düzeltmesi için, kod stili önerileri, **Test** Gezgini'nde hiyerarşi-görünümü , Tüme Git **(Ctrl** + **T)** gibi performans ve üretkenlik geliştirmelerinden faydalanın. 

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Farklı bir düzenleyiciden klavye kısayollarına alışabilirsiniz

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15.8'de yeni**

::: moniker-end

Başka bir IDE veya kodlama ortamından geliyorsanız, klavye düzeninizi Visual Studio Code *veya* *ReSharper (Visual Studio) olarak değiştirebilirsiniz:*

![Visual Studio'de Klavye Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Bazı uzantılar da klavye düzenleri sağlar:

- [Visual Studio için HotKeys (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs Öykünmesi](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Aşağıdakiler popüler Visual Studio kısayollardır:

| Kısayol (Tüm Profiller) | Komut | Açıklama |
|-|-|-|
| **Ctrl tuşunu basılı tutarak** + **T** | Tamam'a git | Herhangi bir dosyaya, türe, üyeye veya sembol bildirimine gidin |
| **F12** **(ayrıca Ctrl** + **tuşuna basın)** | Tanıma Git | Sembolün tanımlandığı yere gidin |
| **Ctrl tuşunu basılı tutarak** + **F12** | Uygulamaya Git | Temel tür veya üyeden çeşitli uygulamalarına gidin |
| **Shift ile kaydırma** + **F12** | Tüm Başvuruları Bul | Tüm simge veya değişmez başvurulara bakın |
| **Alt** + **Giriş** | Temele Git | Devralma zincirinde gezinme |
| **Ctrl tuşunu basılı tutarak** + **.** (ayrıca **Alt** +  C# Profili'ne girin) | Hızlı Eylemler ve Yeniden Düzenlemeler | İmleç konumunuz veya kod seçiminiz üzerinde hangi kod düzeltmelerini, kod oluşturma eylemlerini, yeniden düzenlemelerini veya diğer hızlı eylemlerin kullanılabilir olduğunu görme |
| **Ctrl tuşunu basılı tutarak** + **D** | Yinelenen satır | İmlecin içinde olduğu kod satırı yineler **(Visual Studio 2017 sürüm 15.6** ve sonraki sürümlerde kullanılabilir) |
| **Shift ile kaydırma** + **Alt**+**+**/**-** | Genişlet/Sözleşme seçimi | Düzenleyicide geçerli seçimi genişleter veya sözleşmeler **(2017 Visual Studio 15.5** ve sonraki sürümlerde kullanılabilir) |
| **Shift ile kaydırma**  +  **Alt**  +  **.** | Sonraki Eşleşen Caret Ekle | Geçerli seçimle eşleşen bir sonraki konuma bir seçim ve dikkat Visual Studio **(2017 sürüm 15.8** ve sonraki sürümlerde kullanılabilir) |
| **Ctrl tuşunu basılı tutarak** + **Q** | Arayın | Tüm Visual Studio ara |
| **F5** | Hata Ayıklamayı Başlat | Uygulamanıza hata ayıklamaya başlama |
| **Ctrl tuşunu basılı tutarak** + **F5** | Hata Ayıklama olmadan çalıştırma | Hata ayıklama olmadan yerel olarak uygulama çalıştırma |
| **Ctrl tuşunu basılı tutarak** + **K,****D** (Varsayılan Profil) veya **Ctrl** + **E**,**D** (C# Profili) | Belgeyi Biçimlendir | Dosyanız için yeni satır, aralık ve girinti ayarlarına göre biçimlendirme ihlallerini temizler |
| **Ctrl** + **\\** ,**Ctrl** + **E** (Varsayılan Profil) veya **Ctrl** + **W**,**E** (C# Profili) | Hata Listesini Görüntüleme | Belgeniz, projeniz veya çözümünüzle ilgili tüm hataları görme |
| **Alt**  +  **PgUp/PgDn** | Sonraki/Önceki Soruna Git | Belgenizin önceki/sonraki hata, uyarı ve öneriye atlayın **(Visual Studio 2017 sürüm 15.8** ve sonraki sürümlerde kullanılabilir) |
| **Ctrl tuşunu basılı tutarak** + **K**,**/** | Tek satırlı açıklamayı açıp/açıklamayı geri alma | Bu komut, seçiminize zaten açıklama ekli olup olmadığınıza bağlı olarak tek satırlık bir açıklama ekler veya kaldırır |
| **Ctrl tuşunu basılı tutarak** + **Shift ile kaydırma**+**/** | Blok açıklamalarını açıp kapat/açıklamayı geri alma | Bu komut, seçtiğinize bağlı olarak blok açıklamalarını ekler veya kaldırır |

> [!NOTE]
> Bazı uzantılar varsayılan anahtar bağlamalarını Visual Studio bağlamayı geri aldı. Yukarıdaki komutları kullanmak için Araçlar İçeri ve Dışarı Aktarma Ayarları Tüm ayarları Visual Studio Araçlar Seçenekleri Klavye Sıfırlama'ya gidip tuş bağlamalarınızı varsayılan ayarlarına  >    >     >    >    >  **geri yükleyebilirsiniz.**

Klavye kısayolları ve komutları hakkında daha fazla bilgi için [bkz. Üretkenlik kısayolları ve](../ide/productivity-shortcuts.md) [Popüler klavye kısayolları.](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)

## <a name="navigate-quickly-to-files-or-types"></a>Dosyalara veya türlere hızla gidin

Visual Studio Git **(** **Ctrl** T ) adlı bir özelliği + **vardır.** **Tüm Sayfalara Git** özelliği herhangi bir dosyaya, türe, üyeye veya sembol bildirimine hızlıca atlamanız için olanak sağlar.

- Dişli simgesini kullanarak bu arama çubuğunun konumunu değiştirebilir veya canlı gezinti önizlemesini **kapatabilirsiniz.**
- Gibi söz dizimi kullanarak sonuçları `t mytype` filtrele.
- Aramanızı yalnızca geçerli belgeyle kapsamına ekleyin.
- Büyük/büyük harf eşleştirmesi de destekler.

![Visual Studio'da Tüm'e Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Kod stili kurallarını zorlama

Kodlama kurallarınızı kodlamak ve kaynakla birlikte yolculuk yapmak için editorConfig dosyasını kullanabilirsiniz.

![Visual Studio'de kod stili Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Varsayılan veya ekleyin. Yeni Öğe Ekle'yi seçerek NET stili EditorConfig **dosyasını**  >  **projenize ekleyin.** Yeni Öğe **Ekle iletişim** kutusunda "editorconfig" araması yazın. editorconfig Dosya öğesi **şablonlarından birini** ve ardından Ekle'yi **seçin.**

   ![Visual Studio'de EditorConfig öğe şablonları](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Araçlar Seçenekler Metin Düzenleyici  C# Kod Stili'nde kod stili ayarlarınıza göre otomatik olarak bir *.editorconfig* dosyası >  >  >  > **oluşturun.**

   ![VS 2019'da ayarlardan .editorconfig dosyası oluşturma](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- [IntelliCode'daki kod](/visualstudio/intellicode/code-style-inference) çıkarma özelliği Visual Studio kod stillerinizi mevcut koddan çıkartır. Ardından kod stili tercihleriniz önceden tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Doğrudan düzenleyici aracılığıyla bir kod stili kuralının önem derecelerini yapılandırma. Şu anda bir .editorconfig dosyanız yoksa sizin için bir tane oluşturulur. İmlecinizi hata, uyarı veya öneri üzerine yerleştirerek **Ctrl tuşlarına** + **basın.** hızlı eylemler ve yeniden düzenleme menüsünü açın. Sorunları **Yapılandır veya Bastır'ı seçin.** Daha sonra kuralı seçin ve bu kural için yapılandırmak istediğiniz önem derecesini seçin. Bu, mevcut EditorConfig dosyanızı kuralın yeni önem derecesiyle güncelleştirir.

   ![Doğrudan düzenleyicide bir kod stili kuralının önem derecelerini yapılandırma](../ide/media/configure-severity-level.png)

Tam bir [EditorConfig dosyası örneği de içeren .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options) kodlama kuralı seçenekleri belgelerine göz atabilirsiniz.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Kod temizleme

Visual Studio kod **Temizleme** özelliği aracılığıyla kod stili tercihleri de dahil olmak üzere kod dosyanız için isteğe bağlı biçimlendirme sağlar. Kod temizlemeyi çalıştırmak için düzenleyicinin altındaki Broom simgesine tıklayın veya **CTRL** + **K**, **CTRL** + **E** tuşlarına basın.

![Visual Studio 2019 ' de kod temizleme düğmesi](media/execute-code-cleanup.png)

Ayrıca, tüm proje veya çözümünüz genelinde kod temizleme işlemini de çalıştırabilirsiniz. **Çözüm Gezgini**' de proje veya çözüm adına sağ tıklayın, **Çözümle ve kod temizleme**' yi seçin ve ardından **kod temizlemeyi Çalıştır**' ı seçin.

![Kod temizlemeyi tüm proje veya çözüm genelinde Çalıştır](media/run-code-cleanup-project-solution.png)

Dosyanızı boşluk, girintiler, et cetera için biçimlendirmeye ek olarak, **kod temizleme** de seçili kod stilleri uygular. Her kod stili için tercihleriniz, proje için bir tane varsa veya **Seçenekler** iletişim kutusundaki [kod stili ayarlarından](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) , [editorconfig dosyasından](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)okunurdur.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Yeniden düzenlemeler ve kod düzeltmeleri

Visual Studio çok sayıda yeniden düzenlemeler, kod oluşturma eylemi ve kod düzeltmesiyle birlikte gelir. Red dalgalı çizgiler hataları, yeşil dalgalı çizgiler uyarıları temsil eder ve üç gri noktayla kod önerilerini temsil eder. Ampul veya screwsürücü simgesine tıklayarak veya **CTRL** tuşuna basarak kod düzeltmelere erişebilirsiniz + **.** veya **alt** + **girin**. Her bir onarım, düzeltmesinin nasıl çalıştığına ilişkin canlı bir kod farkı gösteren bir önizleme penceresiyle birlikte gelir.

Popüler hızlı düzeltmeler ve yeniden düzenlemeler şunları içerir:

- Rename
- Ayıklama Yöntemi
- Yöntem Imzasını Değiştir
- Oluşturucu oluştur
- Oluşturma yöntemi
- Türü dosyaya taşı
- Null-Check Ekle
- Parametre Ekle
- Gereksiz kullanımları kaldır
- LINQ sorgusuna veya LINQ yöntemine foreach döngüsü
- Üyeleri çekme

Daha fazla bilgi için bkz. [kod oluşturma özellikleri](code-generation-in-visual-studio.md).

Kod sorunlarını işaretlemek için [FxCop çözümleyicileri yükleyebilirsiniz](../code-quality/install-fxcop-analyzers.md) . Ya da [Roslyn çözümleyicilerine](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md)sahip kendi yeniden düzenleme veya kod düzeltmesini yazın.

Birçok topluluk üyesi, ek kod İncelemeleri ekleyen ücretsiz uzantılar yazdı:

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [Visual Studio için Sonarlınt](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [Stylecopçözümleyiciler](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [Visual Studio için Sonarlınt](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [Stylecopçözümleyiciler](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Visual Studio 'da yeniden düzenlemeler](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Kullanımlar bulun, uygulamaya gidin ve derlenmiş derlemelere gidin

Visual Studio 'da, [kodunuzda gezinmenize ve gezinmenize](../ide/navigating-code.md)yardımcı olacak birçok özellik bulunur.

| Özellik | Kısayol | Ayrıntılar/geliştirmeler |
|- | - | -|
| Tüm Başvuruları Bul | **SHIFT** + **F12**| Sonuçlar renklendirilir ve okuma veya yazma gibi proje, tanım ve başvuru türüne göre gruplanabilir. Ayrıca "kilitle" sonuçlarını da kullanabilirsiniz. |
| Uygulamaya git | **CTRL** + **F12** | `override`Geçersiz kılınan üyeye gitmek için anahtar sözcüğü üzerinde go to Definition kullanabilirsiniz |
| Tanıma Git | **F12** veya **CTRL** + **tıklama**| Tanıma gitmek için tıklarken **CTRL** tuşuna basın |
| Tanıma Göz At | **Alt** + **F12** | Bir tanım için satır içi görünüm |
| Yapı görselleştiricisi | Köşeli ayraçlar arasında gri, noktalı çizgiler | Kod yapınızı görmek için üzerine gelin |
| Ayrıştırılmış derlemelere gezinti | **F12** veya **CTRL** + **tıklama** | Özelliği etkinleştirerek dış kaynak (ılspy ile derlenen) bölümüne gidin: **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **C#**  >  **Gelişmiş**,  >  **ayrıştırılmış kaynaklara gezinmeyi etkinleştirir**. |

![Tümüne git ve tüm başvuruları bul](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Geliştirilmiş IntelliSense

Yalnızca alfabetik bir liste yerine [bağlam kullanan kod tamamlamalar](/visualstudio/intellicode/intellicode-visual-studio) almak Için Visual Studio Için ıntellicode kullanın. Ayrıca, kendi etki alanına özgü kitaplıklarınızı temel alarak [özel bir IntelliSense modeli](/visualstudio/intellicode/custom-model-faq) de eğitebilirsiniz.

## <a name="unit-testing"></a>Birim testi

Visual Studio 2017 ' den başlayarak, test deneyiminde çok sayıda iyileştirme vardır. MSTest v1, MSTest v2, NUnit veya XUnit test çerçeveleri ile test edebilirsiniz.

- **Test Gezgini** test keşfi hızlıdır.

- Testleri **Test Gezgini** 'nde *hiyerarşik sıralamaya* göre düzenleyin.

   ![Visual Studio 'da metin Gezgini için hiyerarşi görünümü](../ide/media/VSGuide_Testing.png)

- [Canlı birim testi](../test/live-unit-testing.md) , kod değişikliklerinden etkilenen testleri sürekli çalıştırır ve testlerinizin durumunu bilmenizi sağlamak için satır içi düzenleyici simgelerini güncelleştirir. Canlı test kümesinden belirli testleri veya test projelerini dahil edin veya hariç tutun. (Yalnızca Visual Studio Enterprise Edition.)

## <a name="debugging"></a>Hata Ayıklama

Visual Studio 'dan bazılarının hata ayıklama özellikleri şunları içerir:

::: moniker range=">=vs-2019"

- **İzleme**, **oto** ve **Yerel öğeler** pencerelerinde dize arama özelliği.
- *' A tıklayarak* bir kod satırının yanına gelin, görüntülenen yeşil ' oynat ' simgesine basın ve bu satıra ulaşana kadar programınızı çalıştırın.
- En önemli bilgileri iletişim kutusunda en üst düzeyde (örneğin, bir değişken) yerleştiren **özel durum Yardımcısı** `null` `NullReferenceException` .
- Önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın geçmişte bulunduğu durumu görüntülemenizi sağlayan [hata ayıklama işlemini geri](../debugger/view-historical-application-state.md)alabilirsiniz.
- Bir özel durum oluştuğunda canlı bir Web uygulamasının durumunu araştırmanıza olanak tanıyan [anlık görüntü hata ayıklaması](/azure/application-insights/app-insights-snapshot-debugger)(Azure 'da olmalıdır).

::: moniker-end

::: moniker range="vs-2017"

- *' A tıklayarak* bir kod satırının yanına gelin, görüntülenen yeşil ' oynat ' simgesine basın ve bu satıra ulaşana kadar programınızı çalıştırın.
- En önemli bilgileri iletişim kutusunda en üst düzeyde (örneğin, bir değişken) yerleştiren **özel durum Yardımcısı** `null` `NullReferenceException` .
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
| Dosyayı Çözüm Gezgini bul | **Çözüm Gezgini** 'de etkin dosyayı vurgular | **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **Çözüm Gezgini etkin öğeyi izle** |
| Başvuru derlemelerindeki ve NuGet paketlerindeki türler için using 'ler ekleyin | Başvurulmayan bir tür için NuGet paketini yüklemek üzere kod düzeltmesinin bulunduğu bir hata ampul gösterir | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Başvuru derlemelerindeki türler için kullanımlar önerin** ve **NuGet paketlerindeki türler için kullanımlar** önerin |
| Tam çözüm analizini etkinleştirme | **Hata listesi** çözümünüzdeki tüm hataları görün | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Tam çözüm analizini etkinleştir** |
| Derlenmekte olan kaynaklara gezinmeyi etkinleştir | Dış kaynaklardaki türlerde/üyelerde tanıma git 'e izin ver ve Yöntem gövdelerini göstermek için ılspy kaynak koda dönüştürücü kullanın | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Derlenmekte olan kaynaklara gezinmeyi etkinleştir** |
| Tamamlama/öneri modu | IntelliSense 'de tamamlama davranışını değiştirir. IntelliJ arka planlarına sahip geliştiriciler burada varsayılan olmayan bir ayar kullanmaya eğilimlidir. | **Menü**  >  **Düzenle**  >  **IntelliSense**  >  **Tamamlama modunu aç** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Düzenleyicide kod başvuru bilgilerini ve değişiklik geçmişini görüntüler. (Kaynak denetimi CodeLens göstergeleri Visual Studio Community Edition 'da kullanılamaz.) | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **Tüm diller**  >  **CodeLens** |
| [Kod parçacıkları](../ide/visual-csharp-code-snippets.md) | Ortak ortak kod saplamaya yardımcı olma | Bir kod parçacığı adı yazın ve **Tab** tuşuna iki kez basın. |
