---
title: SSS-hata ayıklama özelliğini bulma
description: Uygulamanızda hata ayıklamanıza yardımcı olacak hata ayıklayıcı özelliğini belirlemenize yardımcı olmak için sık sorulan sorular
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
ms.openlocfilehash: a34aa926fca081a498173cd5fcc439a6b3886ba7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728037"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>SSS-Visual Studio 'da ihtiyacınız olan hata ayıklama özelliğini bulma

Hata ayıklama görevinizi ilgili Visual Studio hata ayıklayıcının doğru özelliğine eşlemek için yardıma ihtiyacınız varsa, bu makalede sağlanan bağlantıları kullanın. Buradaki görev listesi, hata ayıklama, değişkenleri İnceleme ve **Çıkış** penceresine ileti gönderme gibi genel görevleri içerir. Hata ayıklayıcı özelliklerine genel bir bakış gerekirse, bkz. bunun yerine [hata ayıklayıcıya](debugger-feature-tour.md) bakın.

## <a name="fix-an-exception"></a>Özel durumu çözme

- Bkz. [bir özel durumu giderme](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Çalışan kodu Duraklat

- **Bir hata içerebilecek kod satırını incelemek için kodu çalıştırmayı duraklatın**

  Bir kesme noktası ayarlayın. Daha fazla bilgi için bkz. [kesme noktaları kullanma](using-breakpoints.md).

- **Uygulamanızı belirli bir duruma ulaştığında duraklatın ve inceleyin**

  Bir kesme noktasının koşullu mantık kullanarak nerede ve ne zaman etkin olduğunu denetlemek için koşullu bir kesme noktası deneyin. Daha fazla bilgi için bkz. [kesme noktası koşulları](using-breakpoints.md#breakpoint-conditions).

- **Kodu yalnızca belirli bir nesnenin özelliği veya değeri değiştiğinde Duraklat**

  C++ için bir [veri kesme noktası](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)ayarlayın. 
  ::: moniker range=">= vs-2019"
  .NET Core 3 kullanan uygulamalar için bir [veri kesme noktası](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)da ayarlayabilirsiniz.
  ::: moniker-end

  Aksi halde, yalnızca C# ve F # için bir [nesne kimliğini koşullu kesme noktasıyla izleyebilirsiniz](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Belirli bir yinelemede döngü içindeki kodu duraklatma**

  **İsabet sayısı** ' nı koşul olarak kullanarak bir kesme noktası ayarlayın. Daha fazla bilgi için bkz. [isabet sayısı](using-breakpoints.md#set-a-hit-count-condition).

- **İşlev adını bildiğiniz ancak konumunu not ettiğinizde bir işlevin başlangıcında kodu duraklatma**

  Bunu bir işlev kesme noktası ile yapabilirsiniz. Daha fazla bilgi için bkz. [işlev kesme noktalarını ayarlama](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Aynı ada sahip birden çok işlevin başlangıcında kodu Duraklat**

  Aynı ada sahip birden fazla işleviniz varsa (farklı projelerde aşırı yüklenmiş işlevler veya işlevler), bir [işlev kesme noktası](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)kullanabilirsiniz.

- **Kesme noktalarınızı yönetin ve izleyin**

  **Kesme noktaları** penceresini kullanın. Daha fazla bilgi için bkz. [kesme noktalarını yönetme](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Belirli bir işlenmiş veya işlenmemiş özel durum oluştuğunda kodu duraklatma ve hata ayıklama**

  Özel durum Yardımcısı sizi bir hata oluştuğunu gösteriyor olsa da, belirli bir hatayı duraklatmak ve hata ayıklamak istiyorsanız, [bir özel durum oluştuğunda hata ayıklayıcıya kesilmesini söyleyebilirsiniz](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Çağrı yığınından bir kesme noktası ayarlayın**

  Yürütme akışını incelerken veya **çağrı yığını** pencerelerinin işlevlerini görüntülerken kodu duraklatmak ve hata ayıklamak istiyorsanız, bkz. [çağrı yığını penceresinde bir kesme noktası ayarlama](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Belirli bir derleme yönergesinde kodu duraklatma**

  Bunu, [ayrıştırma penceresinden bir kesme noktası ayarlayarak](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)yapabilirsiniz.

## <a name="execute-code"></a>Kodu Yürüt

- **Hata ayıklarken kodunuzda adım adım ilerme komutlarını öğrenin**

  Daha fazla bilgi için bkz. [hata ayıklayıcıyla koda gitme](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Verileri inceleme

- **Uygulamanızı çalıştırırken değişkenlerin değerini denetleyin**

  [Veri ipuçlarını](view-data-values-in-data-tips-in-the-code-editor.md) kullanarak değişkenlerin üzerine gelin veya [oto ve Yereller penceresinde değişkenleri inceleyin](autos-and-locals-windows.md).

- **Belirli bir değişkenin değişen değerini gözlemleyin**

  Değişkende bir izleme ayarlayın. Daha fazla bilgi için bkz. [değişkenlerde Izleme ayarlama](watch-and-quickwatch-windows.md).

- **Hata ayıklayıcı penceresi için çok uzun olan dizeleri görüntüleme**

  Hata ayıklama sırasında yerleşik [dize görselleştiricisi](view-strings-visualizer.md) ' i açın.

## <a name="debug-an-app-that-is-already-running"></a>Zaten çalışan bir uygulamada hata ayıklama

- Bkz. [çalışan Işlemlere iliştirme](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Çok iş parçacıklı uygulamaların hatalarını ayıklama

- Bkz. çok [iş parçacıklı uygulamalarda hata ayıklama](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

- **Hata ayıklayıcı ayarlarını yapılandırma**

  Hata ayıklayıcı seçeneklerini ve hata ayıklayıcı proje ayarlarını yapılandırmak için bkz. [hata ayıklayıcı ayarları ve hazırlığı](debugger-settings-and-preparation.md).

- **Hata ayıklayıcıda gösterilen bilgileri özelleştirme**

  Nesne türü dışındaki bilgileri farklı hata ayıklayıcı pencerelerinin değeri olarak göstermek isteyebilirsiniz. C#, Visual Basic, F # ve C++/CLı kodu için [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliğini kullanın. Daha gelişmiş seçenekler için [özel bir Görselleştirici](create-custom-visualizers-of-data.md)oluşturarak Kullanıcı arabirimini de özelleştirebilirsiniz.

  Yerel C++ için [Natvis çerçevesini](create-custom-views-of-native-objects.md)kullanın.

## <a name="additional-tasks"></a>Ek görevler

- **Hata ayıklama oturumu sırasında kodu düzenleme**

  [Düzenle ve devam et ' i](edit-and-continue.md)kullanın. XAML için [xaml etkin yeniden yükleme](../xaml-tools/xaml-hot-reload.md)kullanın.

- **Kod değiştirmeden çıkış penceresine ileti gönderme**

  İzleme noktası ayarlayın. Daha fazla bilgi için bkz. [izleme noktalarını kullanma](using-tracepoints.md).

- **İşlevlerin çağrıldığı sırayı görüntüleme**

  Bkz. [çağrı yığınını görüntüleme](how-to-use-the-call-stack-window.md).

- **Uzak makinelerde hata ayıkla**

  Bkz. [Uzaktan hata ayıklama](remote-debugging.md).

- **Performans sorunlarını çözme**

  Bkz [. profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
