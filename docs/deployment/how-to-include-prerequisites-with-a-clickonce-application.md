---
title: Önkoşulları dahil et (ClickOnce uygulaması)
description: Geliştirme bilgisayarınız için ClickOnce uygulamanızı dağıtmaya yönelik önkoşullar için yükleyici paketleri almayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9199bb720cb94bc949a04bd59d5d3b6527108ed
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351199"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları dahil etme
Önkoşul yazılımlarını bir uygulamayla dağıtabilmeniz için önce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bu önkoşulların yükleyici paketlerini geliştirme bilgisayarınıza indirmeniz gerekir. Bir uygulamayı yayımladığınızda ve Uygulamam **ile aynı konumdan önkoşulları indir** ' i seçtiğinizde, yükleyici paketleri **paketler** klasöründe değilse bir hata oluşur.

> [!NOTE]
> .NET Framework için bir yükleyici paketi eklemek için, bkz. [geliştiriciler için .NET Framework dağıtım kılavuzu](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Package.xml kullanarak bir yükleyici paketi eklemek için

1. Dosya Gezgini 'nde **paketler** klasörünü açın.

    Varsayılan olarak yol olur `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` .

2. Eklemek istediğiniz önkoşul için klasörünü açın ve sonra yüklü sürümünüz için dil klasörünü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (örneğin, İngilizce için) açın. **en**

3. Not defteri 'nde *Package.xml* dosyasını açın.

4. İçeren **ad** öğesini bulun `http://go.microsoft.com/fwlink` ve URL 'yi kopyalayın. **LinkId** bölümünü dahil edin.

   > [!NOTE]
   > Hiçbir **ad** öğesi içermiyorsa `http://go.microsoft.com/fwlink` , önkoşul için kök klasörde **Product.xml** dosyasını açın ve **fwlink** dizesini bulun.

   > [!IMPORTANT]
   > Bazı ön koşullar (örneğin, 32-bit veya 64-bit sistemler için) birden çok yükleme paketine sahiptirler. Birden çok **ad** öğesi **fwlink** içeriyorsa, her biri için kalan adımları tekrarlamanız gerekir.

5. URL 'YI tarayıcınızın adres çubuğuna yapıştırın ve sonra çalıştırmanız veya kaydetmeniz istendiğinde **Kaydet** ' i seçin.

    Bu adım, yükleyici dosyasını bilgisayarınıza yükler.

6. Dosyayı ön koşul için kök klasörüne kopyalayın.

    Örneğin, Windows Installer 4,5 önkoşulu için dosyasını *\Packages\ WindowsInstaller4_5* klasörüne kopyalayın.

    Şimdi, yükleyici paketi uygulamanız ile dağıtabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
