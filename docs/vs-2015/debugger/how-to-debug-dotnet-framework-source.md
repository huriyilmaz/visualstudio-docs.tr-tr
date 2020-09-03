---
title: 'Nasıl yapılır: .NET Framework kaynakta hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205437"
---
# <a name="how-to-debug-net-framework-source"></a>Nasıl Yapılır: .NET Framework Kaynağında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En son sürümü, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklama için yeni özellikler sağlar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Kaynakta hata ayıklamak için [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , kodun hata ayıklama sembollerine erişiminizin olması gerekir. Ayrıca, kaynak üzerinde adımlamayı etkinleştirmeniz gerekir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **Seçenekler** iletişim kutusunda atlama ve sembol indirmeyi etkinleştirebilirsiniz. Sembol indirmeyi etkinleştirdiğinizde sembolleri hemen indirmeyi seçebilir veya daha sonra karşıdan yükleme seçeneğini etkinleştirebilirsiniz. Sembolleri hemen indirmediyseniz, uygulamanız bir dahaki sefer hata ayıklamaya başladığınızda semboller indirilir. Ayrıca **modüller** penceresinden veya **çağrı yığını** penceresinden el ile karşıdan yükleme yapabilirsiniz.  
  
### <a name="to-enable-net-framework-source-debugging"></a>.NET Framework kaynak hata ayıklamayı etkinleştirmek için  
  
1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.  
  
2. **Seçenekler** iletişim kutusunda, **hata ayıklama** kategorisine tıklayın.  
  
3. **Genel** kutusunda .NET Framework kaynak adımlamayı **Etkinleştir** ' i ayarlayın.  
  
    1. Yalnızca kendi kodum etkinleştirdiyseniz, bir uyarı iletişim kutusu size Yalnızca kendi kodum artık devre dışı bırakıldığını söyler. **Tamam**’a tıklayın.  
  
    2. Sembol önbelleği konum ayarladıysanız, başka bir uyarı iletişim kutusu size varsayılan bir sembol önbelleği konumunun ayarlandığını söyler. **Tamam**’a tıklayın.  
  
4. **Hata ayıklama** kategorisi altında **semboller**' e tıklayın.  
  
5. Semboller Önbellek konumunu değiştirmek istiyorsanız:  
  
    1. Soldaki kutudan **hata ayıklama** düğümünü açın.  
  
    2. **Hata ayıklama** düğümü altında **semboller**' e tıklayın.  
  
    3. **Sembol sunucularından bu dizine önbellek simgelerdir** konumunu düzenleyin veya bir konum seçmek Için, **Araştır** ' a tıklayın.  
  
6. Sembolleri hemen indirmek isterseniz, **Yukarıdaki konumları kullanarak sembolleri yükle**' ye tıklayın.  
  
     Bu düğme tasarım modunda kullanılamaz.  
  
     Sembolleri şimdi indirmeyi tercih ediyorsanız, programınızda hata ayıklamayı bir sonraki başlatmanızda semboller otomatik olarak indirilir.  
  
7. **Seçenekler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Modüller penceresini kullanarak çerçeve sembolleri yüklemek için  
  
1. **Modüller** penceresinde, simgelerin yüklenmediği bir modüle sağ tıklayın. Semboller **durum** sütununa bakarak simgelerin yüklenip yüklenmediğini veya yüklenmediğini söyleyebilirsiniz.  
  
2. Simgeleri yükle ' nin üzerine **gelin ve Microsoft** ortak semboller sunucusundan sembolleri veya **sembol yolundan** daha önce sembolleri depoladığınız bir dizinden yüklenecek simgeleri Indirmek için **Microsoft sembol sunucuları** ' na tıklayın.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Çağrı yığını penceresini kullanarak çerçeve simgeleri yüklemek için  
  
1. **Çağrı yığını** penceresinde, simgelerin yüklenmediği bir çerçeveye sağ tıklayın. Çerçeve devre dışı bırakılır.  
  
2. **Sembolleri yükle** ' nin üzerine gelin ve **Microsoft sembol sunucuları** veya **sembol yolu**' na tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
