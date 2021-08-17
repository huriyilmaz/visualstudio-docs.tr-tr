---
description: İletiler sekmesini kullanarak İletiler Görünümü'ne hangi ileti türlerinin listelen adreslen adreslen olduğunu seçin ve ileti arama ölçütlerini belirtin.
title: İletiler Sekmesi, İleti Seçenekleri İletişim Kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e1b81fd00da997912a0b9ad1ece7abc28136f8e7c7bb06fd91dd571d5cd752b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391258"
---
# <a name="messages-tab-message-options-dialog-box"></a>İletiler Sekmesi, İleti Seçenekleri İletişim Kutusu
İletiler **sekmesini** kullanarak İletiler Görünümü'ne hangi ileti türlerinin [listelen adreslen adreslen](../debugger/messages-view.md)olduğunu seçin ve ileti arama ölçütlerini belirtin. İleti Seçenekleri İletişim [Kutusunu görüntülemek için Spy](../debugger/message-options-dialog-box.md) **menüsünden Günlük** İletileri'ne tıklayın. 

 Genellikle, önce İleti **Grupları'ı seçer** ve ardından Görünüm'e tek tek İletiler'i **seçerek seçimde ince ayarlarlarsınız.** Tüm **düğmesi** tüm ileti türlerini seçer ve Hiçbiri **düğmesi** tüm türleri temizler.

 İletiler sekmesinde aşağıdaki ayarlar **kullanılabilir:**

 **Görüntülenilen İletiler** Görüntülemek için belirli iletileri seçin. Yeni bir İletiler penceresi 7.000.000'e kadar tüm iletileri görüntüler. İletiler sekmesinden  iletileri filtreleyelirken, bu filtre yalnızca yeni iletiler için geçerlidir; bu filtre, daha önce Windows uygulanır.

 **İleti Grupları** Görüntülemek için ileti gruplarını seçin. Kullanılabilir gruplar şunlardır:

- WM_USER: bir kod büyük veya bu değere eşit WM_USER

- Registered: **RegisterWindowMessage çağrısıyla** kaydedildi

- Bilinmiyor: 0 ile arasında bilinmeyen iletiler (WM_USER - 1)

  Bu İleti **Gruplarının, Görüntülemek** için İletiler altındaki belirli girişlere **eşlenemli olmadığını unutmayın.** Bir grup seçerek seçim doğrudan ileti akışına uygulanır.

  İleti Grupları içinde gri renkli bir  **onay kutusu,** Görüntülenilecek İletiler liste kutusunun o gruptaki iletiler için değiştirildiğinden; bu gruptaki tüm ileti türleri seçilmez.

  **Varsayılan Ayarlar olarak kaydetme** Geçerli ayarları daha sonra ileti arama seçenekleri olarak kullanmak üzere kaydedin. Bu ayarlar Spy++ çıkışında da kaydedilir.
