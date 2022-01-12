---
title: önkoşulları dahil et (ClickOnce uygulaması)
description: geliştirme bilgisayarınız için ClickOnce uygulamanıza dağıtılacak önkoşullar için yükleyici paketleri almayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e0ad4c47a2bab3c10e67c21ba4c78af83590663e
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750722"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>nasıl yapılır: ClickOnce uygulamayla önkoşulları dahil etme
Önkoşul yazılımlarını bir uygulamayla dağıtabilmeniz için önce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bu önkoşulların yükleyici paketlerini geliştirme bilgisayarınıza indirmeniz gerekir. Bir uygulamayı yayımladığınızda ve Uygulamam **ile aynı konumdan önkoşulları indir**' i seçtiğinizde, yükleyici paketleri **paketler** klasöründe değilse bir hata oluşur.

> [!NOTE]
> .NET Framework için bir yükleyici paketi eklemek için, bkz. [geliştiriciler için .NET Framework dağıtım kılavuzu](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Package.xml kullanarak bir yükleyici paketi eklemek için

1. Dosya Gezgini 'nde **paketler** klasörünü açın.

    Varsayılan olarak yol olur `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` .

>[!NOTE]
> Visual Studio 2019 güncelleştirme 7 ' den başlayarak, yol altında da sürüm önyükleyicisi paketleri de bulunur `<VS Install Path>\MSBuild\Microsoft\VisualStudio\BootstrapperPackages` .

2. Eklemek istediğiniz önkoşul için klasörünü açın ve sonra yüklü sürümünüz için dil klasörünü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (örneğin, İngilizce için) açın. 

3. Not Defteri, *Package.xml* dosyasını açın.

4. İçeren **ad** öğesini bulun `http://go.microsoft.com/fwlink` ve URL 'yi kopyalayın. **LinkId** bölümünü dahil edin.

   > [!NOTE]
   > Hiçbir **ad** öğesi içermiyorsa `http://go.microsoft.com/fwlink` , önkoşul için kök klasörde **Product.xml** dosyasını açın ve **fwlink** dizesini bulun.

   > [!IMPORTANT]
   > Bazı ön koşullar (örneğin, 32-bit veya 64-bit sistemler için) birden çok yükleme paketine sahiptirler. Birden çok **ad** öğesi **fwlink** içeriyorsa, her biri için kalan adımları tekrarlamanız gerekir.

5. URL 'YI tarayıcınızın adres çubuğuna yapıştırın ve sonra çalıştırmanız veya kaydetmeniz istendiğinde **Kaydet**' i seçin.

    Bu adım, yükleyici dosyasını bilgisayarınıza yükler.

6. Dosyayı ön koşul için kök klasörüne kopyalayın.

    örneğin, .NET Framework 4.7.2 önkoşulu için dosyayı *\packages\dotnetfx472* klasörüne kopyalayın.

    Şimdi, yükleyici paketi uygulamanız ile dağıtabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: ClickOnce uygulamayla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
