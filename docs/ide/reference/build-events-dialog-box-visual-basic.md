---
title: Derleme Olayları İletişim Kutusu (Visual Basic)
description: Derleme yapılandırma yönergelerini ve derleme öncesi ya da oluşturma sonrası olaylarının çalıştırıldığı koşulları belirtmek için derleme olayları iletişim kutusunu nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 6ce6bb21e00470203c5a47dbb0f102c43d0ac0bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836428"
---
# <a name="build-events-dialog-box-visual-basic"></a>Derleme Olayları İletişim Kutusu (Visual Basic)

Derleme yapılandırma yönergelerini belirtmek için **derleme olayları** iletişim kutusunu kullanın. Ayrıca, herhangi bir oluşturma öncesi veya oluşturma sonrası olayının çalıştırıldığı koşulları belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Oluşturma öncesi olay komut satırı**

Yapı başlamadan önce yürütülecek komutları belirtir. Uzun komutları yazmak için, oluşturma öncesi [olay/oluşturma sonrası olay komut satırı Iletişim kutusunu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)göstermek Için **derleme ön yapısını Düzenle** ' ye tıklayın.

> [!NOTE]
> Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

**Oluşturma sonrası olay komut satırı**

Yapı bittikten sonra yürütülecek komutları belirtir. Uzun komutları yazmak için derleme sonrası **olay/oluşturma sonrası olay komut satırı** iletişim kutusunu göstermek üzere **derlemeyi Düzenle** ' ye tıklayın.

> [!NOTE]
> `call`. Bat dosyalarını çalıştıran tüm derleme sonrası komutlarının önüne bir ifade ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

**Oluşturma sonrası olayını Çalıştır**

Aşağıdaki tabloda gösterildiği gibi, oluşturma sonrası olayının çalıştırılacağı koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her zaman**|Oluşturma sonrası olay, yapılandırmanın başarılı olup olmamasına bakılmaksızın çalışacaktır.|
|**Başarılı derleme üzerinde**|Oluşturma sonrası olay, derleme başarılı olursa çalışır. Bu olay, derleme başarılı olduğu sürece güncel olan bir proje için de çalışır. Bu varsayılan ayardır.|
|**Derleme proje çıkışını güncelleştirdiğinde**|Oluşturma sonrası olay, yalnızca derleyicinin çıkış dosyası (. exe veya. dll) önceki derleyici çıkış dosyasından farklı olduğunda çalışır. Bir proje güncel ise, oluşturma sonrası bir olay çalıştırılmaz.|

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Oluşturma öncesi olay/oluşturma sonrası olay komut satırı Iletişim kutusu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)