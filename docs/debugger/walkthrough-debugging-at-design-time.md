---
title: Tasarım zamanında hata ayıkla | Microsoft Docs
description: Uygulamayı çalıştırmadan, tasarım zamanında kodun hatalarını ayıklamak için hemen penceresini kullanın. Bir işlevi yürütebilir ve bir kesme noktası isabet edildiğinde durumu inceleyebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 360bdb1ac3d3dfce56a60f1e1c33e97d76885c6a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627765"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Visual Studio 'de tasarım zamanında hata ayıklama (C#, C++/clı, Visual Basic, F #)

Bir uygulama çalışırken, tasarım zamanında kodda hata ayıklamak için, **hemen** penceresini kullanabilirsiniz.

Dizi temelli veri bağlama senaryoları gibi XAML Tasarımcısı 'ndan bir uygulamanın arkasındaki xaml kodunda hata ayıklamak için, **hata ayıklama**  >  **iliştirme işlemini** kullanabilirsiniz.

## <a name="use-the-immediate-window"></a>Hemen penceresini kullanma

uygulamanızı çalıştırmadan bir işlevi veya alt yordamı yürütmek için Visual Studio **hemen** penceresini kullanabilirsiniz. işlev veya alt yordam bir kesme noktası içeriyorsa Visual Studio kesme noktasında kesilir. Daha sonra program durumlarınızı incelemek için hata ayıklayıcı pencerelerini kullanabilirsiniz. Bu özellik *tasarım zamanında hata ayıklama* olarak adlandırılır.

Aşağıdaki örnek Visual Basic. Ayrıca C#, F # ve C++/CLı uygulamalarında tasarım zamanında **hemen** penceresini de kullanabilirsiniz.

1. aşağıdaki kodu boş bir Visual Basic konsol uygulamasına yapıştırın:

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

1. Satır **sonu işlevinde** bir kesme noktası ayarlayın.

1.  **hata ayıkla**  >  **Windows**  >  **hemen**' ni seçerek hemen pencereyi açın. `?MyFunction`Pencereyi yazın ve ardından **ENTER** tuşuna basın.

   Kesme noktası isabet ediyor ve **Yereller** penceresindeki **MyFunction** değeri **1**' dir. Uygulama kesme modundayken çağrı yığınını ve diğer hata ayıklama pencerelerini inceleyebilirsiniz.

1. Visual Studio araç çubuğunda **devam** ' ı seçin. Uygulama sona erer ve **1** **hemen** penceresinde döndürülür. Hala tasarım modunda olduğunuzdan emin olun.

1. `?MyFunction` **Hemen** penceresini yeniden yazın ve **ENTER** tuşuna basın. Kesme noktası isabet ediyor ve **Yereller** penceresindeki **MyFunction** değeri **2**' dir.

1. **Devam**' i seçmeden, `?MySub()` **hemen** penceresine yazın ve ardından **ENTER** tuşuna basın. Kesme noktası isabet ediyor ve **Yereller** penceresindeki **MyFunction** değeri **3**' dir. Uygulama kesme modundayken uygulama durumunu inceleyebilirsiniz.

1. **Devam**’ı seçin. Kesme noktası yeniden isabet ediyor ve **Locals** penceresinde **MyFunction** değeri artık **2**' dir. **Komut** penceresi dönüş **ifadesi değerlendirildi ve bir değere sahip değil**.

1. **Devam et** ' i seçin. Uygulama sona erer ve **2** **hemen** penceresinde döndürülür. Hala tasarım modunda olduğunuzdan emin olun.

1. **Hemen** pencerenin içeriğini temizlemek için, pencereyi sağ tıklatın ve **Tümünü Temizle**' yi seçin.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>XAML tasarımcısına ekleyerek tasarım zamanında özel bir XAML denetiminde hata ayıklama

1. Çözümünüzü veya projenizi Visual Studio açın.

1. Çözüm/proje oluşturun.

1. Hata ayıklamak istediğiniz özel denetimi içeren XAML sayfasını açın.

   Windows build 16299 veya üzeri bir sürümü hedefleyen UWP projeleri için, bu adım *UwpSurface.exe* işlemini başlatacak. Windows build 16299 veya üzeri bir sürümü hedefleyen WPF projeleri için, bu adım *WpfSurface.exe* işlemini başlatacak. Windows build 16299 ' den önceki WPF veya UWP sürümleri için bu adım *XDesProc.exe* işlemini başlatacak. 

1. Visual Studio ikinci bir örneğini açın. İkinci örnekte bir çözüm veya proje açmayın.

1. Visual Studio ikinci örneğinde, **hata ayıkla** menüsünü açın ve **işleme ekle...** seçeneğini belirleyin.

1. Proje türüne bağlı olarak (önceki adımlara bakın), kullanılabilir işlemler listesinden *UwpSurface.exe*, *WpfSurface.exe* veya *XDesProc.exe* işlemini seçin.

1. **Işleme İliştir** Iletişim kutusunun **İliştir** alanına hata ayıklamak istediğiniz özel denetim için doğru kod türünü seçin.

   Özel denetiminiz bir .NET dilinde yazılmışsa, **yönetilen (CoreCLR)** gibi uygun .NET kod türünü seçin. Özel denetiminiz C++ dilinde yazılmışsa **Yerel**' i seçin.

1. **ekle** düğmesine tıklayarak Visual Studio ikinci örneğini iliştirin.

1. Visual Studio ikinci örneğinde, hata ayıklamak istediğiniz özel denetimle ilişkili kod dosyalarını açın. Tüm çözüm veya proje için değil, yalnızca dosyaları açık olduğunuzdan emin olun.

1. Gerekli kesme noktalarını önceden açılan dosyalara yerleştirin.

1. Visual Studio ilk örneğinde, hata ayıklamak istediğiniz özel denetimi içeren XAML sayfasını kapatın (önceki adımlarda açtığınız sayfa).

1. ilk Visual Studio örneğinde, önceki adımda kapattığınız XAML sayfasını açın. Bu, Visual Studio ikinci örneğinde ayarladığınız ilk kesme noktasında hata ayıklayıcının durdurulmasına neden olur.

1. Visual Studio ikinci örneğindeki kodda hata ayıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)