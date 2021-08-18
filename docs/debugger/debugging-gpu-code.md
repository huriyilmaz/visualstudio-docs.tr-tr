---
title: GPU KoduNda Hata Ayıklama | Microsoft Docs
description: Visual Studio'da grafik işleme biriminde (GPU) çalışan C++ kodunda hata ayıklama hakkında Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 86e7593ff4df88efb24592fcd758156575eb9fd4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113097"
---
# <a name="debugging-gpu-code"></a>GPU Kodunda Hata Ayıklama
Grafik işleme biriminde (GPU) çalışan C++ kodunda hata ayıkabilirsiniz. Visual Studio'daki GPU hata ayıklama desteği; yarış algılama, başlatma işlemleri ve buna ekleme ve hata ayıklama pencerelerine tümleştirme içerir.

## <a name="supported-platforms"></a>Desteklenen Platformlar
 Hata ayıklama , , [!INCLUDE[win7](../debugger/includes/win7_md.md)] [!INCLUDE[win8](../debugger/includes/win8_md.md)] Windows 10, , [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] ve [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] Windows Server 2016. Yazılım öykünücüsünün hata ayıklaması [!INCLUDE[win8](../debugger/includes/win8_md.md)] için, Windows 10 [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] veya , Windows Server 2016 gereklidir. Donanımda hata ayıklama için grafik kartınız için sürücüleri yüklemeniz gerekir. Tüm donanım satıcıları tüm hata ayıklayıcı özelliklerini uygulamaz. Sınırlamalar için satıcı belgelerine bakın.

> [!NOTE]
> Visual Studio'de GPU hata ayıklamasını desteklemek isteyen bağımsız donanım satıcılarının VSD3DDebug arabirimini uygulayan ve kendi sürücülerini hedef alan bir DLL oluşturması gerekir.

## <a name="configuring-gpu-debugging"></a>GPU Hata Ayıklamayı Yapılandırma
 Hata ayıklayıcısı aynı uygulama yürütmesinde hem CPU kodunda hem de GPU kodunda kesme olamaz. Varsayılan olarak, hata ayıklayıcı CPU kodunda bozar. GPU kodunda hata ayıklamak için şu iki adımdan birini kullanın:

- Standart araç **çubuğundaki Hata** Ayıklama Türü **listesinde Yalnızca** **GPU'su seçin.**

- Bu **Çözüm Gezgini** proje kısayol menüsünde Özellikler'i **seçin.** Özellik Sayfaları **iletişim kutusunda** Hata Ayıklama'ya **tıklayın** ve ardından Hata Ayıklayıcı **Türü listesinden Yalnızca** **GPU'ya** tıklayın.

## <a name="launching-and-attaching-to-applications"></a>Uygulamaları Başlatma ve Uygulamalara Ekleme
 GPU hata ayıklamasını başlatmak Visual Studio hata ayıklama komutlarını kullanabilirsiniz. Daha fazla bilgi için [bkz. Hata Ayıklayıcı ile Kodda Gezinme.](../debugger/navigating-through-code-with-the-debugger.md) GPU hata ayıklayıcısını çalışan bir işleme de iliştirebilirsiniz, ancak yalnızca bu işlem GPU kodu yürütürse. Daha fazla bilgi için [bkz. Çalışan İşlemlere Ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Geçerli Kutucuğu İmleçte Çalıştır ve İmleçte Çalıştır
 GPU'da hata ayıklarken, imleç konuma çalıştırmak için iki seçeneğiniz vardır. Her iki seçeneğin komutlarını da kod düzenleyicisinin kısayol menüsünde bulabilirsiniz.

1. **İmleçten Imleçe** Çalıştır komutu, imleç konuma ulaşana ve sonra sonlara ulaşana kadar uygulamanızı çalıştırır. Bu, geçerli iş parçacığının imleçte çalıştırıldıklarını ifade eder; bunun yerine, imleç noktasına ulaşan ilk iş parçacığının kesmeyi tetikley olduğu anlamına gelir. Bkz. [Hata Ayıklayıcı ile Kodda Gezinme](../debugger/navigating-through-code-with-the-debugger.md)

2. Geçerli **Kutucuğu İmleçten** Imleçe Çalıştır komutu, geçerli kutucukta yer alan tüm iş parçacıkları imleçe ulaşana ve sonra kesmelere ulaşana kadar uygulamanızı çalıştırır.

## <a name="debugging-windows"></a>Hata ayıklama Windows
 Belirli hata ayıklama pencerelerini kullanarak GPU iş parçacıklarını inceler, bayraklar ve dondurabilir. Daha fazla bilgi için bkz.

- [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)

- [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)

- [Nasıl: Paralel İzleme Penceresini Kullanma](../debugger/how-to-use-the-parallel-watch-window.md)

- [İş Parçacıklarında ve İşlemlerde Hata Ayıklama](../debugger/debug-threads-and-processes.md) (Hata Ayıklama Konumu araç çubuğu)

- [Nasıl: GPU İş Parçacıkları Penceresini Kullanma](../debugger/how-to-use-the-gpu-threads-window.md)

## <a name="data-synchronization-exceptions"></a>Veri Eşitleme Özel Durumları
 Hata ayıklayıcısı, yürütme sırasında çeşitli veri eşitleme koşullarını tanımlayabilir. Bir koşul algılandığında hata ayıklayıcı kesme durumuna girer. İki seçeneğiniz vardır:**Kesme veya** **Devam.** Özel Durumlar **iletişim kutusunu** kullanarak, hata ayıklayıcının bu koşulları algılayan ve hangi koşullar için bozacaklarını yapılandırabilirsiniz. Daha fazla bilgi için, [bkz. Managing Exceptions with the Debugger](../debugger/managing-exceptions-with-the-debugger.md). Yazılan veriler verilerin **değerini** değiştirmezse hata ayıklayıcının özel durumları yoksaymak zorunda olduğunu belirtmek için Seçenekler iletişim kutusunu da kullanabilirsiniz. Daha fazla bilgi için [bkz. Genel, Hata Ayıklama, Seçenekler İletişim Kutusu.](../debugger/general-debugging-options-dialog-box.md)

## <a name="troubleshooting"></a>Sorun giderme

### <a name="specifying-an-accelerator"></a>Hızlandırıcı belirtme
 GPU kodundaki kesme noktalarına yalnızca kod hızlandırıcıda çalışıyorsa isabet [eder::d irect3d_ref](/cpp/parallel/amp/reference/accelerator-class#direct3d_ref) (REF) hızlandırıcısı. Kodda bir hızlandırıcı belirtmezseniz, ref hızlandırıcısı proje özelliklerinde Hata Ayıklama **Hızlandırıcısı Türü olarak otomatik** olarak seçilir. Kodunuz bir hızlandırıcıyı açıkça seçerse, HATA AYıKLAMA sırasında REF hızlandırıcısı kullanılmaz ve GPU donanımınız hata ayıklama desteğine sahip olmadığı sürece kesme noktalarına isabet olmaz. Hata ayıklama sırasında REF hızlandırıcısını kullanması için kodunuzu yazarak bu sorunu giderebilirsiniz. Daha fazla bilgi için bkz. Proje özellikleri ve [C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)Hata Ayıklama Yapılandırması [accelerator_view](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) hızlandırıcı ve Project Ayarlar nesneleri kullanma.

### <a name="conditional-breakpoints"></a>Koşullu Kesme Noktaları
 GPU kodundaki koşullu kesme noktaları desteklene, ancak cihazda her ifade değerlendirilene değildir. Bir ifade cihazda değerlendirilenene kadar hata ayıklayıcıda değerlendirilir. Hata ayıklayıcısı cihazdan daha yavaş çalışır.

### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Hata: Seçilen Hata Ayıklama Hızlandırıcısı Türü ile ilgili bir yapılandırma sorunu var.
 Bu hata, proje ayarları ile hata ayıklamakta olduğunuz bilgisayar yapılandırması arasında bir tutarsızlık olduğunda gerçekleşir. Daha fazla bilgi için [bkz. Project Ayarlar C++ Hata Ayıklama Yapılandırması.](../debugger/project-settings-for-a-cpp-debug-configuration.md)

### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Hata: Seçilen Hata Ayıklama Hızlandırıcısı Türü için hata ayıklama sürücüsü hedef makineye yüklenmedi.
 Bu hata, uzak bir bilgisayarda hata ayıklarken gerçekleşir. Hata ayıklayıcı, sürücülerin uzak bilgisayarda yüklü olup olmadığını çalışma süresine kadar belirleyamaz. Sürücüler, grafik kartının üreticisinden kullanılabilir.

### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Hata: Uzak sitede Zaman Aşımı Algılama ve Kurtarma (TDR) devre dışı bırakılmıştır.
 Bu hesaplamaların C++ AMP algılama ve kurtarma işlemi (TDR) tarafından Windows zaman aralığını aşması mümkündür. Bu durumda hesaplama iptal edilir ve veriler kaybolur. Daha fazla bilgi için [bkz. TDR'leri C++ AMP.](/archive/blogs/nativeconcurrency/handling-tdrs-in-c-amp)

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: C++ AMP Uygulamanın Hata Ayıklaması](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)
- [Project Ayarlar C++ Hata Ayıklama Yapılandırması için Yapılandırma](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Visual Studio'da GPU Hata Ayıklamayı başlatma](/archive/blogs/nativeconcurrency/start-gpu-debugging-in-visual-studio-2012)