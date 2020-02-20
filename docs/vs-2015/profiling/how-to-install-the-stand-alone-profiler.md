---
title: 'Nasıl yapılır: tek başına profil oluşturucuyu yüklemek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 026162a2c8334c7163f9c7853d2de30e58e5939a
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476793"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Nasıl yapılır: Bağımsız Profil Oluşturucuyu Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 'yi yüklemeden çalıştırılabilen bir komut satırı tabanlı tek başına profil oluşturucu sağlar. Bu durum, bir bilgisayar bir geliştirme ortamının yüklü olmadığı veya içermediği durumlarda oluşur. Örneğin, bir üretim Web sunucusuna bir geliştirme ortamı yüklememelisiniz.  
  
> [!NOTE]
> ASP.NET Web sitesi için performans verilerini toplamak üzere tek başına profil oluşturucuyu kullanırken, [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) satırı aracı [VSPerfCmd](../profiling/vsperfcmd.md) aracından önerilir.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Tek başına profil oluşturucuyu yüklemek için  
  
1. Tek başına profil yükleyicisini (vs_profiler. exe), \Tek başına profil oluşturucu yolunu içeren dizindeki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yükleme medyasında bulun ve çalıştırın.  
  
2. Vsintr. exe ve Msdis150. dll ' nin yolunu sistem yoluna ekleyin.  
  
    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]varsayılan yüklemesinde vsinstr. exe ve Msdis150. dll, \Program Files\Visual Studio 10 \ Team Tools\Performance Tools konumundadır.  
  
3. Komut isteminde **vsinstr**yazın.  
  
    > [!NOTE]
    > Vsinstr. exe kullanım bilgileri görüntüleniyorsa her şey doğru şekilde ayarlanır. Vsinstr. exe durumu veya bağımlılıklarından biri bulunamadığı için bir hata görürseniz, yollarınızın adım 2 ' de açıklandığı gibi doğru ayarlandığından emin olun.  
  
4. **_NT_SYMBOL_PATH** değişkeninizi `symsrv*symsrv.dll*c:\localcache* https://msdl.microsoft.com/download/symbols` olarak ayarlayarak sembol sunucusunu ayarlayın  
  
5. Sembol sunucunuzu sistem ortam değişkenlerini kullanarak ayarladıktan sonra, yeni bir komut isteminde komut satırı profil oluşturucu Araçları ' nı çalıştırın. Bu, yeni ortam değişkenlerinin etkili olmasına olanak sağlar. Komut istemi penceresinde aşağıdaki komutu yazın:  
  
     **başlatma% COMSPEC%**  
  
    > [!NOTE]
    > Sembol sunucusu paketini ayarlama hakkında ayrıntılı yönergeler için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Sembollerinizi profil oluşturma verileri (. vsp) dosyasına seri hale getirmek için [VSPerfReport](../profiling/vsperfreport.md) aracını kullanın. **VSPerfReport/summary: all/packsymbols** anahtarlarını kullanın. Veri dosyanıza eklenen semboller yoksa _NT_SYMBOL_PATH ortam değişkeni ayarlanmış olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut satırı  profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)  
 [Izlenecek yol: örnekleme  kullanarak komut satırı profili oluşturma](../profiling/walkthrough-command-line-profiling-using-sampling.md)  
 [Izlenecek yol: izleme  kullanarak komut satırı profili oluşturma](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)  
 [Nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
