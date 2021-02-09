---
title: Hata ayıklama 64-bit uygulamalar | Microsoft Docs
description: Visual Studio ile 64 bitlik bir uygulamada hata ayıklamayı öğrenin. Beklenmedik hata ayıklama gecikmeleriyle ilgili sorunları gidermeye yönelik ipuçları vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18ea2ade8ed87bfc58280bf5b2dc45c633eb2055
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857603"
---
# <a name="debug-64-bit-applications"></a>64 Bit Uygulamalarda Hata Ayıklama
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

- Visual Studio 'Nun yanıt vermediği bir sorun veya diğer performans sorunları üzerinde çalışıyorsunuz. Sorun düzenli olarak gerçekleşmişse, Visual Studio (devenv.exe) ve çalışan işlemi (msvsmon.exe) dökümünü toplayabilir ve bunları Microsoft 'a gönderebilirsiniz. Sorun bildirme hakkında daha fazla bilgi için bkz. [Visual Studio Ile sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [64 bit Uygulamalar](/dotnet/framework/64-bit-apps)
- [64 bit için programları yapılandırma](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Visual Studio IDE 64 bit desteği](../ide/visual-studio-ide-64-bit-support.md)
- [Döküm Dosyalarını Kullanma](../debugger/using-dump-files.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)