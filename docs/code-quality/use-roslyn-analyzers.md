---
title: Çözümleyici yapılandırması
ms.date: 05/10/2021
description: Roslyn çözümleyici kurallarını özelleştirmeyi öğrenin. Bkz. çözümleyici önem derecelerine ayarlama, ihlalleri gösterme ve dosyaları oluşturulan kod olarak belirleme.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 79add0c27936b29d52f8fcbf903e62acfad6aa14
ms.sourcegitcommit: 1c0eda2db1b1fff9595ca644503f467bf3e223e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137094889"
---
# <a name="overview"></a>Genel Bakış

Her bir Roslyn *Çözümleyicisi veya* kuralı, bir varsayılan önem ve gizleme durumuna sahiptir ve projeniz için bu geçersiz kılınabilir ve özelleştirilebilir. Bu makalede, çözümleyici önem derecelerine ayarlama ve çözümleyici ihlallerinin gizlenmesi ele alınmaktadır.

## <a name="configure-severity-levels"></a>Önem düzeylerini yapılandırma

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16,3 ' den başlayarak, çözümleyici kurallarının önem derecesini veya *tanılamayı*, bir [editorconfig dosyasında](#set-rule-severity-in-an-editorconfig-file), [ampul menüsünden](#set-rule-severity-from-the-light-bulb-menu)ve hata listesinden yapılandırabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

çözümleyiciler NuGet paketi olarak [yüklüyorsanız](../code-quality/install-roslyn-analyzers.md) , çözümleyici kurallarının önem derecesini veya *tanılamayı* yapılandırabilirsiniz. Bir kuralın [Çözüm Gezgini](#set-rule-severity-from-solution-explorer) önem derecesini [bir kural kümesi dosyasında](#set-rule-severity-in-the-rule-set-file)değiştirebilirsiniz.

::: moniker-end

> [!NOTE]
> hatalar, derlemelerin Visual Studio başarısız olmasına neden olur, ancak [dotnet derlemesinin](/dotnet/core/tools/dotnet-build) başarısız olmasına neden olmak için `enforcecodestyleinbuild` `true` [proje özellikleri sayfasında](/dotnet/core/project-sdk/msbuild-props#enforcecodestyleinbuild)olarak ayarlamanız gerekir.

Aşağıdaki tabloda farklı önem derecesi seçenekleri gösterilmektedir:

| Önem derecesi (Çözüm Gezgini) | Önem derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *hata* olarak görünür ve yapıların başarısız olmasına neden olur.| Sorunlu kodun kırmızı renkli bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenir. |
| Uyarı | `warning` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *Uyarı* olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Sorunlu kodun yeşil bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir yeşil kutu ile işaretlenir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıktısında değil, Hata Listesi *iletiler* olarak görünür. | Sorunlu kodun gri dalgalı çizgi ile altı çizilir ve kaydırma çubuğundaki küçük bir gri kutusuyla işaretlenir. |
| Gizli | `silent` | Kullanıcıya görünür değil. | Kullanıcıya görünür değil. Ancak tanılama, IDE tanılama altyapısına bildirilir. |
| Hiçbiri | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kural için varsayılan değerin ne olduğunu belirlemek için Özellikler penceresi bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (sorunlu kod altında bir *dalgalı çizgi* olarak) ve hata listesi penceresinde raporlanır.

Hata listesinde bildirilen çözümleyici ihlalleri kuralın [önem derecesi düzeyi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eşleşir. Çözümleyici ihlalleri Ayrıca kod düzenleyicisinde, sorunlu kodun altında dalgalı çizgiler olarak görünür. Aşağıdaki görüntüde &mdash; bir hata (kırmızı dalgalı çizgi), bir uyarı (yeşil dalgalı çizgi) ve bir öneri (üç gri noktalı) olmak üzere üç ihlal gösterilmektedir:

![Visual Studio kod düzenleyicisinde dalgalı çizgiler](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsünde Hata Listesi göründükleri üç ihlal gösterilmektedir:

![Hata Listesi hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

Birçok çözümleyici kuralı veya *tanılaması*, kural ihlalini düzeltmek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmesiyle* sahiptir. Kod düzeltmeleri, ampul simgesi menüsünde diğer [hızlı eylem](../ide/quick-actions.md)türleriyle birlikte gösterilir. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Genel Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve hızlı eylem kodu onarımı](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>' Hidden ' önem derecesine ve ' none ' önem derecesine karşı

`Hidden` Varsayılan olarak etkinleştirilen önem kuralları, devre dışı veya `None` önem kurallarından birkaç yolla farklıdır.

- bir önem derecesi kuralı için herhangi bir kod onarımı kaydedilmişse `Hidden` , gizli tanı kullanıcıya görünür olmasa bile, bu, Visual Studio ' de bir hafif ampul kodu yeniden düzenleme eylemi olarak sunulur. Devre dışı bırakılan önem kuralları için bu durum değildir `None` .
- `Hidden` önem derecesi kuralları, [birden çok çözümleyici kuralının kural önem derecesini bir EditorConfig dosyasında bir kez ayarlanmış](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file)girişler tarafından toplu olarak yapılandırılabilir. `None` önem derecesi kuralları bu şekilde yapılandırılamaz. Bunun yerine, [her kural kimliği için bir EditorConfig dosyasında kural önem derecesi ayarlanmış](#set-rule-severity-in-an-editorconfig-file)girişler aracılığıyla yapılandırılması gerekir.

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Bir EditorConfig dosyasında kural önem derecesini ayarlama

(Visual Studio 2019 sürüm 16,3 ve üzeri)

Aşağıdaki söz dizimine sahip bir EditorConfig dosyasındaki Derleyici uyarıları veya çözümleyici kuralları için önem derecesini ayarlayabilirsiniz:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Bir EditorConfig dosyasında bir kuralın önem derecesini ayarlamak, bir kural kümesinde veya Çözüm Gezgini ayarlanan herhangi bir önem derecesine göre önceliklidir. Bir EditorConfig dosyasındaki önem derecesini [el ile](#manually-configure-rule-severity-in-an-editorconfig-file) yapılandırabilir veya bir ihlalin yanında görünen ampul aracılığıyla [otomatik olarak](#set-rule-severity-from-the-light-bulb-menu) yapılandırabilirsiniz.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Birden çok çözümleyici kuralının kural önem derecesini bir EditorConfig dosyasında bir kez ayarlama

(Visual Studio 2019 sürüm 16,5 ve üzeri)

Belirli bir çözümleyici kuralları kategorisi veya bir EditorConfig dosyasında tek girişli tüm çözümleyici kuralları için önem derecesini ayarlayabilirsiniz.

- Çözümleyici kuralları kategorisi için kural önem derecesini ayarlayın:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Tüm çözümleyici kuralları için kural önem derecesini ayarla:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Birden çok çözümleyici kuralını tek seferde yapılandırma girişleri yalnızca *Varsayılan olarak etkinleştirilen* kurallar için geçerlidir. Çözümleyici paketinde varsayılan olarak devre dışı olarak işaretlenen çözümleyici kuralları açık girişler aracılığıyla etkinleştirilmelidir `dotnet_diagnostic.<rule ID>.severity = <severity>` .

Belirli bir kural KIMLIĞI için geçerli olan birden çok girdiniz varsa, uygulanabilir girişi seçmek için öncelik sırası aşağıda verilmiştir:

- Tek bir kural için önem derecesi girişi, bir kategori için önem derecesine göre öncelik alır.
- Bir kategori için önem derecesi, tüm çözümleyici kuralları için önem derecesine göre öncelik girişi alır.

Aşağıdaki EditorConfig örneğini göz önünde bulundurun, burada [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) "Performance" kategorisine sahiptir:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Yukarıdaki örnekte, üç girişin tümü CA1822 için geçerlidir. Bununla birlikte, belirtilen öncelik kurallarını kullanarak, sonraki girişler üzerinden WINS ilk kural KIMLIĞI tabanlı önem derecesi girişi. Bu örnekte, CA1822 "Error" etkili bir önem derecesine sahip olacaktır. "Performans" kategorisindeki tüm kalan kuralların önem derecesi "uyarı" olacaktır. "Performans" kategorisine sahip olmayan tüm geri kalan çözümleyici kurallarının önem derecesi "önerisi" olacaktır.

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Bir EditorConfig dosyasında kural önem derecesini el ile yapılandırma

1. Projeniz için zaten bir EditorConfig dosyanız yoksa, [bir tane ekleyin](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Karşılık gelen dosya uzantısı altında yapılandırmak istediğiniz her kural için bir giriş ekleyin. Örneğin, [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) için önem derecesini C# dosyaları için ayarlamak üzere `error` , giriş aşağıdaki gibi görünür:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> IDE kod stili Çözümleyicileri için, bunları bir EditorConfig dosyasında farklı bir sözdizimi kullanarak da yapılandırabilirsiniz, örneğin, `dotnet_style_qualification_for_field = false:suggestion` . Ancak, söz dizimini kullanarak önem derecesi ayarlarsanız `dotnet_diagnostic` , öncelik kazanır. Daha fazla bilgi için bkz. [EditorConfig Için dil kuralları](/dotnet/fundamentals/code-analysis/style-rules/language-rules).

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Ampul menüsünden Kural önem derecesini ayarlama

Visual Studio, bir kuralın önem derecesini [hızlı eylemler](../ide/quick-actions.md) ampul menüsünden yapılandırmanın kolay bir yolunu sağlar.

1. Bir ihlal oluştuktan sonra, düzenleyicide ihlalin üzerine gelin ve ampul menüsünü açın. Ya da imlecinizi satıra yerleştirip **CTRL** tuşuna basın + **.** (nokta).

2. Ampul menüsünde **yapılandırma veya gizleme sorunları** > **yapılandırma \<rule ID> önem derecesi**' ni seçin.

   ![Visual Studio 'teki ampul menüsünden Kural önem derecesini yapılandırma](media/configure-rule-severity.png)

3. Buradan, önem derecesi seçeneklerinden birini belirleyin.

   ![Öneri olarak kural önem derecesini yapılandırma](media/configure-rule-severity-suggestion.png)

   Visual Studio, önizleme kutusunda gösterildiği gibi, kuralı istenen düzeye yapılandırmak için editorconfig dosyasına bir giriş ekler.

   > [!TIP]
   > projede zaten bir editorconfig dosyanız yoksa Visual Studio sizin için bir tane oluşturur.

### <a name="set-rule-severity-from-the-error-list-window"></a>Hata Listesi penceresinden kural önem derecesini ayarlama

Visual Studio ayrıca, hata listesi bağlam menüsünden bir kuralın önem derecesini yapılandırmak için kullanışlı bir yol sağlar.

1. Bir ihlal oluştuktan sonra, hata listesindeki tanılama girdisini sağ tıklatın.

2. Bağlam menüsünde **önem derecesi ayarla**' yı seçin.

   ![Visual Studio içindeki hata listesinden kural önem derecesini yapılandırma](media/configure-rule-severity-error-list.png)

3. Buradan, önem derecesi seçeneklerinden birini belirleyin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için editorconfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede henüz bir EditorConfig dosyanız yoksa, sizin Visual Studio bir tane oluşturur.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecelerini Çözüm Gezgini

Çözümleyici tanılamalarını özelleştirmenin büyük bir **Çözüm Gezgini.** Çözümleyicileri [bir çözümleyici](../code-quality/install-roslyn-analyzers.md) paketi NuGet,  Çözüm Gezgini'daki Başvurular veya Bağımlılıklar **düğümü** altında **bir Çözümleyiciler Çözüm Gezgini.**  **Çözümleyiciler'i** ve ardından çözümleyici derlemelerinden birini genişlettiklerinde, derlemede tüm tanılamaları görüyorsunuz.

![Çözüm Gezgini'de çözümleyiciler düğümü](media/analyzers-expanded-in-solution-explorer.png)

Özellikler penceresinde bir tanılamanın açıklamasını ve varsayılan önem derecesini de içeren özelliklerini **görüntüebilirsiniz.** Özellikleri görüntülemek için kurala sağ tıklayın ve Özellikler'i **seçin** veya kuralı seçin ve ardından Alt Enter **tuşuna** + **basın.**

![Özellikler penceresi'de tanılama özellikleri](media/analyzer-diagnostic-properties.png)

Tanılamaya ilişkin çevrimiçi belgeleri görmek için tanılamaya sağ tıklayın ve Yardımı **Görüntüle'yi seçin.**

Her tanılamanın yanındaki **simgeler Çözüm Gezgini** düzenleyicide açarak kural kümesinde gördüğünüz simgelere karşılık gelecektir:

- Dairenin "x" değeri Hata [önem derecesine](#configure-severity-levels) **işaret**
- Bir üçgende yer alan "!" işareti Uyarı [önem derecesine](#configure-severity-levels) **işaret eder**
- Dairenin "i" değeri Bilgi [önem derecesine](#configure-severity-levels) **işaret**
- Açık renkli arka plandaki dairenin "i" değeri, Gizli [önem derecesine](#configure-severity-levels) işaret **eder**
- Dairenin aşağı dönük ok değeri tanılamanın gizleniyor olduğunu gösterir

![Çözüm Gezgini'de tanılama simgeleri](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Mevcut bir Kural Kümesi dosyasını EditorConfig dosyasına dönüştürme

2019 Visual Studio 16.5 sürümünden başlayarak, kural kümesi dosyaları yönetilen kod için çözümleyici yapılandırması için EditorConfig dosyası için kullanım dışıdır. Çözümleyici kuralı Visual Studio yapılandırmaya yönelik en önemli araç, kural kümesi dosyaları yerine EditorConfig dosyalarında çalışacak şekilde güncelleştirildi. EditorConfig dosyaları, IDE kod stili seçenekleri dahil olmak üzere hem çözümleyici kuralı Visual Studio çözümleyici seçeneklerini yapılandırmaya olanak sağlar. Mevcut kural kümesi dosyanızı bir EditorConfig dosyasına dönüştürmeniz kesinlikle önerilir. Ayrıca, EditorConfig dosyasını, repo'nizin köküne veya çözüm klasörüne kaydetmeniz de önerilir. Repo veya çözüm klasörünün kökünü kullanarak, bu dosyanın önem derecesi ayarlarının sırasıyla tüm repo veya çözüme otomatik olarak uygulandığından emin olursanız.

Mevcut bir kural kümesi dosyasını EditorConfig dosyasına dönüştürmenin birkaç yolu vardır:

- Visual Studio'daki Kural Kümesi Düzenleyicisi'nde (2019 16.5 veya sonraki bir Visual Studio gerektirir). Projeniz zaten olarak belirli bir kural kümesi dosyası kullanıyorsa, projenizin içindeki Kural Kümesi Düzenleyicisi'nde bunu eşdeğer bir `CodeAnalysisRuleSet` EditorConfig dosyasına Visual Studio.

    1. Dosyanın içinde kural kümesi dosyasına çift Çözüm Gezgini.

       Kural Kümesi dosyası Kural Kümesi Düzenleyicisi'nde açılmıştır. Kural kümesi düzenleyicisinin üst **kısmında tıklanabilir** bir bilgi çubuğu görüyor gerekir.

       ![Kural Kümesi Düzenleyicisi'nde Kural Kümesi'ni EditorConfig dosyasına dönüştürme](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Bilgi **çubuğu bağlantısını** seçin.

       Bunun, **EditorConfig dosyasını** oluşturmak istediğiniz dizini seçmenize olanak sağlayan bir Farklı Kaydet iletişim kutusu açması gerekir.

    3. EditorConfig **dosyasını** oluşturmak için Kaydet düğmesini seçin.

       Oluşturulan EditorConfig'in düzenleyicide açılması gerekir. Ayrıca, MSBuild özelliği, artık özgün kural kümesi dosyasına başvurulmayacak `CodeAnalysisRuleSet` şekilde proje dosyasında güncelleştirilir.

- Komut satırından:

    1. [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)paketini yükleyin. NuGet

    2. Kural kümesi dosyasının ve EditorConfig dosyasının yolları komut satırı bağımsız değişkenleri olarak `RulesetToEditorconfigConverter.exe` yüklü paketten yürütün.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Dönüştürülecek örnek bir kural kümesi dosyası şöyledir:

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

Dönüştürülen EditorConfig dosyası şu şekildedir:

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
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecelerini Çözüm Gezgini

1. Bu Çözüm Gezgini, Başvuru **Çözümleyicileri**  >  **(veya** .NET Core **projeleri için** Bağımlılık  >  **Çözümleyicileri)** genişletin.

2. Önem derecesini ayarlamak istediğiniz kuralı içeren derlemeyi genişletin.

::: moniker range=">=vs-2019"
3. Kurala sağ tıklayın ve Önem derecelerini **ayarla'yı seçin.** Bağlam menüsünde önem derecelerinden birini seçin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler. Projeniz EditorConfig dosyası yerine bir kural kümesi dosyası kullanıyorsa, önem derecesi girişi kural kümesi dosyasına eklenir.

   > [!TIP]
   > Projede editorConfig dosyası veya kural kümesi dosyası yoksa, Visual Studio yeni bir EditorConfig dosyası oluşturur.
::: moniker-end

::: moniker range="vs-2017"
3. Kurala sağ tıklayın ve Kural Kümesi **Önem Derecesine Ayarla'yı seçin.** Bağlam menüsünde önem derecelerinden birini seçin.

   Kuralın önem derecesi etkin kural kümesi dosyasına kaydedilir.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Kural kümesi dosyasında kural önem derecelerini ayarlama

![Dosyanın kural kümesi Çözüm Gezgini](media/ruleset-in-solution-explorer.png)

1. Etkin kural kümesi dosyasını aşağıdaki yöntemlerden birini ile açın:

- Bu **Çözüm Gezgini** dosyasına çift tıklayın, Başvurular Çözümleyicileri düğümüne sağ tıklayın ve Etkin Kural  >   Kümesi **Aç'ı seçin.**
- Projenin **Code Analysis** sayfasında Aç'ı **seçin.**

  Kural kümesi ilk kez düzen alıyorsanız Visual Studio varsayılan kural kümesi dosyasının bir kopyasını oluşturur, *\<projectname> .ruleset* olarak adlar ve projenize ekler. Bu özel kural kümesi ayrıca projeniz için etkin kural kümesi olur.

   > [!NOTE]
   > .NET Core ve .NET Standard projeleri, 'de kural kümeleri için menü komutlarını **desteklemez Çözüm Gezgini,** örneğin, **Etkin Kural Kümesi Aç.** Bir .NET Core veya .NET Standard için varsayılan olmayan bir kural kümesi belirtmek için [ **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) özelliğini proje dosyasına el ile ekleyin. Kural kümesi düzenleyicisi kullanıcı arabiriminde kural kümesi içinde Visual Studio yine de yapılandırabilirsiniz.

1. İçeren derlemesini genişleterek kurala göz at.

1. Eylem **sütununda,** açılan listeyi açmak için değeri seçin ve listeden istediğiniz önem derecesine tıklayın.

   ![Kural kümesi dosyası düzenleyicide açılır](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Oluşturulan kodu yapılandırma

Çözümleyiciler bir proje içinde tüm kaynak dosyaları üzerinde çalışır ve bunlar üzerinde ihlaller raporlar. Ancak, bu ihlaller tasarımcı tarafından oluşturulan kod dosyaları, derleme sistemi tarafından oluşturulan geçici kaynak dosyalar gibi oluşturulan kod dosyalarında kullanışlı değildir. Kullanıcılar bu dosyaları el ile düzenleyemez ve/veya bu tür araç tarafından oluşturulan dosyalarda ihlalleri düzeltmekle kaygılanmaz.

Varsayılan olarak, çözümleyicileri yürüten çözümleyici sürücüsü dosyaları belirli bir adla, dosya uzantısıyla veya otomatik olarak oluşturulan dosya üst bilgisinde oluşturulan kod dosyaları olarak kabul ediyor. Örneğin, veya ile biten bir dosya `.designer.cs` `.generated.cs` adı, oluşturulan kod olarak kabul edilir. Ancak, bu üristikler kullanıcının kaynak kodunda özel olarak oluşturulan tüm kod dosyalarını tanımlayamaz.

2019 16.5 Visual Studio'den başlayarak, son kullanıcılar editorConfig dosyasında oluşturulan kod olarak kabul edilen belirli dosyaları ve/veya klasörleri [yapılandırabilir.](https://editorconfig.org/) Böyle bir yapılandırma eklemek için aşağıdaki adımları izleyin:

1. Projeniz için henüz bir EditorConfig dosyanız yoksa bir [ekleyin.](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Belirli `generated_code = true | false` dosyalar ve/veya klasörler için girdiyi ekleyin. Örneğin, adı ile sona eren tüm dosyaları oluşturulan `.MyGenerated.cs` kod olarak işlediğinde, girdi aşağıdaki gibi olur:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>İhlalleri gizleme

Çeşitli yöntemleri kullanarak kural ihlallerini bastırebilirsiniz. Daha fazla bilgi için [bkz. Kod analizi ihlallerini gizleme.](../code-quality/in-source-suppression-overview.md)

## <a name="command-line-usage"></a>Komut satırı kullanımı

Projenizi komut satırına derlemeniz, aşağıdaki koşullar karşılanırsa derleme çıkışında kural ihlalleri görünür:

- Çözümleyiciler VSIX uzantısı olarak değil. .NET SDK ile veya NuGet paketi olarak yüklenir.

  .NET SDK kullanılarak yüklenmiş çözümleyiciler için çözümleyicileri [etkinleştirmeniz gerekebilir.](../code-quality/install-net-analyzers.md) Kod stilleri için, bir derleme [özelliği ayarerek kod](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) stillerini MSBuild yapabilirsiniz.

- Projenin kodunda bir veya daha fazla kural ihlal edildi.

- İhlal edilmiş bir kuralın önem derecesi uyarı olarak ayarlanır; bu durumda ihlaller derlemenin başarısız olmasına veya hataya neden olmaz ve bu durumda ihlaller derlemenin başarısız olmasına neden olur. [](#configure-severity-levels)

Derleme çıkışının ayrıntılılığı, kural ihlallerinin gösterilip gösterilmeyeceğini etkilemez. Sessiz **ayrıntılılık** olsa bile, derleme çıkışında kural ihlalleri görünür.

> [!TIP]
> *FxCopCmd.exe* veya **RunCodeAnalysis** bayrağıyla msbuild aracılığıyla komut satırı üzerinden eski analizi çalıştırmaya alışkınsanız, kod çözümleyicileri ile bunu nasıl yapabilirsiniz?

msbuild kullanarak projenizi derlemek için komut satırına çözümleyici ihlallerini görmek için aşağıdakine benzer bir komut çalıştırın:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Aşağıdaki görüntüde çözümleyici kuralı ihlali içeren bir proje derlemenin komut satırı derleme çıktısı gösterilir:

![MSBuild ihlali olan bir çıkış](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Bağımlı projeler

Bir .NET Core projesinde, farklı çözümleyicileri olan bir projeye NuGet eklersiniz, bu çözümleyiciler de bağımlı projeye otomatik olarak eklenir. Bu davranışı devre dışı bırakmak için, örneğin bağımlı proje bir birim testi projesi ise **PrivateAssets** özniteliğini ayarerek NuGet paketini başvurulan projenin *.csproj* veya *.vbproj* dosyasında özel olarak işaretle:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da kod çözümleyicilere genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Kod çözümleyicisi hatası gönderme](https://github.com/dotnet/roslyn-analyzers/issues)
- [Kural kümelerini kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Kod analizi uyarılarını gizleme](../code-quality/in-source-suppression-overview.md)
- [Kod analizi için yapılandırma seçenekleri (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
