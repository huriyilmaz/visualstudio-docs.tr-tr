---
title: Çözümleyici yapılandırması
ms.date: 01/24/2022
description: Roslyn çözümleyici kurallarını özelleştirmeyi öğrenin. Bkz. çözümleyici önem derecelerine ayarlama, ihlalleri gösterme ve dosyaları oluşturulan kod olarak belirleme.
ms.custom: SEO-VS-2020, devdivchpfy22
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
ms.openlocfilehash: 928cc90c5e9017f7e2362e179bea0fc2edb2c03f
ms.sourcegitcommit: f303d052e451bcfd4722b99a9adbcb3f575d1678
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137816836"
---
# <a name="overview"></a>Genel Bakış

Her bir Roslyn *Çözümleyicisi veya* kuralı, bir varsayılan önem ve gizleme durumuna sahiptir ve projeniz için bu geçersiz kılınabilir ve özelleştirilebilir. Bu makalede, çözümleyici önem derecelerine ayarlama ve çözümleyici ihlallerinin gizlenmesi ele alınmaktadır.

## <a name="configure-severity-levels"></a>Önem düzeylerini yapılandırma

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16,3 ' den başlayarak, bir [editorconfig dosyasında](#set-rule-severity-in-an-editorconfig-file), [ampul menüsünden](#set-rule-severity-from-the-light-bulb-menu)ve hata listesinden çözümleyici kurallarının önem derecesini veya *tanılamayı* yapılandırabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

çözümleyiciler NuGet paketi olarak [yüklüyorsanız](../code-quality/install-roslyn-analyzers.md) , çözümleyici kurallarının önem derecesini veya *tanılamayı* yapılandırabilirsiniz. Bir kuralın [Çözüm Gezgini](#set-rule-severity-from-solution-explorer) önem derecesini [bir kural kümesi dosyasında](#set-rule-severity-in-the-rule-set-file)değiştirebilirsiniz.

::: moniker-end

Aşağıdaki tabloda farklı önem derecesi seçenekleri gösterilmektedir:

| Önem derecesi (Çözüm Gezgini) | Önem derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *hata* olarak görünür ve yapıların başarısız olmasına neden olur.| Sorunlu kodun kırmızı renkli bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenir. |
| Uyarı | `warning` | İhlaller Hata Listesi ve komut satırı derleme çıkışında *Uyarı* olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Sorunlu kodun yeşil bir dalgalı çizgi ile altı çizilir ve kaydırma çubuğunda küçük bir yeşil kutu ile işaretlenir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıktısında değil, Hata Listesi *iletiler* olarak görünür. | Sorunlu kodun gri dalgalı çizgi ile altı çizilir ve kaydırma çubuğundaki küçük bir gri kutusuyla işaretlenir. |
| Gizli | `silent` | Kullanıcıya görünür değil. | Kullanıcıya görünür değil. Ancak tanılama, IDE tanılama altyapısına bildirilir. |
| Hiçbiri | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kural için varsayılan değerin ne olduğunu belirlemek için Özellikler penceresi bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Çözümleyici tarafından bulunan kural ihlalleri, kod Düzenleyicisi 'nde (sorunlu kod altında *dalgalı bir çizgi* olarak) ve çözümleyici tarafından hata listesi penceresinde görünür.

Hata listesinde bildirilen çözümleyici ihlalleri kuralın [önem derecesi düzeyi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eşleşir. Çözümleyici ihlalleri Ayrıca kod düzenleyicisinde, sorunlu kodun altında dalgalı çizgiler olarak görünür. Aşağıdaki görüntüde &mdash; bir hata (kırmızı dalgalı çizgi), bir uyarı (yeşil dalgalı çizgi) ve bir öneri (üç gri noktalı) olmak üzere üç ihlal gösterilmektedir:

![Visual Studio kod düzenleyicisinde dalgalı çizgiler](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsünde Hata Listesi göründükleri üç ihlal gösterilmektedir:

![Hata Listesi hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

Birçok çözümleyici kuralı veya *tanılaması*, kural ihlalini düzeltmek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmesiyle* sahiptir. Kod düzeltmeleri, ampul simgesi menüsünde diğer [hızlı eylem](../ide/quick-actions.md)türleriyle birlikte gösterilir. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Genel Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve hızlı eylem kodu onarımı](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>' Hidden ' önem derecesine ve ' none ' önem derecesine karşı

`Hidden` Varsayılan olarak etkinleştirilen önem derecesi, belirli açılardan devre dışı veya `None` önem kurallarından farklıdır.

- bir önem derecesi kuralı için herhangi bir kod onarımı kayıtlıysa `Hidden` Visual Studio, gizli tanı kullanıcı tarafından görülemese bile, çözümü hafif ampul kodu olarak yeniden düzenleme eylemi olarak sunar. Önem derecesi kuralı olarak devre dışı bırakılmışsa Bu çözüm sunulmaz `None` .
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

Belirli bir kural KIMLIĞI için geçerli olan birden çok girdiniz varsa, ilgili girişe ilişkin öncelik sırası aşağıdaki gibidir:

- Tek bir kural için önem derecesi girişi, bir kategori için önem derecesine göre öncelik alır.
- Bir kategori için önem derecesi, tüm çözümleyici kuralları için önem derecesine göre öncelik girişi alır.

Aşağıdaki EditorConfig örneğini göz önünde bulundurun, burada [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) "Performance" kategorisine sahiptir:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Yukarıdaki örnekte, üç girişin tümü CA1822 için geçerlidir. Bununla birlikte, belirtilen öncelik kurallarını kullanarak, sonraki girişler üzerinden WINS ilk kural KIMLIĞI tabanlı önem derecesi girişi. Bu örnekte, CA1822 "Error" etkili bir önem derecesine sahiptir. "Performans" kategorisindeki kalan kuralların önem derecesi "uyarı" ve "performans" kategorisine sahip olmayan çözümleyici kuralları "öneri" önem derecesine sahiptir.

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
   > projede zaten bir editorconfig dosyanız yoksa Visual Studio sizin için bir tane oluşturur.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecesini Çözüm Gezgini ayarla

**Çözüm Gezgini**'den çözümleyici tanılamayı özelleştirmenin çoğunu yapabilirsiniz. çözümleyiciler NuGet paketi olarak [yüklerseniz](../code-quality/install-roslyn-analyzers.md) , **Çözüm Gezgini** içindeki **başvurular** veya **bağımlılıklar** düğümü altında bir **çözümleyiciler** düğümü görüntülenir. **Çözümleyicileri** genişlettikten sonra çözümleyici derlemelerinden birini genişletirseniz, derlemede tüm tanılamayı görürsünüz.

![Çözüm Gezgini içinde düğüm Çözümleyicileri](media/analyzers-expanded-in-solution-explorer.png)

**Özellikler** penceresinde, açıklaması ve varsayılan önem derecesi dahil olmak üzere bir tanı özelliklerini görüntüleyebilirsiniz. Özellikleri görüntülemek için kurala sağ tıklayın ve **Özellikler**' i seçin veya kuralı seçin ve ardından **alt** + **ENTER** tuşuna basın.

![Özellikler penceresi tanılama özellikleri](media/analyzer-diagnostic-properties.png)

Bir Tanılamanın çevrimiçi belgelerini görmek için, tanılamayı sağ tıklatın ve **Yardımı görüntüle**' yi seçin.

**Çözüm Gezgini** içindeki her bir Tanılamanın yanındaki simgeler, düzenleyicide açtığınızda kural kümesinde gördüğünüz simgelere karşılık gelir:

- bir daire içinde "x", **hatanın** [önem derecesini](#configure-severity-levels) gösterir
- bir üçgende "!", **uyarının** [önem derecesini](#configure-severity-levels) gösterir
- bir daire içinde "i", **bilgi** [önem derecesini](#configure-severity-levels) gösterir
- açık renkli bir arka planda "i" bir daire içinde **gizli** bir [önem derecesi](#configure-severity-levels) olduğunu belirtir
- Bir daire içinde aşağı işaret eden ok, Tanılamanın bastırılmadığını belirtir

![Çözüm Gezgini tanılama simgeleri](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Varolan bir RuleSet dosyasını EditorConfig dosyasına Dönüştür

Visual Studio 2019 sürüm 16,5 ' den başlayarak, ruleset dosyaları, yönetilen kodun çözümleyici yapılandırması için editorconfig dosyasında kullanım dışı bırakılmıştır. çözümleyici kuralları için Visual Studio araçları önem derecesi yapılandırması, ruleset dosyaları yerine editorconfig dosyalarında çalışacak şekilde güncelleştirilir. editorconfig dosyaları, Visual Studio ıde kod stili seçenekleri de dahil olmak üzere hem çözümleyici kuralı, hem de çözümleyici seçeneklerini yapılandırmanızı sağlar. Mevcut RuleSet dosyanızı bir EditorConfig dosyasına dönüştürmeniz önerilir. Ayrıca, EditorConfig dosyasını deponuzın köküne veya çözüm klasörüne kaydedin. Depo veya çözüm klasörünüzün kökünü kullanarak, bu dosyadaki önem derecesi ayarlarının, sırasıyla tüm depo veya çözüme otomatik olarak uygulanmasını sağlayabilirsiniz.

Varolan bir RuleSet dosyasını bir EditorConfig dosyasına dönüştürmenin birkaç yolu vardır:

- Visual Studio içindeki ruleset düzenleyicisinden (Visual Studio 2019 16,5 veya üzeri bir sürümü gerektirir). Projeniz zaten belirli bir RuleSet dosyası kullanıyorsa `CodeAnalysisRuleSet` , Visual Studio Içindeki RuleSet düzenleyicisinden eşdeğer bir EditorConfig dosyasına dönüştürebilirsiniz.

    1. Çözüm Gezgini RuleSet dosyasına çift tıklayın.

       Ruleset dosyası RuleSet düzenleyicisinde açılmalıdır. RuleSet düzenleyicisinin en üstünde tıklatılabilir bir **bilgi çubuğu** görmeniz gerekir.

       ![RuleSet düzenleyicisinde RuleSet 'i EditorConfig dosyasına Dönüştür](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Bilgi çubuğu** bağlantısını seçin.

       Bu eylem, EditorConfig dosyasını oluşturmak istediğiniz dizini seçmenize olanak sağlayan bir **farklı kaydet** iletişim kutusu açması gerekir.

    3. EditorConfig dosyasını oluşturmak için **Kaydet** düğmesini seçin.

       Oluşturulan EditorConfig düzenleyicide açılmalıdır. ayrıca, MSBuild özelliği `CodeAnalysisRuleSet` proje dosyasında güncellenir, böylece artık özgün ruleset dosyasına başvurmayacaktır.

- Komut satırından:

    1. [Microsoft. codeanalysis. rulesettoeditorconfigconverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)NuGet paketini yükler.

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

Dönüştürülen EditorConfig dosyası aşağıda verilmiştir:

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

1. Çözüm Gezgini, **başvuru**  >  **Çözümleyicileri** (veya   >  .NET Core projeleri için bağımlılıklar **Çözümleyicileri** ) öğesini genişletin.

2. Önem derecesini ayarlamak istediğiniz kuralı içeren derlemeyi genişletin.

::: moniker range=">=vs-2019"
3. Kurala sağ tıklayın ve **önem derecesi ayarla**' yı seçin. Bağlam menüsünde önem derecesi seçeneklerinden birini seçin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için editorconfig dosyasına bir giriş ekler. Projeniz bir EditorConfig dosyası yerine bir RuleSet dosyası kullanıyorsa, ' önem derecesi girişi RuleSet dosyasına eklenir.

   > [!TIP]
   > projede zaten bir editorconfig dosyanız veya ruleset dosyanız yoksa Visual Studio, sizin için yeni bir editorconfig dosyası oluşturur.
::: moniker-end

::: moniker range="vs-2017"
3. Kurala sağ tıklayın ve **kural kümesi önem derecesi ayarla**' yı seçin. Bağlam menüsünde önem derecesi seçeneklerinden birini seçin.

   Kuralın önem derecesi, etkin kural kümesi dosyasına kaydedilir.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Kural önem derecesini kural kümesi dosyasında ayarla

1. Etkin kural kümesi dosyasını aşağıdaki yollarla açın:

    - **Çözüm Gezgini**, dosyaya **çift tıklayın,** bulunan  >  **çözümleyiciler** düğümüne sağ tıklayın ve **etkin kural kümesini aç**' ı seçin.
  
        ![Çözüm Gezgini kural kümesi dosyası](media/ruleset-in-solution-explorer.png)

    - projenin **Code Analysis** özellik sayfasında **aç** ' ı seçin.

    kural kümesini ilk kez düzenliyorsanız, Visual Studio varsayılan kural kümesi dosyasının bir kopyasını oluşturur, *\<projectname> . ruleset* olarak adlandırır ve projenize ekler. Bu özel kural kümesi, projeniz için etkin kural kümesi de olur.

    > [!NOTE]
    > .NET Core ve .NET Standard projeleri, **Çözüm Gezgini** kural kümeleri için menü komutlarını desteklemez, örneğin, **etkin kural kümesi açın**. .NET Core veya .NET Standard projesi için varsayılan olmayan bir kural kümesi belirtmek için, [ **CodeAnalysisRuleSet** özelliğini](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) proje dosyasına el ile ekleyin. kural kümesi içinde kuralları Visual Studio kural kümesi düzenleyicisi kullanıcı arabiriminde yapılandırabilirsiniz.

1. İçeren derlemeyi genişleterek kurala gidin.

1. **Eylem** sütununda, bir açılan listeyi açmak için değeri seçin ve listeden istenen önem derecesini seçin.

   ![Düzenleyicide kural kümesi dosyası aç](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Oluşturulan kodu Yapılandır

Çözümleyiciler bir projedeki tüm kaynak dosyalarında çalışır ve bunlar üzerinde ihlalleri bildirir. Ancak, ihlaller, tasarımcı tarafından oluşturulan kod dosyaları, derleme sistemi tarafından oluşturulan geçici kaynak dosyaları vb. gibi oluşturulan kod dosyalarında yararlı değildir. Kullanıcılar dosyaları el ile düzenleyemez ve araç tarafından oluşturulan dosyalardaki ihlallerin düzeltilmesi konusunda endişe yoktur.

Varsayılan olarak, çözümleyiciler çalıştıran çözümleyici sürücüsü, dosyaları belirli adlara, dosya uzantılarına veya oluşturulan kod dosyaları olarak otomatik olarak oluşturulan dosya başlıklarına göre değerlendirir. Örneğin,. Designer. cs veya. generated. cs ile biten bir dosya adı üretilen kod olarak kabul edilir. Ancak, bu buluşsal yöntemler kullanıcının kaynak kodundaki tüm özel oluşturulmuş kod dosyalarını tanımlayamayabilir.

Visual Studio 2019 16,5 ' den itibaren, son kullanıcılar belirli dosyaları ve/veya klasörleri bir [editorconfig dosyasında](https://editorconfig.org/)oluşturulan kod olarak değerlendirilecek şekilde yapılandırabilir. Böyle bir yapılandırma eklemek için aşağıdaki adımları izleyin:

1. Projeniz için zaten bir EditorConfig dosyanız yoksa, [bir tane ekleyin](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. `generated_code = true | false`Belirli dosya ve/veya klasörlere yönelik girişi ekleyin. Örneğin, adı biten tüm dosyaları `.MyGenerated.cs` oluşturulan kodla işlemek için, giriş aşağıdaki gibi olacaktır:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>İhlalleri gösterme

Çeşitli yöntemleri kullanarak kural ihlallerinin görüntülenmesini sağlayabilirsiniz. Daha fazla bilgi için bkz. [Kod Analizi Ihlallerini gösterme](../code-quality/in-source-suppression-overview.md).

## <a name="command-line-usage"></a>Komut satırı kullanımı

Projenizi komut satırında oluşturduğunuzda, aşağıdaki koşullar karşılanıyorsa, yapı çıkışında kural ihlalleri görüntülenir:

- çözümleyiciler .net SDK ile veya bir NuGet paketi olarak yüklenir ve vsıx uzantısı olarak değildir.

  .NET SDK kullanılarak yüklenen çözümleyiciler için [çözümleyicilerin etkinleştirilmesi](../code-quality/install-net-analyzers.md)gerekebilir. kod stilleri için bir MSBuild özelliğini ayarlayarak [derleme üzerinde kod stilleri](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) de uygulayabilirsiniz.

- Projenin kodunda bir veya daha fazla kural ihlal edildi.

- Bir ihlal kuralının [önem derecesi](#configure-severity-levels) , **Uyarı** olarak ayarlanır; Bu durumda ihlallerin başarısız olmasına neden olmaz veya **hata**, bu durum ihlallerinin başarısız olmasına neden olur.

Yapı çıkışının ayrıntı düzeyi, kural ihlallerinin gösterilip gösterilmeyeceğini etkilemez. **Sessiz** ayrıntı düzeyine sahip olsa bile, yapı çıkışında kural ihlalleri görüntülenir.

> [!TIP]
> Komut satırından, *FxCopCmd.exe* veya **RunCodeAnalysis** bayrağıyla MSBuild aracılığıyla eski analizler çalıştırmaya alışkın değilseniz, bunu kod Çözümleyicileri ile nasıl yapacağıdır.

MSBuild kullanarak projenizi oluştururken komut satırında çözümleyici ihlallerini görmek için şöyle bir komut çalıştırın:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Aşağıdaki görüntüde, bir çözümleyici kuralı ihlali içeren bir proje derlemeden komut satırı derleme çıkışı gösterilmektedir:

![kural ihlali ile çıkış MSBuild](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Bağımlı projeler

bir .net Core projesinde, NuGet çözümleyicileri olan bir projeye başvuru eklerseniz, bu çözümleyiciler da otomatik olarak bağımlı projeye eklenir. bu davranışı devre dışı bırakmak için örneğin, bağımlı proje bir birim testi projem ise, **privatevarlıkların** özniteliğini ayarlayarak başvurulan projenin *. csproj* veya *. vbproj* dosyasında NuGet paketini özel olarak işaretleyin:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'de kod Çözümleyicileri 'ne genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Kod Çözümleyicisi hatası gönderme](https://github.com/dotnet/roslyn-analyzers/issues)
- [Kural kümelerini kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Kod Analizi uyarılarını gösterme](../code-quality/in-source-suppression-overview.md)
- [Kod analizi için yapılandırma seçenekleri (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)