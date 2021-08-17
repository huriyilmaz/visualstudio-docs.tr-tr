---
title: İletiler Görünümü | Microsoft Docs
description: Her pencere, iş parçacığı ve işlem, bir İleti Görünümü penceresinde görüntülen ilişkilendirilmiş bir ileti akışına sahiptir. İletiler Görünümünü açmayı ve denetlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 858620450452080dbbdf6c9aa5da8ed7c44c13e2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065416"
---
# <a name="messages-view"></a>İletiler Görünümü
Her pencerede ilişkili bir ileti akışı vardır. İletiler görünüm penceresi bu ileti akışını görüntüler. Pencere tanıtıcısı, ileti kodu ve ileti gösterilir. Bir iş parçacığı veya işlem için de İletiler görünümü oluşturabilirsiniz. Bu, özellikle pencere başlatma iletilerini yakalamak için yararlı olan belirli bir işlem veya iş parçacığına ait tüm pencerelere gönderilen iletileri görüntülemeye olanak sağlar.

 Aşağıda tipik bir İletiler görünümü penceresi görüntülenir. İlk sütunda pencere tanıtıcısı, ikinci sütunda ise bir ileti kodu (İleti Kodları'da açıklanmıştır) [yer alır.](../debugger/message-codes.md) Kodu çözülen ileti parametreleri ve dönüş değerleri sağdadır.

 ![Spy&#43;&#43; İletileri Görünümü](../debugger/media/spy--_messagesview.png "Spy++_MessagesView") Spy++ İletileri Görünümü

## <a name="procedures"></a>Yordamlar

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Bir pencere, işlem veya iş parçacığı için İletiler görünümünü açmak için

1. Odağı Görünüm, [İşlemler Windows](../debugger/windows-view.md)veya İş [Parçacıkları Görünümü penceresine](../debugger/processes-view.md) [taşıma.](../debugger/threads-view.md)

2. İletilerini incelemek istediğiniz öğenin düğümünü bulun ve seçin.

3. Spy **menüsünden Günlük** İletileri'ne **tıklayın.**

     İleti [Seçenekleri İletişim Kutusu](../debugger/message-options-dialog-box.md) açılır.

4. Görüntülemek istediğiniz ileti için seçenekleri belirleyin.

5. İletileri **günlüğe kaydetmeye** başlamak için Tamam'a basın.

     İletiler görünümü penceresi açılır ve Spy++ **araç** çubuğuna bir İletiler menüsü eklenir. Seçilen seçeneklere bağlı olarak, iletiler etkin İletiler görünüm penceresine akışa başlar.

6. Yeterli iletiye sahipken İletiler **menüsünden Günlüğü** Durdur'a tıklayın. 

## <a name="in-this-section"></a>Bu Bölümde
 [İletiler Görünümünü Denetleme](../debugger/how-to-control-messages-view.md) İletiler görünümünü yönetmeyi açıklar.

 [Bul Penceresinden İletiler Görünümünü Açma](../debugger/how-to-open-messages-view-from-find-window.md) Pencere Bul iletişim kutusunda İletiler görünümünün nasıl aç açıklar.

 [İletiler Görünümünde İleti Arama](../debugger/how-to-search-for-a-message-in-messages-view.md) İletiler görünümünde belirli bir iletinin nasıl bulun olduğunu açıklar.

 [İleti Günlüğü Görüntülemeyi Başlatma ve Durdurma](../debugger/how-to-start-and-stop-the-message-log-display.md) İleti günlüğünü başlatmayı ve durdurmayı açıklar.

 [İleti Kodları](../debugger/message-codes.md) İletiler görünümünde listelenen iletilerin kodlarını tanımlar.

 [İleti Özelliklerini Görüntüleme](../debugger/how-to-display-message-properties.md) İleti hakkında daha fazla bilgi gösterme.

## <a name="related-sections"></a>İlgili Bölümler
 [Spy++ Görünümleri](../debugger/spy-increment-views.md) Pencerelerin, iletilerin, işlemlerin ve iş parçacıklarının Spy++ ağaç görünümlerini açıklar.

 [Spy++ kullanma](../debugger/using-spy-increment.md) Spy++ aracını tanıtıyor ve nasıl kullanıLl olduğunu açıklar.

 [İleti Seçenekleri İletişim Kutusu](../debugger/message-options-dialog-box.md) Etkin İletiler görünümünde hangi iletilerin listelenmiş olduğunu seçmek için kullanılır.

 [İleti Arama İletişim Kutusu](../debugger/message-search-dialog-box.md) İletiler görünümünde belirli bir iletinin düğümünü bulmak için kullanılır.

 [İleti Özellikleri İletişim Kutusu](../debugger/message-properties-dialog-box.md) İleti görünümünde seçilen iletinin özelliklerini görüntülemek için kullanılır.

 [Spy++ Başvurusu](../debugger/spy-increment-reference.md) Her Spy++ menüsünü ve iletişim kutusunu açıklayan bölümler içerir.