---
title: ParallelForEach &lt; T &gt; Etkinlik Tasarımcısı
description: Bu İş Akışı Tasarımcısı, ParallelForEach etkinliğinin bir koleksiyonun öğelerini nasıl numaralara ekli olduğunu ve koleksiyonun her öğesi için paralel bir deyim <T> yürütmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 07158b14beca37272c19f4a5b896d7c70223a667
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114569"
---
# <a name="parallelforeach-activity-designer"></a>ParallelForEach Etkinlik Tasarımcısı

Etkinlik bir koleksiyonun öğelerini numaralandırarak koleksiyonun her öğesi için aynı iş parçacığında zaman uyumsuz olarak paralel bir şekilde katıştırılmış bir <xref:System.Activities.Statements.ParallelForEach%601> deyim yürütür. Bu etkinliğin alt etkinliklerinin <xref:System.Activities.Statements.Sequence> boşta olması bekleniyorsa etkinlik yerine bu akış denetimi etkinliğini kullanın.

<xref:System.Activities.Statements.ParallelForEach%601>Etkinliğin, kullanıcı tarafından belirtilen bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> ifadeyi içeren Visual Basic vardır. Etkinlik, <xref:System.Activities.Statements.ParallelForEach%601> her dal tamamlandıktan sonra bu özelliği değerlendirir. true olarak **değerlendirilirse,** etkinlik <xref:System.Activities.Statements.ParallelForEach%601> diğer dalları yürütmeden tamamlanır. true <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> olarak değerlendirilmezse, tüm alt etkinlikleri tamamlandığında etkinlik  <xref:System.Activities.Statements.ParallelForEach%601> tamamlanır.

## <a name="the-parallelforeacht-activity"></a>ParallelForEach<T \> Etkinliği

<xref:System.Activities.Statements.ParallelForEach%601> , değerlerini numaralar ve <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> numaralı olduğu her değer için değerini zamanlar. Yalnızca <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> zamanlar. Gövdenin nasıl çalıştırılma durumu, boşta olup <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> olmadığına bağlıdır.

boşta durmazsa, zamanlanan etkinlikler bir yığın olarak işlandığı için ters sırada yürütülür, ilk olarak zamanlanan son <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> etkinlik yürütülür. Örneğin, içinde bir koleksiyonunuz varsa {1,2,3,4} ve değeri yazmak için gövde olarak <xref:System.Activities.Statements.ParallelForEach%601> **WriteLine** kullanırsanız. Konsolda 4, 3, 2, 1 yazdırılmış. Bunun nedeni **WriteLine'ın** boşta kalmama nedenidir, bu nedenle 4 **WriteLine** etkinlikleri zamanlandıktan sonra bir yığın davranışı kullanılarak yürütülür (son olarak).

Ancak içinde etkinlik veya etkinlik gibi boşta kalma <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> süresine sahip <xref:System.ServiceModel.Activities.Receive> etkinliklerin <xref:System.Activities.Statements.Delay> varsa. Bu şekilde tamamlanacakları zaman beklemelerine gerek yoktur. <xref:System.Activities.Statements.ParallelForEach%601> bir sonraki zamanlanmış gövde etkinliğine gider ve yürütmeyi deneyin. Bu etkinlik de boşta olursa bir <xref:System.Activities.Statements.ParallelForEach%601> sonraki gövde etkinliğine geç.

### <a name="using-the-parallelforeacht-activity-designer"></a>ParallelForEach Etkinlik \<T> Tasarımcısını Kullanma

Araç Kutusunun **Denetim \<T> Denetimi Flow ParallelForEach** etkinlik **tasarımcısına erişin.** 

**ParallelForEach \<T>** etkinlik tasarımcısı Araç Kutusundan  sürüklenerek etkinlik tasarımcılarının normalde yerleştirilmeleri (örneğin, bir Sıra etkinliği  tasarımcısının içine) İş Akışı Tasarımcısı yüzeyine bırakılır. Varsayılan olarak <xref:System.Activities.Statements.ParallelForEach%601> <xref:System.Activities.Activity.DisplayName%2A> **Int32 İş Akışı Tasarımcısı ParallelForEach \>** içeren bir etkinlik<oluşturur.

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'de ParallelForEach<T \> Özellikleri

Aşağıdaki tabloda en kullanışlı etkinlik <xref:System.Activities.Statements.ParallelForEach%601> özellikleri ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **ParallelForEach'tir. \<Int32>** Değer isteğe bağlı olarak Özellikler kılavuzunda **veya** doğrudan etkinlik tasarımcısı üst bilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Yanlış|Koleksiyonda her öğe için yürütülecek etkinlik. Etkinliği eklemek <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> için araç kutusundan **ParallelForEach \<T>** etkinlik tasarımcısında "Etkinliği Buraya Bırak" ipucu metniyle Gövde  kutusuna bir etkinlik bırakın.|
|**TypeArgument**|Doğru|T genel parametresi tarafından <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> belirtilen koleksiyondaki öğelerin *türü.* **TypeArgument varsayılan olarak** **Int32 olarak ayarlanır.** **ParallelForEach \>**<T etkinlik tasarımcısında T türünü değiştirmek için Property Grid'de **TypeArgument** birleşik giriş kutusunun değerini değiştirebilirsiniz.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Doğru|Tekrar etmek için öğe koleksiyonu. ayarlamak için <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> **ForEach \><T**   etkinlik tasarımcısının Değerler kutusuna "VB ifadesi girin" ipucu metniyle veya Özellikler penceresindeki Değerler kutusuna bir  Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Her yineleme tamamlandıktan sonra değerlendirilir. True olarak değerlendirilirse, zamanlanmış bekleyen yinelemeler iptal edilir. Bu özellik ayarlanmazsa, tüm zamanlanmış deyimler tamamlanana kadar yürütülür.|

Varsayılan olarak, döngü tekrarlayıcı öğe olarak adlandırılmıştır. **ParallelForEach \<T>** etkinlik tasarımcısında **ForEach** kutusunda bir daha fazla değişkenin adını değiştirebilirsiniz. Döngü tekrarlayıcı, etkinliğin en küçük ifadelerinde <xref:System.Activities.Statements.ParallelForEach%601> kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Paralel](../workflow-designer/parallel-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)