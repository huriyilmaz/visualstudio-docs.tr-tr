---
title: EditorConfig ayarları
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 5fdb0cc217062190e02e70b6361c8a3a2aa2f935
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81648533"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig ile taşınabilir, özel düzenleyici ayarları oluşturma

Kod tabanında çalışan herkes için tutarlı kodlama stilleri zorlamak için projenize veya codebase'inize bir [EditorConfig](https://editorconfig.org/) dosyası ekleyebilirsiniz. EditorConfig ayarları, genel Visual Studio metin düzenleyicisi ayarlarını öncelikliolarak alır. Bu, her kod temelini o projeye özel metin düzenleyici ayarlarını kullanmak üzere uyarlayabileceğiniz anlamına gelir. Visual Studio **Options** iletişim kutusunda kendi kişisel düzenleyici tercihlerinizi ayarlayabilirsiniz. Bu ayarlar, *.editorconfig* dosyası olmadan bir kod tabanında çalışırken veya *.editorconfig* dosyası belirli bir ayarı geçersiz kılmadığında geçerlidir. Böyle bir tercihe örnek olarak&mdash;girintisi stil sekmeleri veya boşluklar bulunur.

EditorConfig ayarları Visual Studio da dahil olmak üzere çok sayıda kod editörü ve IDE tarafından desteklenir. Kodunuzla seyahat eden ve Visual Studio dışında bile kodlama stillerini uygulayabilen taşınabilir bir bileşendir.

::: moniker range=">=vs-2019"

Visual Studio'daki projenize bir EditorConfig dosyası eklediğinizde, EditorConfig ayarlarına göre yeni kod satırları biçimlendirilir. Aşağıdaki komutlardan birini çalıştırmadığınız sürece varolan kodun biçimlendirmesi değiştirilmez:

 - [Kod Temizleme](../ide/code-styles-and-code-cleanup.md) (**Ctrl**+**K**, **Ctrl**+**E**), girintisi stili ve `using` yönergeleri sıralama gibi seçili kod stili ayarları gibi tüm beyaz alan ayarlarını uygular.
 - Yalnızca girintisi stili gibi beyaz alan ayarlarını uygulayan **Gelişmiş** > **Biçim Belgesini** (veya varsayılan profildeki **Ctrl**+**K**, **Ctrl**+**D)** **edin.** >

 ::: moniker-end

::: moniker range="=vs-2017"

Visual Studio'daki projenize bir EditorConfig dosyası eklediğinizde, EditorConfig ayarlarına göre yeni kod satırları biçimlendirilir. Belgeyi biçimlendirmediğiniz sürece varolan kodun biçimlendirmesi değiştirilmez **(Varsayılan** >  **Ctrl**+**profilde** Gelişmiş**Biçim Belgesini** veya **Ctrl**+**K'yi****edit).** >  Belgeyi biçimlendirmek, [biçimlendirme](../ide/code-styles-and-code-cleanup.md#apply-code-styles)belgesini ek kod temizleme gerçekleştirmek üzere yapılandırmadığınız sürece yalnızca girinti stil gibi beyaz alan ayarlarını etkiler.

 ::: moniker-end

::: moniker range="vs-2017"

[ **Biçimlendirme** seçenekleri sayfasında](reference/options-text-editor-csharp-formatting.md#format-document-settings) **Format Belgesi'nin** hangi EditorConfig ayarlarını uygulayabileceğinizi tanımlayabilirsiniz.

::: moniker-end

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Visual Studio'da Mac için EditorConfig'e](/visualstudio/mac/editorconfig)bakın.

## <a name="code-consistency"></a>Kod tutarlılığı

EditorConfig dosyalarındaki ayarlar, kullandığınız düzenleyici veya IDE'den bağımsız olarak girinti stil, sekme genişliği, satır sonu karakterleri, kodlama ve daha fazlası gibi tutarlı kodlama stillerini ve ayarlarını bir kod tabanında korumanızı sağlar. Örneğin, C#'da kodlama yaparken, kod tabanınızda girintinlerin her zaman beş boşluk karakterinden oluştuğunu tercih eden bir kuralı varsa, belgeler UTF-8 kodlamasını kullanır ve her satır her zaman bir CR/LF ile biterse, bunu yapmak için bir *.editorconfig* dosyasını yapılandırabilirsiniz.

Kişisel projelerinizde kullandığınız kodlama kuralları, ekibinizin projelerinde kullanılanlardan farklı olabilir. Örneğin, kodlama yaparken girintinleme nin bir sekme karakteri ekleyebileceğinitercih edebilirsiniz. Ancak, takımınız girintinin sekme karakteri yerine dört boşluk karakteri ekleyebileceğini tercih edebilir. EditorConfig dosyaları, her senaryo için bir yapılandırmaya sahip olduğunuzu sağlayarak bu sorunu giderir.

Ayarlar kod tabanındaki bir dosyada bulunduğundan, bu kod tabanıyla birlikte hareket ederler. Code dosyasını EditorConfig uyumlu bir düzenleyicide açtığınız sürece metin düzenleyicisi ayarları uygulanır. EditorConfig dosyaları hakkında daha fazla bilgi için [EditorConfig.org](https://editorconfig.org/) web sitesine bakın.

> [!NOTE]
> EditorConfig dosyasında ayarlanan sözleşmeler şu anda bir CI/CD ardışık alanında yapı hataları veya uyarılar olarak uygulanamaz. Herhangi bir stil sapmaları yalnızca Visual Studio düzenleyicisinde ve **Hata Listesinde**görünür.

## <a name="supported-settings"></a>Desteklenen ayarlar

Visual Studio editörü [EditorConfig özellikleri](https://editorconfig.org/#supported-properties)çekirdek kümesi destekler:

- indent_style
- indent_size
- tab_width
- of_line\_sonu
- Charset
- kırpma\_trailing_whitespace
- final_newline\_ekle
- kök

EditorConfig düzenleyici ayarları XML hariç tüm Visual Studio destekli dillerde desteklenir. Buna ek olarak, EditorConfig [dil,](../ide/editorconfig-language-conventions.md) [biçimlendirme](../ide/editorconfig-formatting-conventions.md)ve C# ve Visual Basic için [adlandırma](../ide/editorconfig-naming-conventions.md) kuralları gibi [kod stili](../ide/editorconfig-code-style-settings-reference.md) kurallarını destekler.

## <a name="add-and-remove-editorconfig-files"></a>EditorConfig dosyalarını ekleme ve kaldırma

Projenize veya codebase'inize bir EditorConfig dosyası eklediğinizde, yazdığınız yeni kod satırları EditorConfig dosyasına göre biçimlendirilir. Ancak, EditorConfig dosyası eklemek, belgeyi biçimlendirene veya Kod [Temizleme'yi](../ide/code-styles-and-code-cleanup.md)çalıştırana kadar varolan stilleri yeni stilleri dönüştürmez. Örneğin, dosyanızda sekmelerle biçimlendirilmiş girintinleriniz varsa ve boşluklarla girintisi olan bir EditorConfig dosyası eklerseniz, girinti karakterler otomatik olarak boşluklara dönüştürülmez. Belgeyi biçimlendirdiğinizde **(Gelişmiş** > **Biçim Belgesini** veya **Ctrl**+**K'yi****edit** > , **Ctrl**+**D**), EditorConfig dosyasındaki beyaz alan ayarları varolan kod satırlarına uygulanır.

Bir EditorConfig dosyasını projenizden veya codebase'inizden kaldırırsanız ve yeni kod satırlarının genel düzenleyici ayarlarına göre biçimlendirilmesini istiyorsanız, açık kod dosyalarını kapatıp yeniden açmanız gerekir.

### <a name="add-an-editorconfig-file-to-a-project"></a>Projeye EditorConfig dosyası ekleme

1. Visual Studio'da bir proje veya çözüm açın. *.editorconfig* ayarlarınızın çözümdeki tüm projelere mi yoksa yalnızca bir projeye mi uygulanacağı konusunda proje veya çözüm düğümünü seçin. *Ayrıca.editorconfig* dosyasını eklemek için projenizde veya çözümünüzde bir klasör seçebilirsiniz.

1. Menü çubuğundan **Project** > **Add New Item'i**seçin veya **Ctrl**+**Shift**+A**tuşuna**basın.

   **Yeni Öğe Ekle** iletişim kutusu açılır.

1. Arama kutusunda, **editorconfig**için arama .

   Arama sonuçlarında iki **editorconfig Dosya** öğesi şablonu gösterilir.

   ![Visual Studio'da EditorConfig dosya öğesi şablonları](media/editorconfig-item-templates.png)

1. Girinti stili ve boyutu için iki çekirdek EditorConfig seçeneğiyle doldurulmuş bir EditorConfig dosyası eklemek için **editorconfig File (varsayılan)** şablonunu seçin. Veya, varsayılan [.NET kod stili, biçimlendirme ve adlandırma kurallarıyla](../ide/editorconfig-code-style-settings-reference.md)önceden doldurulmuş bir EditorConfig dosyası eklemek için **editorconfig File (.NET)** şablonu'nu seçin.

   Solution Explorer'da bir *.editorconfig* dosyası görünür ve düzenleyicide açılır.

   ![.editorconfig dosyası Solution Explorer ve düzenleyici](media/editorconfig-dotnet.png)

1. Dosyayı istediğiniz gibi edin.

### <a name="other-ways-to-add-an-editorconfig-file"></a>EditorConfig dosyası eklemenin diğer yolları

Projenize Bir EditorConfig dosyası eklemenin birkaç yolu daha vardır:

- IntelliCode for Visual Studio'nun [kod çıkarım özelliği,](/visualstudio/intellicode/code-style-inference) kod stillerinizi varolan koddan çıkarır. Daha sonra zaten tanımlanmış kod stili tercihleri ile boş olmayan bir EditorConfig dosyası oluşturur.

- Visual Studio 2019'dan **itibaren, Araçlar** > **Seçenekleri'ndeki**kod [stili ayarlarınızı temel alan bir EditorConfig dosyası oluşturabilirsiniz.](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)

## <a name="file-hierarchy-and-precedence"></a>Dosya hiyerarşisi ve öncelik

Dosya hiyerarşinizdeki bir klasöre *bir .editorconfig* dosyası eklediğinizde, ayarları bu düzeyde ve altındaki tüm geçerli dosyalar için geçerlidir. Ayrıca, belirli bir proje, codebase veya kod tabanının bir parçası için EditorConfig ayarlarını geçersiz kılabilirsiniz, bu da kod tabanının diğer bölümlerinden farklı kurallar kullanır. Bu, kodu başka bir yerden birleştirdiğinizde ve kurallarını değiştirmek istemediğinizde yararlı olabilir.

EditorConfig ayarlarının bazılarını veya tümünün geçersiz kılınmasını sağlamak için, dosya hiyerarşisi düzeyinde bir *.editorconfig* dosyası ekleyin, bu geçersiz kılınan ayarların uygulanmasını istediğiniz. Yeni EditorConfig dosya ayarları aynı düzeydeki dosyalar ve herhangi bir alt dizinler için geçerlidir.

![EditorConfig hiyerarşisi](../ide/media/vside_editorconfig_hierarchy.png)

Ayarların bazılarını geçersiz kılmak istiyorsanız, *.editorconfig* dosyasında sadece bu ayarları belirtin. Yalnızca alt düzey dosyada açıkça listelediğiniz özellikler geçersiz kılınmış. Üst düzey *.editorconfig* dosyalarından diğer ayarlar uygulanmaya devam ediyor. Codebase'in bu bölümüne _üst_ düzey *.editorconfig* dosyalarından _hiçbir_ ayar uygulanmadığından emin ```root=true``` olmak istiyorsanız, özelliği alt düzey *.editorconfig* dosyasına ekleyin:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig dosyaları yukarıdan aşağıya okunur. Aynı ada sahip birden çok özellik varsa, bu ada sahip en son bulunan özellik önceliklidir.

## <a name="edit-editorconfig-files"></a>EditorConfig dosyalarını edit

Visual Studio, IntelliSense tamamlama listeleri sağlayarak *.editorconfig* dosyalarını düzenlemenize yardımcı olur.

![Bir .editorconfig dosyasında IntelliSense](media/editorconfig-intellisense-no-extension.png)

EditorConfig dosyanızı düzenledikten sonra, yeni ayarların etkili olması için kod dosyalarınızı yeniden yüklemeniz gerekir.

Çok sayıda *.editorconfig* dosyasını edinirseniz, [EditorConfig Dil Hizmeti uzantısını](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) yararlı bulabilirsiniz. Bu uzantının bazı özellikleri arasında sözdizimi vurgulama, geliştirilmiş IntelliSense, doğrulama ve kod biçimlendirme sayılabilir.

![EditorConfig Dil Servisi uzantısı ile IntelliSense](media/editorconfig-intellisense.png)

## <a name="example"></a>Örnek

Aşağıdaki örnek, projeye bir *.editorconfig* dosyası eklemeden önce ve sonra bir C# kodu snippet'in girintisi durumunu gösterir. Visual Studio metin düzenleyicisi için **Seçenekler** iletişim kutusundaki **Sekmeler** ayarı, **Sekme** tuşuna bastığınızda boşluk karakterleri oluşturmak üzere ayarlanır.

![Metin Düzenleyicisi sekmesi ayarı](../ide/media/vside_editorconfig_tabsetting.png)

Beklendiği gibi, bir sonraki satırdaki **Sekme** tuşuna basıldığında, dört ek boşluk karakteri ekleyerek satır girintisi kalır.

![EditorConfig kullanmadan önce kod](../ide/media/vside_editorconfig_before.png)

Projeye aşağıdaki içeriklerle *birlikte .editorconfig* adlı yeni bir dosya ekleyin. Ayar, `[*.cs]` bu değişikliğin yalnızca projedeki C# kod dosyaları için geçerli olduğu anlamına gelir.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Şimdi, **Sekme** tuşuna bastığınızda, boşluk yerine sekme karakterleri alırsınız.

![Sekme tuşu Sekme karakterini ekler](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Sorun Giderme EditorConfig ayarları

Projenizin bulunduğu konumda veya üstünde dizin yapısında bir EditorConfig dosyası varsa, Visual Studio bu dosyadaki düzenleyici ayarlarını düzenleyicinize uygular. Bu durumda, durum çubuğunda aşağıdaki iletiyi görebilirsiniz:

   **"Bu dosya türü için kullanıcı tercihleri, bu projenin kodlama kuralları tarafından geçersiz kılındı."**

Bu, **Tools** > **Options** > Metin Düzenleyicisi'ndeki herhangi bir düzenleyici ayarlarının (girinat boyutu ve stili, sekme boyutu veya kodlama kuralları gibi) dizin yapısındaki projedeki veya üstündeki EditorConfig dosyasında belirtilmişse, EditorConfig dosyasındaki sözleşmeler **Seçenekler'deki**ayarları geçersiz kılar.**Text Editor**  >  **Araçlar** > **Seçenekleri**Metin Düzenleyicisi'nde **proje kodlama kurallarını takip** etme seçeneğini değiştirerek bu davranışı denetleyebilirsiniz.**Text Editor** Seçeneğin denetiminin karşıdan altı, Visual Studio için EditorConfig desteğini kapatır.

![Araçlar Seçenekleri - proje kodlama kurallarını izleyin](media/coding_conventions_option.png)

Komut istemini açarak ve projenizi içeren diskin kökünden aşağıdaki komutu çalıştırarak ana dizinlerde herhangi bir *.editorconfig* dosyasını bulabilirsiniz:

```Shell
dir .editorconfig /s
```

EditorConfig sözleşmelerinizin kapsamını, ```root=true``` *.editorconfig* dosyasındaki özelliği repo'nuzun kökünde veya projenizin bulunduğu dizinde ayarlayarak denetleyebilirsiniz. Visual Studio, açılan dosyanın dizininde ve her üst dizininde *.editorconfig* adlı bir dosya arar. Arama, kök dosya yoluna ulaştığında veya *.editorconfig* ```root=true``` dosyası bulunduğunda sona erer.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kod stili kuralları](../ide/editorconfig-code-style-settings-reference.md)
- [Bir dil hizmeti için EditorConfig'i destekleme](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Kod düzenleyicisinin özellikleri](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Mac için Visual Studio)](/visualstudio/mac/editorconfig)
