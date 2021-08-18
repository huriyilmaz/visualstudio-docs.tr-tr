---
title: C# düzenleyicisi biçimlendirme seçenekleri
description: C# dilinde programlama yapmak üzere kod düzenleyicisinde kod biçimlendirme seçeneklerini ayarlamak için Biçimlendirme seçenekleri sayfasını ve alt sayfasını kullanmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041145"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Seçenekler iletişim kutusu: Metin Düzenleyici \> C# \> Kod Stili \> Biçimlendirme

Kod **düzenleyicisinde** kodu biçimlendirme seçeneklerini [](#indentation-page)ayarlamak için Biçimlendirme seçenekleri sayfasını ve alt sayfaları (Girintileme, Yeni Satırlar, Aralık ve **Kaydırma)** kullanın.

Bu seçenekler sayfasına erişmek için menü  >  **çubuğundan Araçlar** Seçenekler'i seçin. Seçenekler iletişim **kutusunda** Metin Düzenleyici C# **Kod Stili**  >    >  **Biçimlendirme'yi**  >  **seçin.**

> [!TIP]
> **Girintileme,** **Yeni Satırlar,**  **Boşluk** ve Sarmalama alt sayfaları, altta her bir seçeneğin etkisini gösteren bir önizleme penceresi görüntüler. Önizleme penceresini kullanmak için bir biçimlendirme seçeneği belirleyin. Önizleme penceresinde, seçili seçeneğin bir örneği gösterilir. Bir radyo düğmesini veya onay kutusunu seçerek bir ayarı değiştirerek, önizleme penceresi yeni ayarın etkisini gösterecek şekilde değişir.

## <a name="formatting-general-page"></a>Biçimlendirme (Genel) sayfası

### <a name="general-settings"></a>Genel ayarlar

Bu ayarlar, *kod düzenleyicisinin* koda biçimlendirme seçeneklerini ne zaman uygulaması olduğunu etkiler.

|Etiketle|Açıklama|
|-----------|-----------------|
|**Yazarken otomatik olarak biçimlendirme**|Seçimi kaldırıldığında, üzerinde **biçim deyimi ve** } **seçeneklerindeki biçim bloğu devre** dışı bırakılır.|
|**üzerinde deyimi otomatik olarak biçimlendirin;**|Seçildiğinde, tamamlandıktan sonra deyimleri düzenleyici için seçilen biçimlendirme seçeneklerine göre biçimlendirin.|
|**} üzerinde bloğu otomatik olarak biçimlendirme**|Seçildiğinde, kod bloğu tamamlandıktan hemen sonra düzenleyici için seçilen biçimlendirme seçeneklerine göre kod bloklarını biçimlendirin.|
|**Dönüşte otomatik olarak biçimlendirme**|Seçildiğinde, Enter **tuşuna** basıldığında metni biçimlendirin ve düzenleyici için seçilen biçimlendirme seçeneklerine uyacak şekilde biçimlendirin.|
|**Yapıştırma sırasında otomatik olarak biçimlendirme**|Seçildiğinde, düzenleyici için seçilen biçimlendirme seçeneklerine uyacak şekilde düzenleyiciye yapıştırilen metni biçimlendirin.|

::: moniker range="vs-2019"

Daha önce Visual Studio 2017'de  belgeyi Biçimlendir komutunu kullanarak C# dosyaları için kod stili ayarları uyguladıysanız, bu işlevsellik artık Kod Temizleme [**olarak kullanılabilir.**](../code-styles-and-code-cleanup.md#apply-code-styles)

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Belge ayarlarını biçimlendirme

Bu ayarlar, bir **dosyada ek** kod temizleme işlemi gerçekleştirmek için Belgeyi Biçimlendir komutunu yapılandırır. Bu ayarların nasıl uygulandığı hakkında daha fazla bilgi için bkz. [Belgeyi Biçimlendir komutu.](../code-styles-and-code-cleanup.md#apply-code-styles)

|Etiketle|Açıklama|İlgili EditorConfig ve Araçlar > Kuralları|
|-----------|-----------------|-----------------|-----------------|
|**Tüm C# biçimlendirme kurallarını uygulama (girintileme, sarmalama, aralık)**|Belgeyi **Biçimlendir komutu** biçimlendirme sorunlarını her zaman düzeltir. Bu ayar değiştirilemez.| [Çekirdek EditorConfig seçenekleri](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig biçimlendirme seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Biçimlendirme** > [**Girintileme** veya **Yeni Satırlar veya** **Aralık** veya **Kaydırma**]|
|**Biçimlendirme sırasında ekleme kodu temizleme gerçekleştirme**|Seçildiğinde, **Edit.FormatDocument** komutunda aşağıda belirtilen kurallar için düzeltmeler uygular.| Yok |
|**Gereksiz kullanmaları kaldırma**|Seçildiğinde, `using` **Edit.FormatDocument** tetiklendiğinde gereksiz yönergeleri kaldırır.| Yok |
|**Kullanmaları sıralama**|Seçildiğinde, `using` **Edit.FormatDocument tetiklendiğinde yönergeleri** sıralar.| dotnet_sort_system_directives_first<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Gelişmiş**  >  **Usings sıralamada 'System' yönergelerini ilk önce yer** |
|**Tek satırlı denetim deyimleri için ayraç ekleme/kaldırma**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde tek satırlı denetim deyimlerinden küme ayraçları ekler veya kaldırır.| csharp_prefer_braces<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **Kod bloğu tercihleri**  >  **Küme ayraçlarını tercih** |
|**Erişilebilirlik değiştiricileri ekleme**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde eksik erişilebilirlik değiştiricileri ekler.| dotnet_style_require_accessibility_modifiers |
|**Erişilebilirlik değiştiricilerini sıralama**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde erişilebilirlik değiştiricilerini sıralar.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**İfade/blok gövdesi tercihlerini uygulama**|Seçildiğinde, **edit.FormatDocument** tetiklendiğinde ifadeye dönüştürülmüş üyeleri blok gövdelerine veya tam tersine dönüştürür.| [İfadeye göre yapılandırılmış üye EditorConfig seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/language-rules#expression-bodied-members)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **İfade tercihleri**  >  **Yöntemler, oluşturucular vb. için ifade gövdelerini kullanın.** |
|**Örtülü/açık tür tercihlerini uygulama**|Seçildiğinde, `var` **Edit.FormatDocument** tetiklendiğinde açık türe veya tersine dönüştürür.| [Açık tür EditorConfig seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **'var' tercihleri** |
|**Satır içi 'out' değişken tercihlerini uygulama**|Seçildiğinde, `out` **Edit.FormatDocument** tetiklendiğinde mümkün olduğunca değişkenlerin çizgilerini çizin.| csharp_style_inlined_variable_declaration<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **Değişken tercihleri**  >  **Büyük/büyük değişken bildirimini tercih** |
|**Dil/çerçeve türü tercihlerini uygulama**|Seçildiğinde, dil türlerini çerçeve türlerine veya **Edit.FormatDocument tetiklendiğinde** çerçeve türlerine dönüştürür.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **önceden tanımlanmış tür tercihleri** |
|**Nesne/koleksiyon başlatma tercihlerini uygulama**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde mümkün olduğunda nesne ve koleksiyon başlatıcılarını kullanır.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **İfade tercihleri**  >  **Nesne başlatıcıyı tercih veya** **Koleksiyon başlatıcıyı tercih** |
|**'This.' nitelik tercihlerini uygulama**|Seçildiğinde, `this.` **Edit.FormatDocument tetiklendiğinde** tercihleri uygular.| [Bu. nitelik EditorConfig seçenekleri](/dotnet/fundamentals/code-analysis/style-rules/language-rules#this-and-me)<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **'this.' tercihleri** |
|**Mümkün olduğunda özel alanları salt okunur yapma**|Seçildiğinde, `readonly` **Edit.FormatDocument** tetiklendiğinde mümkün olduğunca özel alanlar yapar.| dotnet_style_readonly_field<br/><br/>**Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyici**  >  **C#**  >  **Kod Stili**  >  **Alan tercihleri**  >  **Salt okunur tercih** |
|**Gereksiz dökümleri kaldırma**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde mümkün olduğunca gereksiz dönüştürmeleri kaldırır.| Yok |
|**Kullanılmayan değişkenleri kaldırma**|Seçildiğinde, **Edit.FormatDocument** tetiklendiğinde kullanılmayan değişkenleri kaldırır.| Yok |

![Visual Studio'da C# için kod temizleme ayarları](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Girintileme sayfası

Kod otomatik olarak biçimlendirilirken bu sayfada girintileme seçenekleri uygulanır. Kodun otomatik olarak biçimlendirilirken dosyaya kod yapıştırırken Yapıştırma sırasında otomatik olarak biçimlendir'in seçili **olduğu** bir örnektir. **(Yapıştırılırken otomatik olarak biçimlendir** seçeneği Biçimlendirme'nin **altında**  >  **Genel**.)

![Visual Studio 'de C# Metin Düzenleyicisi girintileme seçenekleri](media/csharp-indentation-options.png)

> [!TIP]
> Ayrıca, **metin düzenleyici**  >  **C#**  >  **sekmeleri** Seçenekler sayfasında girintileme seçenekleri de vardır. Bu seçenekler yalnızca, satırın sonunda **ENTER** tuşuna bastığınızda, imleci yalnızca kod düzenleyicisinin nereye yerleştirdiği belirlenir.
>
> ![Visual Studio C# Metin Düzenleyicisi sekmeleri seçenekleri](media/csharp-tabs-options.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)
