---
title: GPU kodunda hata ayıklama | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02900bc7e0d3746e465c8e4741036605a76190d4
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599959"
---
# <a name="debugging-gpu-code"></a>GPU Kodunda Hata Ayıklama
Grafik işleme birimi (GPU) üzerinde çalışan C++ kodunda hata ayıklaması yapabilirsiniz. Visual Studio 'da GPU hata ayıklama desteği, yarış algılama, işlem başlatma ve bunlara ekleme ve hata ayıklama pencerelerini tümleştirme içerir.

## <a name="supported-platforms"></a>Desteklenen Platformlar
 Hata ayıklama,, [!INCLUDE[win7](../debugger/includes/win7_md.md)] [!INCLUDE[win8](../debugger/includes/win8_md.md)] Windows 10, [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] ve Windows Server 2016 ' de desteklenir. Yazılım öykünücüsünde hata ayıklama için, [!INCLUDE[win8](../debugger/includes/win8_md.md)] Windows 10 veya [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] windows Server 2016 gereklidir. Donanımda hata ayıklama için, grafik kartınızın sürücülerini yüklemelisiniz. Tüm donanım satıcıları tüm hata ayıklayıcı özelliklerini uygulamaz. Sınırlamalar için satıcı belgelerine bakın.

> [!NOTE]
> Visual Studio 'da GPU hata ayıklamayı desteklemek isteyen bağımsız donanım satıcıları, VSD3DDebug arabirimini uygulayan ve kendi sürücülerini hedefleyen bir DLL oluşturmanız gerekir.

## <a name="configuring-gpu-debugging"></a>GPU hata ayıklamayı yapılandırma
 Hata ayıklayıcı aynı uygulama yürütmesindeki hem CPU kodunda hem de GPU kodunda kesilebilir. Varsayılan olarak, hata ayıklayıcı CPU kodunu keser. GPU kodunda hata ayıklamak için şu iki adımdan birini kullanın:

- **Standart** araç çubuğundaki **hata ayıklama türü** listesinde **yalnızca GPU**' yı seçin.

- **Çözüm Gezgini**, projenin kısayol menüsünde **Özellikler**' i seçin. **Özellik sayfaları** iletişim kutusunda, **hata ayıklama**' ı seçin ve ardından yalnızca **hata ayıklayıcı türü** listesinde **GPU** ' yı seçin.

## <a name="launching-and-attaching-to-applications"></a>Uygulamalara başlatma ve ekleme
 GPU hata ayıklamasını başlatmak ve durdurmak için Visual Studio hata ayıklama komutlarını kullanabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcıyla kod aracılığıyla gezinme](../debugger/navigating-through-code-with-the-debugger.md). Ayrıca, GPU hata ayıklayıcısını çalışan bir işleme ekleyebilirsiniz, ancak bu işlem yalnızca GPU kodunu yürütür. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Imleç ve Imlece çalıştırmak için geçerli kutucuğu Çalıştır
 GPU 'da hata ayıklarken, imleç konumuna çalıştırmak için iki seçeneğiniz vardır. Her iki seçenek için de komutlar, kod düzenleyicisinin kısayol menüsünde bulunur.

1. **Imlece Çalıştır** komutu, İmlecin konumuna ulaşana kadar uygulamanızı çalıştırır ve ardından kesilir. Bu, geçerli iş parçacığının imlece çalıştığını göstermez; Bunun yerine, imleç noktasına ulaşan ilk iş parçacığının kesmeyi tetiklediği anlamına gelir. Bkz [. hata ayıklayıcı Ile kod aracılığıyla gezinme](../debugger/navigating-through-code-with-the-debugger.md)

2. **Şu anki kutucuğu Imlece Çalıştır** komutu, geçerli kutucuktaki tüm iş parçacıklarının imlece ulaşmasını ve sonra kesilene kadar uygulamanızı çalıştırır.

## <a name="debugging-windows"></a>Windows hata ayıklama
 Belirli hata ayıklama pencerelerini kullanarak GPU iş parçacıklarını inceleyebilir, işaret edebilir ve dondurabilirsiniz. Daha fazla bilgi için bkz.

- [Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)

- [Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)

- [Nasıl yapılır: paralel Izleme penceresini kullanma](../debugger/how-to-use-the-parallel-watch-window.md)

- [Hata ayıklama Iş parçacıkları ve süreçler](../debugger/debug-threads-and-processes.md) (hata ayıklama konumu araç çubuğu)

- [Nasıl yapılır: GPU Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md)

## <a name="data-synchronization-exceptions"></a>Veri eşitleme özel durumları
 Hata ayıklayıcı yürütme sırasında çeşitli veri eşitleme koşullarını tanımlayabilir. Bir koşul algılandığında, hata ayıklayıcı kesme durumuna girer. İki seçeneğiniz vardır:**Break** veya **Continue**. **Özel durumlar** iletişim kutusunu kullanarak, hata ayıklayıcının bu koşulları algıladığını ve ayrıca hangi koşulları kesmeyeceğini yapılandırabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı Ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md). Ayrıca, yazılan veriler verilerin değerini değiştirmezse hata ayıklayıcının özel durumları yoksayması gerektiğini belirtmek için **Seçenekler** iletişim kutusunu da kullanabilirsiniz. Daha fazla bilgi için bkz. [Genel, hata ayıklama, Seçenekler Iletişim kutusu](../debugger/general-debugging-options-dialog-box.md).

## <a name="troubleshooting"></a>Sorun giderme

### <a name="specifying-an-accelerator"></a>Hızlandırıcı belirtme
 GPU kodundaki kesme noktaları yalnızca, kod [Hızlandırıcı::d irect3d_ref](/cpp/parallel/amp/reference/accelerator-class#direct3d_ref) (Ref) hızlandırıcısında çalışıyorsa isabet alır. Kodunuzda bir Hızlandırıcı belirtmezseniz, başvuru Hızlandırıcısı proje özelliklerinde **hata ayıklama Hızlandırıcı türü** olarak otomatik seçilir. Kodunuz açıkça bir Hızlandırıcı seçerse, başvuru Hızlandırıcısı hata ayıklama sırasında kullanılmaz ve GPU donanımınızın hata ayıklama desteği yoksa kesme noktaları isabet etmez. Hata ayıklama sırasında başvuru hızlandırıcıyı kullanması için kodunuzu yazarak bunu ortadan kaldırabilirsiniz. Daha fazla bilgi için bkz. proje özellikleri ve [bir C++ hata ayıklama yapılandırması için](../debugger/project-settings-for-a-cpp-debug-configuration.md) [accelerator_view nesneleri](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) ve proje ayarlarını kullanma.

### <a name="conditional-breakpoints"></a>Koşullu kesme noktaları
 GPU kodundaki koşullu kesme noktaları desteklenir, ancak cihazda her ifade değerlendirilemiyor. Bir ifade cihazda değerlendirilemez, hata ayıklayıcıda değerlendirilir. Hata ayıklayıcının cihazdan daha yavaş çalışması olasıdır.

### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Hata: Seçili hata ayıklama Hızlandırıcı türünde bir yapılandırma sorunu var.
 Bu hata, proje ayarları ile hata ayıkladığınız BILGISAYARıN yapılandırması arasında bir tutarsızlık olduğunda meydana gelir. Daha fazla bilgi için bkz. [C++ hata ayıklama yapılandırması Için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Hata: Seçili hata ayıklama Hızlandırıcı türü için hata ayıklama sürücüsü hedef makinede yüklü değil.
 Uzak bir bılgısayarda hata ayıklaması yapıyorsanız bu hata oluşur. Hata ayıklayıcı, sürücülerin uzak BILGISAYARA yüklenip yüklenmediğine bakılmaksızın çalışma zamanına kadar belirleyemez. Sürücüler, grafik kartının üreticisinden kullanılabilir.

### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Hata: uzak sitede zaman aşımı algılama ve kurtarma (TDR) devre dışı bırakılmalıdır.
 C++ AMP hesaplamaların, Windows zaman aşımı algılama ve kurtarma işlemi (TDR) tarafından ayarlanan varsayılan zaman aralığını aşması mümkündür. Bu durumda, hesaplama iptal edilir ve veriler kaybolur. Daha fazla bilgi için bkz. [C++ amp Içindeki TDRs işleme](/archive/blogs/nativeconcurrency/handling-tdrs-in-c-amp).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: C++ AMP uygulamasında hata ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)
- [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Visual Studio 'da GPU hata ayıklamayı başlatma](/archive/blogs/nativeconcurrency/start-gpu-debugging-in-visual-studio-2012)