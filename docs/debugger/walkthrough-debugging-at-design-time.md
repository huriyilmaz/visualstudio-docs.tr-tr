---
title: Tasarım zamanında hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: beb16ae52f880e31bd19a185d47b13c02026752f
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916151"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Visual Studio 'da tasarım zamanında hata ayıklama (C#, C++/CLI, Visual Basic, F#)

Tasarım zamanında yerine uygulama çalışırken kodda hata ayıklamak için çalışıyor, kullanabileceğiniz **hemen** penceresi.

Dizi bildirim temelli veri bağlama senaryoları gibi XAML Tasarımcısı 'ndan bir uygulamanın arkasındaki XAML kodunda hata ayıklamak için, **Işleme eklemek** > **hata ayıklama** kullanabilirsiniz.

## <a name="use-the-immediate-window"></a>Komut penceresi kullanın

Visual Studio kullanabileceğiniz **hemen** uygulamanızı çalıştırmadan bir işlev veya alt yordamı yürütmek için penceresi. İşlev veya alt yordam bir kesme noktası içeriyorsa, Visual Studio kesme noktasında çalışmamasına neden olur. Ardından, programınızın durumunu incelemek için hata ayıklayıcı penceresini kullanabilirsiniz. Bu özelliğin adı *tasarım zamanında hata ayıklama*.

Aşağıdaki örnek, Visual Basic'te. Ayrıca C#, F#ve C++/CLI uygulamalarında tasarım zamanında **hemen** penceresini de kullanabilirsiniz.

1. Boş bir Visual Basic konsol uygulamasına aşağıdaki kodu yapıştırın:

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Satırına bir kesme noktası ayarlamak **End işlevi**.

1. Açık **hemen** penceresini seçerek **hata ayıklama** > **Windows** > **hemen**. Tür `?MyFunction` penceresi ve ENTER tuşuna **Enter**.

   Kesme noktası isabet ve değeri olan **MyFunction** içinde **Yereller** penceresi **1**. Uygulama kesme modunda çalışırken, çağrı yığını ve diğer hata ayıklama windows inceleyebilirsiniz.

1. Seçin **devam** Visual Studio araç. Uygulamanın sona erer ve **1** döndürülür **hemen** penceresi. Yine de tasarım modunda olduğundan emin olun.

1. Tür `?MyFunction` içinde **hemen** penceresini tekrar ve tuşuna **Enter**. Kesme noktası isabet ve değeri olan **MyFunction** içinde **Yereller** penceresi **2**.

1. Seçmeden **devam**, türü `?MySub()` içinde **hemen** penceresi ve ENTER tuşuna **Enter**. Kesme noktası isabet ve değeri olan **MyFunction** içinde **Yereller** penceresi **3**. Uygulama kesme modundayken, uygulama durumunu inceleyebilirsiniz.

1. Seçin **devam**. Kesme noktası isabet yeniden ve değeri olan **MyFunction** içinde **Yereller** penceresi, artık **2**. **Hemen** pencereyi döndürür **ifade değerlendirildi ve değeri**.

1. Seçin **devam** yeniden. Uygulamanın sona erer ve **2** döndürülür **hemen** penceresi. Yine de tasarım modunda olduğundan emin olun.

1. İçeriğini temizlemek için **hemen** penceresi, pencere seçip sağ **Tümünü Temizle**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>XAML tasarımcısına ekleyerek tasarım zamanında özel bir XAML denetiminde hata ayıklama

1. Çözümünüzü veya projenizi Visual Studio 'da açın.

1. Çözüm/proje oluşturun.

1. Hata ayıklamak istediğiniz özel denetimi içeren XAML sayfasını açın.

   Windows Build 16299 veya üstünü hedefleyen UWP projeleri için bu adım *Uıwpsurface. exe* işlemini başlatacak. Windows Build 16299 ' den önceki WPF veya UWP sürümlerinde bu adım *Xdesproc. exe* işlemini başlatacak.

1. Visual Studio 'nun ikinci bir örneğini açın. İkinci örnekte bir çözüm veya proje açmayın.

1. Visual Studio 'nun ikinci örneğinde **Hata Ayıkla** menüsünü açın ve **işleme Ekle...** seçeneğini belirleyin.

1. Proje türüne bağlı olarak (önceki adımlara bakın), kullanılabilir işlemler listesinden *Uıwpsurface. exe* veya *xdesproc. exe* işlemini seçin.

1. **Işleme İliştir** Iletişim kutusunun **İliştir** alanına hata ayıklamak istediğiniz özel denetim için doğru kod türünü seçin.

   Özel denetiminiz bir .NET dilinde yazılmışsa, **yönetilen (CoreCLR)** gibi uygun .NET kod türünü seçin. Özel denetiminiz ' de C++yazılmışsa, **Yerel**' i seçin.

1. **Ekle** düğmesine tıklayarak Visual Studio 'nun ikinci örneğini iliştirin.

1. Visual Studio 'nun ikinci örneğinde, hata ayıklamak istediğiniz özel denetimle ilişkili kod dosyalarını açın. Tüm çözüm veya proje için değil, yalnızca dosyaları açık olduğunuzdan emin olun.

1. Gerekli kesme noktalarını önceden açılan dosyalara yerleştirin.

1. Visual Studio 'nun ilk örneğinde, hata ayıklamak istediğiniz özel denetimi içeren XAML sayfasını kapatın (önceki adımlarda açtığınız sayfa).

1. Visual Studio 'nun ilk örneğinde, önceki adımda kapattığınız XAML sayfasını açın. Bu, Visual Studio 'nun ikinci örneğinde ayarladığınız ilk kesme noktasında hata ayıklayıcının durdurulmasına neden olur.

1. Visual Studio 'nun ikinci örneğindeki kodda hata ayıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)