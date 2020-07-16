---
title: Hata ayıklama 64-bit uygulamalar | Microsoft Docs
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
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0eaa719bb3eeca2eb3dfe558184699ccca42819
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387206"
---
# <a name="debug-64-bit-applications"></a>64 Bit Uygulamalarda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konunun en son sürümü, [hata ayıklama 64 bit uygulamalarında](/visualstudio/debugger/debug-64-bit-applications) bulunabilir.  
  
Yerel bilgisayarda veya uzak bir bilgisayarda çalışan 64 bitlik bir uygulamada hata ayıklaması yapabilirsiniz.  
  
 Uzak bilgisayarda çalışan 64 bitlik bir uygulamada hata ayıklamak için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
 Visual Studio, 64 bitlik uygulamalarda yerel olarak hata ayıklamak için 64 bit çalışan işlemi (msvsmon.exe) kullanır ve bu işlem, 32-bit Visual Studio işleminin içinden gerçekleştirilemez düşük düzeyli işlemleri gerçekleştirir.  
  
 .NET Framework sürüm 3,5 veya önceki bir sürümü kullanan 64 bit işlemlerde karışık modda hata ayıklama desteklenmez.  
  
## <a name="debug-a-64-bit-application"></a>64 bitlik bir uygulamada hata ayıklama  
 64 bitlik bir uygulamada hata ayıklamayı denemek için:  
  
1. Örneğin bir C# konsol uygulaması gibi bir Visual Studio çözümü oluşturun.  
  
2. Configuration Manager kullanarak yapılandırmayı 64 bit olarak ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: projeleri hedef platformları Için yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3. Bu noktada, uzaktan hata ayıklayıcı 'nın 64 bit sürümü (msvsmon.exe) başlatılır. 64 bit yapılandırmasına sahip çözüm açık olduğu sürece çalışır.  
  
4. Hata ayıklamayı başlatın. 32 bitlik bir yapılandırmayla aynı deneyimle sahip olmanız gerekir. Hata alırsanız aşağıdaki sorun giderme bölümüne bakın.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Sorun giderme 64-bit hata ayıklama  
 Bir hata görebilirsiniz: "64 bit hata ayıklama işlemi beklenenden uzun sürüyor." Bu durumda, Visual Studio msvsmon.exe 64 bit sürümüne bir istek gönderdi ve bu isteğin geri gelmesi uzun zaman aldı.  
  
 Bu hatanın başlıca iki nedeni vardır:  
  
- Bilgisayarınızda, ağ yığınının güvenilmez hale gelmesinin ve localhost üzerinden gelen paketleri bıraktığı ağ güvenlik yazılımı yüklü. Tüm ağ güvenlik yazılımlarını devre dışı bırakıp çözmediğine bakın. Bu durumda, yazılımın localhost trafiğiyle çakışmasını engelleyen ağ güvenliği yazılım satıcınıza rapor edin.  
  
- Visual Studio 'Nun yanıt vermemesine neden olan bir sorun veya diğer performans sorununu çalıştırıyorsunuz. Sorun düzenli olarak gerçekleşmişse, Visual Studio (devenv.exe) ve çalışan işlemi (msvsmon.exe) dökümünü toplayabilir ve bunları Microsoft 'a gönderebilirsiniz. 
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [64 bitlik uygulamalar](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [64 bit için programları yapılandırma](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Visual Studio IDE 64 bit desteği](../ide/visual-studio-ide-64-bit-support.md)   
 [Döküm dosyalarını kullanma](../debugger/using-dump-files.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
