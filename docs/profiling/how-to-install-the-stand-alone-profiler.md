---
title: 'Nasıl: Tek Başına Profiler yükleyin | Microsoft Dokümanlar'
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
ms.openlocfilehash: ec0f211db3d9906d83d9bcf7c7a0ab79ec3e1b7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557831"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Nasıl yapılır: Bağımsız profil oluşturucuyu yükleme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE'yi yüklemeden çalıştırılabilen tek başına bir profil oluşturucu komut satırı sağlar. Bu durum, bir bilgisayarın bir geliştirme ortamıyüklü olmadığı veya yüklenemediği zaman oluşur. Örneğin, bir üretim web sunucusuna bir geliştirme ortamı yüklememelisiniz.

> [!NOTE]
> ASP.NET bir web sitesi için performans verileri toplamak için tek başına profil oluşturucuyu kullanırken, [VSPerfCmd](../profiling/vsperfcmd.md) aracı nın üzerinde [VSPerfAsPNetCmd](../profiling/vsperfaspnetcmd.md) satır aracı önerilir.

### <a name="to-install-the-stand-alone-profiler"></a>Tek başına profil oluşturucuyu yüklemek için

1. Visual [Studio için Performans Araçlarını](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio)Indirin.

1. Performans araçlarını indirdiğiniz tek başına profil yükleyicisini *(vs_standaloneprofiler.exe)* bulun ve çalıştırın.

2. *Vsinstr.exe* için yolu sistem yoluna ekleyin.

   > [!NOTE]
   > Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

3. Komut isteminde **VSInstr**yazın.

   > [!NOTE]
   > vsinstr.exe'nin kullanım bilgileri görüntülenirse, her şey doğru şekilde ayarlanır. Vsinstr.exe'yi belirten veya bağımlılıklarından birinin bulunamadığını belirten bir hata görürseniz, yollarınızın adım 2'de açıklandığı gibi doğru şekilde ayarlandığınızdan emin olun.

4. **symsrv\*symsrv.dll\*c:\localcache\* ** için **_NT_SYMBOL_PATH** değişkenayarlayarak sembol sunucusu ayarlama

5. Sistem ortamı değişkenlerini kullanarak sembol sunucunuzu ayarladıktan sonra, komut satırı profil oluşturucu araçlarını yeni bir komut isteminde çalıştırın. Bu, yeni ortam değişkenlerinin etkili olmasını sağlar. Komut istemi penceresinde aşağıdaki komutu yazın:

    **başlangıç %COMSPEC%**

   > [!NOTE]
   > Sembol sunucu paketinin nasıl ayarlanacağına ilişkin ayrıntılı talimatlar için [bkz.](../profiling/how-to-reference-windows-symbol-information.md)

6. Sembollerinizi profil oluşturma verileri (.vsp) dosyasına seri hale getirmek için [VSPerfReport](../profiling/vsperfreport.md) aracını kullanın. **VSPerfReport /summary:all /packsymbols** anahtarlarını kullanın. Veri dosyanıza semboller eklenmiş değilse, _NT_SYMBOL_PATH ortam değişkeni kümesine sahip olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Walkthrough: Enstrümantasyon kullanarak komut satırı profilleme](command-line-profiling-of-stand-alone-applications.md)
- [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
