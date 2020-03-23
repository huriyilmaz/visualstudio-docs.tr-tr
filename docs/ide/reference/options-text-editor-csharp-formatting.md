---
title: C# düzenleyici biçimlendirme seçenekleri
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1176232eb3354a9b425e9432eb83037367ee7706
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303080"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Seçenekler iletişim kutusu: \> Metin \> Düzenleyicisi C# Kodu Stil \> Biçimlendirme

Kod düzenleyicisinde kodu biçimlendirme seçenekleri ayarlamak için **Biçimlendirme** seçenekleri sayfasını ve alt sayfalarını[**(Girinti,**](#indentation-page) **Yeni Satırlar,** **Aralıklar**ve **Sarma)** kullanın.

Bu seçenekler sayfasına erişmek için menü çubuğundan **Araçlar** > **Seçenekleri'ni** seçin. **Seçenekler** iletişim kutusunda Metin **Düzenleyicisi** > **C#** > **Kodu Stili** > **Biçimlendirme'yi**seçin.

> [!TIP]
> **Girintisi,** **Yeni Satırlar,** **Aralıklar**ve **Sarma** alt sayfaları, her seçeneğin etkisini gösteren en altta bir önizleme penceresi görüntüler. Önizleme penceresini kullanmak için bir biçimlendirme seçeneği seçin. Önizleme penceresi, seçili seçeneğin bir örneğini gösterir. Bir radyo düğmesi veya onay kutusu seçerek bir ayarı değiştirdiğinizde, önizleme penceresi yeni ayarın etkisini göstermek için güncellenir.

## <a name="formatting-general-page"></a>Biçimlendirme (Genel) sayfası

### <a name="general-settings"></a>Genel ayarlar

Bu ayarlar, kod düzenleyicisi koda biçimlendirme seçenekleri *uyguladığında* etkiler.

|Etiketle|Açıklama|
|-----------|-----------------|
|**Yazarken otomatik olarak biçimlendirme**|Deselected zaman, **biçim deyimi;** ve } seçenekleri **biçim bloğu** devre dışı bırakılır.|
|**İfadeyi otomatik olarak biçimlendir;**|Seçildiğinde, düzenleyici için seçilen biçimlendirme seçeneklerine göre tamamlamada deyimleri biçimlendirin.|
|**} üzerindeki bloğu otomatik olarak biçimlendirme**|Seçildiğinde, kod bloğunu tamamlar tamamlamaz düzenleyici için seçilen biçimlendirme seçeneklerine göre kod bloklarını biçimlendirin.|
|**Dönüşte otomatik biçimlendirme**|Seçildiğinde, enter tuşuna **basıldığında,** düzenleyici için seçilen biçimlendirme seçeneklerini sığdırmak için metni biçimlendirin.|
|**Yapıştır'da otomatik olarak biçimlendirme**|Seçildiğinde, düzenleyici için seçilen biçimlendirme seçeneklerini sığdırmak için düzenleyiciye yapıştırılan metni biçimlendirin.|

::: moniker range="vs-2019"

Visual Studio 2017'de **Belge Biçimlendirme** komutunu kullanarak C# dosyaları için kod stili ayarlarını daha önce uyguladıysanız, bu işlevsellik artık [**Kod Temizleme**](../code-styles-and-code-cleanup.md#apply-code-styles)olarak kullanılabilir.

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Belge ayarlarını biçimlendir

Bu ayarlar, belge üzerinde ek kod temizleme gerçekleştirmek için **Belge biçimlendirme** komutunu yapılandırır. Bu ayarların nasıl uygulandığı hakkında daha fazla bilgi için [Belgeyi Biçimlendir komutuna](../code-styles-and-code-cleanup.md#apply-code-styles)bakın.

|Etiketle|Açıklama|İlgili EditorConfig ve Araçlar > Seçenekleri kuralları|
|-----------|-----------------|-----------------|-----------------|
|**Tüm C# biçimlendirme kurallarını uygulayın (girintinasyon, kaydırma, aralık)**|**Belgeyi Biçimlendir** komutu her zaman biçimlendirme sorunlarını giderir. Bu ayar değiştirilemez.| [Çekirdek EditorConfig seçenekleri](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig biçimlendirme seçenekleri](../../ide/editorconfig-formatting-conventions.md)<br/><br/>**Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **C#** > **Biçimlendirme** > [**Girinti** veya **Yeni Satırlar** veya **Boşluk** veya **Sarma**]|
|**Biçimlendirme sırasında ek kodu temizleme gerçekleştirme**|Seçildiğinde, **Edit.FormatDocument** komutunda aşağıda belirtilen kurallar için düzeltmeler uygular.| Yok |
|**Gereksiz kullanımı kaldırma**|Seçildiğinde, `using` **Edit.FormatDocument** tetiklendiğinde gereksiz yönergeleri kaldırır.| Yok |
|**Kullanımları sıralama**|Seçildiğinde, `using` **Edit.FormatDocument** tetiklendiğinde yönergeleri sıralar.| dotnet_sort_system_directives_first<br/><br/>**Tools** > **Options** > **Text Editor** > **C#** > **Advanced** > **Place 'System' yönergesi ilk olarak kullanır sıralama yaparken** |
|**Tek satırlı denetim ifadeleri için ayraç ekleme/kaldırma**|**Edit.FormatDocument** tetiklendiğinde, seçildiğinde, parantezleri tek satırlık denetim ekstrelerinden ekler veya kaldırır.| csharp_prefer_braces<br/><br/>**Araçlar** > **Seçenekleri** > **Metin Düzenleyici** > **C#** > **Kod Stil** > **Kodu blok tercihleri** > **Tercih ayraçları** |
|**Erişilebilirlik değiştiriciler ekleme**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde eksik erişilebilirlik değiştiriciler ekler.| dotnet_style_require_accessibility_modifiers |
|**Erişilebilirlik değiştiricilerini sırala**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde erişilebilirlik değiştiriciler sıralar.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**İfade/blok gövde tercihlerini uygulama**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde ifade gövdeli üyeleri gövdeleri engellemeye veya tam tersi olarak dönüştürür.| [İfade gövdeli üye EditorConfig seçenekleri](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>**Araçlar** > **Seçenekleri** > **Metin Düzenleyici** > **c#** > Kod**Stili** > **İfade tercihleri** > **Yöntemler, yapıcılar vb. için ifade gövdesini kullanın.** |
|**Örtük/açık tür tercihleri uygulama**|Seçildiğinde, `var` **Edit.FormatDocument** tetiklendiğinde açık türe veya tam tersi olarak dönüştürülür.| [Açık tip EditorConfig seçenekleri](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>**Araçlar** > **Seçenekleri** > **Metin Düzenleyici** > **C#** > **Kod Stili** > **'var' tercihleri** |
|**Satır satırlı 'çıkış' değişkenleri tercihlerini uygulayın**|Seçildiğinde, `out` **Edit.FormatDocument** tetiklendiğinde mümkün olduğunca satır lı değişkenler.| csharp_style_inlined_variable_declaration<br/><br/>**Araçlar** > **Seçenekleri** > Metin**Düzenleyicic#** > **Text Editor** > **Kod Stili** > **Değişken tercihleri** > **Sıralı değişken bildirimini tercih edin** |
|**Dil/çerçeve türü tercihlerini uygulama**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde dil türlerini çerçeve türlerine veya tam tersi olarak dönüştürür.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Araçlar** > **Seçenekleri** > **Metin Düzenleyici** > **c#** > **Kod Stili** > **önceden tanımlanmış tür tercihleri** |
|**Nesne/toplama başlatma tercihlerini uygulama**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde mümkün olduğunda nesne ve toplama başlatanları kullanır.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Araçlar** > **Seçenekleri** > Metin**Düzenleyicic#** > **Text Editor** > **Kod Stili** > **İfade tercihleri** > Nesne baş**harflerini tercih edin** veya **toplama başlatmayı tercih edin** |
|**'Bu.' yeterlilik tercihlerini uygulayın**|Seçildiğinde, `this.` **Edit.FormatDocument** tetiklendiğinde tercihleri uygular.| [Bu. yeterlilik EditorConfig seçenekleri](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>**Araçlar** > **Seçenekleri** > Metin**Düzenleyicic#** > **Text Editor** > **Kod Stili** > **'this.' tercihleri** |
|**Özel alanları yalnızca mümkün olduğunda okuma**|Seçildiğinde, `readonly` **Edit.FormatDocument** tetiklendiğinde mümkün olduğunca özel alanlar yapar.| dotnet_style_readonly_field<br/><br/>**Araçlar** > **Seçenekleri** > **Metin Düzenleyici** > **C#** > Kod**Stili** > **Alan tercihleri** > **Yalnızca okunur** |
|**Gereksiz dökümleri kaldırma**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde mümkün olduğunca gereksiz dökümleri kaldırır.| Yok |
|**Kullanılmayan değişkenleri kaldırma**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde kullanılmayan değişkenleri kaldırır.| Yok |

![Visual Studio'da C# için kod temizleme ayarları](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Girintisi sayfası

Kod otomatik olarak biçimlendiğinde bu sayfadaki girintinseçenekleri geçerlidir. Kodun otomatik olarak biçimlendirildiğinde n için bir örnek, yapıştır'da **otomatik biçim biçimi** seçilirken kodu dosyaya yapıştırdığınızda dır. (Yapıştır **seçeneğindeki Otomatik biçimlendirme** **Genel** **Biçimlendirme** > altındadır.)

![Visual Studio'da C# metin editörü girintisi seçenekleri](media/csharp-indentation-options.png)

> [!TIP]
> **Metin Düzenleyicisi** > **C#** > **Sekmeleri** seçenekleri sayfasında girintinasyon seçenekleri de vardır. Bu seçenekler yalnızca bir satırın sonunda **Enter** tuşuna bastığında kod düzenleyicisinin imleci nereye yerleştirdiğinizi belirler.
>
> ![Visual Studio'da C# metin düzenleyicisi sekmeleri seçenekleri](media/csharp-tabs-options.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Çevre, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)
