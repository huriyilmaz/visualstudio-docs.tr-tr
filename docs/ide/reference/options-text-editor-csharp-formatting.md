---
title: C#Düzenleyici biçimlendirme seçenekleri
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596248"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>Seçenekler iletişim kutusu: metin Düzenleyicisi \> C# \> kod stili \> biçimlendirme

Kod düzenleyicisinde biçimlendirme kodu seçeneklerini ayarlamak için **biçimlendirme** seçenekleri sayfasını ve alt sayfalarını ([**girintileme**](#indentation-page), **yeni satırlar**, **boşluk**ve **kaydırma**) kullanın.

Bu seçenekler sayfasına erişmek için, menü çubuğundan **araçlar** > **Seçenekler** ' i seçin. **Seçenekler** iletişim kutusunda, **kod stili** > **biçimlendirme** > **metin düzenleyici** > **C#** seçin.

> [!TIP]
> **Girinti**, **yeni satırlar**, **Aralık**ve **kaydırma** alt sayfaları her bir seçeneğin etkisini gösteren bir önizleme penceresi görüntüler. Önizleme penceresini kullanmak için bir biçimlendirme seçeneği belirleyin. Önizleme penceresinde seçilen seçeneğe bir örnek gösterilir. Bir seçimi bir radyo düğmesi veya onay kutusu seçerek değiştirdiğinizde, Önizleme penceresi Yeni ayarın etkisini gösterecek şekilde güncelleştirilir.

## <a name="formatting-general-page"></a>Biçimlendirme (genel) sayfası

### <a name="general-settings"></a>Genel ayarlar

Bu ayarlar, kod düzenleyicisinin koda biçimlendirme seçeneklerini uyguladığı *zaman* etkiler.

|Etiketle|Açıklama|
|-----------|-----------------|
|**Yazarken Otomatik Biçimlendir**|Seçimi kaldırıldığında,, ve biçim **bloğu on}** seçeneklerinde **Biçim açıklaması** devre dışı bırakılır.|
|**; Üzerinde otomatik olarak biçim ekstresi**|Seçildiğinde, deyimi, düzenleyici için seçilen biçimlendirme seçeneklerine göre tamamlama sırasında biçimlendirir.|
|**} Üzerindeki blok otomatik olarak Biçimlendir**|Seçildiğinde kod bloğunu, kod bloğunu tamamladıktan hemen sonra düzenleyici için seçilen biçimlendirme seçeneklerine göre biçimlendirir.|
|**Dönüşte otomatik olarak Biçimlendir**|Seçildiğinde, düzenleyici için seçilen biçimlendirme seçeneklerine uyacak şekilde, **ENTER** tuşuna basıldığında metin biçimlendirir.|
|**Yapıştırırken otomatik olarak Biçimlendir**|Seçildiğinde, düzenleyiciye yapıştırılan metni düzenleyici için seçilen biçimlendirme seçeneklerine uyacak şekilde biçimlendirir.|

::: moniker range="vs-2019"

Visual Studio 2017 ' deki **belgeyi Biçimlendir** komutunu C# kullanarak daha önce dosyalar için kod stili ayarları uyguladıysanız, bu işlev artık [**kod temizleme**](../code-styles-and-code-cleanup.md#apply-code-styles)olarak kullanılabilir.

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>Belge ayarlarını Biçimlendir

Bu ayarlar, dosya üzerinde ek kod temizleme işlemini gerçekleştirmek için **Biçim belgesi** komutunu yapılandırır. Bu ayarların nasıl uygulandığı hakkında daha fazla bilgi için bkz. [belge komutunu Biçimlendir](../code-styles-and-code-cleanup.md#apply-code-styles).

|Etiketle|Açıklama|İlgili EditorConfig ve Araçlar > seçenekleri kuralları|
|-----------|-----------------|-----------------|-----------------|
|**Tüm C# biçimlendirme kurallarını Uygula (girintileme, kaydırma, Aralık)**|**Biçim belgesi** komutu her zaman biçimlendirme sorunlarını düzeltir. Bu ayar değiştirilemez.| [Core EditorConfig seçenekleri](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig biçimlendirme seçenekleri](../../ide/editorconfig-formatting-conventions.md)<br/><br/>**Araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **C#**  > **biçimlendirme** > [**girintileme** veya **yeni çizgiler** veya **boşluk** ya da **kaydırma**]|
|**Biçimlendirme sırasında ek kod temizlemeyi gerçekleştir**|Seçildiğinde, **Edit. FormatDocument** komutunda belirtilen kurallara ilişkin düzeltmeleri uygular.| YOK |
|**Gereksiz kullanımları kaldır**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde gereksiz `using` yönergeleri kaldırır.| YOK |
|**Using deyimlerini Sırala**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde `using` yönergeleri sıralar.| dotnet_sort_system_directives_first<br/><br/>**Araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **C#**  > **Gelişmiş** >  **' sistem ' yönergelerini sıralama, using deyimlerini sıralarken** |
|**Tek satırlı denetim deyimleri için küme ayraçları Ekle/Kaldır**|Seçildiğinde, **Edit. FormatDocument** tetiklendiğinde tek satırlık denetim deyimlerine küme ayraçları ekler veya kaldırır.| csharp_prefer_braces<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyici** > **C#**  > **kod stili** > **kod bloğu tercihleri** > , **küme ayraçlarını tercih et** |
|**Erişilebilirlik değiştiricileri Ekle**|Seçildiğinde, **Edit. FormatDocument** tetiklendiğinde eksik erişilebilirlik değiştiricileri ekler.| dotnet_style_require_accessibility_modifiers |
|**Erişilebilirlik değiştiricilerini sıralama**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde erişilebilirlik değiştiricilerini sıralar.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**İfade/blok gövdesi tercihlerini Uygula**|Seçildiğinde, ifade Bodied üyeleri, **Edit. FormatDocument** tetiklendiğinde ya da tam tersi olarak blok gövdeler halinde dönüştürür.| [İfade-Bodied member EditorConfig seçenekleri](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyici** > **C#**  > **kod stili** > **Ifade tercihleri** > **Yöntemler, oluşturucular vb. için ifade gövdesi kullan.** |
|**Örtük/açık tür tercihleri Uygula**|Seçildiğinde, `var` **. FormatDocument** tetiklendiğinde açık türe dönüştürür veya tam tersi de geçerlidir.| [Açık tür EditorConfig seçenekleri](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyicisi** > **C#**  > **kod stili** >  **' var ' tercihleri** |
|**Satır içi ' Out ' değişkenleri tercihlerini Uygula**|Seçildiğinde, Inlines, **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğu durumlarda `out`.| csharp_style_inlined_variable_declaration<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyicisi** > **C#**  > **kod stili** > **değişken tercihleri** > **satır içi değişken bildirimini tercih et** |
|**Dil/çerçeve türü tercihlerini Uygula**|Seçildiğinde, dil türlerini çerçeve türlerine dönüştürür veya bunun tersini yapın **. FormatDocument** tetiklenir.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyicisi** > **C#**  > **kod stili** > **önceden tanımlanmış tür tercihleri** |
|**Nesne/koleksiyon başlatma tercihlerini Uygula**|Seçildiğinde nesne ve koleksiyon başlatıcıları, **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğunca kullanılır.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyici** > **C#**  > **kod stili** > **Ifade tercihleri** > **nesne Başlatıcısı tercih et** veya **koleksiyon başlatıcısı tercih et** |
|**' This. ' nitelik tercihlerini Uygula**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde `this.` tercihleri uygular.| [Bunun. nitelik Düzenleyicisi yapılandırma seçenekleri](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyici** > **C#**  > **kod stili** >  **' this. ' tercihleri** |
|**Mümkünse özel alanları ReadOnly yap**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğunca özel alanlar `readonly` olur.| dotnet_style_readonly_field<br/><br/>**Araçlar** > **Seçenekler** > **metin düzenleyicisi** > **C#**  > **kod stili** > **alan tercihleri** > **salt okunur tercih et** |
|**Gereksiz yayınları kaldır**|Seçildiğinde, **düzenleme. FormatDocument** tetiklendiğinde mümkün olduğunda gereksiz yayınları kaldırır.| YOK |
|**Kullanılmayan değişkenleri kaldır**|Seçildiğinde, **Edit. FormatDocument** tetiklendiğinde kullanılmayan değişkenleri kaldırır.| YOK |

![Visual Studio 'da için C# kod temizleme ayarları](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>Girintileme sayfası

Bu sayfadaki girintileme seçenekleri, kod otomatik olarak biçimlendirilirken geçerlidir. Kod otomatik olarak biçimlendirildiğinde bir örnek, **yapıştırırken otomatik olarak Biçimlendir** seçildiğinde kodu dosyaya yapıştırmaktır. ( **Yapıştırma sırasında otomatik biçim** seçeneği, **genel** > **biçimlendirme** aşamasındadır.)

![C#Visual Studio 'da metin düzenleyici girintileme seçenekleri](media/csharp-indentation-options.png)

> [!TIP]
> Ayrıca, **metin düzenleyici** > **C#**  > **sekmeleri** Seçenekler sayfasında girintileme seçenekleri de vardır. Bu seçenekler yalnızca, satırın sonunda **ENTER** tuşuna bastığınızda, imleci yalnızca kod düzenleyicisinin nereye yerleştirdiği belirlenir.
>
> ![C#Visual Studio 'da metin düzenleyici sekmeleri seçenekleri](media/csharp-tabs-options.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)
