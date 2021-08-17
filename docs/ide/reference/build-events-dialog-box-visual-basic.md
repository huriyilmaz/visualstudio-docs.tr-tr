---
title: Derleme Olayları İletişim Kutusu (Visual Basic)
description: Derleme yapılandırma yönergelerini ve derleme öncesi veya derleme sonrası olayların çalıştır olduğu koşulları belirtmek için Derleme Olayları iletişim kutusunu nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89526efde0424cecaf8808b0a869e664fec7d2c55d3aa893b9e76c8deec25863
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372640"
---
# <a name="build-events-dialog-box-visual-basic"></a>Derleme Olayları İletişim Kutusu (Visual Basic)

Derleme yapılandırma **yönergelerini** belirtmek için Derleme Olayları iletişim kutusunu kullanın. Derleme öncesi veya derleme sonrası olayların hangi koşullar altında çalıştırılamayacaklarını da belirtsiniz. Daha fazla bilgi için, [bkz. How to: Specify Build Events (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Derleme öncesi olay komut satırı**

Derleme başlamadan önce yürütülecek komutları belirtir. Uzun komutlar yazarak Derleme **Öncesi Düzenle'ye** tıklar ve Derleme Öncesi [Olay/Derleme Sonrası Olay Komut Satırı İletişim Kutusunu görüntüler.](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)

> [!NOTE]
> Proje güncelse ve derleme tetiklendiğinde derleme öncesi olaylar çalıştırlanmaz.

**Derleme sonrası olay komut satırı**

Derleme sona erdikten sonra yürütülecek komutları belirtir. Uzun komutlar yazın, Derleme **Öncesi Olay/Derleme** Sonrası Olay Komut Satırı iletişim kutusunu görüntülemek için Derleme sonrası **düzenle'ye** tıklayın.

> [!NOTE]
> Tüm derleme `call` sonrası komutlar ve dosyalarda çalıştırmadan önce .bat ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

**Derleme sonrası olayı çalıştırma**

Aşağıdaki tabloda gösterildiği gibi derleme sonrası olayı için çalıştıracak koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her zaman**|Derleme sonrası olay, derlemenin başarılı olup olmadığına bakılmaksızın çalıştıracak.|
|**Başarılı derlemede**|Derlemenin başarılı olması durumunda derleme sonrası olay çalıştıracak. Derleme başarılı olduğu sürece, olay güncel bir proje için bile çalışmasına neden olur. Bu varsayılan ayardır.|
|**Derleme proje çıkışını güncelleştirmesi**|Derleme sonrası olayı yalnızca derleyicinin çıkış dosyası (.exe veya .dll) önceki derleyici çıktı dosyasından farklı olduğunda çalışmasına neden olur. Bir proje güncelse derleme sonrası olay çalıştırlanmaz.|

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Derleme Öncesi Olay/Derleme Sonrası Olay Komut Satırı İletişim Kutusu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)