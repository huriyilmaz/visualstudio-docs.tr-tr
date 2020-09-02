---
title: 'Nasıl yapılır: Ürün bildirimi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73e2c3f2c9736fd762a9e763827ed641ea5069f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153822"
---
# <a name="how-to-create-a-product-manifest"></a>Nasıl yapılır: Ürün Bildirimi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanız için önkoşulları dağıtmak üzere bir önyükleyici paketi oluşturabilirsiniz. Önyükleyici paketi tek bir ürün bildirim dosyası, ancak her yerel ayar için bir paket bildirimi içerir. Paket bildirimi, paketinizin yerelleştirmeye özgü yönlerini içerir. Buna dizeler, son kullanıcı lisans sözleşmeleri ve dil paketleri dahildir.  
  
 Ürün bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Ürün bildirimini oluşturma  
  
#### <a name="to-create-the-product-manifest"></a>Ürün bildirimini oluşturmak için  
  
1. Önyükleyici paketi için bir dizin oluşturun. Bu örnek C:\packagekullanır.  
  
2. Visual Studio 'da adlı yeni bir XML dosyası oluşturun `product.xml` ve C:\Package klasörüne kaydedin.  
  
3. Aşağıdaki XML 'i, paketin XML ad alanını ve ürün kodunu tanımlayacak şekilde ekleyin. Ürün kodunu paket için benzersiz bir tanımlayıcı ile değiştirin.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4. Paketin bir bağımlılığı olduğunu belirtmek için XML ekleyin. Bu örnek Microsoft Windows Installer 3,1 ' de bir bağımlılık kullanır.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5. Önyükleyici paketindeki tüm dosyaları listelemek için XML ekleyin. Bu örnek CorePackage.msi paket dosyası adını kullanır.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6. CorePackage.msi dosyasını kopyalayın veya C:\Package klasörüne taşıyın.  
  
7. Önyükleyici komutlarını kullanarak paketi yüklemek için XML ekleyin. Önyükleyici, sessizce yüklenecek. msi dosyasına **/qn** bayrağını otomatik olarak ekler. Dosya bir. exe ise, önyükleyici kabuğu kullanarak. exe dosyasını çalıştırır. Aşağıdaki XML CorePackage.msi için bağımsız değişken göstermez, ancak komut satırı bağımsız değişkenini bağımsız değişkenler özniteliğine koyabilirsiniz.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8. Bu Önyükleyici paketinin yüklü olup olmadığını denetlemek için aşağıdaki XML 'i ekleyin. Ürün kodunu yeniden dağıtılabilir bileşen için GUID ile değiştirin.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Önyükleyici bileşeninin zaten yüklü olup olmadığı öğesine bağlı olarak önyükleyici davranışını değiştirmek için XML ekleyin. Bileşen yüklüyse, önyükleyici paketi çalıştırılmaz. Aşağıdaki XML, bu bileşen yönetici ayrıcalıkları gerektirdiğinden geçerli kullanıcının yönetici olup olmadığını denetler.  
  
    ```  
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
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Önyükleyici komutlarının bölümünü sonlandırmak için aşağıdaki XML 'i ekleyin.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. C:\Package klasörünü Visual Studio önyükleyici dizinine taşıyın. Visual Studio 2010 için bu, \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages dizinidir.  
  
## <a name="example"></a>Örnek  
 Ürün bildirimi, özel önkoşullara yönelik yükleme yönergelerini içerir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ürün ve Paket Şema Başvurusu](../deployment/product-and-package-schema-reference.md)
