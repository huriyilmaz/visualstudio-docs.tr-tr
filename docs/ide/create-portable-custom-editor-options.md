---
title: EditorConfig ayarları
description: Kod tabanında çalıştırılan herkes için tutarlı kodlama stillerini zorlamak üzere projenize veya kod tabanınıza bir EditorConfig dosyası eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 6dee0f9dc003e91cdb8d2ba24fc0804d5df5ae54
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109519"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig ile taşınabilir, özel düzenleyici ayarları oluşturma

Kod tabanında çalıştırılan herkes için tutarlı kodlama stillerini zorlamak üzere projenize veya kod tabanınıza bir EditorConfig dosyası ekleyebilirsiniz. editorconfig ayarları, genel Visual Studio metin düzenleyicisi ayarlarından önceliklidir. Bu, her kod temelini o projeye özel metin düzenleyici ayarlarını kullanmak üzere uyarlayabileceğiniz anlamına gelir. Visual Studio **seçenekleri** iletişim kutusunda kendi kişisel düzenleyici tercihlerinizi ayarlamaya devam edebilirsiniz. Bu ayarlar, *. editorconfig* dosyası olmayan bir kod tabanında her çalıştığınızda veya *. editorconfig* dosyası belirli bir ayarı geçersiz kılmazsa geçerlidir. Bu tür bir tercihe bir örnek, girinti stili &mdash; sekmeleri veya boşluklardan oluşur.

EditorConfig ayarları, Visual Studio dahil olmak üzere çok sayıda kod Düzenleyicisi ve Ides tarafından desteklenir. Bu, kodunuza taşınan taşınabilir bir bileşendir ve Visual Studio dışında bile kodlama stillerini uygulayabilir.

::: moniker range=">=vs-2019"

Visual Studio ' de projenize bir editorconfig dosyası eklediğinizde, yeni kod satırları editorconfig ayarlarına göre biçimlendirilir. Aşağıdaki komutlardan birini çalıştırmadığınız takdirde varolan kodun biçimlendirmesi değiştirilmez:

 - [Kod temizleme](../ide/code-styles-and-code-cleanup.md) (**CTRL** + **K**, **CTRL** + **E**), girinti stili gibi tüm beyaz boşluk ayarlarını ve nasıl sıralama yönergeleri gibi seçili kod stili ayarlarını uygular `using` .
 - **Düzenle** > **Gelişmiş** >   +   + Yalnızca girinti stili gibi beyaz boşluk ayarlarını uygulayan belgeyi (veya varsayılan profilde CTRL **D** ) biçimlendirin.

 ::: moniker-end

::: moniker range="=vs-2017"

Visual Studio ' de projenize bir editorconfig dosyası eklediğinizde, yeni kod satırları editorconfig ayarlarına göre biçimlendirilir. Belgeyi biçimlendirmediğiniz **(**  >  **Gelişmiş**  >  **Biçim belgesi** veya **CTRL** + **K**, varsayılan profilde **CTRL** + **D** ), varolan kodun biçimlendirmesi değiştirilmez. Belgeyi biçimlendirmek, [ek kod temizleme işlemini gerçekleştirmek](../ide/code-styles-and-code-cleanup.md#apply-code-styles)üzere biçim belgesi yapılandırmadığınız sürece yalnızca girinti stili gibi beyaz boşluk ayarlarını etkiler.

 ::: moniker-end

::: moniker range="vs-2017"

[ **Biçimlendirme** seçenekleri sayfasında](reference/options-text-editor-csharp-formatting.md#format-document-settings) **Belge biçimini biçimlendirmek** istediğiniz düzenleyici yapılandırma ayarlarını tanımlayabilirsiniz.

::: moniker-end

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için, [Mac için Visual Studio içindeki editorconfig](/visualstudio/mac/editorconfig)bölümüne bakın.

## <a name="code-consistency"></a>Kod tutarlılığı

editorconfig dosyalarındaki Ayarlar, kullandığınız düzenleyiciden veya ıde 'den bağımsız olarak, bir kod tabanında, girinti stili, sekme genişliği, satır sonu karakterleri, kodlama ve daha fazlası gibi tutarlı kodlama stilleri ve ayarları korumanıza olanak sağlar. Örneğin, C# dilinde kodlarken, kod tabanınızın her zaman beş boşluk karakteri içermesi için bir kuralı varsa, belgeler UTF-8 kodlaması kullanır ve her satır her zaman bir CR/LF ile sona erer ve bunu yapmak için bir *. editorconfig* dosyası yapılandırabilirsiniz.

Kişisel projeleriniz üzerinde kullandığınız kodlama kuralları, takımınızın projelerinde kullanılanlardan farklı olabilir. Örneğin, kodlama yaparken, girintileme bir sekme karakteri ekliyor seçeneğini tercih edebilirsiniz. Ancak ekibiniz, girintileme 'nin bir sekme karakteri yerine dört boşluk karakteri eklemesine tercih edebilir. EditorConfig dosyaları, her senaryo için bir yapılandırmanıza izin vererek bu sorunu çözer.

Ayarlar kod temelindeki bir dosyada bulunduğundan, bu kod temeli ile birlikte seyahat ederler. Kod dosyasını bir EditorConfig uyumlu düzenleyicide açtığınız sürece, metin düzenleyici ayarları uygulanır. EditorConfig dosyaları hakkında daha fazla bilgi için bkz. [EditorConfig.org](https://editorconfig.org/) Web sitesi.

> [!NOTE]
> Bir EditorConfig dosyasında ayarlanan kurallar, derleme hataları veya uyarılar olarak bir CI/CD ardışık düzeninde zorlanamaz. stil sapmaları yalnızca Visual Studio düzenleyicide ve **Hata Listesi** görünür.

## <a name="supported-settings"></a>Desteklenen ayarlar

Visual Studio düzenleyici, [editorconfig özelliklerinin](https://editorconfig.org/#supported-properties)çekirdek kümesini destekler:

- indent_style
- indent_size
- tab_width
- Son \_ of_line
- karakter
- kırpma \_ trailing_whitespace
- \_final_newline Ekle
- kök

editorconfig düzenleyicisi ayarları, XML hariç tüm Visual Studio desteklenen dillerde desteklenir. Ayrıca, EditorConfig, C# ve Visual Basic için [dil](/dotnet/fundamentals/code-analysis/style-rules/language-rules), [biçimlendirme](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)ve [adlandırma](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) kuralları da dahil olmak üzere [kod stili](/dotnet/fundamentals/code-analysis/code-style-rule-options) kurallarını destekler.

## <a name="add-and-remove-editorconfig-files"></a>EditorConfig dosyalarını ekleme ve kaldırma

Projenize veya kod tabanınıza bir EditorConfig dosyası eklediğinizde, yazdığınız tüm yeni kod satırları EditorConfig dosyasına göre biçimlendirilir. Ancak, bir EditorConfig dosyası eklemek, belgeyi biçimlendirene veya [kod temizliği](../ide/code-styles-and-code-cleanup.md)çalıştırana kadar mevcut stilleri yeni olanlara dönüştürmez. Örneğin, dosyanızda sekmelerle biçimlendirilmiş Girintileriniz varsa ve boşluklarla girintilenen bir EditorConfig dosyası eklerseniz, girinti karakterleri otomatik olarak boşluklara dönüştürülmez. Belgeyi biçimlendirdiğinizde (  >  **Gelişmiş**  >  **Biçim belgesini** Düzenle veya **CTRL** + **K**, **CTRL** + **D**), editorconfig dosyasındaki boşluk ayarları, varolan kod satırlarına uygulanır.

Bir EditorConfig dosyasını projenizden veya kod tabanınızdan kaldırırsanız ve yeni kod satırlarının genel düzenleyici ayarlarına göre biçimlendirilmesini istiyorsanız, açık kod dosyalarını kapatıp yeniden açmanız gerekir.

### <a name="add-an-editorconfig-file-to-a-project"></a>Bir projeye EditorConfig dosyası ekleme

1. Visual Studio bir proje veya çözüm açın. *. Editorconfig* ayarlarınızın Çözümdeki tüm projelere mi yoksa yalnızca bir tane mi uygulandığına bağlı olarak, proje veya çözüm düğümünü seçin. Ayrıca, *. editorconfig* dosyasını eklemek için projenizde veya çözümünüzde bir klasör seçebilirsiniz.

1. menü çubuğundan **Project**  >  **yeni öğe ekle**' yi seçin veya **Ctrl** + **shıft** + **A**' ya basın.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. Arama kutusunda, **editorconfig**' i arayın.

   Arama sonuçlarında iki **editorconfig dosya** öğesi şablonu gösterilmektedir.

   ![Visual Studio 'de EditorConfig dosya öğesi şablonları](media/editorconfig-item-templates.png)

1. Girinti stili ve boyutu için iki Core EditorConfig seçeneği ile önceden doldurulan bir EditorConfig dosyası eklemek için **Editorconfig dosyası (varsayılan)** şablonunu seçin. Ya da varsayılan [.NET kod stili, biçimlendirme ve adlandırma kurallarıyla](/dotnet/fundamentals/code-analysis/code-style-rule-options)önceden doldurulan bir editorconfig dosyası eklemek için **editorconfig dosyası (.net)** şablonunu seçin.

   Bir *. editorconfig* dosyası Çözüm Gezgini görünür ve düzenleyicide açılır.

   ![Çözüm Gezgini ve düzenleyicideki. editorconfig dosyası](media/editorconfig-dotnet.png)

1. Dosyayı istediğiniz gibi düzenleyin.

### <a name="other-ways-to-add-an-editorconfig-file"></a>EditorConfig dosyası eklemenin diğer yolları

Projenize bir EditorConfig dosyası eklemenin birkaç yolu vardır:

- Visual Studio için ıntellicode 'un [kod çıkarımı özelliği](/visualstudio/intellicode/code-style-inference) , mevcut koddan kod stillerinizi kodlar. Daha sonra, kod stili tercihleriniz zaten tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Visual Studio 2019 ' den başlayarak, **araçlar** [seçeneklerinizde kod stili ayarlarınıza göre bir editorconfig dosyası](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) oluşturabilirsiniz  >  .

## <a name="file-hierarchy-and-precedence"></a>Dosya hiyerarşisi ve önceliği

Dosya hiyerarşinizdeki bir klasöre bir *. editorconfig* dosyası eklediğinizde, ayarları o düzeydeki ve alttaki tüm ilgili dosyalar için geçerlidir. Ayrıca, kod temelinin diğer parçalarından farklı kurallar kullanması gibi belirli bir proje, kod temeli veya kod temelinin bir parçası için EditorConfig ayarlarını geçersiz kılabilirsiniz. Bu, herhangi bir yerden kod eklediğinizde ve kurallarını değiştirmek istemediğinizde yararlı olabilir.

EditorConfig ayarlarının bir kısmını veya tamamını geçersiz kılmak için, bu geçersiz kılınan ayarların uygulanmasını istediğiniz dosya hiyerarşisi düzeyinde bir *. editorconfig* dosyası ekleyin. Yeni EditorConfig dosyası ayarları, dosyalar için aynı düzeyde ve tüm alt dizinlerde geçerlidir.

![EditorConfig hiyerarşisi](../ide/media/vside_editorconfig_hierarchy.png)

Ayarların tümünü geçersiz kılmak istiyorsanız, yalnızca *. editorconfig* dosyasında bu ayarları belirtin. Yalnızca alt düzey dosyada açıkça listeettiğiniz Özellikler geçersiz kılınır. Daha yüksek düzeydeki *. editorconfig* dosyalarındaki diğer ayarlar uygulanmaya devam eder. Kod temelinin bu bölümüne, daha üst düzey _bir_ *. editorconfig* dosyası uygulanmış _hiçbir_ ayar olmamasını sağlamak istiyorsanız, ```root=true``` özelliği alt düzey *. editorconfig* dosyasına ekleyin:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig dosyaları üstten alta okunurdur. Aynı ada sahip birden fazla özellik varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır.

## <a name="edit-editorconfig-files"></a>EditorConfig dosyalarını Düzenle

Visual Studio, ıntellisense tamamlanma listeleri sağlayarak *. editorconfig* dosyalarını düzenlemenize yardımcı olur.

![Bir. editorconfig dosyasında IntelliSense](media/editorconfig-intellisense-no-extension.png)

EditorConfig dosyanızı düzenledikten sonra, yeni ayarların etkili olması için kod dosyalarınızı yeniden yüklemeniz gerekir.

Çok sayıda *. editorconfig* dosyasını düzenlerseniz, [Editorconfig dil hizmeti uzantısını](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) yararlı bulabilirsiniz. Bu uzantının bazı özellikleri, sözdizimi vurgulama, geliştirilmiş IntelliSense, doğrulama ve kod biçimlendirme özelliklerini içerir.

![EditorConfig dil hizmeti uzantısı ile IntelliSense](media/editorconfig-intellisense.png)

## <a name="example"></a>Örnek

Aşağıdaki örnek, projeye bir *. editorconfig* dosyası eklemeden önce ve sonra bir C# kod parçacığının girintileme durumunu gösterir. Visual Studio metin düzenleyicisi için **seçenekler** iletişim kutusundaki **sekmeler** ayarı, **sekme** tuşuna bastığınızda boşluk karakterleri oluşturacak şekilde ayarlanmıştır.

![Metin düzenleyici sekmesi ayarı](../ide/media/vside_editorconfig_tabsetting.png)

Beklenen şekilde, sonraki satırdaki **sekme** tuşuna basmak, dört ek boşluk karakteri ekleyerek çizgiyi girintiler.

![EditorConfig kullanmadan önce kod](../ide/media/vside_editorconfig_before.png)

Projeye, aşağıdaki içerikle *. editorconfig* adlı yeni bir dosya ekleyin. `[*.cs]`Ayar, bu değişikliğin yalnızca projedeki C# kod dosyaları için geçerli olduğu anlamına gelir.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Artık **sekme** tuşuna bastığınızda boşluklar yerine sekme karakterleri alırsınız.

![Sekme tuşu sekme karakteri ekler](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>EditorConfig ayarlarının sorunlarını giderme

Projenizin konumunun dizin yapısında veya üzerinde herhangi bir yerde editorConfig dosyası varsa, Visual Studio düzenleyici ayarlarını düzenleyicinize uygular. Bu durumda, durum çubuğunda aşağıdaki iletiyi görebilir:

   **"Bu dosya türü için kullanıcı tercihleri, bu projenin kodlama kuralları tarafından geçersiz kılınır."**

Bu, Araç Seçenekleri Metin Düzenleyicisi'nde herhangi bir düzenleyici ayarı (girinti boyutu ve stil, sekme boyutu veya kodlama kuralları gibi) dizin yapısında projenin üzerindeki veya üzerindeki editorConfig dosyasında belirtilirse EditorConfig dosyasındaki kuralların Seçenekler'de ayarları geçersiz k olduğu anlamına  >    >   **gelir.** Araçlar Seçenekler Metin Düzenleyicisi'nde Proje kodlama kurallarına **uyma** seçeneğini seçerek **bu**  >  **davranışı**  >  **kontrol edin.** Seçeneğin işaretini kaldırıyorsanız düzenleyici yapılandırma desteği Visual Studio.

![Araçlar Seçenekleri - proje kodlama kurallarına uyma](media/coding_conventions_option.png)

Bir komut istemi açarak ve projenizi içeren diskin kökünden aşağıdaki komutu çalıştırarak üst dizinlerde *herhangi bir .editorconfig* dosyası bulabilirsiniz:

```Shell
dir .editorconfig /s
```

Repo'nizin kökünde veya projenizin bulunduğu dizinde .editorconfig dosyasındaki özelliğini ayarerek EditorConfig kurallarınız kapsamını ```root=true``` kontrol etmek için.  Visual Studio açılan dosyanın dizininde ve her üst dizinde *.editorconfig* adlı bir dosyayı bulun. Arama, kök dosya yoluna ulaştığında veya ile *bir .editorconfig* dosyası bulunursa ```root=true``` sona erer.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kod stili kuralları](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Dil hizmeti için EditorConfig'i destekleme](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Kod düzenleyicisinin özellikleri](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Mac için Visual Studio)](/visualstudio/mac/editorconfig)
