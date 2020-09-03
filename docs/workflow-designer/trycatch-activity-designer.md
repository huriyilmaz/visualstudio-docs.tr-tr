---
title: İş Akışı Tasarımcısı-TryCatch etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b70f1d3174990ec12c621dff4a45ce4d899ceb4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593076"
---
# <a name="trycatch-activity-designer"></a>TryCatch Etkinlik Tasarımcısı

**TryCatch** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.TryCatch> .

## <a name="the-trycatch-activity"></a>TryCatch etkinliği
 <xref:System.Activities.Statements.TryCatch>Etkinlik <xref:System.Activities.Statements.TryCatch.Try%2A> , bir etkinlik, bir **Catch \<TException> ** koleksiyonu ve bir etkinlik içerir <xref:System.Activities.Statements.TryCatch.Finally%2A> . <xref:System.Activities.Statements.Catch%601> **TException** türü bir <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> ve içerir <xref:System.Activities.Statements.Catch%601.Action%2A> . Bunlar birlikte, tipik bir özel durum tabanlı hata işleme mekanizması uygulamak için kullanılır. <xref:System.Activities.Statements.TryCatch>Etkinlik, etkinliğini yürütmeye çalışır <xref:System.Activities.Statements.TryCatch.Try%2A> . <xref:System.Activities.Statements.TryCatch.Try%2A>Etkinlik herhangi bir özel durum oluşturursa, <xref:System.Activities.Statements.TryCatch> etkinlik özel durumu eşleştirmek için **catch<\> TException** koleksiyonunu kullanır. Bir eşleşme varsa, <xref:System.Activities.Statements.Catch%601.Action%2A> karşılık gelen ** \<TException> catch** yürütülür ve özel durum için hata işleme mantığı görevi görür. <xref:System.Activities.Statements.TryCatch.Try%2A>Bölümdeki etkinlikler başarıyla tamamlandıysanız veya başarılı bir şekilde tamamlandıktan sonra etkinlik, <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.TryCatch.Finally%2A> etkinliğini yürütür. Daha fazla bilgi için bkz. [Windows iş akışı özel durumları](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>TryCatch etkinlik tasarımcısını kullanma

**Araç kutusunun** **hata işleme** kategorisindeki **TryCatch** etkinlik tasarımcısına erişin.

**TryCatch** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.TryCatch> , varsayılan TryCatch olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **TryCatch** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, **TryCatch** etkinlik tasarımcısının yüzeyinde düzenlenmelidir.

Genişletilmiş görünümdeki **TRY**, **catch**ve **finally** kutularını görmek için, **TryCatch** Tasarımcısı ' nın sağ üst köşesindeki Genişlet düğmesine tıklayın. Bir catch eklemek için, **TryCatch** tasarımcısında **Yeni catch Ekle** düğmesine tıklayın. Düğme, bir tür açılan kutusu olarak değişir. Catch eklemek için bir özel durum türü seçin ve ENTER tuşuna basın. **Catch eklendikten sonra, catch**alanı genişler ve bir etkinlik, catch için yürütme mantığını tanımlamak üzere catch 'e bırakılabilir. Genişletilmiş catch alanının sağ tarafında bir metin kutusu olduğunu unutmayın. Bu metin kutusunu kullanarak özel durum değişkenine ad verebilirsiniz. Özel durum değişkeni yalnızca aynı **catch**içindeki etkinlikler için kullanılabilir.

**TryCatch** Tasarımcısı, **catch**düzenlemesini desteklemiyor. Özel durum türünü değiştirmek isterseniz, **catch** 'i silip yeni bir tane eklemeniz gerekir. Bir **catch** , seçilip silinerek veya sağ tıklanarak erişilen bağlam menüsünde **Sil** ' i seçerek silinebilir.

### <a name="the-trycatch-properties"></a>TryCatch özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.TryCatch> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.TryCatch> . Varsayılan değer TryCatch ' dir.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Yanlış|İlk yürütüldüğünde etkinlik yürütülür <xref:System.Activities.Statements.TryCatch> .|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Yanlış|**Catch** <xref:System.Activities.Statements.TryCatch.Try%2A> Etkinlik bir özel durum oluşturduğunda denetlenecek catch öğelerinin koleksiyonu.<br /><br /> ' De en az bir etkinlik <xref:System.Activities.Statements.TryCatch.Catches%2A> veya bloktaki bir etkinlik eklemeniz gerekiyor <xref:System.Activities.Statements.TryCatch.Finally%2A> .|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Yanlış|<xref:System.Activities.Statements.TryCatch.Try%2A>Koleksiyonda ve tüm gerekli etkinliklerden <xref:System.Activities.Statements.TryCatch.Catches%2A> yürütme tamamlandığında yürütülecek etkinlik.<br /><br /> ' De en az bir etkinlik <xref:System.Activities.Statements.TryCatch.Catches%2A> veya bloktaki bir etkinlik eklemeniz gerekiyor <xref:System.Activities.Statements.TryCatch.Finally%2A> .|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Yaratır](../workflow-designer/throw-activity-designer.md)
