---
title: C# Düzenleyicisi biçimlendirme seçenekleri
description: C# dilinde programlama yaparken kod düzenleyicisinde biçimlendirme seçeneklerini ayarlamak için biçimlendirme seçenekleri sayfasını ve alt sayfalarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 13c8ca9dd8c71cf091868f1ddd00847209cf3bb1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724911"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Seçenekler iletişim kutusu: metin düzenleyici \> C# \> kod stili \> biçimlendirme

Kod düzenleyicisinde biçimlendirme kodu seçeneklerini ayarlamak için **biçimlendirme** seçenekleri sayfasını ve alt sayfalarını ([**girintileme**](#indentation-page), **yeni satırlar**, **boşluk** ve **kaydırma**) kullanın.

Bu seçenekler sayfasına erişmek için, menü çubuğundan **Araçlar**  >  **Seçenekler** ' i seçin. **Seçenekler** iletişim kutusunda **metin düzenleyici**  >  **C#**  >  **kod stili**  >  **biçimlendirme** öğesini seçin.

> [!TIP]
> **Girinti**, **yeni satırlar**, **Aralık** ve **kaydırma** alt sayfaları her bir seçeneğin etkisini gösteren bir önizleme penceresi görüntüler. Önizleme penceresini kullanmak için bir biçimlendirme seçeneği belirleyin. Önizleme penceresinde seçilen seçeneğe bir örnek gösterilir. Bir seçimi bir radyo düğmesi veya onay kutusu seçerek değiştirdiğinizde, Önizleme penceresi Yeni ayarın etkisini gösterecek şekilde güncelleştirilir.

## <a name="formatting-general-page"></a>Biçimlendirme (genel) sayfası

### <a name="general-settings"></a>Genel ayarlar

Bu ayarlar, kod düzenleyicisinin koda biçimlendirme seçeneklerini uyguladığı *zaman* etkiler.

|Etiketle|Description|
|-----------|-----------------|
|**Yazarken Otomatik Biçimlendir**|Seçimi kaldırıldığında,, ve biçim **bloğu on}** seçeneklerinde **Biçim açıklaması** devre dışı bırakılır.|
|**; Üzerinde otomatik olarak biçim ekstresi**|Seçildiğinde, deyimi, düzenleyici için seçilen biçimlendirme seçeneklerine göre tamamlama sırasında biçimlendirir.|
|**} Üzerindeki blok otomatik olarak Biçimlendir**|Seçildiğinde kod bloğunu, kod bloğunu tamamladıktan hemen sonra düzenleyici için seçilen biçimlendirme seçeneklerine göre biçimlendirir.|
|**Dönüşte otomatik olarak Biçimlendir**|Seçildiğinde, düzenleyici için seçilen biçimlendirme seçeneklerine uyacak şekilde, **ENTER** tuşuna basıldığında metin biçimlendirir.|
|**Yapıştırırken otomatik olarak Biçimlendir**|Seçildiğinde, düzenleyiciye yapıştırılan metni düzenleyici için seçilen biçimlendirme seçeneklerine uyacak şekilde biçimlendirir.|

::: moniker range="vs-2019"

daha önce C# dosyaları için kod stili ayarlarını Visual Studio 2017 ' deki **belge biçimlendir** komutunu kullanarak uyguladıysanız, bu işlev artık [**kod temizleme**](../code-styles-and-code-cleanup.md#apply-code-styles)olarak kullanılabilir.

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Belge ayarlarını Biçimlendir

Bu ayarlar, dosya üzerinde ek kod temizleme işlemini gerçekleştirmek için **Biçim belgesi** komutunu yapılandırır. Bu ayarların nasıl uygulandığı hakkında daha fazla bilgi için bkz. [belge komutunu Biçimlendir](../code-styles-and-code-cleanup.md#apply-code-styles).

|Etiketle|Description|İlgili EditorConfig ve araçlar > seçenekleri kuralları|
|-----------|-----------------|-----------------|-----------------|
|**Tüm C# biçimlendirme kurallarını Uygula (girintileme, kaydırma, Aralık)**|**Biçim belgesi** komutu her zaman biçimlendirme sorunlarını düzeltir. Bu ayar değiştirilemez.| [Core EditorConfig seçenekleri](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig biçimlendirme seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Biçimlendirme** > [**girintileme** veya **yeni çizgiler** ya da **boşluk** ya da **kaydırma**]|
|**Biçimlendirme sırasında ek kod temizlemeyi gerçekleştir**|Seçildiğinde, **Edit. FormatDocument** komutunda belirtilen kurallara ilişkin düzeltmeleri uygular.| Yok |
|**Gereksiz kullanımları kaldır**|Seçildiğinde, `using` **Edit. FormatDocument** tetiklendiğinde gereksiz yönergeleri kaldırır.| Yok |
|**Using deyimlerini Sırala**|Seçildiğinde, `using` **düzenleme. FormatDocument** tetiklendiğinde yönergeleri sıralar.| dotnet_sort_system_directives_first<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Using deyimlerini sıralarken ' System ' yönergelerini ilk olarak Yerleştir** |
|**Tek satırlı denetim deyimleri için küme ayraçları Ekle/Kaldır**|Seçildiğinde, **Edit. FormatDocument** tetiklendiğinde tek satırlık denetim deyimlerine küme ayraçları ekler veya kaldırır.| csharp_prefer_braces<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **Kod bloğu tercihleri**  >  **Küme ayraçlarını tercih et** |
|**Erişilebilirlik değiştiricileri Ekle**|Seçildiğinde, **Edit. FormatDocument** tetiklendiğinde eksik erişilebilirlik değiştiricileri ekler.| dotnet_style_require_accessibility_modifiers |
|**Erişilebilirlik değiştiricilerini sıralama**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde erişilebilirlik değiştiricilerini sıralar.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**İfade/blok gövdesi tercihlerini Uygula**|Seçildiğinde, ifade Bodied üyeleri, **Edit. FormatDocument** tetiklendiğinde ya da tam tersi olarak blok gövdeler halinde dönüştürür.| [İfade-Bodied member EditorConfig seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/language-rules#expression-bodied-members)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **İfade tercihleri**  >  **Yöntemler, oluşturucular vb. için ifade gövdesi kullanın** |
|**Örtük/açık tür tercihleri Uygula**|Seçildiğinde, `var` **. FormatDocument** tetiklendiğinde, açık türe dönüştürür veya tam tersi de geçerlidir.| [Açık tür EditorConfig seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **' var ' tercihleri** |
|**Satır içi ' Out ' değişkenleri tercihlerini Uygula**|Seçildiğinde, `out` **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğu durumlarda satır içi değişkenler.| csharp_style_inlined_variable_declaration<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **Değişken tercihleri**  >  **Satır içi değişken bildirimini tercih et** |
|**Dil/çerçeve türü tercihlerini Uygula**|Seçildiğinde, dil türlerini çerçeve türlerine dönüştürür veya bunun tersini yapın **. FormatDocument** tetiklenir.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **önceden tanımlanmış tür tercihleri** |
|**Nesne/koleksiyon başlatma tercihlerini Uygula**|Seçildiğinde nesne ve koleksiyon başlatıcıları, **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğunca kullanılır.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **İfade tercihleri**  >  **Nesne Başlatıcısı tercih et** veya **koleksiyon başlatıcısı tercih et** |
|**' This. ' nitelik tercihlerini Uygula**|Seçildiğinde, `this.` **düzenleme. FormatDocument** tetiklendiğinde tercihleri uygular.| [Bunun. nitelik Düzenleyicisi yapılandırma seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/language-rules#this-and-me)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **' this. ' tercihleri** |
|**Mümkünse özel alanları ReadOnly yap**|Seçildiğinde, `readonly` **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğunca özel alanları oluşturur.| dotnet_style_readonly_field<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin düzenleyici**  >  **C#**  >  **Kod stili**  >  **Alan tercihleri**  >  **ReadOnly tercih et** |
|**Gereksiz yayınları kaldır**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğunda gereksiz yayınları kaldırır.| Yok |
|**Kullanılmayan değişkenleri kaldır**|Seçildiğinde, **Edit. FormatDocument** tetiklendiğinde kullanılmayan değişkenleri kaldırır.| Yok |

![Visual Studio C# için kod temizleme ayarları](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Girintileme sayfası

Bu sayfadaki girintileme seçenekleri, kod otomatik olarak biçimlendirilirken geçerlidir. Kod otomatik olarak biçimlendirildiğinde bir örnek, **yapıştırırken otomatik olarak Biçimlendir** seçildiğinde kodu dosyaya yapıştırmaktır. ( **Yapıştırma sırasında otomatik biçim** seçeneği **biçimlendirme**  >  aşamasındadır **Genel**.)

![Visual Studio'de C# metin düzenleyicisi girintileme seçenekleri](media/csharp-indentation-options.png)

> [!TIP]
> Metin Düzenleyici C# Sekme seçenekleri **sayfasında**  >  **girintileme**  >  **seçenekleri de** vardır. Bu seçenekler yalnızca satırın sonuna **Enter** tuşuna basarak kod düzenleyicisinin imleci yerleştirecekleri yeri belirler.
>
> ![C# metin düzenleyicisi sekme seçenekleri Visual Studio](media/csharp-tabs-options.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)
