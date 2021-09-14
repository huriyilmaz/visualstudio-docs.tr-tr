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
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: b99c219e3ca4da798b6e685f7ae5ae0ad2906ba8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631808"
---
# <a name="overview"></a>Genel Bakış

Her Roslyn *çözümleyicisi* tanılaması veya kuralı, projeniz için üzerine yazılabilir ve özelleştirilebilir varsayılan önem derecesine ve gizleme durumuna sahip olur. Bu makale, çözümleyicinin önemliliklerini ayarlamayı ve çözümleyici ihlallerini gizlemeyi kapsar.

## <a name="configure-severity-levels"></a>Önem derecelerini yapılandırma

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16.3'te başlayarak, çözümleyici kurallarının veya tanılamanın önem derecelerini [editorConfig](#set-rule-severity-in-an-editorconfig-file)dosyasında, ampul menüsünden [ve](#set-rule-severity-from-the-light-bulb-menu)hata listesinden yapılandırabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

Çözümleyicileri bir çözümleyici paketi olarak yüklüyse *çözümleyici* [kurallarının](../code-quality/install-roslyn-analyzers.md) veya tanılamanın önem derece NuGet yapılandırabilirsiniz. Bir kuralın önem derecesini bir kural [kümesi Çözüm Gezgini](#set-rule-severity-from-solution-explorer) [dosyasından değiştirebilirsiniz.](#set-rule-severity-in-the-rule-set-file)

::: moniker-end

Aşağıdaki tabloda farklı önem derecesi seçenekleri yer alır:

| Önem Derecesi (Çözüm Gezgini) | Önem Derecesi (EditorConfig dosyası) | Derleme zamanı davranışı | Düzenleyici davranışı |
|-|-|-|
| Hata | `error` | İhlaller *Hata* Listesinde ve komut satırı derleme çıkışında Hatalar olarak görünür ve derlemelerin başarısız olmasına neden olur.| Rahatsız olan kodun altı kırmızı bir çizgiyle çizili ve kaydırma çubuğunda küçük bir kırmızı kutu ile işaretlenmiştir. |
| Uyarı | `warning` | İhlaller *Hata* Listesinde ve komut satırı derleme çıkışında Uyarılar olarak görünür, ancak derlemelerin başarısız olmasına neden olmaz. | Soruna neden olan kodun altı yeşil bir geçişle çizili ve kaydırma çubuğunda küçük bir yeşil kutuyla işaretlenmiştir. |
| Bilgi | `suggestion` | İhlaller, komut satırı derleme çıkışında değil Hata Listesinde İletiler olarak görünür.  | Soruna neden olan kod, gri bir geçişle altı çizili ve kaydırma çubuğunda küçük bir gri kutuyla işaretlenmiştir. |
| Gizli | `silent` | Kullanıcı tarafından görülemeyebilir. | Kullanıcı tarafından görülemeyebilir. Ancak tanılama, IDE tanılama altyapısına raporlandı. |
| Hiçbiri | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelen. Kuralın varsayılan değerini belirlemek için aşağıdaki Özellikler penceresi. | Kuralın varsayılan önem derecesine karşılık gelen. |

Kural ihlalleri bir çözümleyici tarafından bulunursa, bunlar kod düzenleyicisinde (soruna neden olan kodun altında bir geçiş olarak) ve Hata Listesi penceresinde rapor edilir. 

Hata listesinde bildirilen çözümleyici ihlalleri, [kuralın önem derecesi ayarıyla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) eş görünür. Çözümleyici ihlalleri, kod düzenleyicisinde rahatsız eden kodun altında geçişler olarak da gösterilir. Aşağıdaki görüntüde bir hata (kırmızı geçiş), bir uyarı (yeşil geçiş) ve bir öneri (üç gri nokta) olmak için üç &mdash; ihlal gösterilir:

![Visual Studio'da kod düzenleyicisinde geçişler](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsünde, Hata Listesinde görünen üç ihlalin aynıları yer alır:

![Hata Listesinde hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

Birçok çözümleyici kuralı veya *tanılama,* kural ihlallerini düzeltmek için uygulayabilecek *bir* veya daha fazla ilişkili kod düzeltmesi içerir. Kod düzeltmeleri, diğer Hızlı Eylemler türleriyle birlikte ampul simgesi menüsünde [gösterilir.](../ide/quick-actions.md) Bu kod düzeltmeleri hakkında daha fazla bilgi için bkz. [Yaygın Hızlı Eylemler](../ide/quick-actions.md).

![Çözümleyici ihlali ve Hızlı Eylem kod düzeltmesi](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>'Gizli' önem derecesi ile 'Hiçbiri' önem derecesi karşılaştırması

`Hidden` varsayılan olarak etkin önem derecesi kuralları, devre dışı veya önem `None` derecesi kurallarından birkaç farklı şekilde farklıdır.

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

- Id'ye göre tek bir kuralın önem derecesi girişi, bir kategoriye ait önem derecesi girdisine göre önceliklidir.
- Bir kategori için önem derecesi girişi, tüm çözümleyici kuralları için önem derecesi girdisine göre önceliklidir.

[CA1822'nin "Performans" kategorisine sahip](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) olduğu aşağıdaki EditorConfig örneğini düşünün:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Yukarıdaki örnekte üç giriş de CA1822 için geçerlidir. Ancak, belirtilen öncelik kuralları kullanılarak, ilk kural kimliği tabanlı önem derecesi girişi sonraki girişlere göre kazanır. Bu örnekte CA1822 etkili bir "hata" önem derecesine sahip olur. "Performans" kategorisine sahip kalan tüm kurallar önem derecesine "uyarı" sahip olur. "Performans" kategorisine sahip olan diğer tüm çözümleyici kuralları önem derecesine "öneri" sahip olur.

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>EditorConfig dosyasında kural önem derecelerini el ile yapılandırma

1. Projeniz için henüz bir EditorConfig dosyanız yoksa bir [ekleyin.](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Yapılandırmak istediğiniz her kural için ilgili dosya uzantısı altında bir giriş ekleyin. Örneğin, C# dosyaları için [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) önem derecesini olarak `error` ayarlamak için giriş aşağıdaki gibi olacaktır:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> IDE kod stili çözümleyiciler için, farklı bir söz dizimi kullanarak bunları bir EditorConfig dosyasında da yapılandırabilirsiniz, `dotnet_style_qualification_for_field = false:suggestion` örneğin, . Ancak, söz dizimi kullanarak bir önem `dotnet_diagnostic` derecesi ayarsanız öncelik alır. Daha fazla bilgi için [bkz. EditorConfig için dil kuralları.](/dotnet/fundamentals/code-analysis/style-rules/language-rules)

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Ampul menüsünden kural önem derecelerini ayarlama

Visual Studio, Hızlı Eylemler ampul menüsünden bir kuralın önem derecelerini yapılandırmak için [kullanışlı bir](../ide/quick-actions.md) yol sağlar.

1. İhlal olduktan sonra düzenleyicide ihlal geçişlerinin üzerine gelin ve ampul menüsünü açın. Veya imlecinizi satıra yerleştirerek **Ctrl tuşuna** + **basın.** (dönem).

2. Ampul menüsünden Sorunları yapılandır veya Bastır **Önem derecelerini** > **\<rule ID> yapılandır'ı seçin.**

   ![Visual Studio'da ampul menüsünden kural önem derecelerini Visual Studio](media/configure-rule-severity.png)

3. Buradan önem derecesi seçeneklerinden birini belirleyin.

   ![Kural önem derecesini Öneri olarak yapılandırma](media/configure-rule-severity-suggestion.png)

   Visual Studio önizleme kutusunda gösterildiği gibi kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede henüz bir EditorConfig dosyanız yoksa, Visual Studio bir tane oluşturur.

### <a name="set-rule-severity-from-the-error-list-window"></a>Hata Listesi penceresinden kural önem derecelerini ayarlama

Visual Studio, hata listesi bağlam menüsünden kuralın önem derecelerini yapılandırmak için kullanışlı bir yol da sağlar.

1. Bir ihlal oluştuktan sonra hata listesinde tanılama girişlerine sağ tıklayın.

2. Bağlam menüsünden Önem derecelerini **ayarla'ya tıklayın.**

   ![Hata listesinden kural önem derecelerini Visual Studio](media/configure-rule-severity-error-list.png)

3. Buradan önem derecesi seçeneklerinden birini belirleyin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede henüz bir EditorConfig dosyanız yoksa, Visual Studio bir tane oluşturur.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecelerini Çözüm Gezgini

Çözümleyici tanılamalarını özelleştirmenin büyük bir **Çözüm Gezgini.** Çözümleyicileri [bir çözümleyici](../code-quality/install-roslyn-analyzers.md) paketi NuGet,  Çözüm Gezgini'daki Başvurular  veya Bağımlılıklar **düğümü** altında **bir Çözümleyiciler Çözüm Gezgini.** **Çözümleyiciler'i** ve ardından çözümleyici derlemelerinden birini genişlettiklerinde, derlemede tüm tanılamaları görüyorsunuz.

![Çözüm Gezgini'de çözümleyiciler düğümü](media/analyzers-expanded-in-solution-explorer.png)

Özellikler penceresinde, bir tanılamanın açıklaması ve varsayılan önem derecesi de dahil olmak üzere özelliklerini **görüntüebilirsiniz.** Özellikleri görüntülemek için kurala sağ tıklayın ve Özellikler'i **seçin** veya kuralı seçin ve ardından Alt Enter **tuşuna** + **basın.**

![Özellikler penceresi'de tanılama özellikleri](media/analyzer-diagnostic-properties.png)

Tanılamaya ilişkin çevrimiçi belgeleri görmek için tanılamaya sağ tıklayın ve Yardımı **Görüntüle'yi seçin.**

Her tanılamanın yanındaki **simgeler Çözüm Gezgini** düzenleyicide açarak kural kümesinde gördüğünüz simgelere karşılık gelecektir:

- Dairenin "x" değeri Hata [önem derecesine](#configure-severity-levels) **işaret**
- Bir üçgende yer alan "!" işareti Uyarı [önem derecesine](#configure-severity-levels) **işaret eder**
- Dairenin "i" değeri Bilgi [önem derecesine](#configure-severity-levels) **işaret**
- Açık renkli arka plandaki bir dairenin "i" değeri, Gizli [önem derecesine işaret](#configure-severity-levels) **eder**
- Dairenin aşağı dönük ok değeri tanılamanın gizleniyor olduğunu gösterir

![Çözüm Gezgini'de tanılama simgeleri](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Mevcut bir Kural Kümesi dosyasını EditorConfig dosyasına dönüştürme

2019 Visual Studio 16.5 sürümünden başlayarak, kural kümesi dosyaları yönetilen kod için çözümleyici yapılandırması için EditorConfig dosyası için kullanım dışıdır. Çözümleyici kuralı Visual Studio yapılandırmaya yönelik en iyi araç, kural kümesi dosyaları yerine EditorConfig dosyalarında çalışacak şekilde güncelleştirildi. EditorConfig dosyaları, IDE kod stili seçenekleri dahil olmak üzere hem çözümleyici kuralı Visual Studio çözümleyici seçeneklerini yapılandırmaya olanak sağlar. Mevcut kural kümesi dosyanızı bir EditorConfig dosyasına dönüştürmeniz kesinlikle önerilir. Ayrıca, editorConfig dosyasını, kendi repo'nizin köküne veya çözüm klasörüne kaydetmeniz de önerilir. Repo veya çözüm klasörünün kökünü kullanarak, bu dosyanın önem derecesi ayarlarının sırasıyla tüm repo veya çözüme otomatik olarak uygulandığından emin olursanız.

Mevcut bir kural kümesi dosyasını EditorConfig dosyasına dönüştürmenin birkaç yolu vardır:

- Visual Studio'daki Kural Kümesi Düzenleyicisi'nde (2019 16.5 veya sonraki bir Visual Studio gerektirir). Projeniz zaten olarak belirli bir kural kümesi dosyası kullanıyorsa, projenizin içindeki Ruleset Editor'dan eşdeğer bir `CodeAnalysisRuleSet` EditorConfig dosyasına Visual Studio.

    1. Dosyanın içinde kural kümesi dosyasına çift Çözüm Gezgini.

       Kural Kümesi dosyası Kural Kümesi Düzenleyicisi'nde açılmıştır. Kural kümesi düzenleyicisinin üst **kısmında tıklanabilir** bir bilgi çubuğu görüyor gerekir.

       ![Kural Kümesi Düzenleyicisi'nde Kural Kümesi'ni EditorConfig dosyasına dönüştürme](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Bilgi **çubuğu bağlantısını** seçin.

       Bunun, **EditorConfig dosyasını** oluşturmak istediğiniz dizini seçmenize olanak sağlayan bir Farklı Kaydet iletişim kutusu açması gerekir.

    3. EditorConfig **dosyasını** oluşturmak için Kaydet düğmesini seçin.

       Oluşturulan EditorConfig'in düzenleyicide açılması gerekir. Ayrıca, MSBuild özelliği proje dosyasında güncelleştirilecek ve böylece artık özgün kural kümesi dosyasına `CodeAnalysisRuleSet` başvurulmayacak.

- Komut satırından:

    1. [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)NuGet paketini yükleyin.

    2. Kural kümesi dosyasının ve EditorConfig dosyasının yolları komut satırı bağımsız değişkenleri olarak yüklü `RulesetToEditorconfigConverter.exe` paketten yürütün.

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

1. Bu Çözüm Gezgini, Başvuru **Çözümleyicileri**  >  **(veya** .NET Core projeleri **için Bağımlılık**  >  **Çözümleyicileri)** genişletin.

2. Önem derecesini ayarlamak istediğiniz kuralı içeren derlemeyi genişletin.

::: moniker range=">=vs-2019"
3. Kurala sağ tıklayın ve Önem derecelerini **ayarla'yı seçin.** Bağlam menüsünde önem derecelerinden birini seçin.

   Visual Studio, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler. Projeniz EditorConfig dosyası yerine bir kural kümesi dosyası kullanıyorsa, önem derecesi girişi kural kümesi dosyasına eklenir.

   > [!TIP]
   > Projede henüz bir EditorConfig dosyanız veya kural kümesi dosyanız yoksa, Visual Studio yeni bir EditorConfig dosyası oluşturur.
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

  Kural kümesi ilk kez düzen alıyorsanız, Visual Studio varsayılan kural kümesi dosyasının bir kopyasını oluşturur, *\<projectname> .ruleset* olarak adlar ve projenize ekler. Bu özel kural kümesi ayrıca projeniz için etkin kural kümesi olur.

   > [!NOTE]
   > .NET Core .NET Standard projeleri, 'de kural kümeleri için menü **komutlarını desteklemez Çözüm Gezgini**, örneğin, **Etkin Kural Kümesi Aç.** Bir .NET Core veya .NET Standard için varsayılan olmayan bir kural kümesi belirtmek için [ **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) özelliğini proje dosyasına el ile ekleyin. Kural kümesi düzenleyicisi kullanıcı arabiriminde kural kümesi içinde Visual Studio yine de yapılandırabilirsiniz.

1. İçeren derlemesini genişleterek kurala göz at.

1. Eylem **sütununda,** açılan listeyi açmak için değeri seçin ve listeden istediğiniz önem derecesine tıklayın.

   ![Kural kümesi dosyası düzenleyicide açılır](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Oluşturulan kodu yapılandırma

Çözümleyiciler bir proje içinde tüm kaynak dosyaları üzerinde çalışır ve bunlar üzerinde ihlaller raporlar. Ancak, bu ihlaller tasarımcı tarafından oluşturulan kod dosyaları, derleme sistemi tarafından oluşturulan geçici kaynak dosyalar gibi oluşturulan kod dosyalarında kullanışlı değildir. Kullanıcılar bu dosyaları el ile düzenleyemez ve/veya bu tür araç tarafından oluşturulan dosyalarda ihlalleri düzeltmekle ilgili endişesi yok.

Varsayılan olarak, çözümleyicileri yürüten çözümleyici sürücüsü dosyaları belirli bir adla, dosya uzantısıyla veya otomatik olarak oluşturulan dosya üst bilgisinde oluşturulan kod dosyaları olarak kabul ediyor. Örneğin, veya ile biten bir dosya `.designer.cs` `.generated.cs` adı, oluşturulan kod olarak kabul edilir. Ancak, bu üristikler kullanıcının kaynak kodunda özel olarak oluşturulan tüm kod dosyalarını tanımyamaz.

2019 Visual Studio 16.5'den başlayarak, son kullanıcılar editorConfig dosyasında oluşturulan kod olarak kabul edilen belirli dosyaları ve/veya klasörleri [yapılandırabilir.](https://editorconfig.org/) Böyle bir yapılandırma eklemek için aşağıdaki adımları izleyin:

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

- Çözümleyiciler VSIX uzantısı olarak değil. .NET SDK ile NuGet bir paket olarak yüklenir.

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

Bir .NET Core projesinde, NuGet çözümleyicileri olan bir projeye başvuru eklersiniz, bu çözümleyiciler de bağımlı projeye otomatik olarak eklenir. Bu davranışı devre dışı bırakmak için, örneğin bağımlı proje bir birim testi projesi ise **PrivateAssets** özniteliğini ayarerek NuGet paketini başvurulan projenin *.csproj* veya *.vbproj* dosyasında özel olarak işaretle:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de kod çözümleyicilere genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Kod çözümleyicisi hatası gönderme](https://github.com/dotnet/roslyn-analyzers/issues)
- [Kural kümelerini kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Kod analizi uyarılarını gizleme](../code-quality/in-source-suppression-overview.md)
- [Kod analizi için yapılandırma seçenekleri (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
