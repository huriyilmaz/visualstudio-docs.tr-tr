---
title: Ayarlar & seçenekleri
description: Özel ayarları ve seçenekleri işlemeye uygun bir tarif.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 3d51941f729e8a8fda0adadfec6848229543c4a0
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516687"
---
# <a name="custom-settings-and-options-in-visual-studio-extensions"></a>Uzantılarda özel ayarlar Visual Studio seçenekleri

Ayarların depolanması ve alınması, birçok uzantı için mutlaka olması gerekir. Şimdi bu hedeflere sahip ayarlarla nasıl çalışabilirsiniz?

* Özel seçenekler sağlamanın basit bir yolu.
* Araçlar ve Seçenekler iletişim **kutusundaki > açın.**
* Ayarlara erişmek ve ayarları değiştirmek için iş parçacığı güvenli yolu.
* Hem zaman uyumlu hem de zaman uyumsuz destek.
* Ayarların başlatılması için paketi yüklemeniz gerek yoktur.

Aşağıdaki videoda uzantıya seçenekler eklemeye gerek yok.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWPmjL]

Araçlar ve Seçenekler iletişim kutusunda aşağıdaki **gibi > gerekir.**

## <a name="add-an-options-page"></a>Seçenekler sayfası ekleme
Projenize sağ tıklayın ve kullanılabilir şablonları **göstermek > Yeni Öğe... öğesini** seçin. Ardından sol **tarafta Genişletilebilirlik** kategorisini ve ardından Seçenekler Sayfası **(Community) şablonunu** seçin. Aşağıdaki **ad** alanına Genel **yazın.**

:::image type="content" source="../media/add-new-item-options.png" alt-text="Yeni Öğe Ekle iletişim kutusundan seçenekler sayfası ekleme.":::

Bu, *projenin kökünde /Options/General.cs'yi* oluşturacak.

:::image type="content" source="../media/options-folder.png" alt-text="Projeye eklenen Seçenekler Sayfası C# dosyası.":::

General.cs dosyasının içeriği şu şekildedir:

```csharp
internal partial class OptionsProvider
{
    // Register the options with these attributes on your package class:
    // [ProvideOptionPage(typeof(OptionsProvider.GeneralOptions), "MyExtension", "General", 0, 0, true)]
    // [ProvideProfile(typeof(OptionsProvider.GeneralOptions), "MyExtension", "General", 0, 0, true)]
    public class GeneralOptions : BaseOptionPage<General> { }
}

public class General : BaseOptionModel<General>
{
    [Category("My category")]
    [DisplayName("My Option")]
    [Description("An informative description.")]
    [DefaultValue(true)]
    public bool MyOption { get; set; } = true;
}
```

Bu kısa ve basit bir işlemdir ve ayrıntıların üzerinden geçin. Ancak öncelikle Seçenekler sayfasını kaydetmemiz gerekir.

## <a name="register-the-options-page"></a>Seçenekler sayfasını kaydetme
*General.cs* dosyasındaki bir kod açıklamasında Seçenekler sayfasının nasıl kayded silinecekleri yönergeleri yer alan yönergelerdir.

Tek yapacaklarımız bu iki özniteliği Package sınıfımıza kopyalamaktır. Bu şuna benzer olabilir:

```csharp
[ProvideOptionPage(typeof(OptionsProvider.GeneralOptions), "MyExtension", "General", 0, 0, true)]
[ProvideProfile(typeof(OptionsProvider.GeneralOptions), "MyExtension", "General", 0, 0, true)]
public sealed class OptionsPackage : ToolkitPackage
{
    ...
}
```

Uzantıyı çalıştırarak Araçlar ve Seçenekler iletişim kutusunda **MyExtension/General** **> görüyoruz.**

:::image type="content" source="../media/tools-options.png" alt-text="Özel seçenekler sayfası kaydedildi.":::

İki öznitelik birbirine çok benzer ancak farklı senaryoları ele almaktadır.

Öznitelik, `ProvideOptionsPage` Seçenekler sayfasının Araçlar ve Seçenekler iletişim kutusunda > **yapar.** Seçenekler sayfasının kullanıcılarınıza görünür durumda olup olmadığını görmek istemiyorsanız bu özniteliği atabilirsiniz.

`ProvideProfile`, seçenekleri dolaşım profiline kaydettirerek, tek tek ayarların farklı örneklerde kullanıcının hesabıyla dolaşıma geçerek kullanıcı Visual Studio. Ayrıca, uygulamanın içeri/dışarı aktarma ayarları özelliğini Visual Studio. Bu öznitelik isteğe bağlıdır.

## <a name="the-individual-options"></a>Tek tek seçenekler
General.cs dosyasında, tek tek seçeneklerin özniteliklerle birlikte dekore edilmiş basit C# özelliklerinden başka bir şey olmadığını görüyorsunuz.

```csharp
    [Category("My category")]
    [DisplayName("My Option")]
    [Description("An informative description.")]
    [DefaultValue(true)]
    public bool MyOption { get; set; } = true;
```

, , , gibi basit veri türlerinin hepsi kullanım örneklerinden çoğunu `string` `bool` `int` kapsayan, ilk olarak desteklemektedir. Diğer veri türleri için tür dönüştürücüleri kullanmamız gerekir. Bazıları, gibi Visual Studio yerleşik olarak yerleşik olarak yer `EnumConverter` alan.

Şu enum'u düşünün:

```csharp
public enum Numbers
{
    First,
    Second,
    Third,
}
```

Aşağıdakini bildirerek bu değerleri açılan bir açılan liste içinde seçenekler olarak ortaya `TypeConverter` çıkarabilirsiniz:

```csharp
[Category("My category")]
[DisplayName("My Enum")]
[Description("Select the value you want from the list.")]
[DefaultValue(Numbers.First)]
[TypeConverter(typeof(EnumConverter))]
public Numbers MyEnum { get; set; } = Numbers.First;
```

:::image type="content" source="../media/tools-options-enum.png" alt-text="Seçenekler sayfasında enum değerleriyle birlikte açılan liste.":::

## <a name="reading-and-writing-options"></a>Okuma ve yazma seçenekleri
Kullanıcılarınızı değerlerini değiştirmesine izin verme seçeneklerini kaydettiniz. Şimdi bu değerleri uzantımızda kullanmak üzere okuyabilirsiniz.

Hem zaman uyumlu hem de zaman uyumsuz bağlamlardan ayarlarla çalışabilirsiniz. Zaman uyumlu ile başlayalım:

```csharp
// read settings
var number = General.Instance.MyEnum;

// write settings
General.Instance.MyEnum = Numbers.Second;
General.Instance.Save();
```

Ayarları okuma ve yazma API'si oldukça basittir ve oldukça basittir.

Zaman uyumsuz bağlamda çalışırken API çok benzer bir görünüme sahiptir.

```csharp
// read settings
var general = await General.GetLiveInstanceAsync();
var number = general.MyEnum;

// write settings
general.MyEnum = Numbers.Second;
await general.SaveAsync();
```

## <a name="events"></a>Ekinlikler
Ayarlar kaydedilirken statik olay `General.Saved` başlatıldı. Bu etkinliğe .NET'te diğer tüm olaylarda olduğu gibi abone olabilirsiniz ve şu şekildedir:

```csharp
General.Saved += OnSettingsSaved;

...

private void OnSettingsSaved(object sender, General e)
{
   
}
```

## <a name="get-the-source-code"></a>Kaynak kodunu alma
Bu uzantının kaynak kodunu örnek deposunda [bulabilirsiniz.](https://github.com/VsixCommunity/Samples)

## <a name="additional-resources"></a>Ek kaynaklar
Bu senaryolarla ilgili tüm ayrıntılar için belgeleri okuyun, ancak daha ayrıntılı belgeler sağlasalar da bu örnekte açıklanan en iyi yöntemleri izleme olduklarını fark edin. Ayrıca, ayarlarla çalışmayı çok Community araç setlerini de kullanmazlar.

* [Seçenekler Sayfası Oluşturma](../../creating-an-options-page.md)
* [Ayarlar Deposu Kullanma](../../using-the-settings-store.md)
* [Kullanıcı Ayarları Deposuna Yazma](../../writing-to-the-user-settings-store.md)
