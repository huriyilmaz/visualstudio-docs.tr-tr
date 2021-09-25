---
title: Özel Galeri için VSIX akışı oluşturma | Microsoft Docs
description: VSıX kullanarak VSIX akışı oluşturmayı ve özel galeri 'de akışı kullanmayı öğrenin.
ms.date: 08/19/2021
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
author: anva
ms.author: anva
manager: tinali
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b5925da18b5d55cc7e5c5c7f77b61a1a97e4962f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128436026"
---
# <a name="how-to-create-the-atom-feed-vsixfeed-for-visual-studio-private-galleries-using-vsixutil"></a>nasıl yapılır: valtutil kullanarak özel galeriler Visual Studio için ATOM akışı (valtfeed) oluşturma
ATOM akışı oluşturmak için Visual Studio vssdk komut satırı yardımcı programı aracını kullanabilirsiniz, bkz. [özel galeriler](../extensibility/private-galleries.md)  

```csharp
VsixUtil  createVsixFeed 
```


## <a name="syntax"></a>Söz dizimi

```csharp
VSIXUtil createVsixFeed -source [sourceValue] -output [outputValue]– filename [fileNameValue] -title [titleValue] – recursive – ignoreErrors  
```

## <a name="arguments"></a>Bağımsız değişkenler

| Parametre | Açıklama |
|---------|-------|
| -Kaynak | Dizin VSıX dosyalarını içerir.  |
| -çıkış | çıkış dizini.  |
| -yinelemeli | Geçerli dizini ve tüm alt dizinlerini bir VSıX arama işleminde içerir.  |
| -IgnoreErrors | VSıX arama işleminde geçersiz bir VSıX öğesini yoksayın.  |
| -Dosya adı | VSıX akışı için dosya adı.  |
| -Başlık | VSıX akışı için başlık. |

## <a name="examples"></a>Örnekler 

* *C:\Extensions* konumundan VSIX dosyalarını arayın ve bu akışı *c:\Extensions* konumunda oluşturun. 

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions 
    ``` 

* *C:\Extensions* konumundan VSIX dosyalarında arama yapın, akışı *c:\Extensions* konumunda oluşturun ve geçersiz VSIX dosyalarını (varsa) atlayın. 

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions -ignoreErrors 
    ``` 
    Bu komut, akışa geçersiz VSıX dosyalarını dahil etmez. 
 

* *C:\Extensions* ve tüm alt dizinlerindeki VSIX dosyalarında arama yapın, ardından akışı *c:\Extensions* konumunda oluşturun. 

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions  -recursive 
    ``` 

* *C:\Extensions* konumundan VSIX dosyalarını arayın ve `PreProdFeed` *c:\Extensions* konumunda akış adını oluşturun.  

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions -ignoreErrors  -recursive -fileName "PreProdFeed"
    ```

* Aracını VSıX dosyalarının bulunduğu dizin altında çalıştırabilir ve ardından akışı aynı konumda oluşturmak için aşağıdaki komutu çalıştırabilirsiniz. 

    ```csharp
    VsixUtil createVsixFeed 
    ```

* Yerel depodan bir akış oluşturun, örneğin, *C:\localextensionprojectrepo* 
 
    ```csharp
    VsixUtil createVsixFeed –source c:\localExtensionProjectRepo -recursive 
    ```

   
Valtutil aracının Install location 'ı *{vs Install Path} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixUtil.exe*. Ayrıca VSıX yardımcı programını içeren [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) 'un en son sürümünü indirebilirsiniz.
    

## <a name="faq"></a>SSS

* Komut tarafından oluşturulan akış konumunu nasıl bulabilirim `VsixUtil createVsixFeed` ? 
    Akışın konumunu komutun çıktısından bulabilirsiniz. 

    Örneğin, `VSIX Feed '<OutPutDirectory>\AtomFeed.xml' created successfully. `

* Hata kodu alıyorum `VsixFeed0001` , ne anlama geliyor ve bunu nasıl giderebilirim?  
    Kaynak geçersiz VSIX dosyaları içerdiği anlamına gelir, geçersiz dosyayı kaynak konumundan kaldırabilir ya da `-ignoreErrors` geçersiz dosyayı atlamak için bağımsız değişkenini kullanabilirsiniz.
    

## <a name="example-of-vsix-entry"></a>VSıX girişi örneği

```xml
<Vsix> 
 <Id></Id> 
 <Version></Version> 
 <References />
 <Rating xsi:nil="true" /> 
 <RatingCount xsi:nil="true" /> 
 <DownloadCount xsi:nil="true" /> 
 <Installations> 
  <Identifier></Identifier> 
  <VersionRange></VersionRange>
  <ProductArchitecture></ProductArchitecture>
 </Installations> 
</Vsix> 
```

## <a name="see-also"></a>Ayrıca bkz.
- [Özel galeriler](../extensibility/private-galleries.md)
