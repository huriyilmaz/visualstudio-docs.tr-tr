---
title: ParallelForEach &lt;T &gt; etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c659e941a8503a0d5ff601fea23fcec69b2bbcf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672607"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach &lt;T &gt; etkinlik Tasarımcısı
@No__t_0 etkinliği bir koleksiyonun öğelerini numaralandırır ve aynı iş parçacığında zaman uyumsuz olan paralel olarak koleksiyonun her öğesi için gömülü bir ifade yürütür. Bu etkinliğin alt etkinliklerinin boşta olması bekleniyorsa <xref:System.Activities.Statements.Sequence> etkinliği yerine bu Flow denetim etkinliğini kullanın.

 @No__t_0 etkinliği, Kullanıcı tarafından belirtilen [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifadesi içeren bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> özelliğine sahiptir. @No__t_0 etkinliği her bir dal tamamlandıktan sonra bu özelliği değerlendirir. **True**olarak değerlendirilirse <xref:System.Activities.Statements.ParallelForEach%601> etkinlik diğer dalları yürütmeden tamamlanır. @No__t_0 **true**olarak değerlendirilmiyorsa, tüm alt etkinlikleri tamamlandığında <xref:System.Activities.Statements.ParallelForEach%601> etkinlik tamamlanır.

## <a name="the-parallelforeacht-activity"></a>ParallelForEach \<T > etkinliği
 <xref:System.Activities.Statements.ParallelForEach%601> değerlerini numaralandırır ve numaralandıraldığı her değer için <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> zamanlar. Yalnızca <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> zamanlar. Gövde nasıl çalıştırılır <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> boşta kalacağından bağımsız olarak değişir.

 @No__t_0 boşta kalırsa, zamanlanmış etkinlikler bir yığın olarak işlendiği için ters sırada yürütülür, en son zamanlanan etkinlik ilk yürütülür. Örneğin, bir {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> koleksiyonunuz varsa ve değeri yazmak için gövde olarak bir **WriteLine** kullanıyorsanız. Konsolda 4, 3, 2, 1 yazdırılmış. Bunun nedeni, **WriteLine** 'ın zamanlanan 4 **WriteLine** etkinliği zamanlanmasından sonra, bir yığın davranışı kullanılarak yürütülemediği (ilk kez geçen süre).

 Ancak <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, bir <xref:System.ServiceModel.Activities.Receive> etkinliği veya <xref:System.Activities.Statements.Delay> etkinliği gibi boş kalabileceğini belirten etkinlikleriniz varsa. Daha sonra bunların tamamlanmasını beklemeniz gerekmez. <xref:System.Activities.Statements.ParallelForEach%601> bir sonraki zamanlanmış gövde etkinliğine gider ve çalıştırmayı dener. Bu etkinlik çok fazla kalırsa, <xref:System.Activities.Statements.ParallelForEach%601> sonraki gövde etkinliğini tekrar gider.

### <a name="using-the-parallelforeacht-activity-designer"></a>ParallelForEach \<T > etkinlik tasarımcısını kullanma
 **ParallelForEach \<T >** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] sol tarafındaki **araç kutusu** sekmesine tıklanarak erişilen **araç kutusunun** **Denetim akışı** kategorisinde bulunabilir (alternatif olarak,  **Araç çubuğundan** **Görünüm** menüsünden veya Ctrl + Alt + X.)

 **ParallelForEach \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin bir **sıra** etkinliği tasarımcısı içindeki etkinlik tasarımcılarının normalde yerleştirildiği [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine bırakılabilir. @No__t_0, bu, varsayılan olarak **ParallelForEach \<Int32 >** <xref:System.Activities.Activity.DisplayName%2A> içeren bir <xref:System.Activities.Statements.ParallelForEach%601> etkinliği oluşturur.

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı \<T ParallelForEach > Özellikleri
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ParallelForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **ParallelForEach \<Int32 >** . Değer, isteğe bağlı olarak **Özellikler** kılavuzunda veya doğrudan etkinlik Tasarımcısı üstbilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Koleksiyondaki her öğe için yürütülecek etkinlik. @No__t_0 etkinliğini eklemek için, araç kutusundan bir etkinliği **ParallelForEach \<T >** etkinlik Tasarımcısı ' nın **' de yer** alan "etkinliği buraya bırak" ipucu metin kutusuna bir etkinlik bırakın.|
|**TypeArgument**|Doğru|Genel parametre *t*tarafından belirtilen <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> koleksiyonundaki öğelerin türü. Varsayılan olarak, **TypeArgument** değeri **Int32**olarak ayarlanır. **ParallelForEach \<T >** Etkinlik tasarımcısında T türünü değiştirmek Için, özellik kılavuzunda **TypeArgument** Birleşik giriş kutusunun değerini değiştirin.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. @No__t_0 ayarlamak için, **Özellikler** penceresindeki "bir vb ifadesi girin" veya **değerler** kutusuna "bir vb ifadesi girin" İpucu **metin kutusuna,** kutuya bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] **> \<T** ifadesi yazın.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Her yineleme tamamlandıktan sonra değerlendirilir. True olarak değerlendirilirse, zamanlanan bekleyen yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, tüm zamanlanmış deyimler tamamlanana kadar yürütülür.|

 Varsayılan olarak, döngü yineleyicisi öğe olarak adlandırılır. Bir yineleyici değişkeninin adını **ParallelForEach \<T >** etkinlik Tasarımcısı ' nda bulunan **foreach** kutusunda değiştirebilirsiniz. Döngü yineleyicisi, <xref:System.Activities.Statements.ParallelForEach%601> etkinliğinin alt öğelerindeki ifadelerde kullanılabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Sıralı](../workflow-designer/sequence-activity-designer.md) [paralel](../workflow-designer/parallel-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)