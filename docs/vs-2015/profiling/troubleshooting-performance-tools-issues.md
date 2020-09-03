---
title: Performans araçları sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: troubleshooting
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 575f17c641eb057dc01fb3302098bd9f8b47f9c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815512"
---
# <a name="troubleshooting-performance-tools-issues"></a>Performans Araçları Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları kullandığınızda aşağıdaki sorunlardan biriyle karşılaşabilirsiniz:  
  
- [Profil Oluşturma Araçları hiçbir veri toplanmadı](#NoDataCollected)  
  
- [Performans görünümleri ve raporlar Işlev adlarının numaralarını görüntüler](#NoSymbols)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a><a name="NoDataCollected"></a> Profil Oluşturma Araçları hiçbir veri toplanmadı  
 Bir uygulamayı profilledikten sonra, bir profil oluşturma verileri (. vsp) dosyası oluşturulmaz ve çıkış penceresinde veya komut penceresinde aşağıdaki uyarıyı alırsınız:  
  
 PRF0025: veri toplanmadı.  
  
 Bu sorun birkaç sorundan kaynaklanıyor olabilir:  
  
- Örnekleme veya .NET bellek yöntemi kullanılarak profili oluşturulmuş bir işlem, uygulamanın çalışmasını gerçekleştiren işlem haline gelen bir alt işlem başlatır. Örneğin, bazı uygulamalar, bir Windows uygulaması veya bir komut satırı uygulaması olarak başlatılıp başlatılmayacağını anlamak için komut satırını okur. Bir Windows uygulaması isteniyorsa, özgün işlem Windows uygulaması olarak yapılandırılmış yeni bir işlem başlatır ve ardından orijinal işlem çıkar. Profil Oluşturma Araçları alt işlemlere yönelik verileri otomatik olarak toplamadığından, hiçbir veri toplanmaz.  
  
     Bu durumda profil oluşturma verilerini toplamak için, profil oluşturucuyu, uygulamayı profil Oluşturucu ile başlatmak yerine alt işleme bağlayın. Daha fazla bilgi için bkz [. nasıl yapılır: performans araçlarını çalışan Işlemlere bağlama ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) ve [Iliştirme (VSPerfCmd)](../profiling/attach.md)  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a><a name="NoSymbols"></a> Performans görünümleri ve raporlar Işlev adlarının numaralarını görüntüler  
 Bir uygulamayı profilledikten sonra, raporlarda ve görünümlerde işlev adları yerine sayılar görürsünüz.  
  
 Bu sorun, Profil Oluşturma Araçları Analysis Engine 'in kaynak kodu bilgilerini, derlenmiş dosyanın işlev adlarını ve satır numaralarını eşleştiren sembol bilgilerini içeren. pdb dosyalarını bulamamasının nedeni. Varsayılan olarak, derleyici, uygulama dosyası yapılandırıldığında. pdb dosyasını oluşturur. . Pdb dosyasının yerel dizinine yönelik bir başvuru, derlenen uygulamada depolanır. Analiz altyapısı,. pdb dosyası için başvurulan dizine ve ardından şu anda uygulama dosyasını içeren dosyaya bakar. . Pdb dosyası bulunamazsa, analiz Altyapısı işlev adları yerine işlev uzaklıklarını kullanır.  
  
 Sorunu iki şekilde giderebilirsiniz:  
  
- . Pdb dosyalarını bulun ve uygulama dosyalarıyla aynı dizine yerleştirin.  
  
- Sembol bilgilerini profil oluşturma verileri (. vsp) dosyasına ekleyin. Daha fazla bilgi için bkz. [performans veri dosyalarıyla sembol bilgilerini kaydetme](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
> Analiz altyapısı,. pdb dosyasının derlenen uygulama dosyasıyla aynı sürümde olmasını gerektirir. Uygulama dosyasının önceki veya sonraki bir derlemeden bir. pdb dosyası çalışmayacak.
