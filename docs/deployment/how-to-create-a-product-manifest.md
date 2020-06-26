---
title: Nasıl yapılır-ürün bildirimi oluşturma | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0f4302756b089376eca8926453399768faaf58f
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382516"
---
# <a name="how-to-create-a-product-manifest"></a>Nasıl yapılır: Ürün bildirimi oluşturma
Uygulamanız için önkoşulları dağıtmak üzere bir önyükleyici paketi oluşturabilirsiniz. Önyükleyici paketi tek bir ürün bildirim dosyası, ancak her yerel ayar için bir paket bildirimi içerir. Paket bildirimi, paketinizin yerelleştirmeye özgü yönlerini içerir. Buna dizeler, son kullanıcı lisans sözleşmeleri ve dil paketleri dahildir.

 Paket bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Ürün bildirimini oluşturma

#### <a name="to-create-the-product-manifest"></a>Ürün bildirimini oluşturmak için

1. Önyükleyici paketi için bir dizin oluşturun. Bu örnek C:\packagekullanır.

2. Visual Studio 'da *product.xml*adlı yenı bir XML dosyası oluşturun ve *c:\Package* klasörüne kaydedin.

3. Aşağıdaki XML 'i, paketin XML ad alanını ve ürün kodunu tanımlayacak şekilde ekleyin. Ürün kodunu paket için benzersiz bir tanımlayıcı ile değiştirin.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Paketin bir bağımlılığı olduğunu belirtmek için XML ekleyin. Bu örnek Microsoft Windows Installer 3,1 ' de bir bağımlılık kullanır.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Önyükleyici paketindeki tüm dosyaları listelemek için XML ekleyin. Bu örnek *CorePackage.msi*paket dosyası adını kullanır.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. *CorePackage.msi* dosyasını kopyalayın veya *c:\Package* klasörüne taşıyın.

7. Önyükleyici komutlarını kullanarak paketi yüklemek için XML ekleyin. Önyükleyici, sessizce yüklenecek *. msi* dosyasına **/qn** bayrağını otomatik olarak ekler. Dosya bir *. exe*ise, önyükleyici kabuğu kullanarak *. exe* dosyasını çalıştırır. Aşağıdaki XML *CorePackage.msi*için bir bağımsız değişken göstermez, ancak komut satırı bağımsız değişkenini `Arguments` özniteliğe yerleştirebilirsiniz.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Bu Önyükleyici paketinin yüklü olup olmadığını denetlemek için aşağıdaki XML 'i ekleyin. Ürün kodunu yeniden dağıtılabilir bileşen için GUID ile değiştirin.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Önyükleyici bileşeninin zaten yüklü olup olmadığı öğesine bağlı olarak önyükleyici davranışını değiştirmek için XML ekleyin. Bileşen yüklüyse, önyükleyici paketi çalıştırılmaz. Aşağıdaki XML, bu bileşen yönetici ayrıcalıkları gerektirdiğinden geçerli kullanıcının yönetici olup olmadığını denetler.

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

10. Yükleme başarılı olursa ve yeniden başlatma gerekliyse çıkış kodlarını ayarlamak için XML ekleyin. Aşağıdaki XML, önyükleyicinin paketleri yüklemeye devam edemeyeceğini belirten başarısız ve FailReboot çıkış kodlarını gösterir.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Önyükleyici komutlarının bölümünü sonlandırmak için aşağıdaki XML 'i ekleyin.

    ```xml
        </Command>
    </Commands>
    ```

12. *C:\Package* klasörünü Visual Studio önyükleyici dizinine taşıyın. Visual Studio 2010 için bu, *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* dizinidir.

## <a name="example"></a>Örnek
 Ürün bildirimi, özel önkoşullara yönelik yükleme yönergelerini içerir.

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