---
title: İş Akışı Tasarımcısında Hata İletileri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72592d21fdaba1ef47a15a113c820dffe0ba71eb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597054"
---
# <a name="error-messages-in-workflow-designer"></a>İş Akışı Tasarımcısında Hata İletileri

Bu konu, İş Akışı Tasarımcısı çalışırken karşılaşılabilecek hata iletilerinin türlerini açıklar.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>İş Akışı Tasarımcısı hatanın oluştuğu durumlar

İş Akışı Tasarımcısı hatalar aşağıdaki durumlarda oluşur:

1. İfadede bir hata var.

2. Etkinliğin doğrulama kısıtlamaları karşılanmadı.

3. XAML dosyasında bir etkinliğin yüklenmesine neden olan hatalar vardır.

4. XAML dosyasında iş akışının yükleme başarısız olmasına neden olan hatalar vardır.

Geçersiz ifadeler ve karşılanmamış doğrulama kısıtlamaları iş akışının derlenmemesine neden olmaz. İş akışınızı oluşturma işlemi başarılı olur, ancak çalışma zamanında bir <xref:System.Activities.InvalidWorkflowException> oluşturulur. XAML dosyasında hatalar varsa, yapı başarısız olur.

Visual Studio 'Nun içinde, bir iş akışı yüklendiğinde, hata **hata listesi**görüntülenir. Hatanın kaynağı olan etkinliğe gitmek için **hata listesi**hataya çift tıklayın.

### <a name="expression-errors"></a>İfade hataları
 Geçersiz bir ifade, ifadenin yanındaki beyaz ünlem işaretine sahip kırmızı bir daire ile belirtilir. Bu simgenin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir. Visual Studio içinde, hata kaynağının altını çizili çizgiyi görüntülemek için ifadeye tıklayın. Çizgili metnin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="activity-validation-errors"></a>Etkinlik doğrulama hataları
 Etkinliğin doğrulama kısıtlamaları karşılanmadığı zaman, etkinliğin sağ üst köşesinde beyaz ünlem işaretine sahip kırmızı bir daire görünür. Bu simgenin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="xaml-load-errors"></a>XAML yükleme hataları
 Bir etkinlik yüklenemediğinde, "XAML içindeki hatalar nedeniyle etkinlik yüklenemedi" metnini içeren kırmızı bir kutu görünür. Bu genellikle etkinliğin türü çözümlenemediğinde oluşur. Geçersiz etkinlik, kırmızı kutuyu seçerek ve silerek tasarımcıda silinebilir.

### <a name="workflow-load-errors"></a>İş akışı yükleme hataları
 Bir iş akışı yüklemesi başarısız olduğunda, "İş Akışı Tasarımcısı metin, çalışma akışının hatasına neden olan özel durum bilgileri ve tasarımcı yüzeyinde" belgenizde sorunlarla karşılaştı "şeklinde görünür. Bu genellikle XAML dosyası ayrıştırılamadığınızda meydana gelir.
