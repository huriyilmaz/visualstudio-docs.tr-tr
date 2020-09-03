---
title: İzleme noktalarıyla bilgileri günlüğe kaydet | Microsoft Docs
ms.date: 10/28/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: fcc9f01315d3783af1a1f124785cd74fafb215bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73187304"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Visual Studio 'da izleme noktalarını kullanarak çıkış penceresinde bilgi günlük kaydı

İzleneme noktaları, kodunuzu değiştirmeden veya durdurmadan, yapılandırılabilir koşullar altındaki çıkış penceresine bilgi günlüğizin verir. Bu özellik hem yönetilen diller (C#, Visual Basic, F #) hem de yerel kod için ve JavaScript ve Python gibi diller için desteklenir.

## <a name="let39s-take-an-example"></a>&#39;s 'nin bir örnek almasına izin ver

Aşağıdaki örnek program, bir `for` sayaç değişkeni olan ve döngünün başka bir yinelemeyi her çalıştırdığında arttığı basit bir döngüdür.

![Sayaç örneği](../debugger/media/counterexample.png "Sayaç örneği")

## <a name="set-tracepoints-in-source-code"></a>Kaynak kodunda izleme noktalarını ayarlama

**Kesme noktası ayarları** penceresindeki **eylem** onay kutusunun altında bir çıktı dizesi belirterek izleme noktaları ayarlayabilirsiniz.

1. Bir izleme noktası başlatmak için, önce izleme noktasını ayarlamak istediğiniz satır numarasının solundaki cilt paya tıklayın.

   ![Kesme noktası Başlatma](../debugger/media/breakpointinitialization.png "Kesme noktası Başlatma")

2. Kırmızı dairenin üzerine gelin ve ardından dişli simgesine tıklayın.
3. Bu, **kesme noktası ayarları** penceresini açar.

   ![Kesme noktası penceresi](../debugger/media/breakpointwindow.png "Kesme noktası penceresi")

4. **Eylem** onay kutusunu seçin.

   ![Denetlenen Eylemler kutusu](../debugger/media/checkedactionsbox.png "Denetlenen Eylemler kutusu")

   Kırmızı dairenin, bir kesme noktasından izleme noktasına geçtiğine işaret eden bir baklava şeklini nasıl değiştirdiğine dikkat edin.

5. Çıkış Penceresi metin kutusunda **Ileti göster** ' e oturum açmak istediğiniz iletiyi girin (Ayrıntılar için, bu makaledeki sonraki bölümlere bakın).

   İzleme noktanız artık ayarlandı. &quot; &quot; Her şey için çıkış penceresi bazı bilgileri günlüğe kaydetmek istiyorsanız Kapat düğmesine basın.

6. İletinizin görüntülenip görüntülenmediğini belirten koşullar eklemek istiyorsanız, **koşullar** onay kutusunu seçin.

   ![Denetlenen koşullar kutusu](../debugger/media/checkedconditionsbox.png "Denetlenen koşullar kutusu")

   Koşullar için üç seçeneğiniz vardır: **koşullu ifade**, **filtre**ve **isabet sayısı**.

## <a name="actions-menu"></a>Eylemler menüsü

Bu menü, çıkış penceresine bir ileti kaydetmenize izin verir. İleti kutusuna çıktısını almak istediğiniz dizeleri yazın (tırnak işareti gerekmez). Değişkenlerin değerlerini göstermek istiyorsanız, küme ayraçları içine aldığınızdan emin olun.

Örneğin, `counter` Çıkış konsolundaki değişkenin değerini göstermek istiyorsanız, ileti metin kutusuna {Counter} yazın.

![Sayaç çıkış Iletisi](../debugger/media/counteroutputmessage.png "Sayaç çıkış Iletisi")

**Kapat** ' a tıklayıp programda hata ayıklaması yaparsanız (**F5**) çıkış penceresinde aşağıdaki çıktıyı görürsünüz.

![Çıkış Penceresi eylemler Iletisi](../debugger/media/actionsmessageinoutputwindow.png "Çıkış Penceresi eylemler Iletisi")

Daha belirli bilgileri göstermek için özel anahtar sözcükler de kullanabilirsiniz. Anahtar sözcüğünü aşağıda gösterildiği gibi tam olarak girin (her anahtar sözcüğünün önünde bir "$" kullanın ve anahtar sözcüğünün kendisi için tüm Cap 'ler).

| Sözcükle | Ne görüntülenir |
| --- | --- |
| $ADDRESS | Geçerli yönerge |
| $CALLER | İşlev adı çağırma |
| $CALLSTACK | Çağrı yığını |
| $FUNCTION | Geçerli işlev adı |
| $PID | İşlem Kimliği |
| $PNAME | İşlem adı |
| $TID | İş parçacığı KIMLIĞI |
| $TNAME   | İş parçacığı adı |
| $TICK | Değer sayısı (Windows GetTickCount 'tan) |

## <a name="conditions-menu"></a>Koşullar menüsü

Koşullar, çıkış iletilerinizi filtrelemenizi sağlar, böylece yalnızca belirli senaryolar altında görüntülenir. Kullanabileceğiniz üç ana koşul türü vardır.

### <a name="conditional-expression"></a>Koşullu ifade
Koşullu bir ifade için, yalnızca belirli koşullar karşılandığında bir çıkış iletisi görüntülenir.

Koşullu ifadeler için, izleme noktasını, belirli bir koşul doğru olduğunda ya da değiştirildiğinde bir iletiyi çıktı olarak ayarlayabilirsiniz. Örneğin, yalnızca döngünün çift yinelemeleri sırasında sayacın değerini göstermek istiyorsanız `for` , **true** seçeneğini seçip `i%2 == 0` ileti metin kutusuna yazabilirsiniz.

![Koşullu Ifade doğru](../debugger/media/conditionalexpressionistrue.png "Koşullu Ifade doğru")

Döngü yinelemesi değiştiğinde sayacın değerini yazdırmak istiyorsanız `for` , **ne zaman değiştirildi** seçeneğini belirleyin ve `i` ileti metin kutusuna yazın.

![Değiştirildiğinde koşullu Ifade](../debugger/media/conditionalexpressionwhenchanged.png "Değiştirildiğinde koşullu Ifade")

Farklı programlama dilleri için  **ne zaman değiştirildi**  seçeneğinin davranışı farklıdır.

- Yerel kod için, hata ayıklayıcı koşulun ilk değerlendirmesini bir değişiklik olacak şekilde düşünmez, bu nedenle ilk değerlendirmede izleme noktasına ulaşmaz.
- Yönetilen kod için, hata ayıklayıcı, **değişiklik**  seçildikten sonra ilk değerlendirmede izleme noktasını alır.

Koşulları ayarlarken kullanabileceğiniz geçerli ifadelere daha kapsamlı bir bakış için bkz. [Hata Ayıklayıcıdaki İfadeler](expressions-in-the-debugger.md).

### <a name="hit-count"></a>İsabet sayısı
İsabet sayısı koşulu yalnızca izleme noktasının ayarlandığı kod satırıyla belirtilen sayıda yürütülene kadar çıkış göndermenizi sağlar.

İsabet sayısı için, izleme noktasının ayarlandığı kod satırı, ' nin katı olan veya belirtilen isabet sayısı değerinden büyük veya bu değere eşit olan bir dizi kez yürütülebileceği zaman bir iletiyi çıkışı seçebilirsiniz. Gereksinimlerinize en uygun seçeneği belirleyin ve ilgili yinelemeyi temsil eden alana (örneğin, 5) bir tamsayı değeri yazın.

![Koşullu Ifade Isabet sayısı](../debugger/media/conditionalexpressionhitcount.png "Koşullu Ifade Isabet sayısı")

### <a name="filter"></a>Filtre
Bir filtre koşulu için, hangi cihaz, işlem veya iş parçacığı çıktısının gösterildiğini belirtin.

![Koşullu Ifade filtresi](../debugger/media/conditionalexpressionfilter.png "Koşullu Ifade filtresi")

Filtre ifadeleri listesi:

- MachineName = "ad"
- Işlemkimliği = değer
- ProcessName = "ad"
- ThreadID = değer
- ThreadName = "ad"

Dizeleri (adlar gibi) çift tırnak içine alın. Değerler tırnak işareti olmadan girilebilir. Yan tümceleri (), (), `&` `AND` () `||` `OR` `!` `NOT` ve parantezleri kullanarak birleştirebilirsiniz.

## <a name="considerations"></a>Dikkat edilmesi gerekenler

İzleme noktaları, temizleyici ve daha sorunsuz bir deneyimde hata ayıklamaya yönelik olarak düşünülirken, bunları kullanmaya ne zaman geldiğini bilmeniz gereken bazı noktalar vardır.

Bazen bir nesnenin bir özelliğini veya özniteliğini incelemenize sonra değeri değişebilir. İnceleme sırasında değer değişirse, izleme noktası özelliğinin kendisinden kaynaklanan bir hata değildir. Ancak, nesneleri denetlemek için izlenenoktaları kullanmak bu yanlışlıkla yapılan değişikliklerden kaçının.

Deyim **eylem** ileti kutusunda değerlendirilme yöntemi, geliştirme için kullanmakta olduğunuz dilden farklı olabilir. Örneğin, bir dizeyi çıkarmak için, normalde veya kullanırken bile bir iletiyi tırnak içine almanız gerekmez `Debug.WriteLine()` `console.log()` . Ayrıca, çıkış ifadelerine küme ayracı sözdizimi ( `{ }` ), geliştirme dilinizde değer çıktısı için olan kurala göre de farklı olabilir. (Ancak, küme ayraçları () içindeki içerikler `{ }` hala geliştirme dili sözdizimi kullanılarak yazılmalıdır.

Canlı bir uygulamada hata ayıklamaya ve benzer bir özelliği aramaya çalışıyorsanız, Snapshot Debugger günlüğe kaydetme noktası özelliğimize göz atın. Anlık görüntü hata ayıklayıcısı, üretim uygulamalarındaki sorunları araştırmak için kullanılan bir araçtır. Günlüğe kaydetme noktaları, kaynak kodu değiştirmek zorunda kalmadan Çıkış Penceresi iletileri göndermenizi ve çalışan uygulamanızı etkilememek için de sağlar. Daha fazla bilgi için bkz. [canlı Azure uygulamasında hata ayıklama](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Visual Studio kullanarak daha iyi C# kodu yazma](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata Ayıklayıcıdaki İfadeler](expressions-in-the-debugger.md)
- [Kesme noktalarını kullanma](../debugger/using-breakpoints.md)
- [Canlı Azure uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md)
