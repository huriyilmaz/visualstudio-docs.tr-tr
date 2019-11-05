---
title: Hata ayıklama görevinizi bulma
description: Uygulamanızda hata ayıklamanıza yardımcı olacak hata ayıklayıcı özelliğini belirler
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
ms.openlocfilehash: b833d8b68af418b727861226df41c700d582805e
ms.sourcegitcommit: d55438841123aad56a524a65332a86ad67af386b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73599289"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Visual Studio 'da hata ayıklama görevinizi bulma

Hata ayıklama görevinizi ilgili Visual Studio hata ayıklayıcının doğru özelliğine eşlemek için yardıma ihtiyacınız varsa, bu makalede sağlanan bağlantıları kullanın. Buradaki görev listesi, hata ayıklama, değişkenleri İnceleme ve **Çıkış** penceresine ileti gönderme gibi genel görevleri içerir. Hata ayıklayıcı özelliklerine genel bir bakış gerekirse, bkz. bunun yerine [hata ayıklayıcıya](debugger-feature-tour.md) bakın.

## <a name="pause-running-code"></a>Çalışan kodu Duraklat

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Bir hata içerebilecek kod satırını incelemek için kodu çalıştırmayı duraklatın

Bir kesme noktası ayarlayın. Daha fazla bilgi için bkz. [kesme noktaları kullanma](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Uygulamanızı belirli bir duruma ulaştığında duraklatın ve inceleyin

Bir kesme noktasının koşullu mantık kullanarak nerede ve ne zaman etkin olduğunu denetlemek için koşullu bir kesme noktası deneyin. Daha fazla bilgi için bkz. [kesme noktası koşulları](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Kodu yalnızca belirli bir nesnenin özelliği veya değeri değiştiğinde Duraklat

İçin C++bir [veri kesme noktası](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)ayarlayın. 
::: moniker range=">= vs-2019"
.NET Core 3 kullanan uygulamalar için bir [veri kesme noktası](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)da ayarlayabilirsiniz.
::: moniker-end

Aksi takdirde, C# ve F# IÇIN, bir [nesne kimliğini koşullu kesme noktasıyla izleyebilirsiniz](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Belirli bir yinelemede döngü içindeki kodu duraklatma

**İsabet sayısı** ' nı koşul olarak kullanarak bir kesme noktası ayarlayın. Daha fazla bilgi için bkz. [isabet sayısı](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>İşlev adını bildiğiniz ancak konumunu not ettiğinizde bir işlevin başlangıcında kodu duraklatma

Bunu bir işlev kesme noktası ile yapabilirsiniz. Daha fazla bilgi için bkz. [işlev kesme noktalarını ayarlama](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Aynı ada sahip birden çok işlevin başlangıcında kodu Duraklat

Aynı ada sahip birden fazla işleviniz varsa (farklı projelerde aşırı yüklenmiş işlevler veya işlevler), bir [işlev kesme noktası](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)kullanabilirsiniz.

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Kesme noktalarınızı yönetin ve izleyin

**Kesme noktaları** penceresini kullanın. Daha fazla bilgi için bkz. [kesme noktalarını yönetme](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Belirli bir işlenmiş veya işlenmemiş özel durum oluştuğunda kodu duraklatma ve hata ayıklama

Özel durum Yardımcısı sizi bir hata oluştuğunu gösteriyor olsa da, belirli bir hatayı duraklatmak ve hata ayıklamak istiyorsanız, [bir özel durum oluştuğunda hata ayıklayıcıya kesilmesini söyleyebilirsiniz](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Çağrı yığınından bir kesme noktası ayarlayın

Yürütme akışını incelerken veya **çağrı yığını** pencerelerinin işlevlerini görüntülerken kodu duraklatmak ve hata ayıklamak istiyorsanız, bkz. [çağrı yığını penceresinde bir kesme noktası ayarlama](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Belirli bir derleme yönergesinde kodu duraklatma

Bunu, [ayrıştırma penceresinden bir kesme noktası ayarlayarak](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)yapabilirsiniz.

## <a name="execute-code"></a>Kodu Yürüt

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Hata ayıklarken kodunuzda adım adım ilerme komutlarını öğrenin

Daha fazla bilgi için bkz. [hata ayıklayıcıyla koda gitme](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Verileri inceleme

### <a name="check-the-value-of-variables-while-running-your-app"></a>Uygulamanızı çalıştırırken değişkenlerin değerini denetleyin

[Veri ipuçlarını](view-data-values-in-data-tips-in-the-code-editor.md) kullanarak değişkenlerin üzerine gelin veya [oto ve Yereller penceresinde değişkenleri inceleyin](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Belirli bir değişkenin değişen değerini gözlemleyin

Değişkende bir izleme ayarlayın. Daha fazla bilgi için bkz. [değişkenlerde Izleme ayarlama](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Hata ayıklayıcı penceresi için çok uzun olan dizeleri görüntüleme

Hata ayıklama sırasında yerleşik [dize görselleştiricisi](view-strings-visualizer.md) ' i açın.

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

### <a name="customize-information-shown-in-the-debugger"></a>Hata ayıklayıcıda gösterilen bilgileri özelleştirme

Nesne türü dışındaki bilgileri farklı hata ayıklayıcı pencerelerinin değeri olarak göstermek isteyebilirsiniz. , C#Visual Basic, F#ve C++/CLI kodu için [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliğini kullanın. Daha gelişmiş seçenekler için [özel bir Görselleştirici](create-custom-visualizers-of-data.md)oluşturarak Kullanıcı arabirimini de özelleştirebilirsiniz.

Yerel C++için [Natvis çerçevesini](create-custom-views-of-native-objects.md)kullanın.

### <a name="configure-debugger-settings"></a>Hata ayıklayıcı ayarlarını yapılandırma

Hata ayıklayıcı seçeneklerini ve hata ayıklayıcı proje ayarlarını yapılandırmak için bkz. [hata ayıklayıcı ayarları ve hazırlığı](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Ek görevler

### <a name="fix-an-exception"></a>Özel durumu çözme

Bkz. [bir özel durumu giderme](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Hata ayıklama oturumu sırasında kodu düzenleme

[Düzenle ve devam et ' i](edit-and-continue.md)kullanın. XAML için [xaml etkin yeniden yükleme](../xaml-tools/xaml-hot-reload.md)kullanın.

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Kod değiştirmeden çıkış penceresine ileti gönderme

İzleme noktası ayarlayın. Daha fazla bilgi için bkz. [izleme noktalarını kullanma](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>İşlevlerin çağrıldığı sırayı görüntüleme

Bkz. [çağrı yığınını görüntüleme](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Uzak makinelerde hata ayıkla

Bkz. [Uzaktan hata ayıklama](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Zaten çalışan bir uygulamada hata ayıklama

Bkz. [çalışan Işlemlere iliştirme](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Çok iş parçacıklı uygulamaların hatalarını ayıklama

Bkz. çok [iş parçacıklı uygulamalarda hata ayıklama](debug-multithreaded-applications-in-visual-studio.md).