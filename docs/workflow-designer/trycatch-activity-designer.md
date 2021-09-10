---
title: İş Akışı Tasarımcısı - TryCatch Etkinlik Tasarımcısı
description: TryCatch etkinliği ve TryCatch etkinliği oluşturmak ve yapılandırmak için TryCatch etkinlik tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 662bea4838b06843bc529cd41adc3e2bf33425ca
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963771"
---
# <a name="trycatch-activity-designer"></a>TryCatch Etkinlik Tasarımcısı

Bir etkinlik oluşturmak ve yapılandırmak için **TryCatch** etkinlik tasarımcısı <xref:System.Activities.Statements.TryCatch> kullanılır.

## <a name="the-trycatch-activity"></a>TryCatch Etkinliği
 Etkinlik <xref:System.Activities.Statements.TryCatch> bir <xref:System.Activities.Statements.TryCatch.Try%2A> etkinlik, bir **Catch \<TException>** koleksiyonu ve bir etkinlik <xref:System.Activities.Statements.TryCatch.Finally%2A> içerir. <xref:System.Activities.Statements.Catch%601> **TException türünde bir ve** <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> <xref:System.Activities.Statements.Catch%601.Action%2A> içerir. Bunlar birlikte tipik bir özel durum tabanlı hata işleme mekanizması uygulamak için kullanılır. Etkinlik, <xref:System.Activities.Statements.TryCatch> etkinliğini yürütmeye <xref:System.Activities.Statements.TryCatch.Try%2A> çalışır. Etkinlik herhangi <xref:System.Activities.Statements.TryCatch.Try%2A> bir özel durum oluşturursa, etkinlik özel durumla eş<<xref:System.Activities.Statements.TryCatch> **TException \>** koleksiyonunu kullanır. Bir eşleşme varsa, özel durum için hata işleme mantığı olarak görev yapan ilgili <xref:System.Activities.Statements.Catch%601.Action%2A> **\<TException> Catch'in** yürütülür. bölümündeki etkinlikler başarıyla <xref:System.Activities.Statements.TryCatch.Try%2A> tamamlanırsa veya başarıyla tamamlandıktan sonra etkinlik etkinlik <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.TryCatch.Finally%2A> yürütülür. Daha fazla bilgi için [bkz. Windows özel durumları.](/dotnet/framework/windows-workflow-foundation/exceptions)

### <a name="using-the-trycatch-activity-designer"></a>TryCatch Etkinlik Tasarımcısını Kullanma

Araç Kutusunun Hata İşleme kategorisinde **tryCatch** **etkinlik** **tasarımcısına erişin.**

**TryCatch** etkinlik tasarımcısı Araç Kutusundan  sürüklenip bir içinde olduğu gibi, İş Akışı Tasarımcısı yerleştirildikten sonra bu alan yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Bu, varsayılan <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Activity.DisplayName%2A> TryCatch değerine sahip bir etkinlik oluşturur. Değer <xref:System.Activities.Activity.DisplayName%2A> **TryCatch** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir. Diğer özellikler **TryCatch** etkinlik tasarımcısının yüzeyinde düzenlenemez.

Genişletilmiş görünümde Try **,** **Catches** ve **Finally** kutularını görmek için **TryCatch** tasarımcısının sağ üst köşesindeki genişlet düğmesine tıklayın. Bir yakalama eklemek için **TryCatch** **tasarımcısında** Yeni catch ekle düğmesine tıklayın. Düğme bir tür birleşik giriş kutusuna değişir. Bir özel durum türü seçin ve yakalamayı eklemek için ENTER tuşuna basın. Bir **Catch ekledikten** sonra, yakalama alanı genişler ve catch için yürütme mantığını tanımlamak üzere bir etkinlik catch içine bırakılır. Genişletilmiş yakalama alanı sağ tarafında bir metin kutusu olduğunu unutmayın. Bu metin kutusunu kullanarak özel durum değişkenine ad veabilirsiniz. Özel durum değişkeni yalnızca aynı Catch içindeki etkinlikler için **kullanılabilir.**

**TryCatch tasarımcısı** Catch'in düzenlenmesini **desteklemez.** Özel durum türünü değiştirmek için Catch'i silmeniz ve **yenisini** eklemeniz gerekir. Bir **Catch,** seçilerek ve silinerek veya sağ  tıklanarak erişilen bağlam menüsünde Sil'i seçerek silinebilir.

### <a name="the-trycatch-properties"></a>TryCatch Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.TryCatch> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını <xref:System.Activities.Statements.TryCatch> belirtir. Varsayılan değer TryCatch'tir.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Yanlış|Etkinlik ilk kez yürütülürken <xref:System.Activities.Statements.TryCatch> yürütülür.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Yanlış|Etkinlik bir **özel** durum lendiğinde denetlenen <xref:System.Activities.Statements.TryCatch.Try%2A> Catch öğelerinin koleksiyonu.<br /><br /> en az bir etkinlik eklemeniz veya <xref:System.Activities.Statements.TryCatch.Catches%2A> blokta bir etkinlik eklemeniz <xref:System.Activities.Statements.TryCatch.Finally%2A> gerekir.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Yanlış|koleksiyonda ve gerekli etkinlikler <xref:System.Activities.Statements.TryCatch.Try%2A> yürütmeyi tamamlandıktan sonra <xref:System.Activities.Statements.TryCatch.Catches%2A> yürütülecek etkinlik.<br /><br /> en az bir etkinlik eklemeniz veya <xref:System.Activities.Statements.TryCatch.Catches%2A> blokta bir etkinlik eklemeniz <xref:System.Activities.Statements.TryCatch.Finally%2A> gerekir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Atmak](../workflow-designer/throw-activity-designer.md)
