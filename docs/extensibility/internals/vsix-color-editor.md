---
title: VSıX renk Düzenleyicisi | Microsoft Docs
description: Visual Studio için özel renkler oluşturup düzenleyebilen ve tema kaynak anahtarları oluşturabilen Visual Studio uzantı rengi düzenleyici aracı hakkında bilgi edinin.
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
ms.openlocfilehash: e19105a9b769810011b5ae3871a3cae03e2bd48611087244fecf5ed40734067a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275105"
---
# <a name="vsix-color-editor"></a>VSIX Renk Düzenleyicisi
Visual Studio uzantısı renk düzenleyicisi aracı, Visual Studio için özel renkler oluşturabilir ve düzenleyebilir. Araç ayrıca, renklerin kodda kullanılabilmesi için tema kaynak anahtarları da oluşturabilir. bu araç, tema oluşturmayı destekleyen bir Visual Studio uzantısı için renkler oluşturmak için faydalıdır. Bu araç,. pkgdef ve .xml dosyaları açabilir. Visual Studio temalar (. vstheme dosyaları), dosya uzantısını .xml olarak değiştirerek Visual Studio uzantısı renk düzenleyiciyle birlikte kullanılabilir. Ayrıca,. vstheme dosyaları geçerli bir .xml dosyasına aktarılabilir.

 ![VSıX renk düzenleyici Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX Renk Düzenleyicisi Hero")

 **Paket tanımı dosyaları**

 Paket tanımı (. pkgdef) dosyaları, temaları tanımlayan dosyalardır. Renkler, bir. pkgdef dosyasına derlenen Tema rengi .xml dosyalarında depolanır. . pkgdef dosyaları, aranabilir konumlara Visual Studio dağıtılır, çalışma zamanında işlenir ve temaları tanımlamak için birlikte birleştirilir.

 **Renk belirteçleri**

 Renk belirteci dört öğeden oluşur:

- **Kategori adı:** Bir renk kümesi için mantıksal gruplama. İstenen kullanıcı arabirimi öğesine veya Kullanıcı arabirimi öğeleri grubuna özgü renkler varsa, var olan bir kategori adı kullanın.

- **Belirteç adı:** Renk belirteci ve belirteç kümeleri için açıklayıcı bir ad. , Arka plan ve ön plan (metin) belirteç adlarını ve bunların tüm durumlarını içerir ve bunların, bu koşulların ve uygulandıkları durumların belirlenmesi kolay olacak şekilde adlandırılması gerekir.

- **Renk değerleri (veya kular):** Her renkli tema için gereklidir. Her zaman, çiftler halinde arka plan ve metin rengi değerleri oluşturun. Metin (ön plan) rengi her zaman çizilme arka plan rengine karşı okunabilir olacak şekilde arka plan/ön plan için renkler eşleştirilir. Bu renkler bağlantılıdır ve Kullanıcı arabiriminde birlikte kullanılacaktır. Arka planın metinle birlikte kullanılması amaçlanmıyorsa, ön plan rengi tanımlamayın.

- **Sistem renk adı:** Yüksek karşıtlıklı ekranlarda kullanım için.

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 mümkün olduğunca ve uygunsa, mevcut Visual Studio renkleri yenilerini oluşturmak yerine yeniden kullanılmalıdır. Ancak, uygun renklerin tanımlanmadığı durumlarda uzantı temalarını uyumlu tutmak için özel renkler oluşturulmalıdır.

 **Yeni renk belirteçleri oluşturma**

 Visual Studio uzantısı renk düzenleyicisini kullanarak özel renkler oluşturmak için aşağıdaki adımları izleyin:

1. Yeni renk belirteçleri için kategori ve belirteç adlarını belirleme.

2. Kullanıcı arabirimi öğesinin her tema için kullanacağı kuları ve Yüksek Karşıtlık için sistem rengini seçin.

3. Yeni renk belirteçleri oluşturmak için renk düzenleyicisini kullanın.

4. Visual Studio uzantılı renkleri kullanın.

5. Visual Studio değişiklikleri test edin.

   **1. Adım: yeni renk belirteçleri için kategori ve belirteç adlarını belirleme.**

   Bir Vscrengi için tercih edilen adlandırma şeması **[Category] [UI Type] [State]**. Boş olduğu için Vscrengnames içinde "Color" sözcüğünü kullanmayın.

   Kategori adları mantıksal gruplandırmaları sağlar ve mümkün olduğunca dar olarak tanımlanmalıdır. Örneğin, tek bir araç penceresinin adı bir kategori adı olabilir, ancak tüm iş birimi veya proje ekibinin adı değildir. Girişlerin kategorilere gruplandırılması, aynı ada sahip renkler arasında karışıklık oluşmasını önlemeye yardımcı olur.

   Belirteç adı, öğe türünü ve durumları ya da rengin uygulanacağı "durumu" açıkça göstermelidir. Örneğin, etkin bir veri ipucunun **[UI türü]** "**datatıp**" olarak adlandırılabilir ve **[State]** adı "**etkin**" olarak adlandırılabilir ve bu da "**datatipactive**" renk adına neden olur. Veri ipuçları metin içerdiğinden, hem ön plan hem de arka plan renginin tanımlanması gerekir. Arka plan/ön plan eşleştirmesi kullanarak, renk Düzenleyicisi arka plan için "**Datatipactive**" renkleri ve ön plan Için "**Datatipactivetext**" renklerini otomatik olarak oluşturur.

   Kullanıcı arabirimi parçasının yalnızca bir durumu varsa, adın **[State]** bölümü atlanabilir. Örneğin, bir arama kutusunun kenarlığı varsa ve kenarlığın rengini etkileyebilecek bir durum değişikliği yoksa, kenarlığın renk belirtecinin adı yalnızca "**Searchboxborder**" olarak çağrılabilir.

   Bazı yaygın durum adları şunlardır:

- Etkin

- Etkin değil

- Gelme olayından

- MouseDown

- Seçili

- Odaklı

  Liste öğesi denetiminin bölümleri için birkaç belirteç adı örnekleri:

- Liste

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **2. Adım: UI öğesinin her tema için kullanacağı kuları ve Yüksek Karşıtlık için sistem rengini seçin.**

  Kullanıcı arabirimi için özel renkler ' i seçerken, benzer bir var olan UI öğesini seçin ve renklerini temel olarak kullanın. Kutu içi kullanıcı arabirimi öğelerinin renkleri, gözden geçirme ve test etme işlemleri gerçekleştirdiklerinden, bu sayede uygun ve tüm temalarda doğru şekilde davranır.

  **3. Adım: yeni renk belirteçleri oluşturmak için renk düzenleyicisini kullanın.**

  Renk düzenleyiciyi başlatın ve yeni bir özel tema renkleri .xml dosyası açın veya oluşturun. Menüden **> yeni rengi Düzenle** ' yi seçin. Bu, kategoriyi belirtmek için bir iletişim kutusu açar ve bu kategoride bulunan renk girdileri için bir veya daha fazla ad vardır:

  ![VSıX renk düzenleyici yeni renk](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX Renk Düzenleyicisi Yeni Renk")

  Mevcut bir kategori seçin veya **Yeni Kategori ' yi seçerek yeni** bir kategori oluşturun. Yeni bir kategori adı oluşturarak başka bir iletişim kutusu açılır:

  ![VSıX renk düzenleyici yeni kategori](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX Renk Düzenleyicisi Yeni Kategori")

  Yeni kategori daha sonra **yeni renk** kategorisi açılan menüsünde kullanılabilir hale gelir. Bir kategori seçtikten sonra her yeni renk belirteci için her satır için bir ad girin ve tamamlandığında "Oluştur" u seçin:

  ![VSıX renk Düzenleyicisi yeni renk dolduruldu](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX Renk Düzenleyicisi Yeni Renk Doldurulmuş")

  Renk değerleri, rengin tanımlanmadığını gösteren "none" ile arka plan/ön plan çiftleri içinde gösterilir. Not: bir rengin metin rengi/arka plan rengi çifti yoksa yalnızca arka planın tanımlanması gerekir.

  ![VSıX renk düzenleyici renk değerleri](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX Renk Düzenleyicisi Renk Değerleri")

  Renk belirtecini düzenlemek için, bu belirtecin teması (sütun) için bir renk girişi seçin. Renk değerini, 8 basamaklı ARGB biçiminde bir onaltılık renk değeri yazarak, hücreye bir sistem renk adı girerek veya bir renk sürgüleri kümesi veya sistem renkleri listesi aracılığıyla istenen rengi seçmek için açılan menüyü kullanarak ekleyin.

  ![VSıX renk Düzenleyicisi düzenleme rengi](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX Renk Düzenleyicisi Rengi Düzenleme")

  ![VSıX Color Düzenleyicisi arka planı](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX Renk Düzenleyicisi Arka Planı")

  Metin görüntülemesi gerekmeyen bileşenlerde yalnızca bir renk değeri girin: arka plan rengi. Aksi takdirde, bir eğik çizgiyle ayrılmış şekilde hem arka plan hem de metin rengi için değerler girin.

  Yüksek Karşıtlık için değer girerken, geçerli Windows sistem renk adları girin. Sabit kodlanmış ARGB değerlerini girmeyin. Renk değeri açılan menülerinden "arka plan: sistem" veya "ön plan: sistem" seçeneğini belirleyerek geçerli sistem renk adlarının listesini görüntüleyebilirsiniz. Metin bileşenlerine sahip öğeler oluştururken, doğru arka plan/metin sistemi renk çiftini kullanın veya metin okunamaz durumda olabilir.

  Renk belirteçleri oluşturmayı, ayarlamayı ve düzenlemenizi bitirdiğinizde, bunları istenen .xml veya. pkgdef biçimine kaydedin. Arka plan veya ön plan kümesi olmayan renk belirteçleri, .xml biçiminde boş renkler olarak kaydedilir, ancak. pkgdef biçiminde atılır. Bir. pkgdef dosyasına boş renkler kaydetmeye çalışırsanız, bir iletişim kutusu olası renk kaybından sizi uyarır.

  **4. adım: Visual Studio uzantılı renkleri kullanın.**

  Yeni renk belirteçlerini tanımladıktan sonra, "derleme eylemi" öğesini "Içerik" olarak ayarlanmış ve "VSıX içinde Ekle" olarak "true" olarak ayarlanmış olan proje dosyasına. pkgdef ekleyin.

  ![VSıX renk Düzenleyicisi pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX Renk Düzenleyicisi pkgdef")

  Visual Studio uzantısı renk düzenleyicisinde, WPF tabanlı kullanıcı arabirimindeki özel renklere erişmek için kullanılan kodu görüntülemek için dosya > kaynak kodunu görüntüle ' yi seçin.

  ![VSıX renk düzenleyici kaynak kodu Görüntüleyici](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX Renk Düzenleyicisi Kaynak Kodu Görüntüleyicisi")

  Bu kodu projedeki statik bir sınıfa ekleyin. **Microsoft.VisualStudio.Shell başvurusu. \<VSVersion>.0.dll** **ThemeResourceKey** türünü kullanmak için projeye eklenmiştir.

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

 Bu, XAML kodundaki renklere erişim sağlar ve kullanıcı arabiriminin tema değişikliklerine yanıt vermelerini sağlar.

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

 **5. Adım: Değişiklikleri Visual Studio.**

 Renk düzenleyicisi, uzantı paketini yeniden oluşturmadan renklere yapılan canlı değişiklikleri Visual Studio için renk belirteçlerini geçici olarak çalışan Visual Studio örneklerine uygulayabilir. Bunu yapmak için, her tema sütunlarının üst bilgisinde bulunan "Bu temayı çalışan Visual Studio pencerelere uygula" düğmesine tıklayın. VSIX Renk Düzenleyicisi kapatılan bu geçici temadan uzaklaşacak.

 ![VSIX Renk Düzenleyicisi Uygula](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX Renk Düzenleyicisi Uygula")

 Değişiklikleri kalıcı yapmak için.pkgdef dosyasına yeni renkler ekledikten ve bu renklerin kullanıla kodunu yazdıktan sonra Visual Studio uzantısını yeniden yeniden yapın. Yeni Visual Studio yeniden oluşturma, yeni renkler için kayıt defteri değerlerini temaların geri kalanıyla birleştirecek. Ardından kullanıcı arabirimini Visual Studio kullanıcı arabirimini yeniden kullanın ve yeni renklerin beklendiği gibi görüntülenmiyor olduğunu doğrulayın.

## <a name="notes"></a>Notlar
 Bu araç, önceden var olan Visual Studio temaları için özel renkler oluşturmak veya özel bir temanın renklerini düzenlemek Visual Studio tasarlanmıştır. Tam özel tema Visual Studio için, Visual Studio Uzantısı [Galerisi'nde](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) Visual Studio Tema Düzenleyicisi uzantısını indirin.

## <a name="sample-output"></a>Örnek Çıktı
 **XML renk çıkışı**

 Araç .xml oluşturulan dosya aşağıdakine benzer:

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

 **PKGDEF renk çıkışı**

 Araç tarafından oluşturulan .pkgdef dosyası aşağıdakine benzer:

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

 **C# kaynak anahtarları sarmalayıcı**

 Araç tarafından oluşturulan renk kaynağı anahtarları aşağıdakine benzer:

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

 **WPF kaynak sözlüğü sarmalayıcı**

 Araç **tarafından oluşturulan ResourceDictionary** anahtarları aşağıdakine benzer:

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
