---
title: .NET geliştirme için üretkenliğinizi artırın
description: Daha iyi .NET kodu daha hızlı yazmanıza yardımcı olacak gezinti, kod analizi, birim testi ve diğer özelliklere genel bakış.
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
ms.openlocfilehash: 094469cdbd41d57e4742023e8b99cc2b5a7c5daf
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431685"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>C# geliştiricileri için Visual Studio üretkenlik kılavuzu

Visual Studio geliştiricilerin her zamankinden daha üretken olmasını nasıl sağlayacağınızı öğrenin. Ön derlenmiş derlemelere gezinti, yazarken değişken adı önerileri, **Test Gezgini**'nde bir hiyerarşi görünümü, + bir akıllı **özel durum Yardımcısı**, kod stili yapılandırma ve zorlama ve birçok yeniden düzenlemeler ve kod düzeltmesi gibi performans ve üretkenlik geliştirmelerinden yararlanın...

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Farklı bir düzenleyiciden klavye kısayolları için kullandım

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15,8 ' de yeni**

::: moniker-end

başka bir ıde veya kodlama ortamından geliyorsanız, klavye düzeninizi *Visual Studio Code* veya *ReSharper (Visual Studio)* olarak değiştirebilirsiniz:

![Visual Studio klavye şemaları](../ide/media/VS2017Guide-Keyboard.png)

Bazı uzantılar da klavye şemaları sunmaktadır:

- [Visual Studio için kısayol tuşları (ReSharper/ıntellij)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs öykünmesi](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Vsvım](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

aşağıda popüler Visual Studio kısayollar verilmiştir:

| Kısayol (tüm profiller) | Komut | Açıklama |
|-|-|-|
| **CTRL** + **T** | Tümüne git | Herhangi bir dosya, tür, üye veya sembol bildirimine gidin |
| **F12** (Ayrıca **CTRL**+ + **tıklama**) | Tanıma Git | Simgenin tanımlandığı yere gitme |
| **CTRL** + **F12** | Uygulamaya git | Temel bir türden veya Üyeden çeşitli uygulamalarına gitme |
| **SHIFT** + **F12** | Tüm Başvuruları Bul | Tüm sembol veya değişmez başvuruları gör |
| **Alt** + **Giriş sayfası** | Temele Git | Devralma zincirinde gezin |
| **CTRL** + **.** (Ayrıca **alt** + C# profilinde **girin** ) | Hızlı Eylemler ve Yeniden Düzenlemeler | İmlecin konumunda veya kod seçiminde kod düzeltmelerinin, kod oluşturma eylemlerinin, yeniden düzenlemeler veya diğer hızlı eylemlerin kullanılabildiğini görün |
| **CTRL** + **D** | Yinelenen satır | imlecin bulunduğu kod satırını çoğaltır ( **Visual Studio 2017 sürüm 15,6** ve üzeri sürümlerde kullanılabilir) |
| **SHIFT** + **Alt**+**+**/**-** | Genişlet/sözleşme seçimi | düzenleyicideki geçerli seçimi genişletir veya sözleşmelerini ( **Visual Studio 2017 sürüm 15,5** ve üzeri sürümlerde mevcuttur) |
| **SHIFT**  +  **Alt**  +  **.** | Sonraki eşleşen giriş Işaretini Ekle | geçerli seçimle eşleşen bir sonraki konuma bir seçim ve giriş işareti ekler ( **Visual Studio 2017 sürüm 15,8** ve üzeri sürümlerde kullanılabilir) |
| **CTRL** + **Soru-cevap** | Arayın | tüm Visual Studio ayarlarını ara |
| **F5** | Hata ayıklamayı Başlat | Uygulamanızda hata ayıklamayı başlatma |
| **CTRL** + **F5** | Hata ayıklama olmadan Çalıştır | Uygulamanızı hata ayıklama olmadan yerel olarak çalıştırma |
| **CTRL** + **K**,**d** (varsayılan profil) veya **CTRL** + **E**,**D** (C# profili) | Belgeyi Biçimlendir | Yeni satır, Aralık ve girintileme ayarlarınıza göre dosyanızdaki biçimlendirme ihlallerini temizler |
| **CTRL** + **\\** ,**CTRL** + **E** (varsayılan profil) veya **CTRL** + **W**,**E** (C# profili) | Hata Listesi görüntüle | Belge, proje veya çözümünüzdeki tüm hataları görün |
| **Alt**  +  **PgUp/PgDn** | Sonraki/önceki soruna git | belgenizde ( **Visual Studio 2017 sürüm 15,8** ve üzeri sürümlerde bulunan) önceki/sonraki hataya, uyarıya ve önerisine atlayın. |
| **CTRL** + **K**,**/** | Tek satır yorum/açıklama kaldır | Bu komut, seçiminizin zaten açıklama eklenmiş olmasına bağlı olarak tek satırlık yorum ekler veya kaldırır |
| **CTRL** + **SHIFT**+**/** | Değiştirme bloğu açıklaması/Açıklama | Bu komut, seçtiğiniz seçeneğe bağlı olarak blok açıklamalarını ekler veya kaldırır |

> [!NOTE]
> bazı uzantılar, varsayılan Visual Studio keybindings bağlantısını çözer. yukarıdaki komutları kullanmak için, **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**  >  **tüm ayarları** veya **araç**  >  **seçenekleri**  >  **klavye**  >  **sıfırlaması**' na giderek keybindings ' ı Visual Studio varsayılanlarına geri yükleyin.

Klavye kısayolları ve komutları hakkında daha fazla bilgi için bkz. [üretkenlik kısayolları](../ide/productivity-shortcuts.md) ve [popüler klavye kısayolları](default-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Dosyalara veya türlere hızlıca git

Visual Studio **tümüne git** (**Ctrl** + **T**) adlı bir özellik vardır. **Tümüne git** , herhangi bir dosyaya, türe, üyeye veya sembol bildirimine hızlı bir şekilde gitmenizi sağlar.

- Bu arama çubuğunun konumunu değiştirin veya **dişli** simgesini kullanarak canlı gezinti önizlemeyi kapatın.
- Sonuçları gibi sözdizimi kullanarak filtreleyin `t mytype` .
- Aramanızın kapsamını yalnızca geçerli belge olarak yapın.
- Camel büyük/küçük harf eşleştirme desteklenir.

![Visual Studio ' de tümüne git](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Kod stili kurallarını zorla

Kodlama kurallarını birlikte kullanmak ve kaynak ile seyahat etmek için bir EditorConfig dosyası kullanabilirsiniz.

![Visual Studio 'de kod stili zorlama](../ide/media/VSGuide_CodeStyle.png)

- Varsayılan bir veya ekleyin. Yeni öğe Ekle seçeneğini belirleyerek projenize net stil editorconfig dosyası **ekleyin**  >  . **Yeni öğe Ekle** iletişim kutusunda, "editorconfig" ifadesini aratın. **Editorconfig dosyası** öğe şablonlarından birini seçin ve ardından **Ekle**' yi seçin.

   ![Visual Studio 'de EditorConfig öğe şablonları](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- **Araçlar** Seçenekler  >  > **metin Düzenleyicisi** > **C#** > **kod stili** içindeki kod stili ayarlarınıza göre otomatik olarak bir. editorconfig dosyası oluşturun.

   ![VS 2019 ' deki ayarlardan. editorconfig dosyası oluştur](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Visual Studio için ıntellicode 'un [kod çıkarımı özelliği](/visualstudio/intellicode/code-style-inference) , mevcut koddan kod stillerinizi kodlar. Daha sonra, kod stili tercihleriniz zaten tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Bir kod stili kuralının önem düzeyini doğrudan düzenleyici aracılığıyla yapılandırın. Şu anda bir. editorconfig dosyanız yoksa, sizin için bir tane oluşturulur. İmlecinizi hata, uyarı veya öneriye yerleştirin ve **CTRL** yazın + **.** Hızlı Eylemler ve yeniden düzenlemeler menüsünü açmak için. **Sorunları Yapılandır veya gizle**' yi seçin. Daha sonra kuralı seçin ve bu kural için yapılandırmak istediğiniz önem derecesini seçin. Bu, mevcut EditorConfig dosyanızı kuralın yeni önem derecesiyle güncelleştirir.

   ![Bir kod stili kuralının önem düzeyini doğrudan düzenleyicide yapılandırma](../ide/media/configure-severity-level.png)

[.Net kodlama kuralı seçenekleri](/dotnet/fundamentals/code-analysis/code-style-rule-options) belgelerine göz atın ve bu da tüm editorconfig dosyasına bir örnek içerir.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Kod temizleme

Visual Studio, kod **temizleme** özelliği aracılığıyla kod stili tercihleri de dahil olmak üzere kod dosyanız için isteğe bağlı biçimlendirme sağlar. Kod temizlemeyi çalıştırmak için düzenleyicinin altındaki Broom simgesine tıklayın veya **CTRL** + **K**, **CTRL** + **E** tuşlarına basın.

![Visual Studio 2019 ' de kod temizleme düğmesi](media/execute-code-cleanup.png)

Ayrıca, tüm proje veya çözümünüz genelinde kod temizleme işlemini de çalıştırabilirsiniz. **Çözüm Gezgini**' de proje veya çözüm adına sağ tıklayın, **Çözümle ve kod temizleme**' yi seçin ve ardından **kod temizlemeyi Çalıştır**' ı seçin.

![Project veya çözüm genelinde kod temizlemeyi çalıştır](media/run-code-cleanup-project-solution.png)

Dosyanızı boşluk, girintiler, et cetera için biçimlendirmeye ek olarak, **kod temizleme** de seçili kod stilleri uygular. Her kod stili için tercihleriniz, proje için bir tane varsa veya **Seçenekler** iletişim kutusundaki [kod stili ayarlarından](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) , [editorconfig dosyasından](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)okunurdur.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Yeniden düzenlemeler ve kod düzeltmeleri

Visual Studio, çok sayıda yeniden düzenlemeler, kod oluşturma eylemi ve kod düzeltmesiyle birlikte gelir. Red dalgalı çizgiler hataları, yeşil dalgalı çizgiler uyarıları temsil eder ve üç gri noktayla kod önerilerini temsil eder. Ampul veya screwsürücü simgesine tıklayarak veya **CTRL** tuşuna basarak kod düzeltmelere erişebilirsiniz + **.** veya **alt** + **girin**. Her bir onarım, düzeltmesinin nasıl çalıştığına ilişkin canlı bir kod farkı gösteren bir önizleme penceresiyle birlikte gelir.

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
- [Visual Studio için SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [Stylecopçözümleyiciler](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [Visual Studio için SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [Stylecopçözümleyiciler](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Visual Studio yeniden düzenlemeler](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Kullanımlar bulun, uygulamaya gidin ve derlenmiş derlemelere gidin

Visual Studio kodunuzda arama ve [gezinmenize](../ide/navigating-code.md)yardımcı olacak birçok özellik vardır.

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

yalnızca alfabetik bir liste yerine [bağlam kullanan kod tamamlamalar](/visualstudio/intellicode/intellicode-visual-studio) almak için Visual Studio için ıntellicode kullanın. Ayrıca, kendi etki alanına özgü kitaplıklarınızı temel alarak [özel bir IntelliSense modeli](/visualstudio/intellicode/custom-model-faq) de eğitebilirsiniz.

## <a name="unit-testing"></a>Birim testi

Visual Studio 2017 ' den başlayarak, test deneyiminde birçok iyileştirme vardır. MSTest v1, MSTest v2, NUnit veya XUnit test çerçeveleri ile test edebilirsiniz.

- **Test Gezgini** test keşfi hızlıdır.

- Testleri **Test Gezgini** 'nde *hiyerarşik sıralamaya* göre düzenleyin.

   ![Visual Studio metin Gezgini için hiyerarşi görünümü](../ide/media/VSGuide_Testing.png)

- [Canlı birim testi](../test/live-unit-testing.md) , kod değişikliklerinden etkilenen testleri sürekli çalıştırır ve testlerinizin durumunu bilmenizi sağlamak için satır içi düzenleyici simgelerini güncelleştirir. Canlı test kümesinden belirli testleri veya test projelerini dahil edin veya hariç tutun. (yalnızca Visual Studio Enterprise edition.)

## <a name="debugging"></a>Hata Ayıklama

Visual Studio hata ayıklama özellikleri şunlardır:

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

![Visual Studio özel durum Yardımcısı](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Sürüm denetimi

Visual Studio ' de kodunuzu depolamak ve güncelleştirmek için git veya TFVC kullanabilirsiniz.

::: moniker range=">=vs-2019"

- Visual Studio çıkmadan çekme isteklerini oluşturmak, gözden geçirmek, kullanıma almak ve çalıştırmak için [Visual Studio için çekme isteklerini](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) yükler.

::: moniker-end

- [Takım Gezgini](reference/team-explorer-reference.md) 'de yerel değişikliklerinizi düzenleyin ve bekleyen işlemeler ve değişiklikleri izlemek için durum çubuğunu kullanın.

- [Visual Studio uzantısı için sürekli teslim araçlarıyla](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) Visual Studio içindeki ASP.NET projeleriniz için sürekli tümleştirme ve dağıtım ayarlayın.

![Visual Studio kaynak denetimi](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Ne öğrenmek gerekir?

Kod yazmayı daha verimli hale getirmek için düzenleyici ve üretkenlik özelliklerinin bir listesi aşağıda verilmiştir. Varsayılan olarak kapalı olduklarından bazı özelliklerin etkinleştirilmesi gerekebilir (bunlar makinenizde dizin oluşturabilir, controversıal veya şu anda deneysel).

| Özellik | Ayrıntılar | Nasıl etkinleştirilir |
|-|-|-|
| Dosyayı Çözüm Gezgini bul | **Çözüm Gezgini** 'de etkin dosyayı vurgular | **Araçlar**  >  **Seçenekler**  >  **Projeler ve çözümler**  >  **Çözüm Gezgini etkin öğeyi izle** |
| başvuru derlemelerindeki ve NuGet paketlerindeki türler için using 'ler ekleyin | başvurulmayan bir tür için NuGet paketini yüklemek üzere kod düzeltmesinin bulunduğu bir hata ampul gösterir | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **başvuru derlemelerindeki türler için kullanımlar önerin** ve **NuGet paketlerindeki türler için kullanımlar** önerin |
| Tam çözüm analizini etkinleştirme | **Hata listesi** çözümünüzdeki tüm hataları görün | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Tam çözüm analizini etkinleştir** |
| Derlenmekte olan kaynaklara gezinmeyi etkinleştir | Dış kaynaklardaki türlerde/üyelerde tanıma git 'e izin ver ve Yöntem gövdelerini göstermek için ılspy kaynak koda dönüştürücü kullanın | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Derlenmekte olan kaynaklara gezinmeyi etkinleştir** |
| Tamamlama/öneri modu | IntelliSense 'de tamamlama davranışını değiştirir. IntelliJ arka planlarına sahip geliştiriciler burada varsayılan olmayan bir ayar kullanmaya eğilimlidir. | **Menü**  >  **Düzenle**  >  **IntelliSense**  >  **Tamamlama modunu aç** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Düzenleyicide kod başvuru bilgilerini ve değişiklik geçmişini görüntüler. (kaynak denetimi codelens göstergeleri Visual Studio Community sürümünde kullanılamaz.) | **Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **Tüm diller**  >  **CodeLens** |
| [Kod parçacıkları](../ide/visual-csharp-code-snippets.md) | Ortak ortak kod saplamaya yardımcı olma | Bir kod parçacığı adı yazın ve **Tab** tuşuna iki kez basın. |
