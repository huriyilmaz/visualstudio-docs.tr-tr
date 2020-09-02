---
title: 'Nasıl yapılır: ASP.NET Işleminin adını bulma | Microsoft Docs'
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685958"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Nasıl Yapılır: ASP.NET İşleminin Adını Bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalışan bir uygulamaya iliştirmek için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] işlemin adını bilmeniz gerekir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- IIS 6,0 veya IIS 7,0 çalıştırıyorsanız, ad w3wp.exe.  
  
- IIS 'nin daha önceki bir sürümünü çalıştırıyorsanız, ad aspnet_wp.exe.  
  
  Veya sonraki sürümleri kullanılarak oluşturulan uygulamalar için [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] , [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod dosya sisteminde bulunabilir ve test sunucusu WebDev.WebServer.exe altında çalıştırılabilir. Bu durumda, işlem yerine WebDev.WebServer.exe eklemeniz gerekir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Bu senaryo yalnızca yerel hata ayıklama için geçerlidir.  
  
  Daha eski ASP uygulamaları, işlem içinde çalışırken inetinfo.exe IIS işlemi içinde çalışır.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Proje kodunun dosya sisteminde mi yoksa IIS 'de mi bulunduğunu belirleme  
  
1. Visual Studio 'da zaten açık değilse **Çözüm Gezgini** açın.  
  
2. Uygulamanın adını içeren en üst düğümü seçin.  
  
3. **Özellikler** penceresi başlığı bir dosya yolu içeriyorsa, uygulama kodu dosya sisteminde bulunur.  
  
     Aksi halde, **Özellikler** penceresi başlığı web sitesinin adını içerir.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Uygulamanın altında çalıştığı IIS sürümünü belirleme  
  
1. **Yönetimsel Araçları** bulun ve çalıştırın. İşletim sisteminize bağlı olarak, bu, **Denetim Masası 'nda**bir simge veya **Başlat**' a tıkladığınızda görüntülenen bir menü girdisi olabilir.  
  
     Windows XP 'de, **Denetim Masası** Kategori görünümünde veya Klasik görünümde olabilir. Kategori görünümünde, **Yönetimsel Araçlar** simgesini görmek Için **Klasik Görünüm** veya **performans ve bakım** ' a geçmeniz gerekir.  
  
2. **Yönetim araçlarından**Internet Information Services çalıştırın. Bir MMC iletişim kutusu görüntülenir.  
  
3. Sol bölmede listelenen birden fazla bilgisayar varsa, uygulama kodunun yer aldığı bir tane seçin.  
  
4. IIS sürümü Sağ bölmenin **Sürüm** sütunnda bulunur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama Web uygulamalarında önkoşuls](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET hata ayıklama hazırlığı yapılıyor](../debugger/preparing-to-debug-aspnet.md)   
 [Web Uygulamalarında ve Betikte Hata Ayıklama](../debugger/debugging-web-applications-and-script.md)
