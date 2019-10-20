---
title: Derleme olayları Iletişim kutusu (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9fa3b4365f49d172e077ca132b26a49580228c25
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660954"
---
# <a name="build-events-dialog-box-visual-basic"></a>Derleme Olayları İletişim Kutusu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Derleme yapılandırma yönergelerini belirtmek için **derleme olayları** iletişim kutusunu kullanın. Ayrıca, herhangi bir oluşturma öncesi veya oluşturma sonrası olayının çalıştırıldığı koşulları belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Oluşturma öncesi olay komut satırı** Yapı başlamadan önce yürütülecek komutları belirtir. Uzun komutları yazmak için, oluşturma öncesi [olay/oluşturma sonrası olay komut satırı Iletişim kutusunu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)göstermek Için **derleme ön yapısını Düzenle** ' ye tıklayın.

> [!NOTE]
> Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

 **Oluşturma sonrası olay komut satırı** Yapı bittikten sonra yürütülecek komutları belirtir. Uzun komutları yazmak için derleme sonrası **olay/oluşturma sonrası olay komut satırı d**ialog kutusunu göstermek üzere **derlemeyi Düzenle** ' ye tıklayın.

> [!NOTE]
> . Bat dosyalarını çalıştıran tüm derleme sonrası komutları önüne bir `call` ekstresi ekleyin. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Oluşturma sonrası olayını Çalıştır** Aşağıdaki tabloda gösterildiği gibi, oluşturma sonrası olayının çalıştırılacağı koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her**|Oluşturma sonrası olay, yapılandırmanın başarılı olup olmamasına bakılmaksızın çalışacaktır.|
|**Başarılı derleme üzerinde**|Oluşturma sonrası olay, derleme başarılı olursa çalışır. Bu olay, derleme başarılı olduğu sürece güncel olan bir proje için de çalışır. Varsayılan ayar budur.|
|**Derleme proje çıkışını güncelleştirdiğinde**|Oluşturma sonrası olay, yalnızca derleyicinin çıkış dosyası (. exe veya. dll) önceki derleyici çıkış dosyasından farklı olduğunda çalışır. Bir proje güncel ise, oluşturma sonrası bir olay çalıştırılmaz.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme sayfası, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [nasıl yapılır: derleme olayları belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [oluşturma öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
