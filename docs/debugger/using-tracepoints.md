---
title: İzleme noktalarıyla günlük | Microsoft Docs
description: Kodunuzu değiştirmeden veya durdurmadan bilgileri Çıkış olarak günlüğe kaydedilirken izleme noktaları ayarlayın. Kesme Noktası Denetimi'nin Eylem onay kutusunun altında bir çıkış dizesi Ayarlar.
ms.custom: SEO-VS-2020
ms.date: 10/28/2019
ms.topic: how-to
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 159754d466f1a9b0113920c2a678bed703600e432ed0e6c8df3fadbb60ddb0c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419461"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Visual Studio'da izleme noktaları kullanarak bilgileri Çıkış penceresine Visual Studio

İzleme noktaları, kodunuzu değiştirmeden veya durdurmadan yapılandırılabilir koşullar altında Bilgileri Çıkış penceresine günlüğe alamanıza olanak sağlar. Bu özellik hem yönetilen diller (C#, Visual Basic, F#) hem de yerel kod ile JavaScript ve Python gibi diller için de kullanılabilir.

## <a name="let39s-take-an-example"></a>Şimdi&#39;örnek alalım

Aşağıdaki örnek program, döngü başka bir yineleme çalıştırsa bir sayaç değişkenine sahip `for` basit bir döngü olur.

![Sayaç Örneği](../debugger/media/counterexample.png "Sayaç Örneği")

## <a name="set-tracepoints-in-source-code"></a>Kaynak kodunda izleme noktaları ayarlama

Kesme noktası denetimi penceresindeki Eylem onay kutusunun altında bir çıkış **dizesi** belirterek **izleme Ayarlar** belirtebilirsiniz.

1. Bir izleme noktası başlatmak için, önce izleme noktası ayarlamak istediğiniz satır numarasının sol tarafından gelen oluklara tıklayın.

   ![Kesme Noktası Başlatma](../debugger/media/breakpointinitialization.png "Kesme Noktası Başlatma")

2. Kırmızı dairenin üzerine gelin ve dişli simgesine tıklayın.
3. Bu işlem **kesme noktası Ayarlar** açar.

   ![Kesme Noktası Penceresi](../debugger/media/breakpointwindow.png "Kesme Noktası Penceresi")

4. Eylem **onay** kutusunu seçin.

   ![İşaretli Eylemler Kutusu](../debugger/media/checkedactionsbox.png "İşaretli Eylemler Kutusu")

   Kırmızı dairenin, bir kesme noktası yerine izleme noktası olarak geçiş yaptığınıza işaret eden bir baklavaya nasıl değiştiklerini fark et.

5. Oturum açmak istediğiniz iletiyi Çıkış Penceresi metin kutusuna girin **(ayrıntılar** için bu makalenin sonraki bölümlerine bakın).

   İzleme noktanız artık ayarlanmış. Tüm &quot; yapmak &quot; istediğiniz bilgileri günlük kaydına almaksa Kapat düğmesine Çıkış Penceresi.

6. İletinizin görüntü olup olmadığını belirleyen koşullar eklemek için Koşullar onay **kutusunu** seçin.

   ![İşaretli Koşullar Kutusu](../debugger/media/checkedconditionsbox.png "İşaretli Koşullar Kutusu")

   Koşullar için üç seçenek vardır: **Koşullu İfade,** **Filtre ve** **Isabet Sayısı.**

## <a name="actions-menu"></a>Eylemler menüsü

Bu menü, Çıkış penceresine bir ileti günlük kaydı göndermenize olanak sağlar. İleti kutusuna çıkış yapmak istediğiniz dizeleri yazın (tırnak işaret gerekmez). Değişkenlerin değerlerini görüntülemek için küme ayraçları içine almak istediğinizden emin olun.

Örneğin, değişkenin değerini çıkış konsolunda görüntülemek `counter` için ileti metin kutusuna {counter} yazın.

![Sayaç Çıkış İletisi](../debugger/media/counteroutputmessage.png "Sayaç Çıkış İletisi")

**Kapat'a tıklar** ve programda (**F5)** hata ayıklarsanız, Çıktı penceresinde aşağıdaki çıkışı görebilirsiniz.

![Eylemler İletisi Çıkış Penceresi](../debugger/media/actionsmessageinoutputwindow.png "Eylemler İletisi Çıkış Penceresi")

Daha belirli bilgileri görüntülemek için özel anahtar sözcükler de kullanabilirsiniz. Anahtar sözcüğünü tam olarak aşağıda gösterildiği gibi girin (her anahtar sözcüğün önünde bir "$" kullanın ve anahtar sözcüğün kendisi için tüm uçları kullanın).

| Anahtar kelime | Görüntülenenler |
| --- | --- |
| $ADDRESS | Geçerli yönerge |
| $CALLER | İşlev adını çağırma |
| $CALLSTACK | Çağrı yığını |
| $FUNCTION | Geçerli işlev adı |
| $PID | İşlem Kimliği |
| $PNAME | İşlem adı |
| $TID | İş Parçacığı Kimliği |
| $TNAME   | İş parçacığı adı |
| $TICK | Onay işareti sayısı (Windows GetTickCount'tan) |

## <a name="conditions-menu"></a>Koşullar menüsü

Koşullar, çıkış iletilerinizi yalnızca belirli senaryolarda görüntülensin diye filtrelemenize olanak sağlar. Size üç farklı türde koşullar sunulmaktadır.

### <a name="conditional-expression"></a>Koşullu ifade
Koşullu ifade için, yalnızca belirli koşullar karşı olduğunda bir çıkış iletisi görüntülenir.

Koşullu ifadeler için, belirli bir koşul true olduğunda veya değiştir olduğunda bir ileti çıkışı yapmak için izleme noktası belirtebilirsiniz. Örneğin, yalnızca döngü yinelemeleri sırasında sayacın değerini görüntülemek için True seçeneğini kullanabilir ve ardından ileti `for` metin kutusuna  `i%2 == 0` yazabilirsiniz.

![Koşullu İfade Doğru](../debugger/media/conditionalexpressionistrue.png "Koşullu İfade Doğru")

Döngü yinelemesi değişirken sayacın değerini yazdırmak için Değiştirildi seçeneğini belirleyin ve `for` ileti metin kutusuna  `i` yazın.

![Değiştiriken Koşullu İfade](../debugger/media/conditionalexpressionwhenchanged.png "Değiştiriken Koşullu İfade")

Değiştirildi  **seçeneğinin davranışı**  farklı programlama dilleri için farklıdır.

- Yerel kod için hata ayıklayıcı koşulun ilk değerlendirmesini bir değişiklik olarak değerlendirmez, bu nedenle ilk değerlendirmede izleme noktası isabet etmez.
- Yönetilen kod için, hata ayıklayıcı Değiştirildikten sonra ilk **değerlendirmede izleme noktasıyla**  karşılaşabilir.

Koşulları ayarlarken kullanabileceğiniz geçerli ifadelere daha kapsamlı bir bakış için bkz. [Hata ayıklayıcısında ifadeler.](expressions-in-the-debugger.md)

### <a name="hit-count"></a>Isabet sayısı
Isabet sayısı koşulu, çıkışı yalnızca izleme noktası ayarlanmış kod satırı belirtilen sayıda yürütülürken göndermenizi sağlar.

Isabet sayısı için, izleme noktası ayarlanmış kod satırı, belirtilen isabet sayısı değerinin katları veya daha büyük olduğunda birkaç kez yürütülürse bir ileti çıkışı seçebilirsiniz. İhtiyaçlarınızı en iyi şekilde uyan seçeneği belirleyin ve alana (örneğin, 5) ilgili yinelemeyi temsil eden bir tamsayı değeri yazın.

![Koşullu İfade Isabet Sayısı](../debugger/media/conditionalexpressionhitcount.png "Koşullu İfade Isabet Sayısı")

### <a name="filter"></a>Filtre
Bir filtre koşulu için hangi cihazların, işlemlerin veya iş parçacıklarının çıkışının gösterildiğini belirtin.

![Koşullu İfade Filtresi](../debugger/media/conditionalexpressionfilter.png "Koşullu İfade Filtresi")

Filtre ifadeleri listesi:

- MachineName = "name"
- ProcessId = değer
- ProcessName = "name"
- ThreadId = değer
- ThreadName = "name"

Dizeleri (adlar gibi) çift tırnak içine alın. Değerler tırnak içine alınarak girilebilir. Yan tümceleri `&` ( `AND` ), ( ) ) ve `||` `OR` `!` `NOT` parantezleri kullanarak birleştirin.

## <a name="considerations"></a>Dikkat edilmesi gerekenler

İzleme noktaları, hata ayıklamayı daha temiz ve daha sorunsuz bir deneyime yöneliktir ancak bunları kullanırken dikkat edilmesi gereken bazı noktalar vardır.

Bazen bir nesnenin özelliğini veya özniteliğini incelerken nesnenin değeri değişebilir. İnceleme sırasında değer değişirse, izleme noktası özelliğinin kendisinde oluşan bir hata değildir. Ancak, nesneleri incelemek için izleme noktaları kullanmak bu yanlışlıkla yapılan değişiklikleri önlemez.

İfadelerin Eylem ileti kutusunda değerlendirilme  yolu, geliştirme için kullanmakta olduğunuz dilden farklı olabilir. Örneğin, bir dizenin çıkışını vermek için, veya kullanırken normalde kullansanız bile bir iletiyi tırnak içine sarmanız `Debug.WriteLine()` gerek `console.log()` değildir. Ayrıca, çıkış ifadelerine küme ayracı söz dizimi ( ) de geliştirme dilinize değer `{ }` çıkışı yapmak için yapılan kuraldan farklı olabilir. (Ancak küme ayraçları ( ) içindeki içerikler yine de geliştirme `{ }` dilinizin söz dizimi kullanılarak yazıldı.

Canlı uygulamada hata ayıklamaya çalışıyorsanız ve benzer bir özellik arıyorsanız, günlük noktası özelliğimizi Snapshot Debugger. Anlık görüntü hata ayıklayıcısı, üretim uygulamalarıyla ilgili sorunları araştırmak için kullanılan bir araçtır. Günlük noktaları, kaynak kodu değiştirmek zorunda kalmadan Çıkış Penceresi ve çalışan uygulamanızı etkilemeden ileti göndermenize de olanak sağlar. Daha fazla bilgi için [bkz. Canlı Azure uygulamasında hata ayıklama.](../debugger/debug-live-azure-applications.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Visual Studio kullanarak daha iyi C# Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısındaki ifadeler](expressions-in-the-debugger.md)
- [Kesme noktalarını kullanma](../debugger/using-breakpoints.md)
- [Canlı Azure uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md)
