---
description: İleti görünümünde listelemek istediğiniz ileti türlerini seçmek için Iletiler sekmesini kullanın ve ileti arama ölçütlerini belirtin.
title: İletiler sekmesi, Ileti seçenekleri Iletişim kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 66c1abcedbf48e8cd80aeafe0c4a5def1ddbb9eb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160374"
---
# <a name="messages-tab-message-options-dialog-box"></a>İletiler Sekmesi, İleti Seçenekleri İletişim Kutusu
İleti [görünümünde](../debugger/messages-view.md)listelemek istediğiniz ileti türlerini seçmek ve ileti arama ölçütlerini belirtmek için **iletiler** sekmesini kullanın. [Ileti seçenekleri Iletişim kutusunu](../debugger/message-options-dialog-box.md)göstermek için **Spy** menüsünde **günlük iletileri** ' ni seçin.

 Genellikle, önce **Ileti grupları**' nı seçin ve ardından **görüntülenecek iletileri** tek tek seçerek seçimi hassas şekilde ayarlayabilirsiniz. All **düğmesi tüm** ileti türlerini seçer ve **hiçbiri** düğmesi tüm türleri temizler.

 **İletiler** sekmesinde aşağıdaki ayarlar kullanılabilir:

 **Görüntülenecek iletiler** Görüntülenecek belirli iletileri seçin. Yeni bir Iletiler penceresi oluşturduğunuzda, tüm iletiler görüntülenebilir. İletileri **iletiler** sekmesinden filtreleyerek, bu filtre yalnızca yeni iletiler için geçerlidir, Windows görünümünde zaten görüntülenmiş iletiler değildir.

 **Ileti grupları** Görüntülenecek ileti gruplarını seçin. Kullanılabilir gruplar şunlardır:

- WM_USER: WM_USER büyük veya eşit bir kodla

- Kaydedildi: **RegisterWindowMessage** çağrısıyla kaydedilir

- Bilinmiyor: 0 ile arasında bilinmeyen iletiler (WM_USER-1)

  Bu **Ileti gruplarının** , **görüntülenecek iletiler** altındaki belirli girdilerle eşlemediğine unutmayın. Bir grup seçtiğinizde, seçim doğrudan ileti akışına uygulanır.

  **Ileti grupları** içindeki gri onay kutusu, görüntülenecek **iletiler** liste kutusunda o gruptaki iletiler için değiştirildiğini belirtir; Bu gruptaki ileti türlerinin hepsi seçili değil.

  **Ayarları varsayılan olarak kaydet** Geçerli ayarları daha sonra ileti arama seçenekleri olarak kullanmak üzere kaydedin. Bu ayarlar, Spy + + ' dan çıkıldığında da kaydedilir.
