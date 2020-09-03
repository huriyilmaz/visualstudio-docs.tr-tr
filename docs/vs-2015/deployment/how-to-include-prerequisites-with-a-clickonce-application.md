---
title: 'Nasıl yapılır: ClickOnce uygulaması ile önkoşulları dahil etme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557679"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulamasına Önkoşullar Dahil Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Önkoşul yazılımlarını bir uygulamayla dağıtabilmeniz için önce [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bu önkoşulların yükleyici paketlerini geliştirme bilgisayarınıza indirmeniz gerekir. Bir uygulamayı yayımladığınızda ve Uygulamam **ile aynı konumdan önkoşulları indir**' i seçtiğinizde, yükleyici paketleri **paketler** klasöründe değilse bir hata oluşur.  
  
> [!NOTE]
> .NET Framework için bir yükleyici paketi eklemek için, bkz. [geliştiriciler için .NET Framework dağıtım kılavuzu](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Package.xml kullanarak bir yükleyici paketi eklemek için  
  
1. Dosya Gezgini 'nde **paketler** klasörünü açın.  
  
     Varsayılan olarak, yol 32 bitlik bir sistemdeki C:\Program Files\Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages ve 64-bit sistemdeki C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages şeklindedir.  
  
2. Eklemek istediğiniz önkoşul için klasörünü açın ve sonra yüklü sürümünüz için dil klasörünü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (örneğin, İngilizce için) açın. **en**  
  
3. Not defteri 'nde **Package.xml** dosyasını açın.  
  
4. İçeren **ad** öğesini bulun `http://go.microsoft.com/fwlink` ve URL 'yi kopyalayın. **LinkId** bölümünü dahil edin.  
  
    > [!NOTE]
    > Hiçbir **ad** öğesi içermiyorsa `http://go.microsoft.com/fwlink` , önkoşul için kök klasörde **Product.xml** dosyasını açın ve **fwlink** dizesini bulun.  
  
    > [!IMPORTANT]
    > Bazı ön koşullar (örneğin, 32-bit veya 64-bit sistemler için) birden çok yükleme paketine sahiptirler. Birden çok **ad** öğesi **fwlink**içeriyorsa, her biri için kalan adımları tekrarlamanız gerekir.  
  
5. URL 'YI tarayıcınızın adres çubuğuna yapıştırın ve sonra çalıştırmanız veya kaydetmeniz istendiğinde **Kaydet**' i seçin.  
  
     Bu adım, yükleyici dosyasını bilgisayarınıza yükler.  
  
6. Dosyayı ön koşul için kök klasörüne kopyalayın.  
  
     Örneğin, Windows Installer 4.5 ön koşulları için dosyayı \Packages\WindowsInstaller4_5 klasörüne kopyalayın.  
  
     Şimdi, yükleyici paketi uygulamanız ile dağıtabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
