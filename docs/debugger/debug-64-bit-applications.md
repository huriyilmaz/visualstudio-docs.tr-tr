---
title: 64 Bit Uygulamalarda Hata Ayıklama | Microsoft Docs
description: Visual Studio ile 64 bitlik bir uygulamada hata ayıklamayı Visual Studio. Beklenmeyen hata ayıklama gecikmeleri için ipuçları vardır.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dc3a841d97b3479eb30d26d66608827e1a771d20
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630813"
---
# <a name="debug-64-bit-applications"></a>64 Bit Uygulamalarda Hata Ayıklama
Yerel bilgisayarda veya uzak bir bilgisayarda çalışan 64 bit uygulamada hata ayıkabilirsiniz.

 Uzak bilgisayarda çalışan 64 bit uygulamanın hatasını ayıklamak için bkz. [Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)

 64 bit uygulamalarda yerel olarak hata ayıklamak için Visual Studio, 64 bit çalışan işlemi (msvsmon.exe) kullanır ve 32 bit çalışma süreci içinde gerçekleştirileb alt düzey işlemleri Visual Studio.

 Karma mod hata ayıklaması, 3.5 veya önceki bir sürümü kullanan .NET Framework 64 bit işlemler için desteklenmiyor.

## <a name="debug-a-64-bit-application"></a>64 bit Uygulamada Hata Ayıklama
 64 bit uygulamada hata ayıklamayı denemek için:

1. C# Visual Studio gibi bir çözüm oluşturun.

2. Yapılandırmayı 64 bit olarak ayarlamak için Yapılandırma Yöneticisi. Daha fazla bilgi için, [bkz. How to: Configure Projects to Target Platforms](../ide/how-to-configure-projects-to-target-platforms.md).

3. Bu noktada, uzak hata ayıklayıcının 64 bit sürümü (msvsmon.exe) başlar. 64 bit yapılandırmaya sahip çözüm açık olduğu sürece çalışır.

4. Hata ayıklamayı başlatın. 32 bit yapılandırmayla aynı deneyimi yaşamanız gerekir. Hata asanız aşağıdaki Sorun giderme bölümüne bakın.

## <a name="troubleshooting-64-bit-debugging"></a>64 bit hata ayıklama sorunlarını giderme
 Şu hatayı alabilirsiniz: "64 bit hata ayıklama işlemi beklenenden uzun sürer." Bu durumda Visual Studio msvsmon.exe 64 bit sürümüne bir istek gönderdi ve bu isteğin sonucu çok uzun sürdü.

 Bu hatanın iki ana nedeni vardır:

- Bilgisayarınızda ağ yığınının güvenilir olmayan bir şekilde teslim edişini ve localhost üzerinden giden paketleri düşüren ağ güvenlik yazılımını yüklemişsinizdir. Tüm ağ güvenlik yazılımlarını devre dışı bırakmayı deneyin ve bunun çözümleyene bakabilirsiniz. Öyleyse, ağ güvenlik yazılımı satıcınıza yazılımın localhost trafiğine engel olduğunu rapor olun.

- Sorunun yanıt vermemeye Visual Studio başka bir performans sorunuyla karşı karşısı var. Sorun düzenli olarak gerçekleşirse, Visual Studio (devenv.exe) ve çalışan işleminin (msvsmon.exe) dökümlerini toplayabilirsiniz ve bunları Microsoft'a göndersiniz. Bir sorunu bildirme hakkında bilgi için [bkz.](../ide/how-to-report-a-problem-with-visual-studio.md)How to Report a Problem with Visual Studio .

## <a name="see-also"></a>Ayrıca bkz.

- [64 bit Uygulamalar](/dotnet/framework/64-bit-apps)
- [Programları 64 Bit için Yapılandırma](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Visual Studio IDE 64 Bit Desteği](../ide/visual-studio-ide-64-bit-support.md)
- [Döküm Dosyalarını Kullanma](../debugger/using-dump-files.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)