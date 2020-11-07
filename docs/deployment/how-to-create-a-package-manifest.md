---
title: Paket bildirimi oluşturma | Microsoft Docs
description: Her yerel ayar için bir paket bildirimi içeren ClickOnce uygulamanız için önkoşulları dağıtmak üzere bir önyükleyici paketi kullanma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43790914be67ddaf2e82f1bb411180d5643ebcbe
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350055"
---
# <a name="how-to-create-a-package-manifest"></a>Nasıl yapılır: Paket bildirimi oluşturma
Uygulamanıza yönelik önkoşulları dağıtmak için bir önyükleyici paketi kullanabilirsiniz. Önyükleyici paketi tek bir ürün bildirim dosyası, ancak her yerel ayar için bir paket bildirimi içerir. Farklı yerelleştirilmiş sürümler genelinde paylaşılan işlevsellik ürün bildirimine gitmelidir.

 Ürün bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Paket bildirimini oluşturma

#### <a name="to-create-the-package-manifest"></a>Paket bildirimi oluşturmak için

1. Önyükleyici paketi için bir dizin oluşturun. Bu örnekte *C:\Package* kullanılmaktadır.

2. Yerel ayar adına sahip bir alt dizin oluşturun *(örneğin, İngilizce için)* .

3. Visual Studio 'da, *package.xml* ADLı bir XML dosyası oluşturun ve *C:\package\en* klasörüne kaydedin.

4. Önyükleyici paketinin adını, bu yerelleştirilmiş paket bildirimi için kültürü ve isteğe bağlı lisans sözleşmesini listelemek için XML ekleyin. Aşağıdaki XML, `DisplayName` ve `Culture` daha sonraki bir öğesinde tanımlanan değişkenleri kullanır.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Yerel ayara özgü dizindeki tüm dosyaları listelemek için XML ekleyin. Aşağıdaki XML, **en** yerel ayar için geçerli olan *eula.txt* adında bir dosya kullanır.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Önyükleyici paketi için yerelleştirilebilir dizeler tanımlamak üzere XML ekleyin. Aşağıdaki XML, **en** yerel ayar için hata dizelerini ekler.

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. *C:\Package* klasörünü Visual Studio önyükleyici dizinine kopyalayın. Visual Studio 2010 için bu, *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* dizinidir.

## <a name="example"></a>Örnek
 Paket bildirimi, hata iletileri, yazılım lisans koşulları ve dil paketleri gibi yerel ayara özgü bilgiler içerir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)