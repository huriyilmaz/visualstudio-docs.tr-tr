---
title: Derleme olayları sayfası, proje Tasarımcısı (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a310de2e1fd754f16fd701f264f8d5ee8aac4166
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660942"
---
# <a name="build-events-page-project-designer-c"></a>Derleme Olayları Sayfası, Proje Tasarımcısı (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yapı yapılandırma yönergelerini belirtmek için **Proje Tasarımcısı** ' nın **Olayları oluştur** sayfasını kullanın. Ayrıca, herhangi bir oluşturma sonrası olayının çalıştırıldığı koşulları belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derleme olaylarını belirtmeC#()](../../ide/how-to-specify-build-events-csharp.md)ve [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>UIElement Listesi
 **Yapılandırma** Bu denetim bu sayfada düzenlenebilir değildir. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platform** Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Oluşturma öncesi olay komut satırı** Yapı başlamadan önce yürütülecek komutları belirtir. Uzun komutları yazmak için, oluşturma öncesi [olay/oluşturma sonrası olay komut satırı Iletişim kutusunu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)göstermek Için **derleme ön yapısını Düzenle** ' ye tıklayın.

> [!NOTE]
> Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

 **Oluşturma sonrası olay komut satırı** Yapı bittikten sonra yürütülecek komutları belirtir. Uzun komutları yazmak için derleme sonrası **olay/oluşturma sonrası olay komut satırı Iletişim kutusunu**göstermek üzere **derlemeyi Düzenle** ' ye tıklayın.

> [!NOTE]
> . Bat dosyalarını çalıştıran tüm derleme sonrası komutları önüne bir `call` ekstresi ekleyin. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Oluşturma sonrası olayını Çalıştır** Aşağıdaki tabloda gösterildiği gibi, oluşturma sonrası olayının çalışması için aşağıdaki koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her**|Oluşturma sonrası olay, yapılandırmanın başarılı olup olmamasına bakılmaksızın çalışacaktır.|
|**Başarılı derleme üzerinde**|Oluşturma sonrası olay, derleme başarılı olursa çalışır. Bu nedenle, derleme başarılı olduğu sürece olay, güncel olan bir proje için de çalışır.|
|**Derleme proje çıkışını güncelleştirdiğinde**|Oluşturma sonrası olay, yalnızca derleyicinin çıkış dosyası (. exe veya. dll) önceki derleyici çıkış dosyasından farklı olduğunda çalışır. Bu nedenle, bir proje güncel ise, derleme sonrası bir olay çalıştırılmaz.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [nasıl yapılır: derleme olaylarını belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md) [Proje özellikleri başvuru](../../ide/reference/project-properties-reference.md) [derleme ve](../../ide/compiling-and-building-in-visual-studio.md) derleme
