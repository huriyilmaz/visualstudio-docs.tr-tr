---
title: Derleme Olayları İletişim Kutusu (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4cd0a46e5ab4cc9c3a9e00773818d536b84891
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461442"
---
# <a name="build-events-dialog-box-visual-basic"></a>Derleme Olayları İletişim Kutusu (Visual Basic)

Yapı yapılandırma yönergelerini belirtmek için **Yapı Olayları** iletişim kutusunu kullanın. Ayrıca, herhangi bir ön yapı veya yapım sonrası olayın çalıştırıldığı koşulları da belirtebilirsiniz. Daha fazla bilgi için [bkz: Yapı Olayları (Visual Basic) belirtin.](../../ide/how-to-specify-build-events-visual-basic.md)

**Önceden oluşturma olay komut satırı**

Yapı başlamadan önce yürütülecek komutları belirtir. Uzun komutlar yazmak için, [Önceden Yapılan Olay/Post-build Olay Komut Satırı İletişim Kutusu'nu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)görüntülemek için **Ön Yapıyı** Düzenle'yi tıklatın.

> [!NOTE]
> Proje güncelse ve hiçbir yapı tetiklenmiyorsa, önceden yapı olayları çalışmaz.

**Oluşturma sonrası olay komut satırı**

Yapı sona erdikten sonra yürütülecek komutları belirtir. Uzun komutlar yazmak için, **Önceden Yapılan olay/Post-build Event Komut Satırı** iletişim kutusunu görüntülemek için **Post-build'i** düzenle'yi tıklatın.

> [!NOTE]
> .bat `call` dosyalarını çalıştıran tüm yapı sonrası komutlardan önce bir deyim ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

**Oluşturma sonrası etkinliği çalıştırma**

Aşağıdaki tabloda gösterildiği gibi, yapı sonrası olayın çalışması için koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her zaman**|Yapının başarılı olup olmadığına bakılmaksızın, oluşturma sonrası olay çalışacaktır.|
|**Başarılı yapıda**|Yapı başarılı olursa, yapı sonrası olay çalışacaktır. Etkinlik, yapı başarılı olduğu sürece güncel bir proje için bile çalışacaktır. Bu varsayılan ayardır.|
|**Yapı proje çıktısını güncellediğinde**|Yapı sonrası olay yalnızca derleyicinin çıktı dosyası (.exe veya .dll) önceki derleyici çıktı dosyasından farklı olduğunda çalışır. Bir proje güncelse, yapı sonrası olay çalıştırılmez.|

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Önceden Yapı Olay/Post-build Olay Komut Satırı İletişim Kutusu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)