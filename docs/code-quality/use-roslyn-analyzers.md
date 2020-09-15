---
title: Çözümleyici yapılandırması
ms.date: 09/02/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6a950a005a4669e74722742b23527a9e85ab5f02
ms.sourcegitcommit: d77da260d79471ab139973c51d65b04e0f80fe2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90560755"
---
# <a name="overview"></a>Genel Bakış

Her bir Roslyn *Çözümleyicisi veya* kuralı, bir varsayılan önem ve gizleme durumuna sahiptir ve projeniz için bu geçersiz kılınabilir ve özelleştirilebilir. Bu makalede, çözümleyici önem derecelerine ayarlama ve çözümleyici ihlallerinin gizlenmesi ele alınmaktadır.

## <a name="configure-severity-levels"></a>Önem düzeylerini yapılandırma

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16,3 ' den başlayarak, çözümleyici kurallarının önem derecesini veya *tanılamayı*, bir [editorconfig dosyasında](#set-rule-severity-in-an-editorconfig-file), [ampul menüsünden](#set-rule-severity-from-the-light-bulb-menu)ve hata listesinden yapılandırabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

Çözümleyiciler bir NuGet paketi olarak [yüklüyorsanız](../code-quality/install-roslyn-analyzers.md) , çözümleyici kurallarının önem derecesini veya *tanılamayı*yapılandırabilirsiniz. Bir kuralın [Çözüm Gezgini](#set-rule-severity-from-solution-explorer) önem derecesini [bir kural kümesi dosyasında](#set-rule-severity-in-the-rule-set-file)değiştirebilirsiniz.

::: moniker-end

Aşağıdaki tabloda farklı önem derecesi seçenekleri gösterilmektedir:

| Önem derecesi (Çözüm Gezgini) | Önem derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *hata* olarak görünür ve yapıların başarısız olmasına neden olur.| Sorunlu kodun kırmızı renkli bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenir. |
| Uyarı | `warning` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *Uyarı* olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Sorunlu kodun yeşil bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir yeşil kutu ile işaretlenir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıktısında değil, Hata Listesi *iletiler* olarak görünür. | Sorunlu kodun gri dalgalı çizgi ile altı çizilir ve kaydırma çubuğundaki küçük bir gri kutusuyla işaretlenir. |
| Gizli | `silent` | Kullanıcıya görünür değil. | Kullanıcıya görünür değil. Ancak tanılama, IDE tanılama altyapısına bildirilir. |
| Yok | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kural için varsayılan değerin ne olduğunu belirlemek için Özellikler penceresi bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (sorunlu kod altında bir *dalgalı çizgi* olarak) ve hata listesi penceresinde raporlanır.

Hata listesinde bildirilen çözümleyici ihlalleri kuralın [önem derecesi düzeyi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eşleşir. Çözümleyici ihlalleri Ayrıca kod düzenleyicisinde, sorunlu kodun altında dalgalı çizgiler olarak görünür. Aşağıdaki görüntüde &mdash; bir hata (kırmızı dalgalı çizgi), bir uyarı (yeşil dalgalı çizgi) ve bir öneri (üç gri noktalı) olmak üzere üç ihlal gösterilmektedir:

![Visual Studio 'da kod düzenleyicisinde dalgalı çizgiler](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsünde Hata Listesi göründükleri üç ihlal gösterilmektedir:

![Hata Listesi hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

Birçok çözümleyici kuralı veya *tanılaması*, kural ihlalini düzeltmek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmesiyle* sahiptir. Kod düzeltmeleri, ampul simgesi menüsünde diğer [hızlı eylem](../ide/quick-actions.md)türleriyle birlikte gösterilir. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Genel Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve hızlı eylem kodu onarımı](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>' Hidden ' önem derecesine ve ' none ' önem derecesine karşı

`Hidden` Varsayılan olarak etkinleştirilen önem kuralları, devre dışı veya `None` önem kurallarından birkaç yolla farklıdır.

- Bir önem derecesi kuralı için herhangi bir kod onarımı kaydedilmişse `Hidden` , gizli tanılama kullanıcıya görünür olmasa bile, bu, Visual Studio 'da hafif ampul kodu yeniden düzenleme eylemi olarak sunulur. Devre dışı bırakılan önem kuralları için bu durum değildir `None` .
- `Hidden` önem derecesi kuralları, [birden çok çözümleyici kuralının kural önem derecesini bir EditorConfig dosyasında bir kez ayarlanmış](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file)girişler tarafından toplu olarak yapılandırılabilir. `None` önem derecesi kuralları bu şekilde yapılandırılamaz. Bunun yerine, [her kural kimliği için bir EditorConfig dosyasında kural önem derecesi ayarlanmış](#set-rule-severity-in-an-editorconfig-file)girişler aracılığıyla yapılandırılması gerekir.

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Bir EditorConfig dosyasında kural önem derecesini ayarlama

(Visual Studio 2019 sürüm 16,3 ve üstü)

Aşağıdaki söz dizimine sahip bir EditorConfig dosyasındaki Derleyici uyarıları veya çözümleyici kuralları için önem derecesini ayarlayabilirsiniz:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Bir EditorConfig dosyasında bir kuralın önem derecesini ayarlamak, bir kural kümesinde veya Çözüm Gezgini ayarlanan herhangi bir önem derecesine göre önceliklidir. Bir EditorConfig dosyasındaki önem derecesini [el ile](#manually-configure-rule-severity-in-an-editorconfig-file) yapılandırabilir veya bir ihlalin yanında görünen ampul aracılığıyla [otomatik olarak](#set-rule-severity-from-the-light-bulb-menu) yapılandırabilirsiniz.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Birden çok çözümleyici kuralının kural önem derecesini bir EditorConfig dosyasında bir kez ayarlama

(Visual Studio 2019 sürüm 16,5 ve üstü)

Belirli bir çözümleyici kuralları kategorisi veya bir EditorConfig dosyasında tek girişli tüm çözümleyici kuralları için önem derecesini ayarlayabilirsiniz.

- Çözümleyici kuralları kategorisi için kural önem derecesini ayarlayın:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Tüm çözümleyici kuralları için kural önem derecesini ayarla:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Birden çok çözümleyici kuralını tek seferde yapılandırma girişleri yalnızca *Varsayılan olarak etkinleştirilen*kurallar için geçerlidir. Çözümleyici paketinde varsayılan olarak devre dışı olarak işaretlenen çözümleyici kuralları açık girişler aracılığıyla etkinleştirilmelidir `dotnet_diagnostic.<rule ID>.severity = <severity>` .

Belirli bir kural KIMLIĞI için geçerli olan birden çok girdiniz varsa, uygulanabilir girişi seçmek için öncelik sırası aşağıda verilmiştir:

- Tek bir kural için önem derecesi girişi, bir kategori için önem derecesine göre öncelik alır.
- Bir kategori için önem derecesi, tüm çözümleyici kuralları için önem derecesine göre öncelik girişi alır.

Aşağıdaki EditorConfig örneğini göz önünde bulundurun, burada [CA1822](./ca1822.md) "Performance" kategorisine sahiptir:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Yukarıdaki örnekte, üç girişin tümü CA1822 için geçerlidir. Bununla birlikte, belirtilen öncelik kurallarını kullanarak, sonraki girişler üzerinden WINS ilk kural KIMLIĞI tabanlı önem derecesi girişi. Bu örnekte, CA1822 "Error" etkili bir önem derecesine sahip olacaktır. "Performans" kategorisindeki tüm kalan kuralların önem derecesi "uyarı" olacaktır. "Performans" kategorisine sahip olmayan tüm geri kalan çözümleyici kurallarının önem derecesi "önerisi" olacaktır.

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Bir EditorConfig dosyasında kural önem derecesini el ile yapılandırma

1. Projeniz için zaten bir EditorConfig dosyanız yoksa, [bir tane ekleyin](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Karşılık gelen dosya uzantısı altında yapılandırmak istediğiniz her kural için bir giriş ekleyin. Örneğin, [CA1822](ca1822.md) için önem derecesini C# dosyaları için ayarlamak üzere `error` , giriş aşağıdaki gibi görünür:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> IDE kod stili Çözümleyicileri için, bunları bir EditorConfig dosyasında farklı bir sözdizimi kullanarak da yapılandırabilirsiniz, örneğin, `dotnet_style_qualification_for_field = false:suggestion` . Ancak, söz dizimini kullanarak önem derecesi ayarlarsanız `dotnet_diagnostic` , öncelik kazanır. Daha fazla bilgi için bkz. [EditorConfig Için dil kuralları](../ide/editorconfig-language-conventions.md).

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Ampul menüsünden Kural önem derecesini ayarlama

Visual Studio, bir kuralın önem derecesini [hızlı eylemler](../ide/quick-actions.md) ampul menüsünden yapılandırmanın kolay bir yolunu sunar.

1. Bir ihlal oluştuktan sonra, düzenleyicide ihlalin üzerine gelin ve ampul menüsünü açın. Ya da imlecinizi satıra yerleştirip **CTRL**tuşuna basın + **.** (nokta).

2. Ampul menüsünde **yapılandırma veya gizleme sorunları** > **yapılandırma \<rule ID> önem derecesi**' ni seçin.

   ![Visual Studio 'da ampul menüsünden Kural önem derecesini yapılandırma](media/configure-rule-severity.png)

3. Buradan, önem derecesi seçeneklerinden birini belirleyin.

   ![Öneri olarak kural önem derecesini yapılandırma](media/configure-rule-severity-suggestion.png)

   Visual Studio, önizleme kutusunda gösterildiği gibi, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede zaten bir EditorConfig dosyanız yoksa, Visual Studio sizin için bir tane oluşturur.

### <a name="set-rule-severity-from-the-error-list-window"></a>Hata Listesi penceresinden kural önem derecesini ayarlama

Visual Studio aynı zamanda bir kuralın önem derecesini hata listesi bağlam menüsünden yapılandırmak için kullanışlı bir yol sağlar.

1. Bir ihlal oluştuktan sonra, hata listesindeki tanılama girdisini sağ tıklatın.

2. Bağlam menüsünde **önem derecesi ayarla**' yı seçin.

   ![Visual Studio 'daki hata listesinden kural önem derecesini yapılandırma](media/configure-rule-severity-error-list.png)

3. Buradan, önem derecesi seçeneklerinden birini belirleyin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede zaten bir EditorConfig dosyanız yoksa, Visual Studio sizin için bir tane oluşturur.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecesini Çözüm Gezgini ayarla

**Çözüm Gezgini**'den çözümleyici tanılamayı özelleştirmenin çoğunu yapabilirsiniz. Çözümleyiciler bir NuGet paketi olarak [yüklüyorsanız](../code-quality/install-roslyn-analyzers.md) , **Çözüm Gezgini**içindeki **Başvurular** veya **Bağımlılıklar** düğümü altında bir **çözümleyiciler** düğümü görüntülenir. **Çözümleyicileri**genişlettikten sonra çözümleyici derlemelerinden birini genişletirseniz, derlemede tüm tanılamayı görürsünüz.

![Çözüm Gezgini içinde düğüm Çözümleyicileri](media/analyzers-expanded-in-solution-explorer.png)

**Özellikler** penceresinde, açıklaması ve varsayılan önem derecesi dahil olmak üzere bir tanı özelliklerini görüntüleyebilirsiniz. Özellikleri görüntülemek için kurala sağ tıklayın ve **Özellikler**' i seçin veya kuralı seçin ve ardından **alt** + **ENTER**tuşuna basın.

![Özellikler penceresi tanılama özellikleri](media/analyzer-diagnostic-properties.png)

Bir Tanılamanın çevrimiçi belgelerini görmek için, tanılamayı sağ tıklatın ve **Yardımı görüntüle**' yi seçin.

**Çözüm Gezgini** içindeki her bir Tanılamanın yanındaki simgeler, düzenleyicide açtığınızda kural kümesinde gördüğünüz simgelere karşılık gelir:

- bir daire içindeki "x", **hatanın** [önem derecesini](#configure-severity-levels) gösterir
- Bir üçgendeki "!", **uyarının** [önem derecesini](#configure-severity-levels) gösterir
- bir daire içindeki "i", **bilgi** [önem derecesini](#configure-severity-levels) gösterir
- açık renkli bir arka plandaki daire içindeki "i", **gizlenen** [önem derecesini](#configure-severity-levels) gösterir
- bir daire içindeki aşağı açılan ok, Tanılamanın bastırılmadığını belirtir

![Çözüm Gezgini tanılama simgeleri](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Varolan bir RuleSet dosyasını EditorConfig dosyasına Dönüştür

Visual Studio 2019 sürüm 16,5 ' den başlayarak, RuleSet dosyaları, yönetilen kodun çözümleyici yapılandırması için EditorConfig dosyasında kullanım dışı bırakılmıştır. Çözümleyici kuralı önem derecesi için Visual Studio Araçları önem derecesi yapılandırması, RuleSet dosyaları yerine EditorConfig dosyalarında çalışacak şekilde güncelleştirilmiştir. EditorConfig dosyaları, Visual Studio IDE kod stili seçenekleri de dahil olmak üzere hem çözümleyici kuralı, hem de Çözümleyici seçeneklerini yapılandırmanızı sağlar. Mevcut RuleSet dosyanızı bir EditorConfig dosyasına dönüştürmeniz önemle önerilir. Ayrıca, EditorConfig dosyasını deponuzdaki veya çözüm klasöründeki bir köke kaydetmeniz önerilir. Depo veya çözüm klasörünüzün kökünü kullanarak, bu dosyadaki önem derecesi ayarlarının, sırasıyla tüm depoya veya çözüme otomatik olarak uygulandığından emin olun.

Varolan bir RuleSet dosyasını bir EditorConfig dosyasına dönüştürmenin birkaç yolu vardır:

- Visual Studio 'daki RuleSet düzenleyicisinden (Visual Studio 2019 16,5 veya üstünü gerektirir). Projeniz zaten belirli bir RuleSet dosyası kullanıyorsa `CodeAnalysisRuleSet` , Visual Studio Içindeki RuleSet Düzenleyicisi 'nden eşdeğer bir EditorConfig dosyasına dönüştürebilirsiniz.

    1. Çözüm Gezgini RuleSet dosyasına çift tıklayın.

       Ruleset dosyası RuleSet düzenleyicisinde açılmalıdır. RuleSet düzenleyicisinin en üstünde tıklatılabilir bir **bilgi çubuğu** görmeniz gerekir.

       ![RuleSet düzenleyicisinde RuleSet 'i EditorConfig dosyasına Dönüştür](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Bilgi çubuğu** bağlantısını seçin.

       Bu, EditorConfig dosyasını oluşturmak istediğiniz dizini seçmenize olanak sağlayan bir **farklı kaydet** iletişim kutusu açar.

    3. EditorConfig dosyasını oluşturmak için **Kaydet** düğmesini seçin.

       Oluşturulan EditorConfig düzenleyicide açılmalıdır. Ayrıca, MSBuild özelliği `CodeAnalysisRuleSet` Proje dosyasında, özgün RuleSet dosyasına artık başvurmayacak şekilde güncelleştirilir.

- Komut satırından:

    1. [Microsoft. CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)NuGet paketini yükler.

    2. `RulesetToEditorconfigConverter.exe`Kural kümesi dosyası ve EditorConfig dosyası yolların komut satırı bağımsız değişkenleri olarak yüklü paketinden yürütün.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Dönüştürülecek örnek bir RuleSet dosyası aşağıda verilmiştir:

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

Dönüştürülmüş EditorConfig dosyası aşağıda verilmiştir:

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

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecesini Çözüm Gezgini ayarla

1. Çözüm Gezgini, **başvuru**  >  **Çözümleyicileri** (veya **Dependencies**  >  .NET Core projeleri için bağımlılıklar**Çözümleyicileri** ) öğesini genişletin.

2. Önem derecesini ayarlamak istediğiniz kuralı içeren derlemeyi genişletin.

::: moniker range=">=vs-2019"
3. Kurala sağ tıklayın ve **önem derecesi ayarla**' yı seçin. Bağlam menüsünde önem derecesi seçeneklerinden birini seçin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler. Projeniz bir EditorConfig dosyası yerine bir RuleSet dosyası kullanıyorsa, ' önem derecesi girişi RuleSet dosyasına eklenir.

   > [!TIP]
   > Projede zaten bir EditorConfig dosyanız veya RuleSet dosyanız yoksa, Visual Studio sizin için yeni bir EditorConfig dosyası oluşturur.
::: moniker-end

::: moniker range="vs-2017"
3. Kurala sağ tıklayın ve **kural kümesi önem derecesi ayarla**' yı seçin. Bağlam menüsünde önem derecesi seçeneklerinden birini seçin.

   Kuralın önem derecesi, etkin kural kümesi dosyasına kaydedilir.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Kural önem derecesini kural kümesi dosyasında ayarla

![Çözüm Gezgini kural kümesi dosyası](media/ruleset-in-solution-explorer.png)

1. Etkin kural kümesi dosyasını aşağıdaki yollarla açın:

- **Çözüm Gezgini**' de, dosyaya **çift tıklayın,** çözümleyiciler öğesine sağ tıklayın  >  **Analyzers** ve **etkin kural kümesini aç**' ı seçin.
- Projenin **Kod Analizi** Özellik sayfasında **Aç** ' ı seçin.

  Kural kümesini ilk kez düzenliyorsanız, Visual Studio varsayılan kural kümesi dosyasının bir kopyasını oluşturur, * \<projectname> . RuleSet*olarak adlandırır ve bunu projenize ekler. Bu özel kural kümesi, projeniz için etkin kural kümesi de olur.

   > [!NOTE]
   > .NET Core ve .NET Standard projeleri, **Çözüm Gezgini**kural kümeleri için menü komutlarını desteklemez, örneğin, **etkin kural kümesi açın**. .NET Core veya .NET Standard projesi için varsayılan olmayan bir kural kümesi belirtmek için, [ **CodeAnalysisRuleSet** özelliğini](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) proje dosyasına el ile ekleyin. Kuralları, Visual Studio kural kümesi Düzenleyicisi Kullanıcı arabirimindeki kural kümesi içinde yine yapılandırabilirsiniz.

1. İçeren derlemeyi genişleterek kurala gidin.

1. **Eylem** sütununda, bir açılan listeyi açmak için değeri seçin ve listeden istenen önem derecesini seçin.

   ![Düzenleyicide kural kümesi dosyası aç](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Oluşturulan kodu Yapılandır

Çözümleyiciler bir projedeki tüm kaynak dosyalarında çalışır ve bunlar üzerinde ihlalleri bildirir. Ancak, Bu ihlaller, tasarımcı tarafından oluşturulan kod dosyaları, derleme sistemi tarafından oluşturulan geçici kaynak dosyaları vb. gibi oluşturulmuş kod dosyalarında yararlı değildir. Kullanıcılar bu dosyaları el ile düzenleyemez ve/veya bu tür bir araç tarafından üretilen dosyada ihlalleri düzeltme konusunda endişe etmez.

Varsayılan olarak, çözümleyiciler yürüten çözümleyici sürücüsü dosyaları belirli bir ad, dosya uzantısı veya oluşturulan kod dosyaları olarak otomatik oluşturulan dosya üstbilgisiyle değerlendirir. Örneğin, veya ile biten bir dosya adı `.designer.cs` `.generated.cs` üretilen kod olarak kabul edilir. Ancak, bu buluşsal yöntemler kullanıcının kaynak kodundaki tüm özel oluşturulmuş kod dosyalarını tanımlayamayabilir.

Visual Studio 2019 16,5 ' den itibaren, son kullanıcılar belirli dosyaları ve/veya klasörleri bir [Editorconfig dosyasında](https://editorconfig.org/)oluşturulan kod olarak değerlendirilecek şekilde yapılandırabilir. Böyle bir yapılandırma eklemek için aşağıdaki adımları izleyin:

1. Projeniz için zaten bir EditorConfig dosyanız yoksa, [bir tane ekleyin](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. `generated_code = true | false`Belirli dosya ve/veya klasörlere yönelik girişi ekleyin. Örneğin, adı biten tüm dosyaları `.MyGenerated.cs` oluşturulan kodla işlemek için, giriş aşağıdaki gibi olacaktır:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>İhlalleri gösterme

Kural ihlallerini bastırmak için birden çok yol vardır:

::: moniker range=">=vs-2019"

- Bir **Editorconfig dosyasında**

  Önem derecesini `none` , örneğin, olarak ayarlayın `dotnet_diagnostic.CA1822.severity = none` .

- **Çözümle** menüsünden

  **Analyze**  >  Geçerli ihlallerin tümünü bastırmak için derlemeyi çözümle ve menü çubuğunda**etkin sorunları Gizle** ' yi seçin. Bu bazen "taban çizgisi" olarak adlandırılır.

::: moniker-end

::: moniker range="vs-2017"

- **Çözümle** menüsünden

  **Analyze**  >  Geçerli ihlallerin tümünü bastırmak için,**Kod analizini Çalıştır ve menü çubuğunda etkin sorunları Gizle** ' yi seçin. Bu bazen "taban çizgisi" olarak adlandırılır.

::: moniker-end

- **Çözüm Gezgini** 'den

  Kuralın önem derecesini **hiçbiri**olarak ayarlayın.

- **Kural kümesi düzenleyicisinden**

  Adının yanındaki onay kutusunu temizleyin veya **eylemi** **none**olarak ayarlayın.

- **Kod düzenleyicisinden**

  İmleci kod satırına yerleştirin ve **Ctrl** + **hızlı eylemler** menüsünü açmak için CTRL**dönemi (.)** tuşuna basın. **Suppress CAXXXX**  >  **Kaynak/gizleme dosyasında**caxxxx 'i Gizle ' yi seçin.

  ![Hızlı Eylemler menüsünden tanılamayı gösterme](media/suppress-diagnostic-from-editor.png)

- **Hata listesi**

  Gizlemek istediğiniz kuralları seçin ve ardından sağ tıklayıp **Suppress**  >  **kaynak/gizleme dosyasında**Gizle ' yi seçin.

  - **Kaynakta**bastırdığınızda, **Değişiklikleri Önizle** iletişim kutusu açılır ve C# [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) veya kaynak koda eklenen Visual Basic [#Disable uyarı](/dotnet/visual-basic/language-reference/directives/directives) yönergesinin önizlemesini gösterir.

    ![Kod dosyasında #pragma uyarı ekleme önizlemesi](media/pragma-warning-preview.png)

  - **Gizleme dosyasını**seçerseniz, **Değişiklikleri Önizle** iletişim kutusu açılır ve <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> genel gizlemeleri dosyasına eklenen özniteliğin önizlemesini gösterir.

    ![Gizleme dosyasına SuppressMessage özniteliği ekleme önizlemesi](media/preview-changes-in-suppression-file.png)

  **Değişiklikleri Önizle** Iletişim kutusunda **Uygula**' yı seçin.

  > [!NOTE]
  > **Çözüm Gezgini**' de **gizleme** menüsü seçeneğini görmüyorsanız, ihlalin büyük olasılıkla canlı Analize değil derlemeden geliyor. **Hata listesi** , hem canlı kod analizinden hem de derlemeden tanılama veya kural ihlalleri görüntüler. Derleme tanılaması eski olduğundan, örneğin, ihlalin giderilmesi için kodu düzenlediyseniz, ancak yeniden oluşturmadıysanız, **hata listesi**bu tanılamayı gizlenemez. Canlı Analize veya IntelliSense 'e yönelik Tanılamalar, geçerli kaynaklarla her zaman güncel değildir ve **hata listesi**gizlenmiş olabilir. *Oluşturma* tanılamayı seçiminizden dışlamak için, **hata listesi** kaynak filtresini **derleme + IntelliSense** 'den **yalnızca IntelliSense**'e geçirin. Daha sonra, gizlemek istediğiniz tanılamayı seçin ve daha önce açıklandığı gibi devam edin.
  >
  > ![Visual Studio 'da Hata Listesi kaynak filtresi](media/error-list-filter.png)

## <a name="command-line-usage"></a>Komut satırı kullanımı

Projenizi komut satırında oluşturduğunuzda, aşağıdaki koşullar karşılanıyorsa, yapı çıkışında kural ihlalleri görüntülenir:

- Çözümleyiciler VSıX uzantısı olarak değil, bir NuGet paketi olarak yüklenir.

- Projenin kodunda bir veya daha fazla kural ihlal edildi.

- Bir ihlal kuralının [önem derecesi](#configure-severity-levels) , **Uyarı**olarak ayarlanır; Bu durumda ihlallerin başarısız olmasına neden olmaz veya **hata**, bu durum ihlallerinin başarısız olmasına neden olur.

Yapı çıkışının ayrıntı düzeyi, kural ihlallerinin gösterilip gösterilmeyeceğini etkilemez. **Sessiz** ayrıntı düzeyine sahip olsa bile, yapı çıkışında kural ihlalleri görüntülenir.

> [!TIP]
> Komut satırından, *FxCopCmd.exe* veya **RunCodeAnalysis** bayrağıyla MSBuild aracılığıyla eski analizler çalıştırmaya alışkın değilseniz, bunu kod Çözümleyicileri ile nasıl yapacağıdır.

MSBuild kullanarak projenizi oluştururken komut satırında çözümleyici ihlallerini görmek için şöyle bir komut çalıştırın:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Aşağıdaki görüntüde, bir çözümleyici kuralı ihlali içeren bir proje derlemeden komut satırı derleme çıkışı gösterilmektedir:

![Kural ihlali ile MSBuild çıkışı](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Bağımlı projeler

Bir .NET Core projesinde, NuGet Çözümleyicileri olan bir projeye başvuru eklerseniz, bu çözümleyiciler otomatik olarak bağımlı projeye de eklenir. Bu davranışı devre dışı bırakmak için örneğin, bağımlı proje bir birim testi projem ise, **Privatevarlıkların** özniteliğini ayarlayarak, başvurulan projenin *. csproj* veya *. vbproj* dosyasında NuGet paketini özel olarak işaretleyin:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod Çözümleyicileri 'ne genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Kod Çözümleyicisi hatası gönderme](https://github.com/dotnet/roslyn-analyzers/issues)
- [Kural kümelerini kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Kod Analizi uyarılarını gösterme](../code-quality/in-source-suppression-overview.md)