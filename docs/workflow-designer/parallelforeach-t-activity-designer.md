---
title: İş Akışı Tasarımcısı-ParallelForEach &lt; T &gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e2d3d33b150bd9c360896f88eddf032837fe9c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876053"
---
# <a name="parallelforeach-activity-designer"></a>ParallelForEach Etkinlik Tasarımcısı

<xref:System.Activities.Statements.ParallelForEach%601>Etkinlik, bir koleksiyonun öğelerini numaralandırır ve aynı iş parçacığında zaman uyumsuz olan paralel olarak koleksiyonun her öğesi için gömülü bir ifade yürütür. <xref:System.Activities.Statements.Sequence>Bu etkinliğin alt etkinliklerinin boşta olması bekleniyorsa etkinlik yerine bu Flow denetim etkinliğini kullanın.

<xref:System.Activities.Statements.ParallelForEach%601>Etkinlik, Kullanıcı tarafından <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> belirtilen Visual Basic ifadesi içeren bir özelliğe sahiptir. <xref:System.Activities.Statements.ParallelForEach%601>Etkinlik her bir dal tamamlandıktan sonra bu özelliği değerlendirir. **True**olarak değerlendirilirse, <xref:System.Activities.Statements.ParallelForEach%601> etkinlik diğer dalları yürütmeden tamamlanır. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> **Doğru**olarak değerlendirilmiyorsa, <xref:System.Activities.Statements.ParallelForEach%601> tüm alt etkinlikleri tamamlandığında etkinlik tamamlanır.

## <a name="the-parallelforeacht-activity"></a>ParallelForEach<T \> etkinliği

<xref:System.Activities.Statements.ParallelForEach%601> değerlerini numaralandırır ve <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> numaralandıraldığı her değer için öğesini zamanlar. Yalnızca ' i zamanlar <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> . Gövde yürütme, boşta kalma olup olmamasına bağlıdır <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> .

<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>Boşta kalırsa, zamanlanmış etkinlikler bir yığın olarak işlendiğinden, en son zamanlanan etkinlik ilk olarak yürütülür. Örneğin, içinde bir koleksiyonunuz varsa {1,2,3,4} <xref:System.Activities.Statements.ParallelForEach%601> ve değeri yazmak için gövde olarak bir **WriteLine** kullanın. Konsolda 4, 3, 2, 1 yazdırılmış. Bunun nedeni, **WriteLine** 'ın zamanlanan 4 **WriteLine** etkinliği zamanlanmasından sonra, bir yığın davranışı kullanılarak yürütülemediği (ilk kez geçen süre).

Ancak içindeki etkinlikleriniz varsa <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> , bir <xref:System.ServiceModel.Activities.Receive> etkinlik veya etkinlik gibi boş kalabilirler <xref:System.Activities.Statements.Delay> . Daha sonra bunların tamamlanmasını beklemeniz gerekmez. <xref:System.Activities.Statements.ParallelForEach%601> bir sonraki zamanlanmış gövde etkinliğine gider ve çalıştırmayı deneyin. Bu etkinlik çok fazla kalırsa, <xref:System.Activities.Statements.ParallelForEach%601> sonraki gövde etkinliğini tekrar gider.

### <a name="using-the-parallelforeacht-activity-designer"></a>ParallelForEach \<T> etkinlik tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisindeki ** \<T> ParallelForEach** etkinlik tasarımcısına erişin.

**ParallelForEach \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin bir **sıra** etkinliği tasarımcısı içinde olan etkinlik tasarımcılarının normalde yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. İş Akışı Tasarımcısı, bu, <xref:System.Activities.Statements.ParallelForEach%601> Varsayılan olarak bir <xref:System.Activities.Activity.DisplayName%2A> **parallelforeach<Int32 \> ** içeren bir etkinlik oluşturur.

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı içindeki ParallelForEach<T \> Özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ParallelForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **ParallelForEach \<Int32> **' dir. Değer, isteğe bağlı olarak **Özellikler** kılavuzunda veya doğrudan etkinlik Tasarımcısı üstbilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Yanlış|Koleksiyondaki her öğe için yürütülecek etkinlik. Etkinliği eklemek için <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> , araç kutusundan bir etkinliği **ParallelForEach \<T> ** etkinlik Tasarımcısı ' nın **gövde** kutusuna, ipucu metni "etkinliği buraya bırak" olarak bırakın.|
|**TypeArgument**|Doğru|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>Genel parametre *T*tarafından belirtilen koleksiyondaki öğelerin türü. Varsayılan olarak, **TypeArgument** değeri **Int32**olarak ayarlanır. **ParallelForEach<t \> ** Etkinlik tasarımcısında t türünü değiştirmek Için, özellik kılavuzunda **TypeArgument** Birleşik giriş kutusunun değerini değiştirin.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. Ayarlamak için <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> , **Özellikler** penceresinde "vb ifadesi girin" veya **değerler** kutusuna "bir vb ifadesi girin" ipucu metnini içeren kutuya **foreach<T \> ** etkinlik Tasarımcısı ' nın **değerler** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Her yineleme tamamlandıktan sonra değerlendirilir. True olarak değerlendirilirse, zamanlanan bekleyen yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, tüm zamanlanmış deyimler tamamlanana kadar yürütülür.|

Varsayılan olarak, döngü yineleyicisi öğe olarak adlandırılır. Bir yineleyici değişkeninin adını **ParallelForEach \<T> ** etkinlik Tasarımcısı ' nda **foreach** kutusunda değiştirebilirsiniz. Döngü yineleyicisi etkinliğin alt öğelerindeki ifadelerde kullanılabilir <xref:System.Activities.Statements.ParallelForEach%601> .

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Paralel](../workflow-designer/parallel-activity-designer.md)
- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)