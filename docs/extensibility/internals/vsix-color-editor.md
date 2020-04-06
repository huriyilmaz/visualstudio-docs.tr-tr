---
title: VSIX Renk Editörü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704039"
---
# <a name="vsix-color-editor"></a>VSIX Renk Düzenleyicisi
Visual Studio Extension Color Editor aracı Visual Studio için özel renkler oluşturabilir ve düzenleme yapabilir. Araç, renklerin kodda kullanılabileceğini bilmek için tema kaynağı anahtarları da oluşturabilir. Bu araç, temalama destekleyen bir Visual Studio uzantısı için renk yapmak için yararlıdır. Bu araç .pkgdef ve .xml dosyalarını açabilir. Visual Studio temaları (.vstheme dosyaları) dosya uzantısını .xml olarak değiştirerek Visual Studio Extension Color Editor ile kullanılabilir. Ayrıca, .vstheme dosyaları geçerli bir .xml dosyasına içe aktarılabilir.

 ![VSIX Renk Editörü Kahraman](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX Renk Editörü Kahraman")

 **Paket tanımı dosyaları**

 Paket tanımı (.pkgdef) dosyaları temaları tanımlayan dosyalardır. Renklerin kendileri bir .pkgdef dosyasında derlenen tema rengi .xml dosyalarında saklanır. .pkgdef dosyaları Visual Studio'da aranabilir konumlara dağıtılır, çalışma zamanında işlenir ve temaları tanımlamak için birleştirilir.

 **Renk belirteçleri**

 Renk belirteci dört öğeden oluşur:

- **Kategori adı:** Bir renk kümesi için mantıksal bir gruplama. İstenilen Kullanıcı Arabirimi öğesine veya Kullanıcı Arabirimi öğeleri grubuna özgü zaten renkler varsa varolan bir kategori adı kullanın.

- **Belirteç adı:** Renk belirteci ve belirteç kümeleri için açıklayıcı bir ad. Kümeler, tüm durumlarının yanı sıra arka plan ve ön plan (metin) belirteç adlarını da içerir ve bu adlar, başvurdukları çiftleri ve durumları kolayca tanımlayabilmek için adlandırılmalıdır.

- **Renk değerleri (veya tonları):** Her renkli tema için gerekli. Her zaman çift olarak arka plan ve metin renk değerleri oluşturun. Renkler arka plan/ön plan için eşleştirilebilir, böylece metin (ön plan) rengi çizildiği arka plan rengiyle her zaman okunabilir. Bu renkler birbirine bağlıdır ve ui'de birlikte kullanılacaktır. Arka plan metinle kullanılmak üzere tasarlanmamışsa, ön plan rengi tanımlamayın.

- **Sistem renk adı:** Yüksek kontrastlı ekranlarda kullanım için.

## <a name="how-to-use-the-tool"></a>Aracı nasıl kullanılır?
 Mümkün olduğunca, ve uygun olduğunda, mevcut Visual Studio renkleri yerine yenilerini yapmak yeniden kullanılmalıdır. Ancak, uygun renklerin tanımlanmamış olduğu durumlarda, uzantı temasını uyumlu tutmak için özel renkler oluşturulmalıdır.

 **Yeni renk belirteçleri oluşturma**

 Visual Studio Extension Color Editor'ı kullanarak özel renkler oluşturmak için aşağıdaki adımları izleyin:

1. Yeni renk belirteçleri için kategori ve belirteç adlarını belirleyin.

2. Yüksek Karşıtlık için her tema ve sistem rengi için UI öğesinin kullanacağı tonları seçin.

3. Yeni renk belirteçleri oluşturmak için renk düzenleyicisini kullanın.

4. Visual Studio uzantısındarenkleri kullanın.

5. Visual Studio'daki değişiklikleri test edin.

   **Adım 1: Yeni renk belirteçleri için kategori ve belirteç adlarını belirleyin.**

   VSColor için tercih edilen adlandırma düzeni **[Kategori] [UI türü] [Durum]** olur. Gereksiz olduğu için VSColor adlarında "renk" sözcüğü kullanmayın.

   Kategori adları mantıksal gruplandırmalar sağlar ve mümkün olduğunca dar bir şekilde tanımlanmalıdır. Örneğin, tek bir araç penceresinin adı bir kategori adı olabilir, ancak tüm bir iş biriminin veya proje ekibinin adı değil. Girişleri kategorilere gruplandırmak, aynı ada sahip renkler arasındaki karışıklığı önlemeye yardımcı olur.

   Belirteç adı, öğe türünü ve durumları veya rengin uygulanacağı "durum"u açıkça belirtmelidir. Örneğin, etkin bir veri ipucunun **[UI türü]** "**DataTip**" olarak adlandırılabilir ve **[Durum]** "**Active**" olarak adlandırılabilir ve bu da "**DataTipActive"** renk adı ile sonuçlanabilir. Veri ipuçları metin olduğundan, hem ön plan hem de arka plan renginin tanımlanması gerekir. Renk düzenleyicisi arka plan için "**DataTipActive**" ve ön plan için "**DataTipActiveText**" renklerini otomatik olarak oluşturur.

   Kullanıcı Arabirimi'nin yalnızca bir durumu varsa, adın **[Durum]** bölümü atlanabilir. Örneğin, bir arama kutusunun kenarlığı varsa ve kenarlığı etkileyecek bir durum değişikliği yoksa, kenarlık renk belirteci adı basitçe **"SearchBoxBorder"** olarak adlandırılabilir.

   Bazı yaygın durum adları şunlardır:

- Etkin

- Etkin değil

- Mouseover

- Mousedown

- Seçildi

- Odaklı

  Liste öğesi denetiminin bölümleri için birkaç belirteç adı örnekleri:

- Listıtem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelected

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **Adım 2: Yüksek Karşıtlık için her tema ve sistem rengi için UI öğesinin kullanacağı tonları seçin.**

  Kullanıcı Arabirimi için özel renkler seçerken, benzer bir varolan Kullanıcı Arabirimi öğesi seçin ve renklerini temel olarak kullanın. In-the-box UI öğeleri için renkler inceleme ve test uğramıştır, bu yüzden uygun görünecek ve tüm temalar doğru şekilde çalışacaktır.

  **Adım 3: Yeni renk belirteçleri oluşturmak için renk düzenleyicisini kullanın.**

  Renk düzenleyicisini başlatın ve yeni bir özel tema renkleri .xml dosyasını açın veya oluşturun. Menüden **Yeni Renk > Edit'i** seçin. Bu, kategoriyi ve bu kategorideki renk girişleri için bir veya daha fazla ad belirtmek için bir iletişim kutusu açar:

  ![VSIX Renk Editörü Yeni Renk](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX Renk Editörü Yeni Renk")

  Varolan bir kategori seçin veya yeni bir kategori oluşturmak için **Yeni Kategori'yi** seçin. Yeni bir kategori adı oluşturarak başka bir iletişim kutusu açılır:

  ![VSIX Renk Editörü Yeni Kategori](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX Renk Editörü Yeni Kategori")

  Yeni kategori daha sonra **Yeni Renk** kategorisi açılır menüsünde kullanılabilir hale gelecektir. Bir kategori seçtikten sonra, her yeni renk belirteci için satır başına bir ad girin ve tamamlandığında "Oluştur"u seçin:

  ![VSIX Renk Editörü Yeni Renk Dolu](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX Renk Editörü Yeni Renk Dolu")

  Renk değerleri arka plan/ön plan çiftleri olarak gösterilir ve rengin tanımlanmadığını belirten "Yok" gösterilir. Not: Bir renk metin rengi/arka plan renk çifti yoksa, yalnızca arka planın tanımlanması gerekir.

  ![VSIX Renk Düzenleyicirenk Değerleri](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX Renk Düzenleyicirenk Değerleri")

  Renk belirteci ni nde bir renk belirteci ni diseetmek için, bu belirteç temasını (sütunu) için bir renk girişi seçin. 8 haneli ARGB biçiminde bir hex renk değeri yazarak, hücreye bir sistem renk adı girerek veya bir renk kaydırıcıkümesi veya sistem renkleri listesi aracılığıyla istenen rengi seçmek için açılır menüyü kullanarak renk değerini ekleyin.

  ![VSIX Renk Editörü Renk Edit](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX Renk Editörü Renk Edit")

  ![VSIX Renk Düzenleyici arka planı](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX Renk Düzenleyici arka planı")

  Metni görüntülemesi gerekmeyen bileşenler için yalnızca bir renk değeri girin: arka plan rengi. Aksi takdirde, hem arka plan hem de metin rengi için değerleri girin, ileri eğik çizgi ile ayrılmış.

  Yüksek Karşıtlık için değerler girerken, geçerli Windows sistem renk adlarını girin. Kodlanmış ARGB değerlerini girmeyin. Renk değeri açılır menülerden "Arka Plan: Sistem" veya "Foreground: System" seçeneğini seçerek geçerli sistem renk adlarının listesini görüntüleyebilirsiniz. Metin bileşenlerine sahip öğeler oluştururken, doğru arka plan/metin sistemi renk çiftini kullanın veya metin okunamayabilir.

  Renk belirteçlerini oluşturmayı, ayarlamayı ve düzenlemeyi bitirdiğinizde, bunları istenilen .xml veya .pkgdef biçimine kaydedin. Arka plan veya ön plan kümesi olmayan renk belirteçleri .xml formatında boş renk olarak kaydedilir, ancak .pkgdef biçiminde atılır. Boş renkleri .pkgdef dosyasına kaydetmeye çalışırsanız, bir iletişim kutusu sizi olası renk kaybına karşı uyarır.

  **Adım 4: Visual Studio uzantısındaki renkleri kullanın.**

  Yeni renk belirteçleri tanımladıktan sonra, "İçerik" olarak ayarlanmış "Eylem Oluştur" ve "VSIX'ye Ekle" ile "Doğru" olarak ayarlanmış proje dosyasına .pkgdef'i ekleyin.

  ![VSIX Renk Editörü pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX Renk Editörü pkgdef")

  Visual Studio Extension Color Editor'da, WPF tabanlı kullanıcı arabirimi'ndeki özel renklere erişmek için kullanılan kodu görüntülemek için Dosya > Kaynak Kodunu Görüntüleyin'i seçin.

  ![VSIX Renk Düzenleyicikaynak Kodu Görüntüleyici](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX Renk Düzenleyicikaynak Kodu Görüntüleyici")

  Bu kodu projeye statik bir sınıfa ekleyin. **Microsoft.VisualStudio.Shell için bir\< başvuru. VSVersion>.0.dll** **ThemeResourceKey** türünü kullanmak için projeye eklenmesi gerekir.

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

 Bu, XAML kodundaki renklere erişim sağlar ve Kullanıcı Birsonucu'nun tema değişikliklerine yanıt vermesine olanak tanır.

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

 **Adım 5: Visual Studio değişiklikleri test edin.**

 Renk düzenleyicisi, uzantı paketini yeniden oluşturmadan renklerdeki canlı değişiklikleri görüntülemek için Visual Studio'nun çalışan örneklerine geçici olarak renk belirteçleri uygulayabilir. Bunu yapmak için, her tema sütununun üstbilgide bulunan "Bu temayı Visual Studio pencerelerini çalıştırana uygula" düğmesini tıklatın. VSIX Renk Düzenleyicisi kapatıldığında bu geçici tema ortadan kaldırAcaktır.

 ![VSIX Renk Editörü Uygula](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX Renk Editörü Uygula")

 Değişiklikleri kalıcı hale getirmek için,.pkgdef dosyasına yeni renkler ekledikten ve bu renkleri kullanacak kodu yazdıktan sonra Visual Studio uzantısını yeniden oluşturup yeniden dağıtın. Visual Studio uzantısıyeniden temaların geri kalanı ile yeni renkler için kayıt defteri değerlerini birleştirir. Ardından Visual Studio'yu yeniden başlatın, UI'yi görüntüleyin ve yeni renklerin beklendiği gibi göründüğünü doğrulayın.

## <a name="notes"></a>Notlar
 Bu araç, önceden varolan Visual Studio temaları için özel renkler oluşturmak veya özel bir Visual Studio temasının renklerini düzenlemek için kullanılmak üzere tasarlanmıştır. Tam özel Visual Studio temaları oluşturmak için [Visual Studio Color Theme Editor uzantısını](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) Visual Studio Extensions Gallery'den indirin.

## <a name="sample-output"></a>Örnek Çıktı
 **XML renk çıkışı**

 Araç tarafından oluşturulan .xml dosyası buna benzer olacaktır:

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

 Araç tarafından oluşturulan .pkgdef dosyası buna benzer olacaktır:

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

 **C# kaynak anahtarları sarıcı**

 Araç tarafından oluşturulan renk kaynağı anahtarları buna benzer olacaktır:

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

 **WPF kaynak sözlük sarıcı**

 Araç tarafından oluşturulan renk **KaynakSözlüğü** anahtarları buna benzer olacaktır:

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
