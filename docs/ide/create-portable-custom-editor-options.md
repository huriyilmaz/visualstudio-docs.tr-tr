---
title: EditorConfig ayarları
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3aee4945b4a3b41a7f6ec532268c2c19f549d0a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589792"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig ile taşınabilir, özel düzenleyici ayarları oluşturma

Kod tabanında çalıştırılan herkes için tutarlı kodlama stillerini zorlamak üzere projenize veya kod tabanınıza bir [Editorconfig](https://editorconfig.org/) dosyası ekleyebilirsiniz. EditorConfig ayarları Düzenleyicisi ayarları genel Visual Studio metin üzerinde önceliklidir. Bu, her kod temelini o projeye özel metin düzenleyici ayarlarını kullanmak üzere uyarlayabileceğiniz anlamına gelir. Visual Studio'da kendi kişisel Düzenleyici tercihleri yine de ayarlayabilirsiniz **seçenekleri** iletişim kutusu. Bir kod temelinde çalışırken sürekli bu ayarlar geçerli bir *.editorconfig* dosyası veya *.editorconfig* dosya belirli bir ayarı geçersiz kılma değil. Böyle bir tercih, girinti stili örneğidir&mdash;sekme veya boşluk.

EditorConfig ayarlar, çok sayıda kod düzenleyici ve IDE'ler, Visual Studio da dahil olmak üzere tarafından desteklenir. Bu kodunuzla dolaşır ve Visual Studio dışında bile kodlama stillerini zorunlu kılabilir taşınabilir bir bileşendir.

::: moniker range=">=vs-2019"

Visual Studio 'da projenize bir EditorConfig dosyası eklediğinizde, yeni kod satırları EditorConfig ayarlarına göre biçimlendirilir. Aşağıdaki komutlardan birini çalıştırmadığınız takdirde varolan kodun biçimlendirmesi değiştirilmez:

 - [Kod temizleme](../ide/code-styles-and-code-cleanup.md) (**CTRL**+**K**, **CTRL**+**E**), girinti stili gibi tüm beyaz boşluk ayarlarını ve `using` yönergelerinin nasıl sıralanması gibi seçili kod stili ayarlarını uygular.
 - **Gelişmiş** > **biçimli belge** (veya **CTRL**+**K**, varsayılan profilde **CTRL**+**D** ) > **düzenleyin** ve yalnızca girinti stili gibi beyaz boşluk ayarlarını uygular.

 ::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 'da projenize bir EditorConfig dosyası eklediğinizde, yeni kod satırları EditorConfig ayarlarına göre biçimlendirilir. Belgeyi biçimlendirmediğiniz **( > ** **Gelişmiş** > **Biçim belgesi** veya **ctrl**+**K**, varsayılan profilde **CTRL**+**D** ) olmadığı takdirde, mevcut kodun biçimlendirmesi değiştirilmez. Belgeyi biçimlendirmek, [ek kod temizleme işlemini gerçekleştirmek](../ide/code-styles-and-code-cleanup.md#apply-code-styles)üzere biçim belgesi yapılandırmadığınız sürece yalnızca girinti stili gibi beyaz boşluk ayarlarını etkiler.

 ::: moniker-end

::: moniker range="vs-2017"

İstediğiniz hangi EditorConfig ayarlar tanımlayabilirsiniz **belgeyi Biçimlendir** uygulamak için [ **biçimlendirme** seçenekleri sayfasında](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio'da EditorConfig](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Kod tutarlılığı

Tutarlı kodlama stili ve girinti stili, sekme genişliği, satır sonu karakterleri, gibi kod tabanında kodlama, ayarları korumak EditorConfig dosyaları ayarlarında etkinleştirmeniz ve daha fazlasını düzenleyicimizi veya IDE'mizi bağımsız olarak kullanırsınız. Örneğin, kod temelinizde girintileri her zaman beş boşluk karakterlerinden oluşamaz tercih edilmesi bir kuralı varsa, C# kodlama, UTF-8 kodlamasını, belgeleri kullanın ve her satırı bir CR/LF ile her zaman sona erer, yapılandırabileceğiniz bir *.editorconfig* Bunu yapmak için dosya.

Kodlama kuralları kişisel projelerinizi kullandığınız takımınızın projelerde kullanılanlardan farklı olabilir. Örneğin, kodlamaya, girintilendirme bir sekme karakteri ekler tercih edebilirsiniz. Ancak, takımınızın girintileme bir sekme karakteri yerine dört boşluk karakterleri ekler tercih edebilirsiniz. EditorConfig dosyaları, her senaryo için bir yapılandırmaya sahip olanak sağlayarak bu sorunu giderin.

Ayarları bir kod temeli dosyasında bulunduğundan, bu kod temeli ile birlikte seyahat. Kod dosyası EditorConfig uyumlu bir düzenleyicide açık olduğu sürece, metin düzenleyici ayarları uygulanır. EditorConfig dosyaları hakkında daha fazla bilgi için bkz. [EditorConfig.org](https://editorconfig.org/) Web sitesi.

> [!NOTE]
> Bir EditorConfig dosyasında ayarlanan kuralları, şu anda hata veya uyarı oluştururken bir CI/CD işlem hattında zorlanamaz. Yalnızca Visual Studio düzenleyicisinde herhangi bir stil sapmaları görünür ve **hata listesi**.

## <a name="supported-settings"></a>Desteklenen ayarlar

Visual Studio düzenleyicisinde çekirdek kümesini destekleyen [EditorConfig özellikleri](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- Son\_of_line
- karakter kümesi
- Trim\_trailing_whitespace
- INSERT\_final_newline
- kök

EditorConfig Düzenleyici ayarları XML dışında tüm Visual Studio tarafından desteklenen dillerde desteklenir. Ayrıca, EditorConfig, ve Visual Basic C# için [dil](../ide/editorconfig-language-conventions.md), [biçimlendirme](../ide/editorconfig-formatting-conventions.md)ve [adlandırma](../ide/editorconfig-naming-conventions.md) kuralları da dahil olmak üzere [kod stili](../ide/editorconfig-code-style-settings-reference.md) kurallarını destekler.

## <a name="add-and-remove-editorconfig-files"></a>EditorConfig dosyalarını ekleme ve kaldırma

Projenize veya kod tabanınıza bir EditorConfig dosyası eklediğinizde, yazdığınız tüm yeni kod satırları EditorConfig dosyasına göre biçimlendirilir. Ancak, bir EditorConfig dosyası eklemek, belgeyi biçimlendirene veya [kod temizliği](../ide/code-styles-and-code-cleanup.md)çalıştırana kadar mevcut stilleri yeni olanlara dönüştürmez. Örneğin, dosyanızda sekmelerle biçimlendirilmiş Girintileriniz varsa ve boşluklarla girintilenen bir EditorConfig dosyası eklerseniz, girinti karakterleri otomatik olarak boşluklara dönüştürülmez. Belgeyi biçimlendirdiğinizde (**düzenle** > **Gelişmiş** > **Biçim belgesi** veya **CTRL**+**K**, **CTRL**+**D**), editorconfig dosyasındaki boşluk ayarları, varolan kod satırlarına uygulanır.

Bir EditorConfig dosyasını projenizden veya kod tabanınızdan kaldırırsanız ve yeni kod satırlarının genel düzenleyici ayarlarına göre biçimlendirilmesini istiyorsanız, açık kod dosyalarını kapatıp yeniden açmanız gerekir.

### <a name="add-an-editorconfig-file-to-a-project"></a>Bir projeye EditorConfig dosyası ekleme

1. Bir proje veya çözüm Visual Studio'da açın. Bağlı olarak proje veya çözüm düğümü seçin, *.editorconfig* ayarları, Çözümdeki tüm projeleri veya tek uygulamalıdır. Ayrıca, proje veya çözümü eklemek için bir klasör seçebilirsiniz *.editorconfig* dosya.

1. Menü çubuğundan seçin **proje** > **Yeni Öğe Ekle**, veya basın **Ctrl**+**Shift** + **A**.

   **Yeni Öğe Ekle** iletişim kutusu açılır.

1. Arama kutusunda, **editorconfig**' i arayın.

   Arama sonuçlarında iki **editorconfig dosya** öğesi şablonu gösterilmektedir.

   ![Visual Studio 'da EditorConfig dosyası öğe şablonları](media/editorconfig-item-templates.png)

1. Girinti stili ve boyutu için iki Core EditorConfig seçeneği ile önceden doldurulan bir EditorConfig dosyası eklemek için **Editorconfig dosyası (varsayılan)** şablonunu seçin. Ya da varsayılan [.NET kod stili, biçimlendirme ve adlandırma kurallarıyla](../ide/editorconfig-code-style-settings-reference.md)önceden doldurulan bir editorconfig dosyası eklemek için **editorconfig dosyası (.net)** şablonunu seçin.

   Bir *.editorconfig* dosyası Çözüm Gezgini'nde görünür ve düzenleyicide açılır.

   ![Çözüm Gezgini ve düzenleyicideki. editorconfig dosyası](media/editorconfig-dotnet.png)

1. Dosyayı istediğiniz gibi düzenleyin.

### <a name="other-ways-to-add-an-editorconfig-file"></a>EditorConfig dosya eklemenin başka yolları

EditorConfig dosyayı projenize ekleyebilirsiniz birkaç yolu vardır:

- Visual Studio için ıntellicode 'un [kod çıkarımı özelliği](/visualstudio/intellicode/code-style-inference) , kod stillerinizi mevcut koddan algılar. Daha sonra, kod stili tercihleriniz zaten tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Visual Studio 2019 ' den başlayarak, **araçlar** > **seçeneklerinde** [kod stili ayarlarınıza göre bir editorconfig dosyası](/visualstudio/ide/code-styles-and-code-cleanup#code-styles-in-editorconfig-files) oluşturabilirsiniz.

## <a name="file-hierarchy-and-precedence"></a>Dosya hiyerarşisi ve önceliği

Eklediğinizde bir *.editorconfig* dosya dosya hiyerarşinizdeki bir klasöre tüm ilgili dosyalar aynı düzeyde ve altı ayarlarını uygulayın. Diğer bölümlerini kod tabanının daha farklı kurallar kullanır, ayrıca belirli proje, codebase veya bir kod temeli bir parçası için EditorConfig ayarları geçersiz kılabilirsiniz. Başka bir yerde koddan birleştirmek ve kendi kuralları değiştirmek istemiyorsanız, bu yararlı olabilir.

Bazı veya tüm EditorConfig ayarlarını geçersiz kılmak için ekleme bir *.editorconfig* dosya düzeyinde geçersiz kılınan bu ayarların uygulanmasını istediğiniz dosya hiyerarşisi. Aynı düzeyde ve alt dizinlerde dosyaları yeni EditorConfig dosya ayarlar uygulanır.

![EditorConfig hiyerarşisi](../ide/media/vside_editorconfig_hierarchy.png)

Bazı geçersiz kılmak istiyorsanız, ancak tüm ayarları yalnızca ayarlarında *.editorconfig* dosya. Yalnızca alt düzey dosyasında açıkça listesinde özellikler geçersiz kılınır. Üst düzey'nden diğer ayarlar *.editorconfig* dosyaları devam uygulamak. Emin olmak istiyorsanız _hiçbir_ ayarlarından _herhangi_ üst düzey *.editorconfig* dosyaları kod tabanının kısmına uygulanır, ekleme ```root=true``` özelliği alt düzey *.editorconfig* dosyası:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig dosyaları üstten alta okunurdur. Aynı ada sahip birden fazla özellik varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır.

## <a name="edit-editorconfig-files"></a>EditorConfig dosyalarını Düzenle

Visual Studio düzenlemenize yardımcı olur *.editorconfig* IntelliSense tamamlanma listelerinde sağlayarak dosyaları.

![.Editorconfig dosyasında IntelliSense](media/editorconfig-intellisense-no-extension.png)

EditorConfig dosyanızı düzenlediğiniz sonra yeni ayarların etkili olması kod dosyalarınızı yeniden yüklemeniz gerekir.

Çok sayıda düzenlerseniz *.editorconfig* dosyaları, ilginizi çekebilecek [EditorConfig dil hizmeti uzantısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) yararlıdır. Bu uzantı özelliklerinden bazılarını söz dizimi vurgulama, geliştirilmiş IntelliSense, doğrulama ve biçimlendirme kodu içerir.

![IntelliSense ile EditorConfig dil hizmeti uzantısı](media/editorconfig-intellisense.png)

## <a name="example"></a>Örnek

Aşağıdaki örnek bir C# kod parçacığı girinti durumunu, önce ve ekledikten sonra gösterir. bir *.editorconfig* projeye dosya. **Sekmeleri** ayarı **seçenekleri** bastığınızda boşluk karakterleri oluşturmak için Visual Studio Metin Düzenleyicisi iletişim kutusu ayarlanmış **sekmesini** anahtarı.

![Metin Düzenleyici sekmesinde ayarı](../ide/media/vside_editorconfig_tabsetting.png)

Beklendiği gibi tuşuna basarak **sekmesini** anahtar sonraki satıra dört ek boşluk karakterleri ekleyerek satırı girintiler.

![EditorConfig kullanmadan önce kod](../ide/media/vside_editorconfig_before.png)

Adlı yeni bir dosya ekleme *.editorconfig* projeye aşağıdaki içeriğe sahip. `[*.cs]` Ayarı, bu değişiklik yalnızca C# kod dosyaları proje uygulandığı anlamına gelir.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Bastığınızda artık **sekmesini** anahtar, sekme karakterlerini yerine boşluk sahip olursunuz.

![Sekme tuşunu sekme karakteri ekler.](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>EditorConfig ayarları sorunlarını giderme

Varsa bir EditorConfig dosyası herhangi bir dizin yapısına veya projenizin konumunu üzerindeki Visual Studio Düzenleyicisi ayarları, dosya düzenleyiciniz için geçerlidir. Bu durumda, durum çubuğundaki şu iletiyi görebilirsiniz:

   **"Bu dosya türü için kullanıcı tercihleri bu projenin kodlama kuralları tarafından geçersiz kılınır."**

Bu durumlarda, herhangi bir düzenleyici ayarları anlamına gelir **Araçları** > **seçenekleri** > **metin düzenleyici** (örneğin, girinti boyutu ve stilini, sekme boyutunu veya kodlama kuralları), bir EditorConfig dosyasında veya proje dizin yapısına üzerindeki belirtilirse, kuralları EditorConfig dosyasındaki ayarları geçersiz kılan **seçenekleri**. Değiştirerek bu davranışı denetleyebilirsiniz **proje kodlaması kurallarını** seçeneğini **Araçları** > **seçenekleri**  >  **Metin düzenleyici**. Bu seçeneğin işaretini Visual Studio için EditorConfig desteğiyle kapatır.

![Araçlar Seçenekler - Proje kodlama kuralları](media/coding_conventions_option.png)

Tüm bulabilirsiniz *.editorconfig* üst dizininde bir komut istemi açıp aşağıdaki komutu çalıştırarak projenizi içeren disk kökünden dosyaları:

```Shell
dir .editorconfig /s
```

Ayarlayarak, EditorConfig kuralları kapsamını denetleyebilirsiniz ```root=true``` özelliğinde *.editorconfig* deponuzun veya projenizin bulunduğu dizine kök dosya. Visual Studio görünen adlı bir dosya için *.editorconfig* açılan dosya dizininde bulunan ve her bir üst dizin. Kök dosya yolunu ulaştığında veya arama biten bir *.editorconfig* ile dosya ```root=true``` bulunur.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kod stili kuralları](../ide/editorconfig-code-style-settings-reference.md)
- [Dil hizmeti için Editorconfig'i destekleme](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Kod Düzenleyicisi özellikleri](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Mac için Visual Studio)](/visualstudio/mac/editorconfig)
