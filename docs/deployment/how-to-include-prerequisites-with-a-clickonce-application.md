---
title: 'Nasıl yapılır: ClickOnce uygulaması ile önkoşulları dahil etme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94ed90b9fcdd0c4ffe35789d00de4bbbd4aaa355
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557636"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları dahil etme
Önkoşul yazılımlarını bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayla dağıtabilmeniz için önce bu önkoşulların yükleyici paketlerini geliştirme bilgisayarınıza indirmeniz gerekir. Bir uygulamayı yayımladığınızda ve Uygulamam **ile aynı konumdan önkoşulları indir**' i seçtiğinizde, yükleyici paketleri **paketler** klasöründe değilse bir hata oluşur.

> [!NOTE]
> .NET Framework için bir yükleyici paketi eklemek için, bkz. [geliştiriciler için .NET Framework dağıtım kılavuzu](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="Package"></a>Package. xml kullanarak bir yükleyici paketi eklemek için

1. Dosya Gezgini 'nde **paketler** klasörünü açın.

    Varsayılan olarak, yol `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\`.

2. Eklemek istediğiniz önkoşul için klasörü açın ve ardından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü sürümünüz için dil klasörünü açın (örneğin, **en** İngilizce).

3. Not defteri 'nde *Package. xml* dosyasını açın.

4. `http://go.microsoft.com/fwlink`içeren **ad** öğesini bulun ve URL 'yi kopyalayın. **LinkId** bölümünü dahil edin.

   > [!NOTE]
   > **Ad** öğesi `http://go.microsoft.com/fwlink`içermiyorsa, önkoşul için kök klasörde **Product. xml** dosyasını açın ve **fwlink** dizesini bulun.

   > [!IMPORTANT]
   > Bazı ön koşullar (örneğin, 32-bit veya 64-bit sistemler için) birden çok yükleme paketine sahiptirler. Birden çok **ad** öğesi **fwlink**içeriyorsa, her biri için kalan adımları tekrarlamanız gerekir.

5. URL 'YI tarayıcınızın adres çubuğuna yapıştırın ve sonra çalıştırmanız veya kaydetmeniz istendiğinde **Kaydet**' i seçin.

    Bu adım, yükleyici dosyasını bilgisayarınıza yükler.

6. Dosyayı ön koşul için kök klasörüne kopyalayın.

    Örneğin, Windows Installer 4,5 önkoşulu için dosyasını *\Packages\ WindowsInstaller4_5* klasörüne kopyalayın.

    Şimdi, yükleyici paketi uygulamanız ile dağıtabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
