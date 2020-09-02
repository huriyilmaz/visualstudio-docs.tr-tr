---
title: 'Nasıl yapılır: performans araçlarını çalıştırma Işlemlerine bağlama ve ayırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b8fc664ee47cd34ab984d1ac448b45c2f17c5b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804969"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Nasıl yapılır: performans araçlarını çalıştırma Işlemlerine bağlama ve ayırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturucu, örnekleme yapmak ve performans verilerini toplamak için çalışan bir işlemden eklemek ya da ayırmak için kullanılabilir. Bu yöntemi, uygulama yükleme süresi hakkında veri toplamayı önlemek veya belirli bir duruma ulaştıktan sonra bir işlemin performansını izlemek istediğinizde bir işlemi profil için kullanabilirsiniz.  
  
> [!NOTE]
> Aşağıdaki adımlar, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Tümleşik geliştirme environmnent (IDE) içinden işlemleri eklemek ve ayırmak için geçerlidir. Komut satırı araçlarını kullanma hakkında daha fazla bilgi için, bkz. [komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md). Hizmetleri profil oluşturma hakkında daha fazla bilgi için bkz. [profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md).  
  
 Profil için kullanılabilen süreçler, bilgisayarın yöneticisi tarafından ayarlanan Kullanıcı erişim Izinlerine bağlıdır. Örneğin, bir kullanıcı hesabı, aşağıdakilerden herhangi biri için izne sahip olabilir:  
  
- Yönetici, sürücüyü ve hizmeti başlatılmak üzere ayarladığınızda gelişmiş profil oluşturma özellikleri.  
  
- Yalnızca örnek profil oluşturma (etki alanı kullanıcıları).  
  
- Herkes için profil oluşturma erişimini engelleyin.  
  
  Daha fazla bilgi için bkz. [profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md) ve [VSPerfCmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.  
  
### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme iliştirmek için  
  
1. **Çözümle** menüsünde **Profil Oluşturucu** ' nın üzerine gelin ve ardından **Ekle/ayır**' a tıklayın.  
  
     \- veya  
  
     **Performans Gezgini**' de, performans oturumuna sağ tıklayın ve ardından **Ekle/ayır**' a tıklayın.  
  
     **Işleme profil oluşturucu Ekle** iletişim kutusu görüntülenir.  
  
2. Eklemek istediğiniz işlemin adına tıklayın.  
  
3. **Ekle**' ye tıklayın.  
  
### <a name="to-detach-from-a-running-process"></a>Çalışan bir işlemden ayrılmak için  
  
1. **Çözümle** menüsünde **Profil Oluşturucu** ' nın üzerine gelin ve ardından **Ekle/ayır**' a tıklayın.  
  
     \- veya  
  
     **Performans Gezgini**' de, performans oturumuna sağ tıklayın ve ardından **Ekle/ayır**' a tıklayın.  
  
     **Işleme profil oluşturucu Ekle** iletişim kutusu görüntülenir.  
  
2. Ayırmak istediğiniz görüntü adına tıklayın.  
  
3. **Ayır**'a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)   
 [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)   
 [Nasıl yapılır: performans veri toplamayı başlatma ve bitirme](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)
