---
title: Manifest from Resources | Microsoft Docs
description: Manifest from Resources Image Service ile kullanmak üzere bir .imagemanifest dosyasına .png veya .xaml dosyaları eklemek için Visual Studio kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f750f61532c3e9c6491698c3d936848243d4979a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626084"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Manifest from Resources aracı, görüntü kaynaklarının (.png veya .xaml dosyaları) listesini alan ve bu görüntülerin Visual Studio Görüntü Hizmeti ile birlikte kullanılmaktadır. Ayrıca, bu araç mevcut bir .imagemanifest'e görüntü eklemek için kullanılabilir. Bu araç, bir üst düzey uzantıya görüntüler için yüksek DPI ve Visual Studio yararlıdır. Oluşturulan .imagemanifest dosyası, bir dosya uzantısının (.vsix) bir parçası olarak Visual Studio ve dağıtılabilir.

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 **Syntax**

 ManifestFromResources /resources: \<Dir1> ; \<Img1> /assembly: \<AssemblyName>\<Optional Args>

 **Bağımsız değişkenler**

|**Anahtar adı**|**Notlar**|**Gerekli veya İsteğe Bağlı**|
|-|-|-|
|/resources|Noktalı virgülle ayrılmış görüntü veya dizin listesi. Bu liste her zaman bildirimde yer alan görüntülerin tam listesini içerir. Yalnızca kısmi bir liste verilirse, dahil edilen girişler kaybolur.<br /><br /> Belirli bir kaynak dosyası bir görüntü şeridi ise, her alt görüntüyü bildirime eklemeden önce araç bunu ayrı görüntülere böler.<br /><br /> Görüntü bir .png dosyası ise, aracın görüntü için doğru öznitelikleri dolduracak şekilde adını şu şekilde biçimlendirmenizi öneririz: \<Name> . \<Width> . \<Height>.png.|Gerekli|
|/assembly|Yönetilen derlemenin adı (uzantı dahil değil) veya kaynakları barındıran yerel derlemenin çalışma zamanı yolu (bildirimin çalışma zamanı konumuyla göreli olarak).|Gerekli|
|/manifest|Oluşturulan .imagemanifest dosyasına verilen ad. Bu, dosyayı farklı bir konumda oluşturmak için mutlak veya göreli bir yol da içerebilir. Varsayılan ad, derleme adıyla eşler.<br /><br /> Varsayılan: \<Current Directory> \\<Assembly \> .imagemanifest|İsteğe Bağlı|
|/guidName|Oluşturulan bildirimde yer alan tüm görüntüler için GUID simgesine verilen ad.<br /><br /> Varsayılan: AssetsGuid|İsteğe Bağlı|
|/rootPath|Yönetilen kaynak URL'leri oluşturmadan önce çıkarılmış olması gereken kök yol. (Bu bayrak, aracın göreli URI yolunu yanlış alan ve kaynakların yüklenemalarına neden olan durumlarda yardımcı olmaktır.)<br /><br /> Varsayılan: \<Current Directory>|İsteğe Bağlı|
|/recursive|Bu bayrağın ayarı araca /resources bağımsız değişkende tüm dizinleri tekrar tekrar aramalarını söyler. Bu bayrağın yok denecek kadar çok dizin araması ile sonuçlandır.|İsteğe Bağlı|
|/isNative|Derleme bağımsız değişkeni yerel derleme için bir yol olduğunda bu bayrağı ayarlayın. Derleme bağımsız değişkeni yönetilen bir derlemenin adı olduğunda bu bayrağı atlar. (Bu bayrak hakkında ek bilgi için Notlar bölümüne bakın.)|İsteğe Bağlı|
|/newGuids|Bu bayrağın ayarı, var olan bildirimden birini birleştirme yerine, aracıya görüntülerin GUID simgesi için yeni bir değer oluşturması söyler.|İsteğe Bağlı|
|/newIds|Bu bayrağın ayarı araca mevcut bildirimden değerleri birleştirme yerine her görüntü için yeni kimlik sembol değerleri oluşturması söyler.|İsteğe Bağlı|
|/noLogo|Bu bayrağın ayarı ürün ve telif hakkı bilgilerini yazdırmayı durdurur.|İsteğe Bağlı|
|/?|Yardım bilgilerini yazdırma.|İsteğe Bağlı|
|/help|Yardım bilgilerini yazdırma.|İsteğe Bağlı|

 **Örnekler**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Notlar

- Araç yalnızca .xaml .png dosyaları destekler. Diğer görüntü veya dosya türleri yoksayılır. Kaynakları ayrıştırırken karşılaşılan tüm desteklenmeyen türler için bir uyarı oluşturulur. Araç kaynakları ayrıştırmayı bitirdikten sonra desteklenen görüntü yoksa bir hata oluşturulur

- Araç, .png görüntüleri için önerilen biçimi takip eden araç, .png boyutu/boyut değerini görüntünün gerçek boyutundan farklı olsa bile belirtilen biçime göre belirler.

- .png için genişlik/yükseklik biçimi atlanabilir, ancak araç görüntünün gerçek genişlik/yükseklik değerini okur ve görüntünün boyut/boyut değeri için bu değerleri kullanır.

- Bu aracı aynı görüntü şeridinde aynı .imagemanifest için birden çok kez çalıştırmanız yinelenen bildirim girişlerine neden olur çünkü araç görüntü şeridini tek başına görüntülere bölmeye ve mevcut bildirime eklemeye çalışır.

- Birleştirme (/newGuids veya /newIds çıkar) yalnızca araç tarafından oluşturulan bildirimlerde yapılabilir. Başka bir şekilde özelleştirilmiş veya oluşturulmuş olan bildirimlerin doğru bir şekilde birleştirilenemleri yok olabilir.

- Yerel derlemeler için oluşturulan bildirimlerin, kimlik sembollerinin yerel derlemenin .rc dosyasındaki kaynak kimlikleri ile eşleşmesi için oluşturma sonrasında el ile düzenlemesi gerekir.

## <a name="sample-output"></a>Örnek Çıktı
 **Basit görüntü bildirimi**

 Bir görüntü bildirimi, bu dosyanın .xml olur:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Görüntü şeridi için görüntü bildirimi**

 Bir görüntü şeridinin görüntü bildirimi, aşağıdaki .xml benzer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Yerel derleme görüntü kaynakları için görüntü bildirimi**

 Yerel görüntüler için bir görüntü bildirimi şu .xml benzer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```
