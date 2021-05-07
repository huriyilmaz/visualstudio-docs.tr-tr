---
title: SSS - Hata ayıklama özelliğinizi bulma
description: Uygulamanızda hata ayıklamanıza yardımcı olacak hata ayıklayıcı özelliğini belirlemenize yardımcı olmak için sık sorulan sorular
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c215b232c64b97c57285618056ee4675587b48e
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800498"
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

  **İsabet sayısı** ' nı koşul olarak kullanarak bir kesme noktası ayarlayın. Daha fazla bilgi için bkz. [Hit count](using-breakpoints.md#set-a-hit-count-condition).

- **İşlev adını biliyor ancak konumunu bilmiyorken işlevin başındaki kodu duraklatma**

  Bunu bir işlev kesme noktasıyla da yapabiliriz. Daha fazla bilgi için [bkz. İşlev kesme noktaları ayarlama.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

- **Aynı adla birden çok işlevin başında kodu duraklatma**

  Aynı adla birden çok işleviniz (farklı projelerde aşırı yüklenmiş işlevler veya işlevler) varsa işlev kesme [noktası kullanabilirsiniz.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

- **Kesme noktalarınızı yönetme ve izleme**

  Kesme **Noktaları penceresini** kullanın. Daha fazla bilgi için [bkz. Kesme noktaları yönetme.](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)

- **Kod duraklatma ve belirli bir tanıtıcı veya işsiz özel durum olduğunda hata ayıklama**

  Özel Durum Yardımcısı size bir hatanın nerede olduğunu gösteriyor olsa da, belirli bir hatayı duraklatmak ve hata ayıklamak için hata ayıklayıcıya bir özel durum [sanız kesmesi söylemek için kullanabilirsiniz.](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)

- **Çağrı yığınından bir kesme noktası ayarlama**

  Yürütme akışını incelerken veya Çağrı Yığını pencerelerde işlevleri görüntülerken kodu duraklatmak ve hata ayıklamak **için** bkz. Çağrı Yığını penceresinde [bir kesme noktası ayarlama.](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

- **Belirli bir derleme yönergesi sırasında kodu duraklatma**

  Bunu yapmak için [Disassembly penceresinden bir kesme noktası ayarlarsınız.](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

## <a name="execute-code"></a>Kodu yürütme

- **Hata ayıklarken kodunuz boyunca adım adım atma komutlarını öğrenin**

  Daha fazla bilgi için [bkz. Hata ayıklayıcı ile kodda gezinme.](navigating-through-code-with-the-debugger.md)

## <a name="inspect-data"></a>Verileri inceleme

- **Uygulamanızı çalıştırma sırasında değişkenlerin değerini denetleme**

  Veri ipuçlarını kullanarak [değişkenlerin üzerine](view-data-values-in-data-tips-in-the-code-editor.md) gelin [veya Otomatikler ve YerelLer penceresinde değişkenleri inceleyebilirsiniz.](autos-and-locals-windows.md)

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

  İzleme noktası ayarlayın. Daha fazla bilgi için [bkz. İzleme noktaları kullanma.](using-tracepoints.md)

- **İşlevlerin çağrılma sıralarını görüntüleme**

  Bkz. [Çağrı yığınını görüntüleme.](how-to-use-the-call-stack-window.md)

- **Uzak makinelerde hata ayıklama**

  Bkz. [Uzaktan hata ayıklama.](remote-debugging.md)

- **Performans sorunlarını çözme**

  Bkz. [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
