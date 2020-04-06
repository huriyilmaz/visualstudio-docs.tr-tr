---
title: Kaynaklardan Bildirim | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707272"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Kaynaklardan Bildirim aracı, görüntü kaynaklarının (.png veya .xaml dosyaları) listesini alan ve bu görüntülerin Visual Studio Image Service ile kullanılmasını sağlayan bir .imagemanifest dosyası oluşturan bir konsol uygulamasıdır. Ayrıca, bu araç varolan bir .imagemanifest'e resim eklemek için kullanılabilir. Bu araç, Visual Studio uzantısına yüksek DPI ve görüntüler için temalı destek eklemek için yararlıdır. Oluşturulan .imagemanifest dosyası visual studio uzantısı (.vsix) bir parçası olarak dahil edilmeli ve dağıtılmalıdır.

## <a name="how-to-use-the-tool"></a>Aracı nasıl kullanılır?
 **Sözdizimi**

 ManifestFromResources /resources:\<Dir1>; \<Img1> /assembly:\< \<AssemblyName> İsteğe Bağlı Args>

 **Bağımsız Değişkenler**

||||
|-|-|-|
|**Anahtar adı**|**Notlar**|**Gerekli veya İsteğe Bağlı**|
|/kaynaklar|Görüntülerin veya dizinlerin yarı sütunlu sınırlı listesi. Bu liste her zaman bildirimde yer alacak görüntülerin tam listesini içermelidir. Yalnızca kısmi bir liste verilirse, dahil olmayan girişler kaybolur.<br /><br /> Belirli bir kaynak dosyası bir görüntü şeridiyse, araç her alt resmi bildirime eklemeden önce onu ayrı görüntülere böler.<br /><br /> Resim bir .png dosyasıysa, aracın görüntü için doğru öznitelikleri doldurabilmesi için adı bu \<şekilde biçimlendirmenizi tavsiye ederiz: Ad>. \<Genişlik>. \<Yükseklik>.png.|Gerekli|
|/montaj|Yönetilen derlemenin adı (uzantı dahil değil) veya kaynakları barındıran yerel derlemenin çalışma zamanı yolu (bildirimin çalışma zamanı konumuna göre).|Gerekli|
|/manifesto|Oluşturulan .imagemanifest dosyasına verilen ad. Bu, dosyayı farklı bir konumda oluşturmak için mutlak veya göreceli bir yol da içerebilir. Varsayılan ad derleme adıyla eşleşir.<br /><br /> Varsayılan: \<Geçerli Dizin \\ \>><Derleme .imagemanifest|İsteğe bağlı|
|/guidName|Oluşturulan bildirimdeki tüm görüntüler için GUID simgesine verilen ad.<br /><br /> Varsayılan: AssetsGuid|İsteğe bağlı|
|/rootPath|Yönetilen kaynak URI'leri oluşturmadan önce sökülmesi gereken kök yol. (Bu bayrak, aracın göreli URI yolunu yanlış aldığı ve kaynakların yüklenmemesine neden olan durumlarda yardımcı olmak içindir.)<br /><br /> Varsayılan: \<Geçerli Dizin>|İsteğe bağlı|
|/özyinelemeli|Bu bayrağı ayarlamak, aracı /kaynaklar bağımsız değişkenindeki dizinleri özyinelemeli olarak aramasını söyler. Bu bayrağın atlanması, yalnızca en üst düzey dizinlerde arama yla sonuçlanır.|İsteğe bağlı|
|/isNative|Derleme bağımsız değişkeni yerel derleme için bir yol olduğunda bu bayrağı ayarlayın. Derleme bağımsız değişkeni yönetilen bir derlemenin adı olduğunda bu bayrağı atla. (Bu bayrak hakkında ek bilgi için Notlar bölümüne bakın.)|İsteğe bağlı|
|/newGuids|Bu bayrağı ayarlamak, aracı varolan bildirimden birleştirmek yerine görüntülerin GUID simgesi için yeni bir değer oluşturmasını söyler.|İsteğe bağlı|
|/newIds|Bu bayrağı ayarlamak, aracı varolan bildirimden değerleri birleştirmek yerine her görüntü için yeni kimlik simgesi değerleri oluşturmasını söyler.|İsteğe bağlı|
|/noLogo|Bu bayrağı ayarlamak, ürün ve telif hakkı bilgilerinin yazdırılmalarını durdurur.|İsteğe bağlı|
|/?|Yardım bilgilerini yazdırın.|İsteğe bağlı|
|/help|Yardım bilgilerini yazdırın.|İsteğe bağlı|

 **Örnekler**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Notlar

- Araç yalnızca .png ve .xaml dosyalarını destekler. Diğer görüntü veya dosya türleri yoksayılır. Kaynakları ayrıştırırken karşılaşılan tüm desteklenmeyen türler için bir uyarı oluşturulur. Araç kaynakları ayrıştırma tamamlandığında desteklenen görüntü bulunmazsa, bir hata oluşturulur

- .png görüntüleri için önerilen biçimi izleyerek, araç .png'nin boyut/boyut değerini görüntünün gerçek boyutundan farklı olsa bile biçim belirtilen boyuta ayarlar.

- Genişlik/yükseklik biçimi .png görüntüler için atlanabilir, ancak araç görüntünün gerçek genişliğini/yüksekliğini okur ve görüntünün boyut/boyut değeri için bunları kullanır.

- Araç görüntü şeridini bağımsız görüntülere bölmeye ve bunları varolan bildirime eklemeye çalıştığından, bu aracı aynı görüntü şeridinde aynı .imagemanifest için birden çok kez çalıştırmak yinelenen bildirim girişlerine neden olur.

- Birleştirme (atlayan /newGuids veya /newIds) yalnızca araç oluşturulan bildirimler için yapılmalıdır. Özelleştirilen veya başka yollarla oluşturulan bildirimler doğru şekilde birleştirilemeyebilir.

- Yerel derlemeler için oluşturulan bildirimlerin, kimlik sembollerinin yerel derlemenin .rc dosyasındaki kaynak kimlikleriyle eşleşmesini sağlamak için nesilden sonra elle düzenlenmesi gerekebilir.

## <a name="sample-output"></a>Örnek Çıktı
 **Basit görüntü bildirimi**

 Bir görüntü bildirimi bu .xml dosyasına benzer olacaktır:

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

 Görüntü şeridi için bir görüntü manifestosu bu .xml dosyasına benzer olacaktır:

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

 **Yerel montaj görüntü kaynakları için görüntü bildirimi**

 Yerel görüntüler için bir görüntü manifestosu bu .xml dosyasına benzer olacaktır:

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
