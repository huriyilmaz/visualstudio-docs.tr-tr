---
title: İş Akışı Tasarımcısı-ParallelForEach &lt;T &gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68cd543ed41408e7510708367c8e539c0702ea1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650086"
---
# <a name="parallelforeach-activity-designer"></a>ParallelForEach etkinlik Tasarımcısı

@No__t_0 etkinliği bir koleksiyonun öğelerini numaralandırır ve aynı iş parçacığında zaman uyumsuz olan paralel olarak koleksiyonun her öğesi için gömülü bir ifade yürütür. Bu etkinliğin alt etkinliklerinin boşta olması bekleniyorsa <xref:System.Activities.Statements.Sequence> etkinliği yerine bu Flow denetim etkinliğini kullanın.

@No__t_0 etkinliği, Kullanıcı tarafından belirtilen Visual Basic ifadesi içeren bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> özelliğine sahiptir. @No__t_0 etkinliği her bir dal tamamlandıktan sonra bu özelliği değerlendirir. **True**olarak değerlendirilirse <xref:System.Activities.Statements.ParallelForEach%601> etkinlik diğer dalları yürütmeden tamamlanır. @No__t_0 **true**olarak değerlendirilmiyorsa, tüm alt etkinlikleri tamamlandığında <xref:System.Activities.Statements.ParallelForEach%601> etkinlik tamamlanır.

## <a name="the-parallelforeacht-activity"></a>ParallelForEach < T \> etkinliği

<xref:System.Activities.Statements.ParallelForEach%601> değerlerini numaralandırır ve numaralandıraldığı her değer için <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> zamanlar. Yalnızca <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> zamanlar. Gövde nasıl çalıştırılır <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> boşta kalacağından bağımsız olarak değişir.

@No__t_0 boşta kalırsa, zamanlanmış etkinlikler bir yığın olarak işlendiği için ters sırada yürütülür, en son zamanlanan etkinlik ilk yürütülür. Örneğin, bir {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> koleksiyonunuz varsa ve değeri yazmak için gövde olarak bir **WriteLine** kullanıyorsanız. Konsolda 4, 3, 2, 1 yazdırılmış. Bunun nedeni, **WriteLine** 'ın zamanlanan 4 **WriteLine** etkinliği zamanlanmasından sonra, bir yığın davranışı kullanılarak yürütülemediği (ilk kez geçen süre).

Ancak <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, bir <xref:System.ServiceModel.Activities.Receive> etkinliği veya <xref:System.Activities.Statements.Delay> etkinliği gibi boş kalabileceğini belirten etkinlikleriniz varsa. Daha sonra bunların tamamlanmasını beklemeniz gerekmez. <xref:System.Activities.Statements.ParallelForEach%601> bir sonraki zamanlanmış gövde etkinliğine gider ve çalıştırmayı dener. Bu etkinlik çok fazla kalırsa, <xref:System.Activities.Statements.ParallelForEach%601> sonraki gövde etkinliğini tekrar gider.

### <a name="using-the-parallelforeacht-activity-designer"></a>ParallelForEach \<T > etkinlik tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisindeki **ParallelForEach \<T >** etkinlik tasarımcısına erişin.

**ParallelForEach \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin bir **sıra** etkinliğinin içindeki etkinlik tasarımcılarının normalde yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir Layana. İş Akışı Tasarımcısı, bu, varsayılan olarak **ParallelForEach < ınt32 \>** <xref:System.Activities.Activity.DisplayName%2A> içeren bir <xref:System.Activities.Statements.ParallelForEach%601> etkinliği oluşturur.

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı ParallelForEach < T \> özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ParallelForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **ParallelForEach \<Int32 >** . Değer, isteğe bağlı olarak **Özellikler** kılavuzunda veya doğrudan etkinlik Tasarımcısı üstbilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Koleksiyondaki her öğe için yürütülecek etkinlik. @No__t_0 etkinliğini eklemek için, araç kutusundan bir etkinliği **ParallelForEach \<T >** etkinlik Tasarımcısı ' nın **' de yer** alan "etkinliği buraya bırak" ipucu metin kutusuna bir etkinlik bırakın.|
|**TypeArgument**|Doğru|Genel parametre *t*tarafından belirtilen <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> koleksiyonundaki öğelerin türü. Varsayılan olarak, **TypeArgument** değeri **Int32**olarak ayarlanır. **ParallelForEach < t \>** Etkinlik tasarımcısında t türünü değiştirmek Için, özellik kılavuzunda **TypeArgument** Birleşik giriş kutusunun değerini değiştirin.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. @No__t_0 ayarlamak için, **Özellikler** penceresinde "vb ifadesi girin" veya **değerler** kutusuna "bir vb ifadesi girin" ipucu metnini içeren kutuya, **foreach < t \>** etkinlik tasarımcısı ' nın **değerler** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Her yineleme tamamlandıktan sonra değerlendirilir. True olarak değerlendirilirse, zamanlanan bekleyen yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, tüm zamanlanmış deyimler tamamlanana kadar yürütülür.|

Varsayılan olarak, döngü yineleyicisi öğe olarak adlandırılır. Bir yineleyici değişkeninin adını **ParallelForEach \<T >** etkinlik Tasarımcısı ' nda bulunan **foreach** kutusunda değiştirebilirsiniz. Döngü yineleyicisi, <xref:System.Activities.Statements.ParallelForEach%601> etkinliğinin alt öğelerindeki ifadelerde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)