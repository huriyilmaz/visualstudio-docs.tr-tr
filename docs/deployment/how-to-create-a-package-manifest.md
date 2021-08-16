---
title: Paket Bildirimi Oluşturma | Microsoft Docs
description: Önkoşulları dağıtmak için önkoşulları her yerel ClickOnce paket bildirimi içeren bir önyükleyici paketi kullanmayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 077926f3e2649a9e3fa49d39168e89e73c0af9fd313afe32bbfd8c20602d7609
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435497"
---
# <a name="how-to-create-a-package-manifest"></a>Nasıl yapılır: Paket bildirimi oluşturma
Uygulamanıza önkoşulları dağıtmak için önyükleyici paketi kullanabilirsiniz. Önyükleyici paketi tek bir ürün bildirim dosyası ama her yerel bölge için bir paket bildirimi içerir. Farklı yerelleştirilmiş sürümler arasında paylaşılan işlevler ürün bildirimine gir gerekir.

 Ürün bildirimleri hakkında daha fazla bilgi için [bkz. Nasıl? Ürün bildirimi oluşturma.](../deployment/how-to-create-a-product-manifest.md)

## <a name="create-the-package-manifest"></a>Paket bildirimini oluşturma

#### <a name="to-create-the-package-manifest"></a>Paket bildirimini oluşturmak için

1. Önyükleyici paketi için bir dizin oluşturun. Bu örnek *C:\package kullanır.*

2. İngilizce için *en* gibi yerel dil adı ile bir alt dizin oluşturun.

3. Bu Visual Studio,package.xmladlı bir XML ** dosyası oluşturun ve *C:\package\en klasörüne* kaydedin.

4. Önyükleyici paketinin adını, bu yerelleştirilmiş paket bildiriminin kültürünü ve isteğe bağlı lisans anlaşmasını listeleye XML ekleyin. Aşağıdaki XML, daha sonraki `DisplayName` bir `Culture` öğede tanımlanan ve değişkenlerini kullanır.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Yerele özgü dizinde yer alan tüm dosyaları listeleye XML ekleyin. Aşağıdaki XML, en yerel için *geçerlieula.txt* adlı bir **dosya** kullanır.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Önyükleyici paketi için yerelleştirilebilir dizeler tanımlamak üzere XML ekleyin. Aşağıdaki XML, en yerel için hata **dizelerini** ekler.

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

7. *C:\package klasörünü* Visual Studio önyükleyici dizinine kopyalayın. 2010'Visual Studio için *bu\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages dizinidir.*

## <a name="example"></a>Örnek
 Paket bildirimi hata iletileri, yazılım lisans koşulları ve dil paketleri gibi yerele özgü bilgiler içerir.

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