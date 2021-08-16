---
title: İş Akışı Tasarımcısında Hata İletileri
description: Verilerle çalışırken karşılaşabilirsiniz hata iletisi türleri hakkında bilgi İş Akışı Tasarımcısı.
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
ms.openlocfilehash: 2e7bf7553867e832c03eb921e6aff51a61ab8b460b5b38fddf10ad01d78a2bf8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121407986"
---
# <a name="error-messages-in-workflow-designer"></a>İş Akışı Tasarımcısında Hata İletileri

Bu konu başlığında, hata iletileriyle çalışırken karşılaşabilirsiniz hata iletisi türleri İş Akışı Tasarımcısı.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>HataNın Oluştuğu İş Akışı Tasarımcısı Durumlar

Aşağıdaki İş Akışı Tasarımcısı hata oluşur:

1. İfadede bir hata var.

2. Etkinliğin doğrulama kısıtlamaları karşılanamadı.

3. XAML dosyasında bir etkinliğin yüklenemedik hatasına neden olan hatalar var.

4. XAML dosyasında iş akışının yüklenemedik hatalarına neden olan hatalar var.

Geçersiz ifadeler ve memnun olmayan doğrulama kısıtlamaları, iş akışının derlemenin başarısız olmasına neden olmaz. İş akışınızı oluşturma başarılı olur, <xref:System.Activities.InvalidWorkflowException> ancak çalışma zamanında bir atılan. XAML dosyasında hatalar varsa derleme başarısız olur.

Bu Visual Studio, bir iş akışı yüklendiğinde, hataları Hata Listesinde **görüntülenir.** Hatanın kaynağı olan etkinlikte gezinmek için Hata Listesinde hataya **çift tıklayın.**

### <a name="expression-errors"></a>İfade Hataları
 Geçersiz bir ifade, ifadenin yanında beyaz ünlem işareti olan kırmızı bir daire ile işaret edilir. Bu simgenin üzerine gelindiğinde hatanın kaynağını açıklayan bir araç ipucu görüntülenir. Hata Visual Studio altındaki satırı görüntülemek için ifadeye tıklayın. Satırlı metnin üzerine gelindiğinde hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="activity-validation-errors"></a>Etkinlik Doğrulama Hataları
 Bir etkinliğin doğrulama kısıtlamaları karşılanmazsa, etkinliğin sağ üst köşesinde beyaz ünlem işareti olan kırmızı bir daire görünür. Bu simgenin üzerine gelindiğinde hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="xaml-load-errors"></a>XAML Yükleme Hataları
 Bir etkinlik yüklenemezse, "XAML'de hatalar nedeniyle etkinlik yüklenemedi" metnine sahip kırmızı bir kutu görüntülenir. Bu durum genellikle etkinliğin türü çözümlenemezse gerçekleşir. Geçersiz etkinlik, kırmızı kutu seçilerek ve silinerek tasarımcıda silinebilir.

### <a name="workflow-load-errors"></a>İş Akışı Yükleme Hataları
 Bir iş akışı yüklenemezse tasarımcı yüzeyinde "İş Akışı Tasarımcısı karşılaşılan sorunlar" metni ve iş akışının yüklenemedi hatasına neden olan özel durum bilgileri görüntülenir. Bu durum genellikle XAML dosyası ayrıştırılamaysa oluşur.
