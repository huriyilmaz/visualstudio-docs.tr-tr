---
title: Manifest from Resources | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea5931c77e267bc6065693be1ae144c250ce6df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536234"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Manifest from Resources Aracı, görüntü kaynakları (. png veya. xaml dosyaları) listesini alan ve bu görüntülerin Visual Studio görüntü hizmeti ile kullanılmasına izin veren bir. ımagemanifest dosyası oluşturan bir konsol uygulamasıdır. Ayrıca, bu araç var olan bir. ımagemanifest öğesine görüntü eklemek için kullanılabilir. Bu araç, Visual Studio uzantısına görüntü için yüksek DPı ve tema desteği eklemek için yararlıdır. Oluşturulan. ımagemanifest dosyası, Visual Studio uzantısının (. vsix) bir parçası olarak içine dahil edilmelidir ve dağıtılmalıdır.

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 **Syntax**

 ManifestFromResources/Resources: \<Dir1> ; \<Img1> /Assembly: \<AssemblyName>\<Optional Args>

 **Arguments**

|**Anahtar adı**|**Notlar**|**Gerekli veya Isteğe bağlı**|
|-|-|-|
|/Resources|Görüntülerin veya dizinlerin noktalı virgülle ayrılmış listesi. Bu liste her zaman bildirimde olacak görüntülerin tam listesini içermelidir. Yalnızca kısmi bir liste verilirse dahil olmayan girişler kaybedilir.<br /><br /> Belirli bir kaynak dosyası bir resim şeridinde ise, araç her bir alt görüntüyü bildirime eklemeden önce onu ayrı görüntülere böler.<br /><br /> Görüntü bir. png dosyası ise, aracın doğru özniteliklerini doldurabilmesi için adı şöyle biçimlendirmeniz önerilir: \<Name> . \<Width> . \<Height> . kitaplığını.|Gerekli|
|/Assembly|Yönetilen derlemenin adı (uzantıyı hariç) veya kaynakları barındıran yerel derlemenin çalışma zamanı yolu (bildirimin çalışma zamanı konumuna göre).|Gerekli|
|/MANIFEST|Oluşturulan. ımagemanifest dosyasına verilecek ad. Bu, dosyayı farklı bir konumda oluşturmak için mutlak veya göreli bir yol da içerebilir. Varsayılan ad, derleme adıyla eşleşir.<br /><br /> Varsayılan: \<Current Directory> \\<Assembly \> . ımagemanifest|İsteğe Bağlı|
|/Gudname|Oluşturulan Bildirimdeki tüm görüntülerin GUID simgesine verilecek ad.<br /><br /> Varsayılan: AssetsGuid|İsteğe Bağlı|
|/rootPath|Yönetilen kaynak URI 'Leri oluşturmadan önce atılması gereken kök yolu. (Bu bayrak, aracın göreli URI yolunu yanlış aldığı ve kaynakların yüklemede başarısız olmasına neden olan durumlarda yardımcı olur.)<br /><br /> Varsayılanını \<Current Directory>|İsteğe Bağlı|
|/recursive|Bu bayrak ayarlandığında, araç,/Resources bağımsız değişkenindeki herhangi bir dizini yinelemeli olarak arayacak şekilde bildirir. Bu bayrağın atlanması, en üst düzey dizin aramasına neden olur.|İsteğe Bağlı|
|/isNative|Derleme bağımsız değişkeni bir yerel derleme için yol olduğunda bu bayrağı ayarlayın. Derleme bağımsız değişkeni yönetilen bir derlemenin adı olduğunda bu bayrağı atlayın. (Bu bayrak hakkında daha fazla bilgi için Notlar bölümüne bakın.)|İsteğe Bağlı|
|/NewGuid 'ler|Bu bayrak ayarlandığında, araç, mevcut bildirimden birini birleştirmek yerine görüntülerin GUID sembolü için yeni bir değer oluşturmasını söyler.|İsteğe Bağlı|
|/Newlar|Bu bayrak ayarlandığında, araç, var olan bildirimdeki değerleri birleştirmek yerine her görüntü için yeni KIMLIK sembol değerleri oluşturmasını söyler.|İsteğe Bağlı|
|/noLogo|Bu bayrak ayarlandığında, ürün ve telif hakkı bilgilerinin yazdırılması durduruluyor.|İsteğe Bağlı|
|/?|Yardım bilgilerini yazdır.|İsteğe Bağlı|
|/help|Yardım bilgilerini yazdır.|İsteğe Bağlı|

 **Örnekler**

- ManifestFromResources/Resources: D:\Images/Assembly: My. Assembly. Name/isNative

- ManifestFromResources/resources:D:\Images\Image1.png;D: \ımages\ımage1.xaml/Assembly: My. Assembly. Name/manifest: Myımagemanifest. ımagemanifest

- ManifestFromResources/resources:D:\Images\Image1.png;D: \ımages\ımage1.xaml/Assembly: My. Assembly. Name/guidName: myImages/NewGuid 'ler/newIds

## <a name="notes"></a>Notlar

- Araç yalnızca. png ve. xaml dosyalarını destekler. Diğer herhangi bir görüntü veya dosya türü yok sayılır. Kaynakları ayrıştırırken karşılaşılan tüm desteklenmeyen türler için bir uyarı oluşturulur. Araç kaynakları ayrıştırmayı bitirdiğinde desteklenen bir görüntü bulunamazsa bir hata oluşturulur

- Araç,. png görüntüleri için önerilen biçimi izleyerek,. png için boyut/boyut değerini görüntünün gerçek boyutundan farklı olsa bile, biçim belirtilen boyuta ayarlar.

- Genişlik/yükseklik biçimi. png görüntüleri için atlanabilir, ancak araç görüntünün gerçek genişlik/yüksekliğini okur ve görüntünün boyut/boyut değeri için bunları kullanır.

- Bu aracın aynı görüntüde birden çok kez çalıştırılması aynı. ımagemanifest, görüntü şeridinin tek başına görüntülere ayrılmaya ve var olan bildirime eklemesini denetiğinden yinelenen bildirim girişlerine neden olur.

- Birleştirme (/NewGuid 'ler veya/newIds) yalnızca araç tarafından oluşturulan bildirimler için yapılmalıdır. Özelleştirilmiş veya diğer yollarla oluşturulan bildirimler doğru birleştirilmeyebilir.

- Yerel derlemeler için oluşturulan bildirimlerin, KIMLIK simgelerinin yerel derlemenin. rc dosyasından kaynak kimlikleriyle eşleşmesini sağlamak için kuşak olduktan sonra el ile düzenlenmesi gerekebilir.

## <a name="sample-output"></a>Örnek Çıktı
 **Basit görüntü bildirimi**

 Bir görüntü bildirimi bu. xml dosyasına benzer olacaktır:

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

 **Resim şeridi için görüntü bildirimi**

 Bir resim şeridinin görüntü bildirimi bu. xml dosyasına benzer olacaktır:

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

 **Yerel derleme görüntüsü kaynakları için görüntü bildirimi**

 Yerel görüntüler için bir görüntü bildirimi, bu. xml dosyasına benzer olacaktır:

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
