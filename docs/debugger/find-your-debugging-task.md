---
title: Hata ayıklama görevinizi bulma
description: Uygulamanızı hata ayıklamanıza yardımcı olacak hata ayıklama özelliğini belirleme
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302184"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Hata ayıklama görevinizi Visual Studio'da bulun

Hata ayıklama görevinizi Visual Studio hata ayıklamanın alakalı doğru özelliğiyle eşlemek için yardıma ihtiyacınız varsa, bu makalede sağlanan bağlantıları kullanın. Buradaki görevler in listesi, hata ayıklamak için kodu duraklatma, değişkenleri denetleme ve **Çıktı** penceresine ileti gönderme gibi yaygın görevleri içerir. Hata ayıklama özelliklerine genel bir bakış gerekiyorsa, bunun yerine [hata ayıklama ilk bakışta](debugger-feature-tour.md) bakın.

## <a name="pause-running-code"></a>Çalışan kodu duraklatma

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Hata içerebilecek bir kod satırını incelemek için çalışma kodunu duraklatma

Bir kırılma noktası ayarlayın. Daha fazla bilgi için [bkz.](using-breakpoints.md)

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Uygulamanızı belirli bir duruma ulaştığında duraklatma ve denetleme

Koşullu mantık kullanarak bir kesme noktasının nerede ve ne zaman etkinleştirildiğini denetlemek için koşullu bir kesme noktası deneyin. Daha fazla bilgi için [Kesme Noktası koşullarına](using-breakpoints.md#breakpoint-conditions)bakın.

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Yalnızca belirli bir nesnenin özelliği veya değeri değiştiğinde kodu duraklatma

C++için bir [veri kesme noktası](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)ayarlayın. 
::: moniker range=">= vs-2019"
.NET Core 3'u kullanan uygulamalar için bir [veri kesme noktası](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)da ayarlayabilirsiniz.
::: moniker-end

Aksi takdirde, yalnızca C# ve F# için [koşullu bir kesme noktası olan bir nesne kimliğini izleyebilirsiniz.](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Belirli bir yinelemede bir döngü içindeki kodu duraklatma

Koşul olarak **Hit sayısını** kullanarak bir kesme noktası ayarlayın. Daha fazla bilgi için [Bkz. Hit sayısı.](using-breakpoints.md#set-a-hit-count-condition)

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>İşlev adını bildiğin ancak konumunu bilmediğin bir işlevin başında ki kodu duraklatma

Bunu bir işlev kesme noktasıyla yapabilirsiniz. Daha fazla bilgi için [bkz.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Aynı ada sahip birden çok işlevin başında ki kodu duraklatma

Aynı ada sahip birden çok işleviniz varsa (farklı projelerde aşırı yüklü işlevler veya işlevler), bir [işlev kesme noktası](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)kullanabilirsiniz.

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Kesme noktalarınızı yönetme ve izleme

Kesme **Noktaları** penceresini kullanın. Daha fazla bilgi için [bkz.](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Belirli bir işlenmiş veya işlenmemiş özel durum atıldığında kodu duraklatma ve hata ayıklama

Özel Durum Yardımcısı size bir hatanın nerede oluştuğunu gösterse de, belirli hatayı duraklatmak ve hata ayıklamak istiyorsanız, [hata ayıklayıcıya bir özel durum atıldığında kırılmasını söyleyebilirsiniz.](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)

### <a name="set-a-breakpoint-from-the-call-stack"></a>Arama yığınından bir kesme noktası ayarlama

**Çağrı Yığını** pencerelerinde yürütme akışını veya işlevleri görüntülerken kodu duraklatmak ve hata ayıklamak istiyorsanız, [Bkz. Çağrı Yığını penceresinde bir kesme noktası ayarla.](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Belirli bir derleme yönergesindeki kodu duraklatma

Bunu, Sökme [penceresinden bir kesme noktası ayarlayarak](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)yapabilirsiniz.

## <a name="execute-code"></a>Kodu yürütme

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Hata ayıklama sırasında kodunuzu geçmek için komutları öğrenin

Daha fazla bilgi için [hata ayıklayıcıyla kodu gezin'](navigating-through-code-with-the-debugger.md)e bakın.

## <a name="inspect-data"></a>Verileri inceleme

### <a name="check-the-value-of-variables-while-running-your-app"></a>Uygulamanızı çalıştırırken değişkenlerin değerini kontrol edin

[Veri ipuçlarını](view-data-values-in-data-tips-in-the-code-editor.md) kullanarak değişkenlerin üzerine dalın veya [Otomatik ve Yerel ler penceresindeki değişkenleri inceleyin.](autos-and-locals-windows.md)

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Belirli bir değişkenin değişen değerini gözlemleyin

Değişkene bir saat ayarlayın. Daha fazla bilgi için [bkz.](watch-and-quickwatch-windows.md)

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Hata ayıklama penceresi için çok uzun olan dizeleri görüntüleme

Hata ayıklama sırasında yerleşik [dize görselleştiricisini](view-strings-visualizer.md) açın.

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

### <a name="customize-information-shown-in-the-debugger"></a>Hata ayıklamada gösterilen bilgileri özelleştirme

Farklı hata ayıklama pencerelerinde değer olarak nesne türü dışındaki bilgileri göstermek isteyebilirsiniz. C#, Visual Basic, F#ve C++/CLI kodu için [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliğini kullanın. Daha gelişmiş seçenekler için, özel bir [görselleştirici](create-custom-visualizers-of-data.md)oluşturarak kullanıcı arabirimi'ni özelleştirebilirsiniz.

Yerel C++için [NatVis çerçevesini](create-custom-views-of-native-objects.md)kullanın.

### <a name="configure-debugger-settings"></a>Hata ayıklama ayarlarını yapılandırma

Hata ayıklama seçeneklerini ve hata ayıklama proje ayarlarını yapılandırmak için [hata ayıklama ayarları ve hazırlama](debugger-settings-and-preparation.md)bölümüne bakın.

## <a name="additional-tasks"></a>Ek görevler

### <a name="fix-an-exception"></a>Özel durumu düzeltme

Bkz. [Bir özel durum düzeltin.](write-better-code-with-visual-studio.md#fix-an-exception)

### <a name="edit-code-during-a-debugging-session"></a>Hata ayıklama oturumu sırasında kodu düzenledi

[Edit'i](edit-and-continue.md)kullanın ve devam edin. XAML için [XAML Sıcak Yeniden Yükleme'yi](../xaml-tools/xaml-hot-reload.md)kullanın.

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Kodu değiştirmeden Çıktı penceresine ileti gönderme

Bir izleme noktası ayarlayın. Daha fazla bilgi için [bkz.](using-tracepoints.md)

## <a name="view-the-order-in-which-functions-are-called"></a>Fonksiyonların çağrılma sırasını görüntüleme

Arama [yığınını nasıl görüntüleyin.](how-to-use-the-call-stack-window.md)

### <a name="debug-on-remote-machines"></a>Uzak makinelerde hata ayıklama

Bkz. [Uzaktan hata ayıklama](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Zaten çalışan bir uygulamanın hata ayıklama

Bkz. [Çalışan işlemlere ekle.](attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="debug-multithreaded-applications"></a>Çok iş parçacıklı uygulamaların hatalarını ayıklama

Bkz. [Hata Ayıklama çok iş parçacığı uygulamaları.](debug-multithreaded-applications-in-visual-studio.md)

### <a name="fix-performance-issues"></a>Performans sorunlarını düzeltme

[Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)