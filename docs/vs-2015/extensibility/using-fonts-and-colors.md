---
title: Yazı tiplerini ve renkleri kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177228"
---
# <a name="using-fonts-and-colors"></a>Yazı Tiplerini ve Renkleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Metin göstermek için yazı tiplerinin ve renklerin kullanılmasına yönelik destek sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yazı Tipi ve Renklere Genel Bakış](../extensibility/font-and-color-overview.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Tümleşik geliştirme ortamında (IDE) metin yazı tipi ve renk ayarlarını açıklar. Ayrıca, kategorilerin ve görüntüleme öğelerinin kavramlarını tanıtır, VSPackages ve çekirdek düzenleyicinin metin özniteliklerini nasıl kullandığını açıklar.  
  
 [Metin Renklendirme İçin Yazı Tipi ve Renk Bilgilerini Alma](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 **Metin Düzenleyicisi**dışındaki **kategorileri** yöneten VSPackages 'ta metin renklendirme uygulamak için yönergeler sağlar.  
  
 [Depolanan Yazı Tipi ve Renk Ayarlarına Erişme](../extensibility/accessing-stored-font-and-color-settings.md)  
 Geçerli yazı tipi ve renk ayarlarının nasıl depolanacağını, alınabileceğini ve uygulanacağını açıklar.  
  
 [Özel Kategoriler ve Görüntüleme Öğeleri Uygulama](../extensibility/implementing-custom-categories-and-display-items.md)  
 Bir pencerenin, metin görüntülemeyi desteklemek için kendi **görüntüleme öğelerini** ve **kategorilerini** oluşturup kullanabileceği temel adımları açıklar.  
  
 Bu yaklaşım, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> arabirimi ve ilgili arabirimleri uygulamak için bir VSPackage gerektirir.  
  
 [Nasıl Yapılır: Yerleşik Yazı Tipi ve Renk Şemasına Erişme](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Yerleşik yazı tipi ve renkler kullanarak bir kategorinin nasıl tanımlanacağını ve kaydedeceğinizi ve sistem tarafından belirtilen yazı tiplerinin ve renklerin kullanımını nasıl başlatabileceğini açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 `IVsFontAndColorDefaults` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> **Seçenekler** iletişim kutusunun **yazı tipleri ve renkler** sayfasında, **ayarları göster** listesinde listelenen belirli bir öğeye karşılık gelen bir örneği veya arabirimi sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Bir pencere veya Kullanıcı arabirimi bileşeni için varsayılan yazı tiplerini ve renkleri tanımlayarak bir VSPackage 'ın IDE **yazı tipi ve renkler** sayfasını desteklemesini sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Yazı tipi ve renk desteği sağlayan bir VSPackage 'ın, iki veya daha fazla kategorinin birleşimini temsil eden bir süper kategori olan bir görüntüleme öğesi grubunu belirtmesini sağlayan bir mekanizma sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Bir VSPackage 'ın yazı tipi ve renk verileri almasını veya kayıt defterine kaydedilmesini sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Yazı tipi ve renk ayarlarındaki değişikliklerle ilgili yazı tipi ve renk bilgilerini kullanan VSPackages 'i bilgilendirir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Yazı tipi ve renk** mekanizmalarının yöntemleri tarafından kullanılan giriş ve çıkış verileriyle çalışmaya yönelik araçlar sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Yazı tipi ve renk ayarlarının önbelleğe alınmasını denetler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Eski Dil Hizmeti Geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)  
 VSPackages 'in düzenleyiciyi özelleştirmek için dil hizmetlerini nasıl kullanabileceğinizi açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Özel Düzenleyicilerde Söz Dizimi Renklendirmesi](../extensibility/syntax-coloring-in-custom-editors.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Düzenleyicinin sözdizimi renklendirme uygulamak için dil hizmetlerini nasıl kullandığını açıklamaktadır.  
  
 [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Hizmetlerin, geri kalanı ile eşleşen kullanıcı arabirimi öğeleri oluşturmak için nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .
