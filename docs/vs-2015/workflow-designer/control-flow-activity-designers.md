---
title: Denetim akışı etkinlik tasarımcıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f17913864f80e04c3e8b8e703f057094c9bdea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656925"
---
# <a name="control-flow-activity-designers"></a>Akış Etkinliği Tasarımcılarını denetleme
[!INCLUDE[wfd1](../includes/wfd1-md.md)], iş akışlarınızı oluştururken kullanabileceğiniz, sistem tarafından sağlanmış bir dizi etkinliği içerir. Bu bölüm, bir iş akışı içindeki akışı denetlemek için kullanılan sistem tarafından sağlanmış etkinlikleri içerir. Aşağıdaki konular bu etkinlikleri anlatmaktadır ve bunların nasıl kullanılacağına ilişkin yönergeler sağlar.

## <a name="in-this-section"></a>Bu Bölümde
 [DoWhile](../workflow-designer/dowhile-activity-designer.md) Belirli bir koşul **true**olarak hesaplanana kadar, gövdesinde bulunan etkinliği en az bir kez yürütür.

 [ForEach \<T >](foreach-t-activity-designer.md) Belirtilen koleksiyondaki her öğe için gövdesinde içerilen etkinliği yürütür.

 Şunu [içeriyorsa](../workflow-designer/if-activity-designer.md) Bir koşulu değerlendirir ve bu değerlendirmenin sonuçlarına bağlı olarak bir etkinliği yürütür.

 [Paralel](../workflow-designer/parallel-activity-designer.md) Bir alt etkinlik koleksiyonunu eşzamanlı olarak yürütür.

 [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) Bir koleksiyonun öğelerini numaralandırır ve her bir koleksiyon öğesi için gömülü bir ifadeyi paralel olarak yürütür

 [Seç](../workflow-designer/pick-activity-designer.md) Olay tabanlı akış denetimi sağlayan bazı bir olaya yanıt olarak çeşitli dallardan birini yürütür.

 [PickBranch](../workflow-designer/pickbranch-activity-designer.md) @No__t_1 etkinliğinde yürütmenin olası yolunu sağlar.

 [Sıra](../workflow-designer/sequence-activity-designer.md) Sırayla çalıştırdığı alt etkinliklerin sıralı bir koleksiyonunu içerir.

 [@No__t_1T > Değiştir](switch-t-activity-designer.md) Belirtilen bir ifadeyi değerlendirir ve aktiviteyi, ilişkili anahtarı değerlendirmeden elde edilen değerle eşleşen bir etkinlik koleksiyonundan yürütür.

 [Sırasında](../workflow-designer/while-activity-designer.md) Belirtilen koşul **doğru**olarak değerlendirirken gövdesinde içerilen etkinliği yürütür.

## <a name="reference"></a>Başvuru
 <xref:System.Activities.Activity>

 <xref:System.Activities.Statements.DoWhile>

 <xref:System.Activities.Statements.ForEach%601>

 <xref:System.Activities.Statements.If>

 <xref:System.Activities.Statements.Parallel>

 <xref:System.Activities.Statements.ParallelForEach%601>

 <xref:System.Activities.Statements.Pick>

 <xref:System.Activities.Statements.PickBranch>

 <xref:System.Activities.Statements.Sequence>

 <xref:System.Activities.Statements.Switch%601>

 <xref:System.Activities.Statements.While>

## <a name="related-sections"></a>İlgili Bölümler
 Diğer etkinlik tasarımcıları türleri için aşağıdaki konulara bakın.

 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)

 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)

 [Messaging](../workflow-designer/messaging-activity-designers.md)

 [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)

 [Temel Türler](../workflow-designer/primitives-activity-designers.md)

 [İşlem](../workflow-designer/transaction-activity-designers.md)

 [Koleksiyon](../workflow-designer/collection-activity-designers.md)

 [Hata İşleme](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Dış Kaynaklar
 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)