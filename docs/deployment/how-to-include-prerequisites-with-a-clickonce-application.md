---
title: Önkoşulları dahil edin (ClickOnce uygulaması)
description: Geliştirme bilgisayarınız için ClickOnce uygulamanıza dağıtma önkoşulları için yükleyici paketlerini nasıl alasınız?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b41529182b7cca8cea8f94206601b7a818d35420
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877747"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Nasıl olur: ClickOnce uygulamasıyla önkoşulları dahil etmek
Önkoşul yazılımlarını bir uygulamayla dağıtmadan önce, bu önkoşullar için yükleyici paketlerini geliştirme [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bilgisayarınıza indirmeniz gerekir. Bir uygulamayı yayımlar ve Önkoşulları uygulamam ile aynı konumdan indir'i **seçerseniz,** yükleyici paketleri Paketler klasöründe yoksa bir **hata** oluşur.

> [!NOTE]
> Dağıtım paketine bir yükleyici paketi .NET Framework için bkz. [.NET Framework Dağıtım Kılavuzu.](/dotnet/framework/deployment/deployment-guide-for-developers)

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Package.xml kullanarak bir yükleyici paketi eklemek için

1. Bu Dosya Gezgini Packages **klasörünü** açın.

    Varsayılan olarak yol `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` olur.

>[!NOTE]
> Visual Studio 2019 Güncelleştirme 7 yayın önyükleyici paketleri de *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages yolunda keşfedildi.*

2. Eklemek istediğiniz önkoşul için klasörü açın ve ardından yüklü sürümünüz için dil klasörünü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açın (örneğin, İngilizce için **en).**

3. Not Defteri'ni açın *vePackage.xml* açın.

4. içeren **Name** öğesini bulun ve `http://go.microsoft.com/fwlink` URL'yi kopyalayın. **LinkID bölümünü dahil** edin.

   > [!NOTE]
   > Name öğesi **yoksa** önkoşul içinProduct.xmlklasöründeki dosyanın adını `http://go.microsoft.com/fwlink` açın ve fwlink **dizesini**  bulun.

   > [!IMPORTANT]
   > Bazı ön koşullar (örneğin, 32-bit veya 64-bit sistemler için) birden çok yükleme paketine sahiptirler. Birden çok **Ad** öğeleri **fwlink içeriyorsa,** kalan adımları her biri için tekrarlamalısiniz.

5. URL'yi tarayıcınızın adres çubuğuna yapıştırın ve çalıştırmanız veya kaydetmeniz istendiğinde Kaydet'i **seçin.**

    Bu adım, yükleyici dosyasını bilgisayarınıza yükler.

6. Dosyayı ön koşul için kök klasörüne kopyalayın.

    Örneğin, .NET Framework 4.7.2 önkoşulları için dosyayı *\Packages\DotNetFX472 klasörüne* kopyalayın.

    Şimdi, yükleyici paketi uygulamanız ile dağıtabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kurulur: ClickOnce uygulamasıyla önkoşulları yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
