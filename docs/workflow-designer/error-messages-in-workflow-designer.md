---
title: İş Akışı Tasarımcısında Hata İletileri
description: İş Akışı Tasarımcısı çalışırken karşılaşabileceğiniz hata iletilerinin türleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 63cdfa5e371f67db2faffa7b18c0eacf4e2db411
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114777"
---
# <a name="error-messages-in-workflow-designer"></a>İş Akışı Tasarımcısında Hata İletileri

Bu konu, İş Akışı Tasarımcısı çalışırken karşılaşılabilecek hata iletilerinin türlerini açıklar.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>İş Akışı Tasarımcısı hatanın oluştuğu durumlar

İş Akışı Tasarımcısı hatalar aşağıdaki durumlarda oluşur:

1. İfadede bir hata var.

2. Etkinliğin doğrulama kısıtlamaları karşılanmadı.

3. XAML dosyasında bir etkinliğin yüklenmesine neden olan hatalar vardır.

4. XAML dosyasında iş akışının yükleme başarısız olmasına neden olan hatalar vardır.

Geçersiz ifadeler ve karşılanmamış doğrulama kısıtlamaları iş akışının derlenmemesine neden olmaz. İş akışınızı oluşturma işlemi başarılı olur, ancak çalışma zamanında bir oluşturulur <xref:System.Activities.InvalidWorkflowException> . XAML dosyasında hatalar varsa, yapı başarısız olur.

Visual Studio içinde, bir iş akışı yüklendiğinde, hataları **Hata Listesi** görüntülenir. Hatanın kaynağı olan etkinliğe gitmek için **hata listesi** hataya çift tıklayın.

### <a name="expression-errors"></a>İfade hataları
 Geçersiz bir ifade, ifadenin yanındaki beyaz ünlem işaretine sahip kırmızı bir daire ile belirtilir. Bu simgenin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir. Visual Studio içinde, hata kaynağının altını çizili çizgiyi görüntülemek için ifadeye tıklayın. Çizgili metnin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="activity-validation-errors"></a>Etkinlik doğrulama hataları
 Etkinliğin doğrulama kısıtlamaları karşılanmadığı zaman, etkinliğin sağ üst köşesinde beyaz ünlem işaretine sahip kırmızı bir daire görünür. Bu simgenin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="xaml-load-errors"></a>XAML yükleme hataları
 Bir etkinlik yüklenemediğinde, "XAML içindeki hatalar nedeniyle etkinlik yüklenemedi" metnini içeren kırmızı bir kutu görünür. Bu genellikle etkinliğin türü çözümlenemediğinde oluşur. Geçersiz etkinlik, kırmızı kutuyu seçerek ve silerek tasarımcıda silinebilir.

### <a name="workflow-load-errors"></a>İş akışı yükleme hataları
 Bir iş akışı yüklemesi başarısız olduğunda, "İş Akışı Tasarımcısı metin, çalışma akışının hatasına neden olan özel durum bilgileri ve tasarımcı yüzeyinde" belgenizde sorunlarla karşılaştı "şeklinde görünür. Bu genellikle XAML dosyası ayrıştırılamadığınızda meydana gelir.
