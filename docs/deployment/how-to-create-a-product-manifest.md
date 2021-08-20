---
title: Ürün Bildirimi Oluşturma | Microsoft Docs
description: Tek bir ürün bildirimi ve her yerel ClickOnce paket bildirimi içeren bir paketle uygulamanızın önkoşullarını dağıtmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e58dbabb15b0d0a3643b38693d614aaf16a4a60c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160744"
---
# <a name="how-to-create-a-product-manifest"></a>Nasıl: Ürün bildirimi oluşturma
Uygulamanıza önkoşulları dağıtmak için bir önyükleyici paketi oluşturabilirsiniz. Önyükleyici paketi tek bir ürün bildirim dosyası ama her yerel bölge için bir paket bildirimi içerir. Paket bildirimi, paketinizin yerelleştirmeye özgü yönlerini içerir. Bu dizeleri, son kullanıcı lisans sözleşmelerini ve dil paketlerini içerir.

 Paket bildirimleri hakkında daha fazla bilgi için [bkz. Nasıl: Paket bildirimi oluşturma.](../deployment/how-to-create-a-package-manifest.md)

## <a name="create-the-product-manifest"></a>Ürün bildirimini oluşturma

#### <a name="to-create-the-product-manifest"></a>Ürün bildirimini oluşturmak için

1. Önyükleyici paketi için bir dizin oluşturun. Bu örnek C:\package kullanır.

2. Bu Visual Studio,product.xmladlı yeni ** bir XML dosyası oluşturun ve *C:\package klasörüne* kaydedin.

3. Paketin XML ad alanını ve ürün kodunu açıklamak için aşağıdaki XML'yi ekleyin. Ürün kodunu paket için benzersiz bir tanımlayıcıyla değiştirin.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Paketin bir bağımlılığı olduğunu belirtmek için XML ekleyin. Bu örnekte, Microsoft Windows Installer 3.1'e bağımlılık 2.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Önyükleyici paketinde yer alan tüm dosyaları listeleye XML ekleyin. Bu örnekte, paket dosyası adı *CorePackage.msi.*

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. CorePackage.msi *C:\package klasörüne* kopyalayın veya taşıyın. 

7. Önyükleyici komutlarını kullanarak paketi yüklemek için XML ekleyin. Önyükleyici, **/qn bayrağını** *.msi* olarak yüklenir. Dosya bir *.exe* ise, önyükleyici.exe *kabuğunu* kullanarak dosyayı çalıştırır. Aşağıdaki XML, komut satırı ** CorePackage.msibağımsız değişkenlerini gösterir, ancak komut satırı bağımsız değişkenlerini özniteliğine `Arguments` koyabilirsiniz.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Bu önyükleyici paketinin yüklü olup olduğunu kontrol etmek için aşağıdaki XML'yi ekleyin. Yeniden dağıtılabilir bileşen için ürün kodunu GUID ile değiştirin.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Önyükleyici bileşeninin zaten yüklü olup bu duruma bağlı olarak önyükleyici davranışını değiştirmek için XML ekleyin. Bileşen yüklüyse önyükleyici paketi çalıştırlanmaz. Aşağıdaki XML, bu bileşen yönetim ayrıcalıkları gerektirdiği için geçerli kullanıcının yönetici olup olduğunu denetler.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. Yükleme başarılı olursa ve yeniden başlatma gerekiyorsa çıkış kodlarını ayarlamak için XML ekleyin. Aşağıdaki XML, önyükleyicinin paketleri yüklemeye devam edeceğini belirten Fail ve FailReboot çıkış kodlarını gösteriyor.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Önyükleyici komutlarının bölümünü sona ert için aşağıdaki XML'yi ekleyin.

    ```xml
        </Command>
    </Commands>
    ```

12. *C:\package klasörünü* Visual Studio önyükleyici dizinine taşıma. 2010'Visual Studio için *bu\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages dizinidir.*

## <a name="example"></a>Örnek
 Ürün bildirimi, özel önkoşullar için yükleme yönergelerini içerir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Custom.Bootstrapper.Package">

  <RelatedProducts>
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
  </RelatedProducts>

  <PackageFiles>
    <PackageFile Name="CorePackage.msi"/>
  </PackageFiles>

  <InstallChecks>
    <MsiProductCheck Product="IsMsiInstalled"
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
  </InstallChecks>

  <Commands>
    <Command PackageFile="CorePackage.msi" Arguments="">

      <InstallConditions>
        <BypassIf Property="IsMsiInstalled"
          Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
          Compare="ValueNotEqualTo" Value="True"
         String="NotAnAdmin"/>
      </InstallConditions>

      <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
      </ExitCodes>
    </Command>
  </Commands>
</Product>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)