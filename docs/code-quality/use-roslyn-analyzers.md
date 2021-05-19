---
title: Çözümleyici yapılandırması
ms.date: 05/10/2021
description: Roslyn çözümleyicisi kurallarını özelleştirmeyi öğrenin. Çözümleyicinin önemliliklerini ayarlamayı, ihlalleri gizlemeyi ve dosyaları oluşturulan kod olarak atamayı görme.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 36a9f1651a4aef7742b6bf52f8691f6ae8f9c616
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973388"
---
# <a name="overview"></a>Genel Bakış

Her Roslyn *çözümleyicisi* tanılaması veya kuralı, projeniz için üzerine yazılabilir ve özelleştirilebilir varsayılan bir önem derecesi ve gizleme durumuna sahip olur. Bu makale, çözümleyicinin önemliliklerini ayarlamayı ve çözümleyici ihlallerini gizlemeyi kapsar.

## <a name="configure-severity-levels"></a>Önem derecelerini yapılandırma

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16.3'te başlayarak, çözümleyici kurallarının veya tanılamanın önem derecelerini [editorConfig](#set-rule-severity-in-an-editorconfig-file)dosyasında, ampul menüsünden [ve](#set-rule-severity-from-the-light-bulb-menu)hata listesinden yapılandırabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

Çözümleyicileri Bir NuGet paketi olarak yüklüyse *çözümleyici* [kurallarının](../code-quality/install-roslyn-analyzers.md) veya tanılamanın önem derecelerini yapılandırabilirsiniz. Bir kuralın önem derecesini bir kural [kümesi Çözüm Gezgini](#set-rule-severity-from-solution-explorer) [dosyasından değiştirebilirsiniz.](#set-rule-severity-in-the-rule-set-file)

::: moniker-end

Aşağıdaki tabloda farklı önem derecesi seçenekleri yer alır:

| Önem Derecesi (Çözüm Gezgini) | Önem Derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller *Hata* Listesinde ve komut satırı derleme çıkışında Hatalar olarak görünür ve derlemelerin başarısız olmasına neden olur.| Soruna neden olan kodun altı kırmızı bir çizgiyle çizili ve kaydırma çubuğunda küçük bir kırmızı kutuyla işaretlenmiştir. |
| Uyarı | `warning` | İhlaller *Hata* Listesinde ve komut satırı derleme çıkışında Uyarılar olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Soruna neden olan kodun altı yeşil bir geçişle çizili ve kaydırma çubuğunda küçük bir yeşil kutuyla işaretlenmiştir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıkışında değil Hata Listesinde İletiler olarak görünür.  | Soruna neden olan kodun altı gri bir geçişle çizili ve kaydırma çubuğunda küçük bir gri kutuyla işaretlenir. |
| Gizli | `silent` | Kullanıcıya görünür değil. | Kullanıcıya görünür değil. Ancak tanılama, IDE tanılama altyapısına bildirilir. |
| Hiçbiri | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kural için varsayılan değerin ne olduğunu belirlemek için Özellikler penceresi bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (sorunlu kod altında bir *dalgalı çizgi* olarak) ve hata listesi penceresinde raporlanır.

Hata listesinde bildirilen çözümleyici ihlalleri kuralın [önem derecesi düzeyi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eşleşir. Çözümleyici ihlalleri Ayrıca kod düzenleyicisinde, sorunlu kodun altında dalgalı çizgiler olarak görünür. Aşağıdaki görüntüde &mdash; bir hata (kırmızı dalgalı çizgi), bir uyarı (yeşil dalgalı çizgi) ve bir öneri (üç gri noktalı) olmak üzere üç ihlal gösterilmektedir:

![Visual Studio 'da kod düzenleyicisinde dalgalı çizgiler](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsünde Hata Listesi göründükleri üç ihlal gösterilmektedir:

![Hata Listesi hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

Birçok çözümleyici kuralı veya *tanılaması*, kural ihlalini düzeltmek için uygulayabileceğiniz bir veya daha fazla ilişkili *kod düzeltmesiyle* sahiptir. Kod düzeltmeleri, ampul simgesi menüsünde diğer [hızlı eylem](../ide/quick-actions.md)türleriyle birlikte gösterilir. Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Genel Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve hızlı eylem kodu onarımı](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>' Hidden ' önem derecesine ve ' none ' önem derecesine karşı

`Hidden` varsayılan olarak etkin önem derecesi kuralları, devre dışı veya önem derecesi `None` kurallarından birkaç farklı şekilde farklıdır.

- Bir önem kuralı için herhangi bir kod düzeltmesi kaydedilmişse, gizli tanılama kullanıcıya görünmese bile düzeltme Visual Studio'de ampul kodu yeniden düzenleme `Hidden` eylemi olarak sunulur. Devre dışı önem derecesi kuralları için `None` bu durum geçerli değildir.
- `Hidden`önem derecesi kuralları, editorConfig dosyasında aynı anda birden çok çözümleyici kuralının kural önem [derecesine ayar eden girişler tarafından toplu yalıtılmıştır.](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file) `None` önem derecesi kuralları bu şekilde yapılandıramaz. Bunun yerine, her kural kimliği için bir EditorConfig dosyasında [kural önem derecesine ayarlanacak girişler aracılığıyla yapılandırıldılar.](#set-rule-severity-in-an-editorconfig-file)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>EditorConfig dosyasında kural önem derecelerini ayarlama

(Visual Studio 2019 sürüm 16.3 ve sonrası)

EditorConfig dosyasında aşağıdaki söz dizimleriyle derleyici uyarıları veya çözümleyici kuralları için önem derecelerini belirtebilirsiniz:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

EditorConfig dosyasında bir kuralın önem derecelerini ayarlamak, kural kümesinde veya kural kümesinde ayarlanmış olan önem derecelerine Çözüm Gezgini. Önem [derecelerini](#manually-configure-rule-severity-in-an-editorconfig-file) editorConfig dosyasında el ile veya [ihlalin](#set-rule-severity-from-the-light-bulb-menu) yanında görünen ampul aracılığıyla otomatik olarak yapılandırabilirsiniz.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>EditorConfig dosyasında aynı anda birden çok çözümleyici kuralının kural önem derecelerini ayarlama

(Visual Studio 2019 sürüm 16.5 ve sonrası)

Belirli bir çözümleyici kuralları kategorisi veya EditorConfig dosyasında tek bir girişe sahip tüm çözümleyici kuralları için önem derecesini belirtebilirsiniz.

- Çözümleyici kuralları kategorisi için kural önem derecesini ayarlayın:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Tüm çözümleyici kuralları için kural önem derecelerini ayarlayın:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Aynı anda birden çok çözümleyici kuralı yapılandırmaya yönelik girişler yalnızca varsayılan olarak *etkinleştirilmiş kurallara uygulanır.* Çözümleyici paketinde varsayılan olarak devre dışı olarak işaretlenmiş çözümleyici kurallarının açık girişler aracılığıyla `dotnet_diagnostic.<rule ID>.severity = <severity>` etkinleştirilmesi gerekir.

Belirli bir kural kimliği için geçerli olan birden çok girdiniz varsa, ilgili girişi seçmek için öncelik sırası aşağıdaki şekildedir:

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

Visual Studio, bir kuralın önem derecesini [hızlı eylemler](../ide/quick-actions.md) ampul menüsünden yapılandırmanın kolay bir yolunu sunar.

1. Bir ihlal oluştuktan sonra, düzenleyicide ihlalin üzerine gelin ve ampul menüsünü açın. Ya da imlecinizi satıra yerleştirip **CTRL** tuşuna basın + **.** (nokta).

2. Ampul menüsünden Sorunları yapılandır veya Bastır **Önem derecelerini** > **\<rule ID> yapılandır'ı seçin.**

   ![Visual Studio'da ampul menüsünden kural önem derecelerini Visual Studio](media/configure-rule-severity.png)

3. Buradan önem derecesi seçeneklerinden birini belirleyin.

   ![Kural önem derecesini Öneri olarak yapılandırma](media/configure-rule-severity-suggestion.png)

   Visual Studio önizleme kutusunda gösterildiği gibi kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede henüz bir EditorConfig dosyanız yoksa, sizin Visual Studio bir tane oluşturur.

### <a name="set-rule-severity-from-the-error-list-window"></a>Hata Listesi penceresinden kural önem derecelerini ayarlama

Visual Studio, hata listesi bağlam menüsünden kuralın önem derecelerini yapılandırmak için kullanışlı bir yol da sağlar.

1. Bir ihlal oluştuktan sonra hata listesinde tanılama girişlerine sağ tıklayın.

2. Bağlam menüsünden Önem derecelerini **ayarla'ya tıklayın.**

   ![Hata listesinden kural önem derecelerini Visual Studio](media/configure-rule-severity-error-list.png)

3. Buradan önem derecesi seçeneklerinden birini belirleyin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede henüz bir EditorConfig dosyanız yoksa, sizin Visual Studio bir tane oluşturur.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecelerini Çözüm Gezgini

Çözümleyici tanılamalarını özelleştirmenin büyük bir **Çözüm Gezgini.** Çözümleyicileri [nuGet](../code-quality/install-roslyn-analyzers.md) paketi olarak yüklürsanız, çözümleyiciler düğümünde, uygulamanın Başvurular veya **Bağımlılıklar** düğümü altında bir **Çözümleyiciler Çözüm Gezgini.**   **Çözümleyiciler'i** ve ardından çözümleyici derlemelerinden birini genişlettiklerinde, derlemede tüm tanılamaları görüyorsunuz.

![Çözüm Gezgini'de çözümleyiciler düğümü](media/analyzers-expanded-in-solution-explorer.png)

Özellikler penceresinde bir tanılamanın açıklamasını ve varsayılan önem derecesini de içeren özelliklerini **görüntüebilirsiniz.** Özellikleri görüntülemek için kurala sağ tıklayın ve **Özellikler**' i seçin veya kuralı seçin ve ardından **alt** + **ENTER** tuşuna basın.

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

- Visual Studio 'daki RuleSet düzenleyicisinden (Visual Studio 2019 16,5 veya üstünü gerektirir). Projeniz zaten olarak belirli bir kural kümesi dosyası kullanıyorsa, projenizin içindeki Ruleset Editor'dan eşdeğer bir `CodeAnalysisRuleSet` EditorConfig dosyasına Visual Studio.

    1. Dosyanın içinde kural kümesi dosyasına çift Çözüm Gezgini.

       Kural Kümesi dosyası Kural Kümesi Düzenleyicisi'nde açılmıştır. Kural kümesi düzenleyicisinin üst **kısmında tıklanabilir** bir bilgi çubuğu görüyor gerekir.

       ![Kural Kümesi Düzenleyicisi'nde Kural Kümesi'ni EditorConfig dosyasına dönüştürme](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Bilgi **çubuğu bağlantısını** seçin.

       Bunun, **EditorConfig dosyasını** oluşturmak istediğiniz dizini seçmenize olanak sağlayan bir Farklı Kaydet iletişim kutusu açması gerekir.

    3. EditorConfig **dosyasını** oluşturmak için Kaydet düğmesini seçin.

       Oluşturulan EditorConfig'in düzenleyicide açılması gerekir. Buna ek olarak, MSBuild özelliği artık özgün kural kümesi dosyasına `CodeAnalysisRuleSet` başvurulmayacak şekilde proje dosyasında güncelleştirilir.

- Komut satırından:

    1. [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)NuGet paketini yükleyin.

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

1. Bu Çözüm Gezgini, Başvuru **Çözümleyicileri**  >   (veya .NET Core projeleri **için Bağımlılık**  >  **Çözümleyicileri)** genişletin.

2. Önem derecesini ayarlamak istediğiniz kuralı içeren derlemeyi genişletin.

::: moniker range=">=vs-2019"
3. Kurala sağ tıklayın ve Önem derecelerini **ayarla'yı seçin.** Bağlam menüsünde önem derecelerinden birini seçin.

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

- **Çözüm Gezgini**' de, dosyaya **çift tıklayın,** çözümleyiciler öğesine sağ tıklayın  >   ve **etkin kural kümesini aç**' ı seçin.
- Projenin **Kod Analizi** Özellik sayfasında **Aç** ' ı seçin.

  Kural kümesini ilk kez düzenliyorsanız, Visual Studio varsayılan kural kümesi dosyasının bir kopyasını oluşturur, *\<projectname> . RuleSet* olarak adlandırır ve bunu projenize ekler. Bu özel kural kümesi, projeniz için etkin kural kümesi de olur.

   > [!NOTE]
   > .NET Core ve .NET Standard projeleri, **Çözüm Gezgini** kural kümeleri için menü komutlarını desteklemez, örneğin, **etkin kural kümesi açın**. .NET Core veya .NET Standard projesi için varsayılan olmayan bir kural kümesi belirtmek için, [ **CodeAnalysisRuleSet** özelliğini](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) proje dosyasına el ile ekleyin. Kuralları, Visual Studio kural kümesi Düzenleyicisi Kullanıcı arabirimindeki kural kümesi içinde yine yapılandırabilirsiniz.

1. İçeren derlemeyi genişleterek kurala gidin.

1. **Eylem** sütununda, bir açılan listeyi açmak için değeri seçin ve listeden istenen önem derecesini seçin.

   ![Düzenleyicide kural kümesi dosyası aç](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Oluşturulan kodu Yapılandır

Çözümleyiciler bir projedeki tüm kaynak dosyalarında çalışır ve bunlar üzerinde ihlalleri bildirir. Ancak, bu ihlaller tasarımcı tarafından oluşturulan kod dosyaları, derleme sistemi tarafından oluşturulan geçici kaynak dosyalar gibi oluşturulan kod dosyalarında kullanışlı değildir. Kullanıcılar bu dosyaları el ile düzenleyemez ve/veya bu tür araç tarafından oluşturulan dosyalarda ihlalleri düzeltmekle kaygılanmaz.

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

- Çözümleyiciler VSIX uzantısı olarak değil.NET SDK ile veya NuGet paketi olarak yüklenir.

  .NET SDK kullanılarak yüklenmiş çözümleyiciler için çözümleyicileri [etkinleştirmeniz gerekebilir.](../code-quality/install-net-analyzers.md) Kod stilleri için, bir MSBuild [özelliği ayarerek kod stillerini](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) derlemede de zorunlu kabilirsiniz.

- Projenin kodunda bir veya daha fazla kural ihlal edildi.

- İhlal edilmiş bir kuralın önem derecesi uyarı olarak ayarlanır; bu durumda ihlaller derlemenin başarısız olmasına veya hataya neden olmaz ve bu durumda ihlaller derlemenin başarısız olmasına neden olur. [](#configure-severity-levels)

Derleme çıkışının ayrıntılılığı, kural ihlallerinin gösterilip gösterilmeyeceğini etkilemez. **Sessiz** ayrıntı düzeyine sahip olsa bile, yapı çıkışında kural ihlalleri görüntülenir.

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
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod Çözümleyicileri 'ne genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Kod Çözümleyicisi hatası gönderme](https://github.com/dotnet/roslyn-analyzers/issues)
- [Kural kümelerini kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Kod Analizi uyarılarını gösterme](../code-quality/in-source-suppression-overview.md)
- [Kod analizi için yapılandırma seçenekleri (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
