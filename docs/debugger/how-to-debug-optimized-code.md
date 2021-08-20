---
title: İyileştirilmiş Kod Hata Ayıklama | Microsoft Docs
description: Mümkünse, en iyi duruma getirme hata ayıklamayı karmaşık hale getirmesi nedeniyle, programınız hata ayık olana kadar bir Win32 Yayın hedefi derlemeyin. Bu makaledeki ayrıntılara bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3d58233f606c3060a1a78f8cfd0a1c3b4c0334de
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128605"
---
# <a name="how-to-debug-optimized-code"></a>Nasıl Yapılır: İyileştirilmiş Kodda Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı Ayarlar'yi seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

> [!NOTE]
> [/Zo (İyileştirilmiş](/cpp/build/reference/zo-enhance-optimized-debugging)Hata Ayıklamayı Geliştir) derleyici seçeneği (Visual Studio Güncelleştirme 3'te tanıtılmış), iyileştirilmiş kod **(/Od** derleyici seçeneğiyle oluşturulmaz projeler) için daha zengin hata ayıklama bilgileri üretir. Bkz. [/O Seçenekleri (Kodu İyileştir)](/cpp/build/reference/o-options-optimize-code)). Bu, yerel değişkenlerin ve büyük/büyük işlevlerin hata ayıklaması için geliştirilmiş destek içerir.
>
> [](../debugger/edit-and-continue-visual-csharp.md) /Zo ocompiler seçeneği **kullanılırken Düzenle** ve Devam Edin devre dışı bırakılır.

 Derleyici kodu en iyi duruma getirmesi, yönergeleri yeniden konumlandırarak yeniden düzenlemesi gerekir. Bunun sonucunda daha verimli bir şekilde derlenmiş kod elde edildi. Bu yeniden düzenleme nedeniyle, hata ayıklayıcı bir dizi yönergelere karşılık gelen kaynak kodu her zaman tanımamaz.

 İyileştirme şunları etkileyebilir:

- İyileştirici tarafından kaldırılan veya hata ayıklayıcının anlamayıldığı konumlara taşınan yerel değişkenler.

- İyileştirici kod bloklarını birleştirse de değişen bir işlevin içindeki konumlar.

- Çağrı yığınında çerçeveler için işlev adları, iyileştirici iki işlevi birleştirse yanlış olabilir.

  Ancak tüm kareler için sembollere sahip olduğunu varsayarak, çağrı yığınında gördüğünüz kareler neredeyse her zaman doğrudur. Yığın bozulması varsa, derleme dilinde yazılmış işlevleriniz varsa veya çağrı yığınında semboller eşleşmeden işletim sistemi çerçeveleri varsa çağrı yığınında çerçeveler yanlış olur.

  Genel ve statik değişkenler her zaman doğru şekilde gösterilir. Yapı düzeni de böyledir. Bir yapıya işaretçiniz varsa ve işaretçinin değeri doğruysa, yapının her üye değişkeni doğru değeri gösterir.

  Bu sınırlamalar nedeniyle, mümkünse programınız için en iyi olmayan bir sürümü kullanarak hata ayıklamanız gerekir. Varsayılan olarak, C++ programının Hata ayıklama yapılandırmasında iyileştirme kapalıdır ve Yayın yapılandırmasında açıktır.

  Ancak, bir hata yalnızca bir programın en iyi duruma getirilmiş sürümünde görünebilir. Bu durumda, iyileştirilmiş kodda hata ayıklaması gerekir.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Hata ayıklama derleme yapılandırmasında iyileştirmeyi açmak için

1. Yeni bir proje oluşturmak için hedefi `Win32 Debug` seçin. Programınız `Win32 Debug` tamamen hata ayıklaması yapılana ve bir hedef derlemeye hazır olana kadar hedefi `Win32 Release` kullanın. Derleyici hedefi `Win32 Debug` iyileştirmez.

2. Proje'de projeyi Çözüm Gezgini.

3. Görünüm menüsünde **Özellik** **Sayfaları'nın üzerine tıklayın.**

4. Özellik **Sayfaları iletişim** kutusunda, Yapılandırma `Debug` açılan listesinde seçili **olduğundan** emin olun.

5. Sol tarafta klasör görünümünde **C/C++ klasörünü** seçin.

6. **C++ klasörünün** altında öğesini `Optimization` seçin.

7. Sağdan özellikler listesinde `Optimization` bulun. Yanındaki ayar büyük olasılıkla `Disabled (` [/Od olarak ifade etti.](/cpp/build/reference/od-disable-debug) `)` Diğer seçeneklerden birini belirleyin ( `Minimum Size``(` [/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization)veya `)` `Custom` ).

8. seçeneğini tercih `Custom` `Optimization` ettiyseniz, artık özellikler listesinde gösterilen diğer özelliklerden herhangi biri için seçenekleri ayarlayın.

9. Proje özellikleri sayfasının Yapılandırma Özellikleri, C/C++, Komut Satırı düğümünü seçin ve Ek Seçenekler metin kutusuna `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` ekleyin. 

    > [!WARNING]
    > `/Zo`, Visual Studio 2013 3 veya sonraki bir sürümü gerektirir.
    >
    >  Ekleme, `/Zo` Düzenle ve [Devam'ı devre dışı bırakacak.](../debugger/edit-and-continue-visual-csharp.md)

   İyileştirilmiş kodda hata ayıklarken, hangi yönergelerin gerçekten oluşturularak yürütülüp oluşturulmamış olduğunu görmek için **Disassembly** penceresini kullanın. Kesme noktaları ayar her zaman, kesme noktası bir yönergeyle birlikte hareket eder. Örneğin, aşağıdaki kodu düşünün:

```cpp
for (x=0; x<10; x++)
```

 Bu satırda bir kesme noktası ayarladklı olduğunu varsayalım. Kesme noktası 10 kez isabet ediyor olabilir, ancak kod iyileştirilmişse kesme noktası yalnızca bir kez isabet ediyordur. Bunun nedeni, ilk yönergenin değerini `x` 0 olarak ayarlar. Derleyici bunun yalnızca bir kez yapılması ve döngüden dışarı taşır. Kesme noktası da bu şekilde taşınır. Karşılaştırma ve artırma yönergeleri `x` döngü içinde kalır. **Disassembly penceresini** görüntülerken, [](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) daha fazla denetim için adım birimi otomatik olarak Yönerge olarak ayarlanır ve bu, iyileştirilmiş kodda adım adım ilerlerken yararlı olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)