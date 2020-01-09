---
title: Çözümleyici kuralı önem derecesi ve gizleme
ms.date: 09/23/2019
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
ms.openlocfilehash: c24164f31ca444d17035f145a1783c69dfb2585b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587205"
---
# <a name="use-code-analyzers"></a>Kod Çözümleyicileri kullanma

.NET Compiler Platform ("Roslyn") kod Çözümleyicileri, siz yazarken C# veya Visual Basic kodunuzu analiz eder. Her bir *Tanılama* veya kuralın, projeniz için üzerine yazılabilir bir varsayılan önem derecesi ve gizleme durumu vardır. Bu makalede kural önem derecesini ayarlama, kural kümelerini kullanma ve ihlalleri gizleme ele alınmaktadır.

## <a name="analyzers-in-solution-explorer"></a>Çözüm Gezgini çözümleyiciler

**Çözüm Gezgini**'den çözümleyici tanılamayı özelleştirmenin çoğunu yapabilirsiniz. Çözümleyiciler bir NuGet paketi olarak [yüklüyorsanız](../code-quality/install-roslyn-analyzers.md) , **Çözüm Gezgini**içindeki **Başvurular** veya **Bağımlılıklar** düğümü altında bir **çözümleyiciler** düğümü görüntülenir. **Çözümleyicileri**genişlettikten sonra çözümleyici derlemelerinden birini genişletirseniz, derlemede tüm tanılamayı görürsünüz.

![Çözüm Gezgini içinde düğüm Çözümleyicileri](media/analyzers-expanded-in-solution-explorer.png)

**Özellikler** penceresinde, açıklaması ve varsayılan önem derecesi dahil olmak üzere bir tanı özelliklerini görüntüleyebilirsiniz. Özellikleri görüntülemek için kurala sağ tıklayın ve **Özellikler**' i seçin veya kuralı seçip **alt**+**ENTER**tuşuna basın.

![Özellikler penceresi tanılama özellikleri](media/analyzer-diagnostic-properties.png)

Bir Tanılamanın çevrimiçi belgelerini görmek için, tanılamayı sağ tıklatın ve **Yardımı görüntüle**' yi seçin.

**Çözüm Gezgini** içindeki her bir Tanılamanın yanındaki simgeler, düzenleyicide açtığınızda kural kümesinde gördüğünüz simgelere karşılık gelir:

- bir daire içindeki "x", **hatanın** [önem derecesini](#rule-severity) gösterir
- Bir üçgendeki "!", **uyarının** [önem derecesini](#rule-severity) gösterir
- bir daire içindeki "i", **bilgi** [önem derecesini](#rule-severity) gösterir
- açık renkli bir arka plandaki daire içindeki "i", **gizlenen** [önem derecesini](#rule-severity) gösterir
- bir daire içindeki aşağı açılan ok, Tanılamanın bastırılmadığını belirtir

![Çözüm Gezgini tanılama simgeleri](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Kural önem derecesi

::: moniker range=">=vs-2019"

Çözümleyiciler bir NuGet paketi olarak [yüklüyorsanız](../code-quality/install-roslyn-analyzers.md) , çözümleyici kurallarının önem derecesini veya *tanılamayı*yapılandırabilirsiniz. Visual Studio 2019 sürüm 16,3 ' den başlayarak bir [EditorConfig dosyasındaki](#set-rule-severity-in-an-editorconfig-file)bir kuralın önem derecesini yapılandırabilirsiniz. Kuralın önem derecesini [Çözüm Gezgini](#set-rule-severity-from-solution-explorer) veya [bir kural kümesi dosyasında](#set-rule-severity-in-the-rule-set-file)da değiştirebilirsiniz.

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
| Hidden | `silent` | Kullanıcıya görünür değil. | Kullanıcıya görünür değil. Ancak tanılama, IDE tanılama altyapısına bildirilir. |
| Yok. | `none` | Tamamen gizlendi. | Tamamen gizlendi. |
| Varsayılan | `default` | Kuralın varsayılan önem derecesine karşılık gelir. Bir kural için varsayılan değerin ne olduğunu belirlemek için Özellikler penceresi bakın. | Kuralın varsayılan önem derecesine karşılık gelir. |

Kod düzenleyicisinin aşağıdaki ekran görüntüsünde, farklı önem derecelerine sahip üç farklı ihlal gösterilmektedir. Sağ taraftaki kaydırma çubuğundaki dalgalı çizgi ve küçük, renkli bir karenin rengine dikkat edin.

![Kod düzenleyicisinde hata, uyarı ve bilgi ihlali](media/diagnostics-severity-colors.png)

Aşağıdaki ekran görüntüsünde Hata Listesi göründükleri üç ihlal gösterilmektedir:

![Hata Listesi hata, uyarı ve bilgi ihlali](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Bir EditorConfig dosyasında kural önem derecesini ayarlama

(Visual Studio 2019 sürüm 16,3 ve üstü)

Bir EditorConfig dosyasındaki bir kuralın önem derecesini belirtmek için genel sözdizimi şöyledir:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Bir EditorConfig dosyasında bir kuralın önem derecesini ayarlamak, bir kural kümesinde veya Çözüm Gezgini ayarlanan herhangi bir önem derecesine göre önceliklidir. Bir EditorConfig dosyasındaki önem derecesini [el ile](#manually-configure-rule-severity) yapılandırabilir veya bir ihlalin yanında görünen ampul aracılığıyla [otomatik olarak](#automatically-configure-rule-severity) yapılandırabilirsiniz.

#### <a name="manually-configure-rule-severity"></a>Kural önem derecesini el ile yapılandır

1. Projeniz için zaten bir EditorConfig dosyanız yoksa, [bir tane ekleyin](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Karşılık gelen dosya uzantısı altında yapılandırmak istediğiniz her kural için bir giriş ekleyin. Örneğin, [CA1822](ca1822.md) için önem derecesini dosyalar için C# `error` olarak ayarlamak için, giriş aşağıdaki gibi görünür:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> IDE kod stili Çözümleyicileri için, farklı bir sözdizimi kullanarak bunları bir EditorConfig dosyasında da yapılandırabilirsiniz, örneğin `dotnet_style_qualification_for_field = false:suggestion`. Ancak, `dotnet_diagnostic` söz dizimini kullanarak önem derecesi ayarlarsanız, öncelik kazanır. Daha fazla bilgi için bkz. [EditorConfig Için dil kuralları](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Kural önem derecesini otomatik olarak Yapılandır

Visual Studio, bir kuralın önem derecesini [hızlı eylemler](../ide/quick-actions.md) ampul menüsünden yapılandırmanın kolay bir yolunu sunar.

1. Bir ihlal oluştuktan sonra, düzenleyicide ihlalin üzerine gelin ve ampul menüsünü açın. Ya da imlecinizi satıra yerleştirip **Ctrl**+tuşuna basın **.** (nokta).

2. Ampul menüsünde, **\<kural kimliği > önem derecesini yapılandırmak**> **sorunları Yapılandır veya gizle** ' yi seçin.

   ![Visual Studio 'da ampul menüsünden Kural önem derecesini yapılandırma](media/configure-rule-severity.png)

3. Buradan, önem derecesi seçeneklerinden birini seçin.

   ![Öneri olarak kural önem derecesini yapılandırma](media/configure-rule-severity-suggestion.png)

   Visual Studio, önizleme kutusunda gösterildiği gibi, kuralı istenen düzeye yapılandırmak için EditorConfig dosyasına bir giriş ekler.

   > [!TIP]
   > Projede zaten bir EditorConfig dosyanız yoksa, Visual Studio sizin için bir tane oluşturur.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Kural önem derecesini Çözüm Gezgini ayarla

1. **Çözüm Gezgini**' de, çözümleyiciler > **Çözümleyicileri** (veya .NET Core projeleri için **çözümleyiciler** > **Bağımlılıklar** ) ' ı genişletin.

1. Önem derecesini ayarlamak istediğiniz kuralı içeren derlemeyi genişletin.

1. Kurala sağ tıklayın ve **kural kümesi önem derecesi ayarla**' yı seçin. Giriş menüsünde, önem derecesi seçeneklerinden birini seçin.

   Kuralın önem derecesi, etkin kural kümesi dosyasına kaydedilir.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Kural önem derecesini kural kümesi dosyasında ayarla

![Çözüm Gezgini kural kümesi dosyası](media/ruleset-in-solution-explorer.png)

1. Etkin kural kümesi dosyasını **Çözüm Gezgini**' de çift tıklayarak açın **, > ** **çözümleyiciler** düğümünün sağ tıklama menüsünde **etkin kural kümesi aç** ' ı seçin veya proje için **Kod Analizi** Özellik sayfasında **Aç** ' ı seçin.

   Kural kümesini ilk kez düzenliyorsanız, Visual Studio varsayılan kural kümesi dosyasının bir kopyasını oluşturur, onu *\<projectname >. RuleSet*olarak adlandırır ve projenize ekler. Bu özel kural kümesi, projeniz için etkin kural kümesi de olur.

   > [!NOTE]
   > .NET Core ve .NET Standard projeleri, **Çözüm Gezgini**kural kümeleri için menü komutlarını desteklemez, örneğin, **etkin kural kümesi açın**. .NET Core veya .NET Standard projesi için varsayılan olmayan bir kural kümesi belirtmek için, [ **CodeAnalysisRuleSet** özelliğini](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) proje dosyasına el ile ekleyin. Kuralları, Visual Studio kural kümesi Düzenleyicisi Kullanıcı arabirimindeki kural kümesi içinde yine yapılandırabilirsiniz.

1. İçeren derlemeyi genişleterek kurala gidin.

1. **Eylem** sütununda, bir açılan listeyi açmak için değeri seçin ve listeden istenen önem derecesini seçin.

   ![Düzenleyicide kural kümesi dosyası aç](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>İhlalleri gösterme

Kural ihlallerini bastırmak için birden çok yol vardır:

::: moniker range=">=vs-2019"

- Bir **Editorconfig dosyasında**

  Önem derecesini `none`, örneğin `dotnet_diagnostic.CA1822.severity = none`olarak ayarlayın.

- **Çözümle** menüsünden

  Tüm geçerli ihlallerin görüntülenmesini sağlamak için, > derlemeyi **Çözümle** ve menü çubuğunda **etkin sorunları gösterme '** yi seçin. Bu bazen "taban çizgisi" olarak adlandırılır.

::: moniker-end

::: moniker range="vs-2017"

- **Çözümle** menüsünden

  Tüm geçerli ihlallerin görüntülenmesini sağlamak için, Kod analizini Çalıştır > **Çözümle** ve menü çubuğundaki **etkin sorunları Gizle '** yi seçin. Bu bazen "taban çizgisi" olarak adlandırılır.

::: moniker-end

- **Çözüm Gezgini** 'den

  Kuralın önem derecesini **hiçbiri**olarak ayarlayın.

- **Kural kümesi düzenleyicisinden**

  Adının yanındaki kutunun işaretini kaldırın veya **eylemi** **none**olarak ayarlayın.

- **Kod düzenleyicisinden**

  İmleci bir kod satırına yerleştirin ve **hızlı eylemler** menüsünü açmak için **CTRL**+**Period (.)** tuşuna basın. **Kaynak/gizleme dosyasında** **caxxxx > Gizle** ' yi seçin.

  ![Hızlı Eylemler menüsünden tanılamayı gösterme](media/suppress-diagnostic-from-editor.png)

- **Hata listesi**

  Gizlemek istediğiniz kuralları seçin ve ardından sağ tıklayıp **kaynak/gizleme dosyasında** > **Gizle** ' yi seçin.

  - **Kaynakta**bastırdığınızda, **Değişiklikleri Önizle** iletişim kutusu açılır ve kaynak koda eklenen C# [#pragma uyarının](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) veya Visual Basic [#Disable uyarı](/dotnet/visual-basic/language-reference/directives/directives) yönergesinin önizlemesini gösterir.

    ![Kod dosyasında #pragma uyarı ekleme önizlemesi](media/pragma-warning-preview.png)

  - **Gizleme dosyası ' nda**, **Değişiklikleri Önizle** iletişim kutusu açılır ve genel gizlemeleri dosyasına eklenen <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğinin önizlemesi gösterilir.

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

- Bir ihlal kuralının [önem derecesi](#rule-severity) , **Uyarı**olarak ayarlanır; Bu durumda ihlallerin başarısız olmasına neden olmaz veya **hata**, bu durum ihlallerinin başarısız olmasına neden olur.

Yapı çıkışının ayrıntı düzeyi, kural ihlallerinin gösterilip gösterilmeyeceğini etkilemez. **Sessiz** ayrıntı düzeyine sahip olsa bile, yapı çıkışında kural ihlalleri görüntülenir.

> [!TIP]
> Bir komut satırından, *FxCopCmd. exe* Ile veya **RunCodeAnalysis** bayrağıyla MSBuild aracılığıyla eski analizler çalıştırmaya alışkın değilseniz, bu işlemi kod Çözümleyicileri ile nasıl yapacağıdır.

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
