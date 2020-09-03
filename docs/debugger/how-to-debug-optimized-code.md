---
title: Iyileştirilmiş kodda hata ayıklama | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c08ce9605560173d6f29817372dee4af8d622e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349984"
---
# <a name="how-to-debug-optimized-code"></a>Nasıl Yapılır: İyileştirilmiş Kodda Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> [/Zo (](/cpp/build/reference/zo-enhance-optimized-debugging)Visual Studio güncelleştirme 3 ' te sunulan) derleyici seçeneği (Visual Studio Update 3 ' te tanıtılan), iyileştirilmiş kod için daha zengin hata ayıklama bilgileri oluşturur ( **/od** derleyici seçeneği ile derlenmeyen projeler). Bkz. [/O Seçenekler (kodu iyileştirme)](/cpp/build/reference/o-options-optimize-code)). Bu, yerel değişkenleri ve satır içi işlevleri hata ayıklama için geliştirilmiş destek içerir.
>
> **/Zo** ocompiler seçeneği kullanıldığında [Düzenle ve devam et](../debugger/edit-and-continue-visual-csharp.md) devre dışı bırakıldı.

 Derleyici kodu en iyi duruma getirirken, yönergeleri yeniden konumlandırır ve yeniden düzenler. Bu, daha verimli derlenmiş koda neden olur. Bu yeniden düzenleme nedeniyle, hata ayıklayıcı her zaman bir yönergeler kümesine karşılık gelen kaynak kodunu tanımlayamıyor.

 İyileştirme şunları etkileyebilir:

- İyileştiricinin kaldırılabileceği veya hata ayıklayıcının anlayamadığı konumlara taşınan yerel değişkenler.

- Bir işlevin içindeki konumlar, iyileştiricinin kod bloklarını birleştirdiğinde değişir.

- Çağrı yığınında çerçeveler için işlev adları; iyileştiricinin iki işlevi birleştirmesi durumunda yanlış olabilir.

  Çağrı yığınında gördüğünüz çerçeveler neredeyse her zaman doğrudur, ancak tüm çerçeveler için simgelere sahip olduğunuz varsayılır. Yığın bozulmadıysanız, derleme dilinde yazılmış işlevleriniz varsa veya çağrı yığınında sembolleri eşleşmeyen işletim sistemi çerçeveleri varsa, çağrı yığınında çerçeveler yanlış olur.

  Genel ve statik değişkenler her zaman doğru şekilde gösterilir. Yapı düzeni. Bir yapıya işaretçiniz varsa ve işaretçinin değeri doğruysa, yapının her üye değişkeni doğru değeri gösterir.

  Bu sınırlamalar nedeniyle, mümkün olduğunda programınızın iyileştirilmemiş bir sürümünü kullanarak hata ayıklaması yapmalısınız. Varsayılan olarak, bir C++ programının hata ayıklama yapılandırmasında iyileştirme kapalıdır ve yayın yapılandırmasında açıktır.

  Ancak, bir hata yalnızca bir programın en iyi duruma getirilmiş bir sürümünde görünebilir. Bu durumda, iyileştirilmiş kodda hata ayıklaması yapmanız gerekir.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Hata ayıklama yapı yapılandırmasında iyileştirmeyi açmak için

1. Yeni bir proje oluşturduğunuzda `Win32 Debug` hedefi seçin. `Win32``Debug`Programınız tam olarak ayıklanana ve bir hedef oluşturmaya başlamaya kadar hedefi kullanın `Win32 Release` . Derleyici hedefi iyileştirmez `Win32 Debug` .

2. Çözüm Gezgini içinde projeyi seçin.

3. **Görünüm** menüsünde, **Özellik sayfaları**' na tıklayın.

4. **Özellik sayfaları** iletişim kutusunda, `Debug` **yapılandırma** açılan listesinde seçili olduğundan emin olun.

5. Soldaki klasör görünümünde **C/C++** klasörünü seçin.

6. **C++** klasörü altında öğesini seçin `Optimization` .

7. Sağdaki Özellikler listesinde bulun `Optimization` . Bunun yanındaki ayar büyük olasılıkla `Disabled (` [/od](/cpp/build/reference/od-disable-debug)' i söylüyor `)` . Diğer seçeneklerden birini ( `Minimum Size``(` [/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)` veya `Custom` ) seçin.

8. `Custom`Seçeneğini belirlediyseniz `Optimization` , artık Özellikler listesinde gösterilen diğer özelliklerden herhangi biri için seçenekleri ayarlayabilirsiniz.

9. Yapılandırma özellikleri, C/C++, proje özellikleri sayfasının komut satırı düğümünü seçin ve `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` **ek seçenekler** metin kutusuna/zo ekleyin.

    > [!WARNING]
    > `/Zo` Visual Studio 2013 güncelleştirme 3 veya sonraki bir sürümünü gerektirir.
    >
    >  Ekleme `/Zo` , [Düzenle ve devam et](../debugger/edit-and-continue-visual-csharp.md)özelliğini devre dışı bırakır.

   İyileştirilmiş kodda hata ayıklarken, hangi yönergelerin gerçekten oluşturulup yürütüleceğini görmek için **ayrıştırma** penceresini kullanın. Kesme noktaları ayarladığınızda, kesme noktasının bir yönergeyle birlikte hareket edebileceğini bilmeniz gerekir. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```cpp
for (x=0; x<10; x++)
```

 Bu satırda bir kesme noktası ayarladığınızı varsayalım. Kesme noktasının 10 kez beklemeniz istenebilir, ancak kod iyileştirildiğinde, kesme noktası yalnızca bir kez vuruş yapılır. Bunun nedeni, birinci yönergenin değerini 0 olarak ayarlamadır `x` . Derleyici bunun yalnızca bir kez yapılması gerektiğini ve döngünün dışına taşındığını algılar. Kesme noktası onunla birlikte gider. Karşılaştırma ve artırma yönergeleri `x` döngünün içinde kalır. **Ayrıştırma** penceresini görüntülediğinizde, [adım birimi](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) , daha fazla denetim için otomatik olarak yönerge olarak ayarlanır ve bu, iyileştirilmiş kodla adım adım yararlı olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)