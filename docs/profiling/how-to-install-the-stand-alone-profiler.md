---
title: 'Nasıl yapılır: tek başına profil oluşturucuyu yüklemek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 05611b74049307fc0d7c038ecdb275f70c983501
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778927"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Nasıl yapılır: tek başına profil oluşturucuyu yüklemek
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 'yi yüklemeden çalıştırılabilen bir komut satırı tabanlı tek başına profil oluşturucu sağlar. Bu durum, bir bilgisayar bir geliştirme ortamının yüklü olmadığı veya içermediği durumlarda oluşur. Örneğin, bir üretim Web sunucusuna bir geliştirme ortamı yüklememelisiniz.

> [!NOTE]
> Bir ASP.NET Web sitesi için performans verilerini toplamak üzere tek başına profil oluşturucu kullandığınızda, [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) satırı aracı [VSPerfCmd](../profiling/vsperfcmd.md) aracı üzerinde önerilir.

### <a name="to-install-the-stand-alone-profiler"></a>Tek başına profil oluşturucuyu yüklemek için

1. [Visual Studio Için performans araçları](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio)'nı indirin.

1. Performans araçlarını indirdiğiniz ve çalıştıran tek başına profil yükleyicisini (*vs_standaloneprofiler. exe*) bulun.

2. *Vsintr. exe* ve *Msdis150. dll ' nin* yolunu sistem yoluna ekleyin.

   > [!NOTE]
   > Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

3. Komut isteminde **vsinstr**yazın.

   > [!NOTE]
   > Vsinstr. exe kullanım bilgileri görüntüleniyorsa her şey doğru şekilde ayarlanır. Vsinstr. exe durumu veya bağımlılıklarından biri bulunamadığı için bir hata görürseniz, yollarınızın adım 2 ' de açıklandığı gibi doğru ayarlandığından emin olun.

4. **_NT_SYMBOL_PATH** değişkeninizi **symsrv\*symsrv. dll\*c:\localcache\*** olarak ayarlayarak sembol sunucusunu ayarlayın http://msdl.microsoft.com/download/symbols

5. Sembol sunucunuzu sistem ortam değişkenlerini kullanarak ayarladıktan sonra, yeni bir komut isteminde komut satırı profil oluşturucu Araçları ' nı çalıştırın. Bu, yeni ortam değişkenlerinin etkili olmasına olanak sağlar. Komut istemi penceresinde aşağıdaki komutu yazın:

    **başlatma% COMSPEC%**

   > [!NOTE]
   > Sembol sunucusu paketini ayarlama hakkında ayrıntılı yönergeler için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md).

6. Sembollerinizi profil oluşturma verileri (. vsp) dosyasına seri hale getirmek için [VSPerfReport](../profiling/vsperfreport.md) aracını kullanın. **VSPerfReport/summary: all/packsymbols** anahtarlarını kullanın. Veri dosyanıza eklenen semboller yoksa _NT_SYMBOL_PATH ortam değişkeni ayarlanmış olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [İzlenecek yol: örnekleme kullanarak komut satırı profili oluşturma](../profiling/walkthrough-command-line-profiling-using-sampling.md)
- [İzlenecek yol: İzleme metodunu kullanarak komut satırı profili oluşturma](command-line-profiling-of-stand-alone-applications.md)
- [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
