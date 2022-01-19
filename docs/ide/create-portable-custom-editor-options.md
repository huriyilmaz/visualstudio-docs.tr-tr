---
title: EditorConfig ayarları
description: Kod temeli içinde çalışan herkes için tutarlı kodlama stilleri uygulamak için projenize veya kod tabanınıza editorConfig dosyası ekleme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.date: 01/07/2021
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 67bd6e342bf65b40e07a0b6f0e5fb9fc5b9c97e6
ms.sourcegitcommit: 658edd3b0dc23fb20728dafc12734b22f8ed1a89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/18/2022
ms.locfileid: "136890780"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig ile taşınabilir, özel düzenleyici ayarları oluşturma

Kod temeli içinde çalışan herkes için tutarlı kodlama stilleri uygulamak için projenize veya kod tabanınıza bir EditorConfig dosyası eklemek için bunu yapabilirsiniz. EditorConfig ayarları, genel metin düzenleyici Visual Studio önceliklidir. Bu, her kod temelini o projeye özel metin düzenleyici ayarlarını kullanmak üzere uyarlayabileceğiniz anlamına gelir. Diğer Seçenekler iletişim kutusunda kendi kişisel düzenleyici tercihlerinizi Visual Studio **ayarlayabilirsiniz.** Bu ayarlar, *.editorconfig* dosyası olmayan bir kod temeli üzerinde çalışırken veya *.editorconfig* dosyası belirli bir ayarı geçersiz kılmazsa geçerlidir. Stil sekmelerini veya boşluklarını girintileme gibi bir &mdash; tercih örneğidir.

EditorConfig ayarları, kod düzenleyiciler ve IDE'ler tarafından Visual Studio. Bu, kodunuzla birlikte gelen taşınabilir bir bileşendir ve kod yazma stillerini uygulamanın dışında bile Visual Studio.

::: moniker range=">=vs-2019"

Visual Studio'da projenize editorConfig dosyası Visual Studio, EditorConfig ayarlarına göre yeni kod satırları biçimlendirildi. Aşağıdaki komutlardan birini çalıştırmadıkça mevcut kodun biçimlendirmesi değişmez:

 - [Girinti stili](../ide/code-styles-and-code-cleanup.md) gibi boşluk ayarlarını ve yönergeleri sıralama gibi seçili kod stili ayarlarını uygulanan Kod Temizleme (**Ctrl** + **K**, **Ctrl** + **E).** `using`
 - **Düzenle** > **Gelişmiş** > **Belgeyi** Biçimlendir **(veya varsayılan** + **profilde** **Ctrl** K , Ctrl D), yalnızca girinti stili gibi +  boşluk ayarlarını uygular.

 ::: moniker-end

::: moniker range="=vs-2017"

Visual Studio'da projenize editorConfig dosyası Visual Studio, EditorConfig ayarlarına göre yeni kod satırları biçimlendirildi. Belgeyi biçimlendirmedikçe (Varsayılan profilde Gelişmiş BiçimBelgesini Düzenle veya  >    >   Ctrl K ,  +  **Ctrl** D) mevcut + **kodun** biçimlendirmesi değişmez. Belgeyi Biçimlendir'i ek kod temizlemesi gerçekleştirecek şekilde yapılandırmadıysanız belgeyi biçimlendirmek yalnızca girinti stili gibi [boşluk ayarlarını etkiler.](../ide/code-styles-and-code-cleanup.md#apply-code-styles)

 ::: moniker-end

::: moniker range="vs-2017"

Biçimlendirme seçenekleri sayfasında Belgeyi **Biçimlendir'in hangi** EditorConfig ayarlarının [ **geçerli olduğunu** tanımlayabilirsiniz.](reference/options-text-editor-csharp-formatting.md#format-document-settings)

::: moniker-end

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için bkz. [Mac için Visual Studio.](/visualstudio/mac/editorconfig)

## <a name="code-consistency"></a>Kod tutarlılığı

editorConfig Ayarlar dosyalarında girinti stili, sekme genişliği, satır sonu karakterleri, kodlama ve daha fazlası gibi tutarlı kodlama stillerini ve ayarlarını, hangi düzenleyici veya IDE'den bağımsız olarak korumanız gerekir? Örneğin, C# ile kod kodlarken, kod tabanınız girintilerin her zaman beş boşluk karakteri olmasını tercih eden bir kurala sahipse belgeler UTF-8 kodlaması kullanır ve her satır her zaman CR/LF ile biter, bunu yapmak için *bir .editorconfig* dosyası yapılandırabilirsiniz.

Kişisel projeleriniz üzerinde kullanılan kodlama kuralları, takımınız projelerinde kullanılanlardan farklı olabilir. Örneğin, kodlamayı tamamlarken girintilemenin sekme karakteri eklense de tercih edersiniz. Ancak, takımınız girintilemenin sekme karakteri yerine dört boşluk karakteri katmayı tercih ediyor olabilir. EditorConfig dosyaları, her senaryo için bir yapılandırmaya sahip olmak için bu sorunu çözer.

Kod tabanındaki bir dosya ayarları içerdiği için, bu kod tabanıyla birlikte ilerler. Kod dosyasını EditorConfig uyumlu bir düzenleyicide açarsanız metin düzenleyici ayarları etkinleştirilir. EditorConfig dosyaları hakkında daha fazla bilgi için EditorConfig.org [bakın.](https://editorconfig.org/)

> [!NOTE]
> EditorConfig dosyasında ayarlanacak kurallar şu anda bir CI/CD işlem hattında derleme hataları veya uyarıları olarak uygulanamıyor. Stil sapmaları yalnızca Visual Studio ve Hata **Listesi'nde görünür.**

## <a name="supported-settings"></a>Desteklenen ayarlar

Visual Studio düzenleyicisi EditorConfig özelliklerinin temel [kümelerini destekler:](https://editorconfig.org/#supported-properties)

- indent_style
- indent_size
- tab_width
- end \_ of_line
- Charset
- kırpma \_ trailing_whitespace
- insert \_ final_newline
- kök

XML Visual Studio EditorConfig düzenleyicisi ayarları dışındaki tüm desteklenen diller. EditorConfig ayrıca dil, [biçimlendirme](/dotnet/fundamentals/code-analysis/code-style-rule-options) [](/dotnet/fundamentals/code-analysis/style-rules/language-rules)ve [](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)C# ve diğer adlar için adlandırma [kuralları](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) gibi kod stili Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>EditorConfig dosyalarını ekleme ve kaldırma

Projenize veya kod tabanınıza bir EditorConfig dosyası eklerken, yazarak yeni kod satırları EditorConfig dosyasına göre biçimlendirilen. Ancak editorConfig dosyası eklemek, siz belgeyi biçimlendirene veya Kod Temizleme'yi çalıştırana kadar mevcut stilleri yeni stillere [dönüştürmez.](../ide/code-styles-and-code-cleanup.md) Örneğin, dosyanıza sekmelerle biçimlendirilmiş girintiler ekler ve boşluklarla girintiler içeren bir EditorConfig dosyası eklersiniz, girinti karakterleri otomatik olarak boşluklara dönüştürülemez. Belgeyi biçimlendirırken (**Gelişmiş** Biçim Belgesini Düzenle  >    >   veya **Ctrl** + **K**, **Ctrl** D ), EditorConfig dosyasındaki boşluk ayarları mevcut + kod satırlarına uygulanır.

Projenize veya kod tabanınıza bir EditorConfig dosyasını kaldırırsanız ve yeni kod satırlarının genel düzenleyici ayarlarına göre biçimlendir biçimlendirilmiş olması için açık kod dosyalarını kapatıp yeniden açabilirsiniz.

### <a name="add-an-editorconfig-file-to-a-project"></a>Projeye EditorConfig dosyası ekleme

1. Bir projeyi veya çözümü Visual Studio. *.editorconfig* ayarlarınızın çözümdeki tüm projelere mi yoksa yalnızca bir taneye mi uygulanıp uygulanamay durumuna bağlı olarak projeyi veya çözüm düğümünü seçin. .editorconfig dosyasını eklemek için proje veya çözümünüzdeki bir *klasörü de* seçin.

1. Menü çubuğundan Yeni Öğe **Ekle'Project**  >  **seçin veya** Ctrl Shift A  + **tuşlarına** + **basın.**

   Yeni **Öğe Ekle iletişim** kutusu açılır.

1. Arama kutusunda **editorconfig araması yazın.**

   Arama **sonuçlarında iki editorconfig** Dosya öğesi şablonu gösterilir.

   ![Visual Studio'de EditorConfig dosya Visual Studio](media/vs-2022/editorconfig-item-templates-new.png)

1. Girinti stili ve boyutu için iki temel EditorConfig seçeneğiyle önceden doldurulan bir EditorConfig dosyası eklemek için editorconfig Dosyası **(varsayılan)** şablonunu seçin. Veya **editorconfig Dosyası (.NET)** şablonunu seçerek varsayılan .NET kod [stili,](/dotnet/fundamentals/code-analysis/code-style-rule-options)biçimlendirme ve adlandırma kurallarıyla önceden doldurulan bir EditorConfig dosyası ekleyin.

   Bir *.editorconfig* dosyası Çözüm Gezgini açılır ve düzenleyicide açılır.

   ![Dosya ve düzenleyicide .editorconfig Çözüm Gezgini.editorconfig dosyası](media/vs-2022/editorconfig-dotnet-new.png)

1. Dosyayı istediğiniz gibi düzenleyin.

### <a name="other-ways-to-add-an-editorconfig-file"></a>EditorConfig dosyası eklemenin diğer yolları

Projenize EditorConfig dosyası eklemenin birkaç farklı yolu vardır:

- [IntelliCode'daki kod](/visualstudio/intellicode/code-style-inference) çıkarma özelliği Visual Studio kod stillerinizi mevcut koddan çıkartır. Ardından kod stili tercihleriniz önceden tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- 2019'Visual Studio başlayarak, Araçlar Seçenekleri'nde kod stili ayarlarınıza göre bir [EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) **dosyası**  >  **oluşturabilirsiniz.**

## <a name="file-hierarchy-and-precedence"></a>Dosya hiyerarşisi ve önceliği

Dosya hiyerarşinizin *bir klasörüne bir .editorconfig* dosyası eklerken, bu dosyanın ayarları bu düzeydeki ve altındaki tüm ilgili dosyalara uygulanır. Ayrıca belirli bir proje, kod temeli veya kod tabanının bir parçası için EditorConfig ayarlarını geçersiz kılabilirsiniz; böylece kod tabanının diğer kısımlarından farklı kuralları kullanır. Bu, kodu başka bir yerden dahil ediyor ve kuralları değiştirmek istemiyorken yararlı olabilir.

EditorConfig ayarlarının bir veya hepsini geçersiz kılmak için, geçersiz kılınan ayarların uygulamalarını istediğiniz dosya hiyerarşisi düzeyinde bir *.editorconfig* dosyası ekleyin. Yeni EditorConfig dosya ayarları aynı düzeydeki dosyalara ve tüm alt dizinlere uygulanır.

![EditorConfig hiyerarşisi](../ide/media/vside_editorconfig_hierarchy.png)

Bazı ayarları geçersiz kılmak ancak tüm ayarları geçersiz kılmak *istemiyorsanız, .editorconfig* dosyasında yalnızca bu ayarları belirtin. Yalnızca alt düzey dosyada açıkça listelene özellikler geçersiz kılınır. Üst düzey *.editorconfig dosyalarında yer alan diğer* ayarlar geçerli olmaya devam eder.

Kod tabanının _bu_ parçasına  herhangi bir üst düzey *.editorconfig* dosyasından hiçbir ayar uygulanmay olduğundan emin olmak için, özelliğini alt düzey ```root=true``` *.editorconfig dosyasına* ekleyin:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig dosyaları en üstten aşağıya okunur. Aynı adla birden çok özellik varsa, bu adla en son bulunan özellik önceliklidir.

## <a name="edit-editorconfig-files"></a>EditorConfig dosyalarını düzenleme

Visual Studio IntelliSense tamamlama listeleri *sağlayarak .editorconfig* dosyalarını düzenlemenizi sağlar.

![.editorconfig dosyasında IntelliSense](media/vs-2022/editorconfig-intellisense-no-extension-new.png)

EditorConfig dosyanızı düzenledikten sonra yeni ayarların etkili olması için kod dosyalarınızı yeniden yükleyebilirsiniz.

Birçok *.editorconfig dosyası düzenlerken* [EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) Dil Hizmeti uzantısı yararlı olabilir. Bu uzantının özelliklerinden bazıları söz dizimi vurgulama, geliştirilmiş IntelliSense, doğrulama ve kod biçimlendirmedir.

![EditorConfig Dil Hizmeti uzantısıyla IntelliSense](media/editorconfig-intellisense.png)

## <a name="example"></a>Örnek

Aşağıdaki örnek, projeye *bir .editorconfig* dosyası eklemeden önce ve ekledikten sonra bir C# kod parçacığının girinti durumunu gösterir. **Sekmeler** iletişim kutusundaki **Sekmeler** ayarı, Visual Studio tuşuna basarak boşluk karakterleri üretecek **şekilde** ayarlanır.

![Metin Düzenleyici sekme ayarı](../ide/media/vs-2022/vside_editorconfig_tabsetting-new.png)

Beklendiği gibi, sonraki **satırda Sekme** tuşuna basmak, dört boşluk karakteri daha ekleyerek satırı girintiler.

![EditorConfig'i kullanmadan önce kod](../ide/media/vs-2022/vside_editorconfig_before-new.png)

Projeye aşağıdaki içeriklerle *.editorconfig* adlı yeni bir dosya ekleyin. ayarı, `[*.cs]` bu değişikliğin yalnızca projesinde C# kod dosyaları için geçerli olduğu anlamına gelir.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Şimdi Sekme tuşuna **basacak** olurken boşluk yerine sekme karakterleri alır.

![Sekme tuşu Sekme karakteri ekler](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>EditorConfig ayarları sorunlarını giderme

projenizin konumunun veya üstündeki dizin yapısında herhangi bir yerde bir editorconfig dosyası varsa Visual Studio, bu dosyadaki düzenleyici ayarlarını düzenleyicinize uygular. Bu durumda, durum çubuğunda aşağıdaki iletiyi görebilirsiniz:

   **"Bu dosya türü için Kullanıcı tercihleri bu projenin kodlama kuralları tarafından geçersiz kılınır."**

Diğer bir deyişle, **Araçlar**  >  **Seçenekler**  >  **metin düzenleyicisinde** (girinti boyutu ve stil, sekme boyutu veya kodlama kuralları gibi) herhangi bir düzenleyici ayarı, dizin yapısında proje üzerinde veya üzerinde bir editorconfig dosyasında belirtildiğinde, editorconfig dosyasındaki kurallar **seçeneklerindeki** ayarları geçersiz kılar. **Araç** seçenekleri metin düzenleyicisinde **Proje kodlama kurallarını izle** seçeneğini değiştirerek bu davranışı kontrol edebilirsiniz  >    >  . Seçeneğin işaretlenmesi, Visual Studio için EditorConfig desteğini devre dışı bırakır.

![Araç seçenekleri-proje kodlama kurallarını izleyin](media/vs-2022/coding_conventions_option-new.png)

Herhangi bir *. editorconfig* dosyasını, bir komut istemi açıp ve projenizi içeren diskin kökünden aşağıdaki komutu çalıştırarak, üst dizinlerde bulabilirsiniz:

```Shell
dir .editorconfig /s
```

```root=true```Deponuzın kökündeki *. editorconfig* dosyasında veya projenizin bulunduğu dizinde özelliğini ayarlayarak editorconfig kurallarınızın kapsamını kontrol edebilirsiniz. Visual Studio, açılan dosyanın dizininde ve her üst dizinde *. editorconfig* adlı bir dosya arar. Arama, kök FilePath 'e ulaştığında veya ile bir *. editorconfig* dosyası bulunursa sona erer ```root=true``` .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kodu stil kuralları](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Dil hizmeti için EditorConfig destekleme](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Kod düzenleyicisinin özellikleri](writing-code-in-the-code-and-text-editor.md)
- [editorconfig (Mac için Visual Studio)](/visualstudio/mac/editorconfig)
