---
title: Stand-Alone Profiler | Microsoft Docs
description: Tek başına profil işleyiciyi yükleme hakkında bilgi edinmek için bu profil Visual Studio öğrenin. Bazı durumlarda Visual Studio yüklenmemiş olması gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d8a5b2454e2a676dcf087becc5475219d9b98f66
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107712"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Nasıl yapılır: Bağımsız profil oluşturucuyu yükleme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , IDE'yi yüklemeden çalıştırlan komut satırı tabanlı tek başına [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilleyici sağlar. Bu durum, bir bilgisayarda yüklü bir geliştirme ortamının yüklü olup olmadığının ortaya çıkar. Örneğin, bir üretim web sunucusuna geliştirme ortamı yüklemeyebilirsiniz.

> [!NOTE]
> ASP.NET web sitesi için performans verilerini toplamak için tek başına profilleyiciyi kullanırken [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) satır aracı [VSPerfCmd](../profiling/vsperfcmd.md) aracı üzerinden önerilir.

### <a name="to-install-the-stand-alone-profiler"></a>Tek başına profilleyiciyi yüklemek için

1. Visual Studio [için Performans Araçları'Visual Studio.](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio)

1. Performans araçlarını indirdiğiniz tek başına *profil yükleyicisini (vs_standaloneprofiler.exe*) bulun ve çalıştırın.

2. Sistem yoluna *vsinstr.exe* yolunu ekleyin.

   > [!NOTE]
   > Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

3. Komut istemine **VSInstr yazın.**

   > [!NOTE]
   > Uygulamanın kullanım bilgileri vsinstr.exe, her şey doğru şekilde ayarlanır. Yollarınızı veya bağımlılıklarından vsinstr.exe bir hatayla karşılaştıysanız, yollarınızı 2. adımda açıklandığı gibi doğru şekilde ayarlayasınız.

4. Simge değişkeninizi **\* \* c:\localcache \* https://msdl.microsoft.com/download/symbols _NT_SYMBOL_PATH symsrv değerinesymsrv.dllsunucuyu ayarlayın** 

5. Sistem ortamı değişkenlerini kullanarak sembol sunucuyu ayardikten sonra, komut satırı profil oluşturma araçlarını yeni bir komut isteminde çalıştırın. Bu, yeni ortam değişkenlerinin etkili olur. Komut istemi penceresinde aşağıdaki komutu yazın:

    **start %COMSPEC%**

   > [!NOTE]
   > Sembol sunucusu paketini ayarlama hakkında ayrıntılı yönergeler için bkz. [Nasıl yapılır: Sembol bilgilerine Windows bakın.](../profiling/how-to-reference-windows-symbol-information.md)

6. Sembollerinizi profil oluşturma verileri (.vsp) dosyasında seri hale getirmeniz için [VSPerfReport](../profiling/vsperfreport.md) aracını kullanın. **VSPerfReport /summary:all /packsymbols** anahtarlarını kullanın. Veri dosyanıza eklenmiş sembolleriniz yoksa, ortam değişkenine sahip _NT_SYMBOL_PATH emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut satırı profili](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Adım adım kılavuz: Araçları kullanarak komut satırı profili oluşturma](command-line-profiling-of-stand-alone-applications.md)
- [Nasıl yapılır: Başvuru pencereleri sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
