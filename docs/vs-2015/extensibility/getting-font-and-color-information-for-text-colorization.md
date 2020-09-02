---
title: Metin renklendirme için yazı tipi ve renk bilgileri alma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696853"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Metin Renklendirme İçin Yazı Tipi ve Renk Bilgilerini Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı arabirimi (UI) öğelerinde renklendirilmiş metin işleyen veya görüntüleyen işlem, proje türüne, teknolojisine ve geliştirici tercihlerine bağlıdır. **Yazı tipleri ve renkler** Özellik sayfası ayarları depolar.  
  
 Renklendirilmiş metni görüntüleyen çoğu uygulama, `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` metin görüntüleme ayarlarını sunmak, almak ve depolamak için ve ilişkili arabirimlere gerek duyar.  
  
> [!NOTE]
> Çekirdek düzenleyiciyi özelleştirirken ( **metin EditorCategory**'ü destekler), dil hizmetindeki renklendirme teknolojisini kullanmanız önemle önerilir. Daha fazla bilgi için bkz. [yazı tipi ve renge genel bakış](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Varsayılan yazı tipi ve renk bilgilerini alma  
 Bir **kategorinin** **görüntüleme öğelerinde** metin görüntüleyen herhangi bir pencerenin **yazı tipi ve renk** ayarları belirtilmelidir. Daha fazla bilgi için bkz. [yazı tipleri ve renkler, ortam, Seçenekler Iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Renklendirmesi için, VSPackage geçerli **yazı tiplerini ve renk** ayarlarını almalıdır. Bir VSPackage, ihtiyaçlarına bağlı olarak aşağıdaki yollarla bunu gerçekleştirebilir:  
  
- Depolanan veya geçerli durumu almak için yazı tipi ve renk kalıcılığı mekanizmasını kullanın. Daha fazla bilgi için bkz. [depolanan yazı tipine ve renk ayarlarına erişme](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> örneğini almak için yazı tipi ve renk verileri sağlayan bir hizmetin arabirimini kullanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , VSPackage de yazı tipi ve renk sağlayıcısı değildir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> arabirimini gerçekleştirin.  
  
  Yoklamayla elde edilen sonuçların güncel olduğundan emin olmak için, arabirimin <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> alma yöntemleri çağrılmadan önce bir güncelleştirme gerekip gerekmediğini öğrenmek için arabirimi kullanmak yararlı olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  
  
  Yazı tipi ve renk bilgilerini elde ettikten sonra, renklendirme gerektiren öğeleri tanımlamak üzere görüntülenecek metni ayrıştırın ve sonra uygun yazı tiplerini ve renkleri kullanarak pencerede metni görüntüleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Yazı tipi ve metin kullanma](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Renklerle çalışma](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (grafik cihaz arabirimi)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
