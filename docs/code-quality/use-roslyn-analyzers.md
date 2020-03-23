---
title: Çözümleyici kural şiddeti ve bastırma
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431416"
---
# <a name="use-code-analyzers"></a>Kod çözümleyicileri kullanma

.NET Derleyici Platformu ("Roslyn") kod analizörleri yazarken C# veya Visual Basic kodunuzu analiz eder. Her *tanılama* veya kural, projeniz için üzerine yazılabilir varsayılan önem ve bastırma durumu vardır. Bu makalede, kural önem derecelerini ayarlama, kural kümelerini kullanma ve ihlalleri bastırma yı kapsar.

## <a name="analyzers-in-solution-explorer"></a>Çözüm Gezgini'nde Çözüm Leyiciler

**Çözüm**Gezgini'nden çözümleyici tanılama özelleştirmesinin çoğunu yapabilirsiniz. [Çözümleyicileri](../code-quality/install-roslyn-analyzers.md) NuGet paketi olarak yüklerseniz, **Çözüm Gezgini'ndeki** **Başvurular** veya **Bağımlılıklar** düğümüaltında bir **Çözümleyici** düğümü görüntülenir. **Çözümleyicileri**genişletir ve çözümleyici derlemelerinden birini genişletirseniz, derlemedeki tüm tanılamaları görürsünüz.

![Çözüm Gezgini'nde çözümleyici düğümü](media/analyzers-expanded-in-solution-explorer.png)

**Özellikler** penceresinde, açıklaması ve varsayılan önem derecesi de dahil olmak üzere tanılamanın özelliklerini görüntüleyebilirsiniz. Özellikleri görüntülemek için kurala sağ tıklayın ve **Özellikler'i**seçin veya kuralı seçin ve **alt**+**enter**tuşuna basın.

![Özellikler penceresinde tanılama özellikleri](media/analyzer-diagnostic-properties.png)

Tanılama için çevrimiçi belgeleri görmek için tanılama üzerine sağ tıklayın ve **Yardım'ı Görüntüle'yi**seçin.

**Çözüm Gezgini'ndeki** her tanılamanın yanındaki simgeler, düzenleyicide açtığınızda kural kümesinde gördüğünüz simgelere karşılık gelir:

- dairedeki "x" **Hatanın** [şiddetini](#rule-severity) gösterir
- üçgendeki "!" **Uyarının** [şiddetini](#rule-severity) gösterir
- bir dairedeki "i" **Bilginin** [şiddetini](#rule-severity) gösterir
- açık renkli bir arka plan üzerinde bir daire içinde "i" **Gizli** bir [şiddeti](#rule-severity) gösterir
- bir daire içinde aşağı doğru işaret eden ok, tanılamanın bastırılmış olduğunu gösterir

![Çözüm Gezgini'nde tanılama simgeleri](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Kural şiddeti

::: moniker range=">=vs-2019"

Çözümleyici kurallarının veya *tanılamanın*önem derecesini, [çözümleyicileri](../code-quality/install-roslyn-analyzers.md) NuGet paketi olarak yüklerseniz yapılandırabilirsiniz. Visual Studio 2019 sürüm 16.3'ten başlayarak, bir [EditorConfig dosyasındaki](#set-rule-severity-in-an-editorconfig-file)kuralın önem derecesini yapılandırabilirsiniz. Bir kuralın önem derecesini [Çözüm Gezgini'nden](#set-rule-severity-from-solution-explorer) veya [kural kümesi dosyasından](#set-rule-severity-in-the-rule-set-file)da değiştirebilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

Çözümleyici kurallarının veya *tanılamanın*önem derecesini, [çözümleyicileri](../code-quality/install-roslyn-analyzers.md) NuGet paketi olarak yüklerseniz yapılandırabilirsiniz. Bir kuralın önem derecesini [Çözüm Gezgini'nden](#set-rule-severity-from-solution-explorer) veya [kural kümesi dosyasından](#set-rule-severity-in-the-rule-set-file)değiştirebilirsiniz.

::: moniker-end

Aşağıdaki tabloda farklı önem seçenekleri gösterilmektedir:

| Önem derecesi (Çözüm Gezgini) | Önem derecesi (EditorConfig dosyası) | Oluşturma zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller Hata Listesinde ve komut satırı oluşturma çıktısında *hatalar* olarak görünür ve yapılarda başarısız lığa neden olur.| Kusurlu kod kırmızı bir dalgalı ile altı çizilir ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenir. |
| Uyarı | `warning` | İhlaller Hata Listesinde ve komut satırı oluşturma çıktısında *Uyarılar* olarak görünür, ancak yapılarda başarısızlığa neden olmaz. | Kusurlu kod yeşil bir dalgalı ile altı çizilir ve kaydırma çubuğunda küçük bir yeşil kutu ile işaretlenir. |
| Bilgi | `suggestion` | İhlaller Hata Listesinde *İletiler* olarak görünür ve komut satırı oluşturma çıktısında hiç görünmez. | Kusurlu kod gri bir dalgalı ile altı çizilir ve kaydırma çubuğunda küçük bir gri kutu ile işaretlenir. |
| Gizli | `silent` | Kullanıcı tarafından görülemez. | Kullanıcı tarafından görülemez. Ancak tanı, IDE tanı motoruna bildirilir. |
| None | `none` | Tamamen bastırılmış. | Tamamen bastırılmış. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kuralın varsayılan değerinin ne olduğunu belirlemek için Özellikler penceresinden bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Kod düzenleyicisinin aşağıdaki ekran görüntüsü, farklı önemlere sahip üç farklı ihlali gösterir. Sağdaki kaydırma çubuğundaki dalgalı rengin rengine ve küçük renkli kareye dikkat edin.

![Kod düzenleyicisinde hata, uyarı ve bilgi ihlali](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsü, Hata Listesinde göründükleri gibi aynı üç ihlali gösterir:

![Hata Listesinde hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>EditorConfig dosyasında kural önem derecelerini ayarlama

(Visual Studio 2019 sürüm 16.3 ve sonrası)

Derleyici uyarıları veya çözümleyici kurallarının önem derecesini bir EditorConfig dosyasında aşağıdaki sözdizimi ile ayarlayabilirsiniz:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Bir DüzenleyiciConfig dosyasında bir kuralın önem derecelerini ayarlamak, bir kural kümesinde veya Solution Explorer'da ayarlanan önem açısından önceliklidir. Bir EditorConfig dosyasında veya ihlalin yanında görünen ampul aracılığıyla [önem](#automatically-configure-rule-severity) derecesini [el ile](#manually-configure-rule-severity) yapılandırabilirsiniz.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>EditorConfig dosyasında birden çok çözümleyici kuralının kural önem derecesini aynı anda ayarlama

(Visual Studio 2019 sürüm 16.5 ve sonrası)

Bir EditorConfig dosyasında tek bir girişle belirli bir çözümleyici kuralları kategorisi nin veya tüm çözümleyici kurallarının önem derecesini ayarlayabilirsiniz.

- Çözümleyici kuralları kategorisi için kural önem derecesini ayarlayın:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Tüm çözümleyici kuralları için kural önem derecelerini ayarlayın:

`dotnet_analyzer_diagnostic.severity = <severity>`

Belirli bir kural kimliği için geçerli olan birden çok girişiniz varsa, geçerli girişi seçmek için öncelik sırası aşağıdakigibidir:

- Kimlik tarafından tek bir kural için önem girişi, bir kategoriiçin önem girişinden önce gelir.
- Bir kategoriiçin önem girişi, tüm çözümleyici kuralları için önem girişinden önce gelir.

[CA1822'nin](https://docs.microsoft.com/visualstudio/code-quality/ca1822) "Performans" kategorisine sahip olduğu aşağıdaki EditorConfig örneğini göz önünde bulundurun:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Önceki örnekte, üç giriş de CA1822 için geçerlidir. Ancak, belirtilen öncelik kurallarını kullanarak, ilk kural kimliği tabanlı önem girişi sonraki girişleri kazanır. Bu örnekte, CA1822 "hata" etkili bir öneme sahip olacaktır. "Performans" kategorisi ile kalan tüm kurallar önem "uyarı" olacaktır. "Performans" kategorisi olmayan kalan tüm çözümleyici kurallarının önem derecesi "öneri" olacaktır.

#### <a name="manually-configure-rule-severity"></a>Kural önem derecelerini el ile yapılandırır

1. Projeniz için zaten bir EditorConfig dosyanız yoksa, [bir tane ekleyin.](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. İlgili dosya uzantısı altında yapılandırmak istediğiniz her kural için bir giriş ekleyin. Örneğin, [CA1822'nin](ca1822.md) önem derecesini `error` C# dosyaları için ayarlamak için giriş aşağıdaki gibi görünür:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> IDE kod stili çözümleyiciler için, bunları bir EditorConfig dosyasında farklı bir sözdizimi kullanarak da yapılandırabilirsiniz, örneğin. `dotnet_style_qualification_for_field = false:suggestion` Ancak, `dotnet_diagnostic` sözdizimini kullanarak bir önem kümesi ayarlarsanız, öncelik alır. Daha fazla bilgi [için EditorConfig için Dil kurallarına](../ide/editorconfig-language-conventions.md)bakın.

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Varolan bir Ruleset dosyasını EditorConfig dosyasına dönüştürme

Visual Studio 2019 sürüm 16.5'ten başlayarak, ruleset dosyaları yönetilen kod için çözümleyici yapılandırması için EditorConfig dosyası lehine amortismana alınır. Çözümleyici kural önem verme yapılandırması için Visual Studio aracının çoğu, kural kümesi dosyaları yerine EditorConfig dosyaları üzerinde çalışacak şekilde güncelleştirildi. EditorConfig dosyaları, Visual Studio IDE kod stili seçenekleri de dahil olmak üzere hem çözümleyici kural önemderecelerini hem de çözümleyici seçeneklerini yapılandırmanızı sağlar. Varolan kural kümesi dosyanızı Bir EditorConfig dosyasına dönüştürmeniz önerilir. Ayrıca, EditorConfig dosyasını repo'nuzun köküne veya çözüm klasörüne kaydetmeniz önerilir. Repo veya çözüm klasörünüzün kökünü kullanarak, bu dosyadaki önem ayarlarının sırasıyla tüm repo veya çözüme otomatik olarak uygulandığından emin olabilirsiniz.

Varolan bir kural kümesi dosyasını EditorConfig dosyasına dönüştürmenin birkaç yolu vardır:

- Visual Studio'daki Ruleset Editor'dan (Visual Studio 2019 16.5 veya sonrası gerektirir). Projeniz zaten belirli bir kural kümesi `CodeAnalysisRuleSet`dosyasını kendi olarak kullanıyorsa, visual studio'daki Ruleset Editor'dan eşdeğer bir EditorConfig dosyasına dönüştürebilirsiniz.

    1. Solution Explorer'da kural kümesi dosyasına çift tıklayın.

       Ruleset dosyası Ruleset Düzenleyicisi'nde açılmalıdır. Kural kümesi düzenleyicisinin üst kısmında tıklanabilir bir **bilgi çubuğu** görmeniz gerekir.

       ![Ruleset Düzenleyici'de Ruleset'i EditorConfig dosyasına dönüştürün](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Bilgi çubuğu bağlantısını **tıklatın.**

       Bu, EditorConfig dosyasını oluşturmak istediğiniz dizin seçmenize olanak tanıyan Bir **Olarak Kaydet** iletişim kutusunu açmalıdır.

    3. EditorConfig dosyasını oluşturmak için **Kaydet** düğmesini **tıklatın.**

       Oluşturulan EditorConfig editörde açılmalıdır. Ayrıca, MSBuild özelliği `CodeAnalysisRuleSet` artık özgün kural kümesi dosyasına başvurulamayacak şekilde proje dosyasında güncelleştirilir.

- Komut satırından:

    1. NuGet paketi [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter yükleyin.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)

    2. Yüklü `RulesetToEditorconfigConverter.exe` paketten, kural kümesi dosyasına ve EditorConfig dosyasına komut satırı bağımsız değişkenleri olarak giden yollar ile çalıştırın.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Burada dönüştürmek için bir örnek kural kümesi dosyası:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Burada dönüştürülmüş EditorConfig dosyası:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```

#### <a name="automatically-configure-rule-severity"></a>Kural önem derecelerini otomatik olarak yapılandırır

##### <a name="configure-from-light-bulb-menu"></a>Ampul menüsünden yapılandır

Visual [Studio, Quick Actions](../ide/quick-actions.md) ampul menüsünden bir kuralın şiddetini yapılandırmak için kullanışlı bir yol sağlar.

1. Bir ihlal oluştuktan sonra, düzenleyicide ihlal squiggle üzerinde gezinmek ve ampul menüsünü açın. Veya imlecinizi çizgiye koyun ve **Ctrl**+tuşuna**basın.** (dönem).

2. Ampul menüsünden, Kural Kimliğini> > **önem \<derecesini** **yapılandır'ı yapılandır veya bastır'ı** seçin.

   ![Visual Studio'da ampul menüsünden kural şiddetini yapılandır](media/configure-rule-severity.png)

3. Buradan önem seçeneklerinden birini seçin.

   ![Öneri olarak kural önem derecelerini yapılandır](media/configure-rule-severity-suggestion.png)

   Visual Studio, önizleme kutusunda gösterildiği gibi kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede zaten bir EditorConfig dosyanız yoksa, Visual Studio sizin için bir dosya oluşturur.

##### <a name="configure-from-error-list"></a>Hata listesinden yapılandırma

Visual Studio ayrıca hata listesi bağlam menüsünden bir kuralın önem derecesini yapılandırmak için kullanışlı bir yol sağlar.

1. Bir ihlal oluştuktan sonra, hata listesindeki tanılama girişini sağ tıklatın.

2. Bağlam menüsünden **önem derecesini ayarla'yı**seçin.

   ![Visual Studio'daki hata listesinden kural önem derecelerini yapılandırma](media/configure-rule-severity-error-list.png)

3. Buradan önem seçeneklerinden birini seçin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede zaten bir EditorConfig dosyanız yoksa, Visual Studio sizin için bir dosya oluşturur.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Solution Explorer'dan kural önem derecelerini ayarlama

1. Çözüm Gezgini'nde, **Başvuru** > **çözümleyicilerini** (veya .NET Core projeleri için Bağımlılık**Çözümleyicileri)** **Dependencies** > genişletin.

2. Önem derecesini ayarlamak istediğiniz kuralı içeren derlemeyi genişletin.

::: moniker range=">=vs-2019"
3. Kuralı sağ tıklatın ve **önem derecesini ayarla'yı**seçin. Bağlam menüsünde önem seçeneklerinden birini seçin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler. Projeniz EditorConfig dosyası yerine bir kural kümesi dosyası kullanıyorsa, önem girişi kural kümesi dosyasına eklenir.

   > [!TIP]
   > Projede zaten bir EditorConfig dosyanız veya kural kümesi dosyanız yoksa, Visual Studio sizin için yeni bir EditorConfig dosyası oluşturur.
::: moniker-end

::: moniker range="vs-2017"
3. Kuralı sağ tıklatın ve **Kural Kümesi Önem Ayarla'yı**seçin. Bağlam menüsünde önem seçeneklerinden birini seçin.

   Kuralın önem derecesi etkin kural kümesi dosyasına kaydedilir.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Kural kümesi dosyasında kural önem derecesini ayarlama

![Çözüm Gezgini'nde kural kümesi dosyası](media/ruleset-in-solution-explorer.png)

1. **Çözüm Gezgini'nde**çift tıklatarak, Başvuru**analizleyiciler** **References** > düğümünün sağ tıklama menüsünde **Etkin Kural Kümesi'ni** seçerek veya proje için **Kod Analizi** özellik sayfasında **Aç'ı** seçerek etkin kural kümesi dosyasını açın.

   Kural kümesini ilk kez bu kez düzenliyorsanız, Visual Studio varsayılan kural kümesi dosyasının bir kopyasını yapar, * \<proje adını>.ruleset*olarak adlandırır ve projenize ekler. Bu özel kural kümesi, projeniz için etkin kural kümesi de olur.

   > [!NOTE]
   > .NET Core ve .NET Standard **projeleri, Çözüm Gezgini'ndeki**kural kümeleri için menü komutlarını desteklemez , örneğin, **Etkin Kural Kümesini Aç.** Bir .NET Core veya .NET Standard projesi için varsayılan olmayan bir kural kümesi belirtmek [ **için, CodeAnalysisRuleSet** özelliğini](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) proje dosyasına el ile ekleyin. Visual Studio kural kümesi düzenleyici UI'de belirlenen kural dahilindeki kuralları yine de yapılandırabilirsiniz.

1. İçerdeki derlemesini genişleterek kurala göz atın.

1. **Eylem** sütununda, açılır liste açmak için değeri seçin ve listeden istenen önem derecesini seçin.

   ![Düzenleyicide kural kümesi dosyası açık](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>İhlalleri bastırma

Kural ihlallerini bastırmanın birden çok yolu vardır:

::: moniker range=">=vs-2019"

- **EditorConfig dosyasında**

  Önem derecesini `none`, örneğin, `dotnet_diagnostic.CA1822.severity = none`.

- **Analiz** menüsünden

  Tüm geçerli ihlalleri bastırmak için menü çubuğundaki**Etkin Sorunları Oluştur'u çözümle'yi** **Analyze** > ve bunları bastır'ı seçin. Bu bazen "taban kaplaması" olarak adlandırılır.

::: moniker-end

::: moniker range="vs-2017"

- **Analiz** menüsünden

  Geçerli tüm ihlalleri bastırmak için Kod**Çözümle'yi ve** menü çubuğundaki Etkin Sorunları Bastır'ı **seçin.** >  Bu bazen "taban kaplaması" olarak adlandırılır.

::: moniker-end

- **Gönderen Çözüm Explorer**

  Kuralın önem derecesini **Yok**olarak ayarlayın.

- Kural **kümesi düzenleyicisinden**

  Adının yanındaki kutunun işaretini kaldırın veya **Eylem'i** **Yok**olarak ayarlayın.

- Kod **düzenleyicisinden**

  İmleci ihlalle birlikte kod satırına yerleştirin ve **Hızlı Eylemler** menüsünü açmak için **Ctrl**+**Period (.)** tuşuna basın. **Kaynak/Baskı Dosyasında** **CAXXXX'i** > Bastır'ı seçin.

  ![Hızlı eylemler menüsünden tanılamayı bastırma](media/suppress-diagnostic-from-editor.png)

- Hata **Listesinden**

  Bastırmak istediğiniz kuralları seçin ve ardından**Kaynak/In Bastırma Dosyasında** **Bastır'ı** > sağ tıklatın.

  - **Kaynak'ta**baskılarsanız, **Önizleme Değişiklikleri** iletişim kutusu açılır ve kaynak koduna eklenen C# [#pragma uyarısı](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) veya Visual Basic #Disable [uyarı](/dotnet/visual-basic/language-reference/directives/directives) yönergesinin önizlemesini gösterir.

    ![Kod dosyasına #pragma uyarı ekleme önizlemesi](media/pragma-warning-preview.png)

  - **Bastırma Dosyası'nda'yı**seçerseniz, **Önizleme Değişiklikleri** iletişim kutusu açılır <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ve genel bastırma dosyasına eklenen özniteliğin önizlemesini gösterir.

    ![Bastırma dosyasına SuppressMessage özniteliği ekleme önizlemesi](media/preview-changes-in-suppression-file.png)

  Değişiklikleri **Önizleme** iletişim kutusunda **Uygula'yı**seçin.

  > [!NOTE]
  > **Çözüm Gezgini'nde** **Suppress** menüsü seçeneğini görmüyorsanız, ihlal büyük olasılıkla canlı analizden değil, yapıdan gelir. **Hata Listesi,** hem canlı kod çözümlemesi hem de oluşturma hatalarını veya kural ihlallerini görüntüler. Yapı tanılama eski olabilir, örneğin, ihlali düzeltmek için kodu düzenlediyseniz ancak yeniden oluşturulmadıysa, bu tanılamaları **Hata Listesinden**bastıramazsınız. Canlı analiz veya IntelliSense'in tanılamaları her zaman güncel kaynaklardan haberdardır ve **Hata Listesinden**bastırılabilir. *Yapı* tanılamalarını seçiminizden hariç tutmak için, **Hata Listesi** kaynak filtresini Build **+ IntelliSense'den** **Yalnızca IntelliSense'e geçirin.** Ardından, bastırmak istediğiniz tanılamayı seçin ve daha önce açıklandığı gibi devam edin.
  >
  > ![Visual Studio'da Hata Listesi kaynak filtresi](media/error-list-filter.png)

## <a name="command-line-usage"></a>Komut satırı kullanımı

Projenizi komut satırında oluşturduğunuzda, aşağıdaki koşullar yerine getirildiğinde kural ihlalleri yapı çıktısında görünür:

- Çözümleyiciler VSIX uzantısı olarak değil, NuGet paketi olarak yüklenir.

- Proje kodunda bir veya daha fazla kural ihlal edilir.

- İhlal edilen bir kuralın önem **warning** [derecesi,](#rule-severity) yapının başarısız olması veya **hata**olması durumunda ihlallerin yapının başarısız olması durumunda uyarıda bulunan adada ayarlanır.

Yapı çıktısının ayrıntılılığı kural ihlallerinin gösterip gösterilmediğini etkilemez. **Sessiz** ayrıntılı olsa bile, kural ihlalleri yapı çıktısında görünür.

> [!TIP]
> *FxCopCmd.exe* veya **RunCodeAnalysis** bayrağıyla msbuild aracılığıyla komut satırından eski analizleri çalıştırmaya alışkınsanız, bunu kod çözümleyicileriyle şu şekilde yapabilirsiniz.

Msbuild kullanarak projenizi oluştururken komut satırında çözümleyici ihlallerini görmek için aşağıdaki gibi bir komut çalıştırın:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Aşağıdaki resimde, çözümleyici kural ihlali içeren bir proje oluşturma komut satırı yapı çıktısı gösterilmektedir:

![Kural ihlali ile MSBuild çıktısı](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Bağımlı projeler

Bir .NET Core projesinde, NuGet çözümleyicileri olan bir projeye bir başvuru eklerseniz, bu çözümleyiciler de bağımlı projeye otomatik olarak eklenir. Bu davranışı devre dışı kılabilir( örneğin bağımlı proje bir birim test projesiyse, NuGet paketini özel olarak *işaretleyin.csproj* veya başvurulan projenin *.vbproj* dosyasında **PrivateAssets** özniteliğini ayarlayarak:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da kod analizörlerinin genel görünümü](../code-quality/roslyn-analyzers-overview.md)
- [Kod çözümleyici sabunu gönderme](https://github.com/dotnet/roslyn-analyzers/issues)
- [Kural kümelerini kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Kod analizi uyarılarını bastırma](../code-quality/in-source-suppression-overview.md)
