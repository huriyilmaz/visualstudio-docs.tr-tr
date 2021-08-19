---
title: VSIX Renk Düzenleyicisi | Microsoft Docs
description: Uygulama için özel Visual Studio ve düzenleme ve tema kaynak anahtarları oluşturan Visual Studio Uzantısı Renk Düzenleyicisi aracı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 013c72ca0bdf95bb0e40ad242b923f3f9db656a6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117702"
---
# <a name="vsix-color-editor"></a>VSIX Renk Düzenleyicisi
Uzantı Visual Studio Düzenleyicisi aracı, uygulama için özel renkler oluşturabilir ve Visual Studio. Araç, renklerin kodda kullanılamayacak şekilde tema kaynak anahtarları da üretebilirsiniz. Bu araç, Visual Studio destekleyen bir Visual Studio için renk yapmak için kullanışlıdır. Bu araç .pkgdef'i açabilir ve .xml açabilir. Visual Studio temaları (.vstheme dosyaları), dosya uzantısı Visual Studio olarak değiştirerek .xml. Buna ek olarak, .vstheme dosyaları geçerli bir dosya .xml aktarabilirsiniz.

 ![VSIX Renk Düzenleyicisi Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSıX renk düzenleyici Hero")

 **Paket tanımı dosyaları**

 Paket tanımı (.pkgdef) dosyaları, temaları tanımlayan dosyalardır. Renkler tema renginde depolanır ve .xml .pkgdef dosyasına derlenmiş dosyalardır. .pkgdef dosyaları aranabilir konumlara Visual Studio, çalışma zamanında işlenir ve temaları tanımlamak için birleştirilir.

 **Renk belirteçleri**

 Renk belirteci dört öğeden oluşur:

- **Kategori adı:** Bir renk kümesi için mantıksal gruplama. İstenen kullanıcı arabirimi öğesine veya kullanıcı arabirimi öğeleri grubuna özgü renkler zaten varsa mevcut bir kategori adını kullanın.

- **Belirteç adı:** Renk belirteci ve belirteç kümeleri için açıklayıcı bir ad. Kümeler arka plan ve ön plan (metin) belirteç adlarının yanı sıra tüm durumları içerir ve çiftleri ve uygulatacakları durumları kolayca tanımlamak için bunlar olarak adlandırılmıştır.

- **Renk değerleri (veya tonları):** Her renkli tema için gereklidir. Her zaman çift olarak arka plan ve metin rengi değerleri oluşturun. Renkler arka plan/ön plan için eşleştirilir; böylece metin (ön plan) rengi, çizilen arka plan rengine göre her zaman okunabilir. Bu renkler bağlantılıdır ve kullanıcı arabiriminde birlikte kullanılır. Arka plan metinle kullanılmak üzere amaçlanmamışsa ön plan rengi tanımlamayın.

- **Sistem rengi adı:** Yüksek karşıtlıklı ekranlarda kullanmak için.

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 Mümkün olduğunca ve uygun olduğunda mevcut Visual Studio renklerinin yenilerini yapmak yerine yeniden kullanılması gerekir. Ancak, uygun renklerin tanımlanmamış olduğu durumlarda, uzantının uyumlu olması için özel renkler oluşturulsun.

 **Yeni renk belirteçleri oluşturma**

 Uzantı Rengi Düzenleyicisi'ni kullanarak Visual Studio renkler oluşturmak için şu adımları izleyin:

1. Yeni renk belirteçleri için kategori ve belirteç adlarını belirleme.

2. Kullanıcı arabirimi öğesinin her tema için kullanabileceği tonları ve her tema için sistem rengini Yüksek Karşıtlık.

3. Yeni renk belirteçleri oluşturmak için renk düzenleyicisini kullanın.

4. Bir uzantıda renkleri Visual Studio kullanın.

5. Değişiklikleri test Visual Studio.

   **1. Adım: Yeni renk belirteçleri için kategori ve belirteç adlarını belirleme.**

   VSColor için tercih edilen adlandırma şeması **[Kategori] [UI türü] [State] 'tir.** VSColor adlarında "color" sözcüğü gereksiz olduğu için kullanmayın.

   Kategori adları mantıksal gruplamalar sağlar ve mümkün olduğunca dar bir şekilde tanımlanmalıdır. Örneğin, tek bir araç penceresinin adı bir kategori adı olabilir, ancak tüm iş biriminin veya proje ekibinin adı değildir. Girişleri kategorilere gruplama, aynı adla renkler arasındaki karışıklığı önlemeye yardımcı olur.

   Belirteç adı, öğe türünü ve rengin uygulanacak olduğu durumları veya "durum"ları açıkça belirtmalıdır. Örneğin, etkin bir veri ipucunda **[UI türü]** "**DataTip**" , **[State]** ise "**Etkin**" olarak adlandırılmış ve bu da "**DataTipActive**" renk adıyla sonuçlanmış olabilir. Veri ipuçlarında metinler olduğu için hem ön plan hem de arka plan rengi tanımlanmalıdır. Arka plan/ön plan eşleştirmesi kullanılarak, renk düzenleyicisi arka plan için "**DataTipActive**" ve ön plan için "**DataTipActiveText**" renklerini otomatik olarak oluşturacaktır.

   Kullanıcı arabiriminin yalnızca bir durumu varsa, adın **[State]** bölümü atlanabilir. Örneğin, bir arama kutusunda kenarlık varsa ve kenarlığın rengini etkileyecek bir durum değişikliği yoksa, kenarlığın renk belirtecin adı basitçe **"SearchBoxBorder"** olarak çağrılabilirsiniz.

   Bazı yaygın durum adları şunlardır:

- Etkin

- Etkin değil

- Mouseover

- Mousedown

- Seçili

- Odaklı

  Liste öğesi denetimi bölümleri için birkaç belirteç adı örneği:

- Listıtem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **2. Adım: Kullanıcı arabirimi öğesinin her tema için kullanabileceği tonları ve kullanıcı arabirimi için sistem Yüksek Karşıtlık.**

  Kullanıcı arabirimi için özel renkler seçerken, benzer bir mevcut kullanıcı arabirimi öğesi seçin ve temel olarak bu öğenin renklerini kullanın. Kutu içinde kullanıcı arabirimi öğelerinin renkleri gözden geçirilmiş ve test edilmiştir, bu nedenle tüm temalarda uygun görünürler ve doğru davranırlar.

  **3. Adım: Yeni renk belirteçleri oluşturmak için renk düzenleyicisini kullanın.**

  Renk düzenleyicisini başlatarak yeni bir özel tema rengi açın veya .xml oluşturun. Menüden **> Yeni Renk'i** seçin. Bu, kategoriyi ve bu kategori içindeki renk girişleri için bir veya daha fazla ad belirtmek için bir iletişim kutusu açar:

  ![VSIX Renk Düzenleyicisi Yeni Renk](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSıX renk düzenleyici yeni renk")

  Mevcut bir kategoriyi seçin veya yeni **bir kategori oluşturmak** için Yeni Kategori'yi seçin. Yeni bir kategori adı oluşturarak başka bir iletişim kutusu açılır:

  ![VSIX Renk Düzenleyicisi Yeni Kategori](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSıX renk düzenleyici yeni kategori")

  Yeni kategori daha sonra Yeni Renk kategorisi **açılan** menüsünde kullanılabilir hale gelecektir. Kategori seçtikten sonra, her yeni renk belirteci için satır başına bir ad girin ve bittiğinde "Oluştur" seçeneğini seçin:

  ![VSIX Renk Düzenleyicisi Yeni Renk Doldurulmuş](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSıX renk Düzenleyicisi yeni renk dolduruldu")

  Renk değerleri arka plan/ön plan çiftleri içinde gösterilir ve rengin tanımlanmamış olduğunu belirten "Hiçbiri" gösterilir. Not: Bir rengin metin rengi/arka plan renk çifti yoksa yalnızca arka plan tanımlanmalıdır.

  ![VSIX Renk Düzenleyicisi Renk Değerleri](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSıX renk düzenleyici renk değerleri")

  Bir renk belirteci düzenlemek için, bu belirteci tema (sütun) için bir renk girdisi seçin. Renk değerini 8 basamaklı ARGB biçiminde bir renk değeri yazarak, hücreye bir sistem rengi adı girerek veya bir dizi renk kaydırıcısı ya da sistem renkleri listesi aracılığıyla istenen rengi seçmek için açılan menüyü kullanarak renk değerini ekleyin.

  ![VSIX Renk Düzenleyicisi Rengi Düzenleme](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSıX renk Düzenleyicisi düzenleme rengi")

  ![VSIX Renk Düzenleyicisi Arka Planı](../../extensibility/internals/media/vsix-color-editor-background.png "VSıX Color Düzenleyicisi arka planı")

  Metin görüntülemesi gerek girmeyen bileşenler için yalnızca bir renk değeri girin: arka plan rengi. Aksi takdirde, hem arka plan hem de metin rengi değerlerini eğik çizgiyle ayırarak girin.

  Sistem için değer girerken Yüksek Karşıtlık adları için geçerli Windows girin. Sabit koda sahip ARGB değerleri girmeyin. Renk değeri açılan menülerinden "Arka Plan: Sistem" veya "Ön Plan: Sistem"i seçerek geçerli sistem renk adlarının listesini görüntüebilirsiniz. Metin bileşenlerine sahip öğeler oluştururken doğru arka plan/metin sistemi renk çiftini kullanın veya metin okunamaz olabilir.

  Renk belirteçlerini oluşturmayı, ayarlamayı ve düzenlemeyi tamamlasanız, bunları istediğiniz .xml veya .pkgdef biçimine kaydedin. Arka plan veya ön plan kümesi olmayan renk belirteçleri, .pkgdef biçiminde .xml boş renkler olarak kaydedilir. Boş renkleri bir .pkgdef dosyasına kaydetmeye çalışırken bir iletişim kutusu sizi olası renk kaybı konusunda uyaracak.

  **4. Adım: Visual Studio kullanın.**

  Yeni renk belirteçlerini tanımlayarak proje dosyasına .pkgdef'i "Derleme Eylemi" "İçerik" ve "VSIX'e dahil edin" "True" olarak ayarlanmış şekilde dahil edin.

  ![VSIX Renk Düzenleyicisi pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSıX renk Düzenleyicisi pkgdef")

  Uzantı Visual Studio Düzenleyicisi'nde, WPF tabanlı kullanıcı arabiriminde özel renklere erişmek için kullanılan kodu görüntülemek için Dosya Adı'> Kaynak Kodunu Görüntüle'yi seçin.

  ![VSIX Renk Düzenleyicisi Kaynak Kodu Görüntüleyicisi](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSıX renk düzenleyici kaynak kodu Görüntüleyici")

  Bu kodu projeye statik bir sınıfa dahil etmek. **ThemeResourceKey** türünü kullanmak Için projeye **Microsoft. VisualStudio. Shell. \<VSVersion>.0.dll** başvurusunun eklenmesi gerekir.

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Bu, XAML kodundaki renklere erişim sağlar ve Kullanıcı arabiriminin Tema değişikliklerine yanıt vermesini sağlar.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **5. Adım: değişiklikleri Visual Studio test edin.**

 renk düzenleyicisi, uzantı paketini yeniden oluşturmadan renklerin canlı değişikliklerini görüntülemek için Visual Studio çalışan örneklerine geçici olarak renk belirteçleri uygulayabilir. bunu yapmak için, her tema sütununun üstbilgisinde yer alan "bu temayı çalıştırmak Visual Studio windows ' a uygula" düğmesine tıklayın. Bu geçici tema, VSıX renk Düzenleyicisi kapalıyken kaybolur.

 ![VSıX renk Düzenleyicisi Uygula](../../extensibility/internals/media/vsix-color-editor-apply.png "VSıX renk Düzenleyicisi Uygula")

 değişiklikleri kalıcı hale getirmek için, yeni renkleri. pkgdef dosyasına ekledikten ve bu renkleri kullanacak kodu yazarak Visual Studio uzantısını yeniden oluşturun ve yeniden dağıtın. Visual Studio uzantısını yeniden oluşturmak, yeni renklerin kayıt defteri değerlerini temaların geri kalanına birleştirir. Visual Studio yeniden başlatın, kullanıcı arabirimini görüntüleyin ve yeni renklerin beklenildiği gibi göründüğünü doğrulayın.

## <a name="notes"></a>Notlar
 bu araç, önceden var olan Visual Studio temalar için özel renkler oluşturmak veya özel bir Visual Studio temasının renklerini düzenlemede kullanılmak üzere tasarlanmıştır. tüm özel Visual Studio temaları oluşturmak için Visual Studio uzantıları galerisinden [Visual Studio Color Theme düzenleyicisi uzantısını](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) indirin.

## <a name="sample-output"></a>Örnek Çıktı
 **XML renk çıkışı**

 Araç tarafından oluşturulan .xml dosyası şuna benzer olacaktır:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **PKGDEF Color çıkışı**

 Araç tarafından oluşturulan. pkgdef dosyası şuna benzer olacaktır:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **C# kaynak anahtarları sarmalayıcısı**

 Araç tarafından oluşturulan renk kaynak anahtarları şuna benzer olacaktır:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **WPF kaynak sözlüğü sarmalayıcısı**

 Araç tarafından oluşturulan renk **ResourceDictionary** anahtarları şuna benzer olacaktır:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
