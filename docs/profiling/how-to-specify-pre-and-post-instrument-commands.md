---
title: Ön ve Son Ölçüm komutlarını | Microsoft Docs
description: Bir performans oturumunda ikili dosyalar takip edildikten önce veya sonra çalıştıracak komutları nasıl belirtebilirsiniz?
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d3350483fe1bf6744449d7a57b40c23b3a3c370e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635726"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Nasıl kullanılır: Ön ve son ölçüm komutları belirtme

Bir performans oturumunda ikili dosyalar takip edildikten önce veya sonra çalıştıracak komutları belirtebilirsiniz. Komut satırı tarafından verilen tüm komutlar, bir ön ölçüm veya son ölçüm olayı olarak belirtilebilir. Örneğin, ikili dosyalar takip edildikten sonra yürütülen bir toplu iş dosyasında bir derlemenin güçlü bir ad anahtarıyla yeniden imzasını otomatikleştiren komutlar belirtebilirsiniz.

Profil oluşturma çalıştırması veya tek tek ikili dosyalar için tüm araçlı ikili dosyalar için komut belirtebilirsiniz. Ancak, daha önce çalıştıracak yalnızca bir ön ölçüm öncesi komutu ve instrumentation işleminin ardından çalıştıracak yalnızca bir son araç sonrası komutu belirtebilirsiniz. Hem tüm ikili dosyalar hem de tek tek ikili dosyalar için komut belirtemezseniz. Tüm ikili dosyalar için komutlar belirttiğinizde, komutlar oturumda her ikili dosyanın ölçümden önce veya sonra çalıştırılıyor.

Komutların yürütültülür çalışma dizini, çalışmakta olduğunu işletim sistemine ve profili profili yapılan [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] uygulamanın hedef platformuna bağlıdır.

Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)

## <a name="to-specify-pre-instrument-commands"></a>Ön ölçüm komutlarını belirtmek için

1. Aşağıdaki adımlardan birini uygulayın:

    - Bir performans oturumunda tüm ikili dosyalar için ön ölçümlü komutlar belirtmek için, Performans Gezgini'de performans oturumu düğümünü seçin ve ardından sağ tıklar ve Özellikler'i **seçin.** 

    - Belirli bir ikili için ön ölçüm komutları belirtmek için, performans  oturumunun Hedefler listesinde ikilinin adına sağ tıklayın ve ardından Özellikler'i **seçin.**

2. Özellik **Sayfaları'nın altında,** Ölçümler'e **tıklayın.**

3. Komutu Komut satırı metin **kutusuna Olayları** Önceden **Ölçümle'nin altına yazın.**

    > [!NOTE]
    > Komut satırı kutusunun yanında bulunan üç nokta düğmesine  **(...)** tıklayarak uygun .exe, .cmd veya .bat seçebilirsiniz.

4. **Tamam**'a tıklayın.

     Komutu kaldırmadan çalıştırmayı devre dışı bırakmak için, Ölçümden **hariç tut onay** kutusunu seçin. Derleyici veya bağlantıleyici ayarlarını değiştirmek için proje özellik sayfalarını kullanın.

## <a name="to-specify-post-instrument-commands"></a>Ölçüm sonrası komutları belirtmek için

1. Aşağıdaki adımlardan birini uygulayın:

    - Bir performans oturumunda tüm ikili dosyalar için son ölçümlü komutlar belirtmek için, Performans Gezgini'de performans oturumu düğümünü seçin ve ardından sağ tıklar ve Özellikler'i **seçin.** 

    - Belirli bir ikili için ölçüm sonrası komutları belirtmek için performans oturumunun Hedefler listesinde ikilinin adına sağ tıklayın ve Özellikler'i **seçin.** 

2. Özellik **Sayfaları'nın altında,** Ölçümler'e **tıklayın.**

3. Komut satırı metin kutusuna  **Post-Instrument events altındaki komutu yazın.**

    > [!NOTE]
    > Komut satırı kutusunun yanında bulunan üç nokta düğmesine  **(...)** tıklayarak uygun .exe, .cmd veya .bat seçebilirsiniz.

4. **Tamam**'a tıklayın.

     Komutu kaldırmadan çalıştırmayı devre dışı bırakmak için, Ölçümden **hariç tut onay** kutusunu seçin. Derleyici veya bağlantıleyici ayarlarını değiştirmek için proje özellik sayfalarını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
