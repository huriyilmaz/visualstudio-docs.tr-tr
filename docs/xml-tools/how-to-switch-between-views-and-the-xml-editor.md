---
title: 'Nasıl yapılır: Görünümler ve XML düzenleyicisi arasında geçiş'
description: XML Şema Tasarımcısı (XSD Tasarımcısı) görünümleri ile XML düzenleyicisi arasında geçiş yapmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1a6f9be548b725aa664cd6223ee2eb9891c77fdc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037752"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Nasıl yapılır: Görünümler ve XML düzenleyicisi arasında geçiş

Bu konuda, XML Şema Tasarımcısı (XSD Tasarımcısı) görünümleri ile XML düzenleyicisi arasında nasıl geçiş olduğu gösterilmektedir. Bu örnek, Satın [alma siparişi şemasını kullanır.](../xml-tools/sample-xsd-file-simple-schema.md)

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Görünümler ile XML düzenleyicisi arasında geçiş yapmak için

1. Yeni bir XML şema dosyası oluşturmak ve düzenlemek için, Nasıl [yapılır: XSD şema dosyası oluşturma ve düzenleme'de yer alan adımları izleyin.](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)

2. XML düzenleyicisinden XML Şema Tasarımcısı'nda geçiş yapmak için XML düzenleyicisinde herhangi bir yere sağ tıklayın ve xml **Görünüm Tasarımcısı.**

3. Filigran kullanarak Graph Görünümüne geçmek için Başlangıç **Görünümü'Graph** düğümler arasındaki ilişkiyi görmek için Graph görünümünü kullan'a tıklayın.

4. XML Şema `USAddress` **Gezgini'nde düğümü Graph** sürükleyin. Görünüm'de `USAddress` düğüme sağ Graph ve bağlam menüsünde İçerik Modeli **Görünümünde Göster'i** seçin.

     Düğümün ayrıntılarının yer alan İçerik Modeli `USAddress` Görünümü görüntülenir.

5. Araç çubuğunu kullanarak İçerik Modeli Görünümünden Başlangıç Görünümüne geçmek için XSD araç **çubuğundaki** Görünümü Başlat düğmesine tıklayın.

6. Kısayol tuşlarını kullanarak görünümler arasında geçiş yapmak için Başlangıç Görünümü için + **Ctrl 1,** Graph Görünümü için **Ctrl** 2 ve İçerik Modeli Görünümü için +   + **3** tuşlarına basın.

7. İçerik Modeli Görünümü'nde XML düzenleyicisine gitmek için düğüme sağ tıklayın ve bağlam menüsünde **Kodu** Görüntüle'yi seçin.
