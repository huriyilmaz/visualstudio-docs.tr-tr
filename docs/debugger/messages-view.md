---
title: İletiler görünümü | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b20ed28518c9156e82c6fe75ecceda74c66615d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62845864"
---
# <a name="messages-view"></a>İletiler Görünümü
Her pencerede ilişkili bir ileti akışı vardır. Bir Iletiler görünümü penceresi bu ileti akışını görüntüler. Pencere tanıtıcısı, ileti kodu ve ileti gösterilir. Bir iş parçacığı veya işlem için de bir Ileti görünümü oluşturabilirsiniz. Bu, belirli bir işlem veya iş parçacığı tarafından sahip olunan tüm pencereler için gönderilen iletileri görüntülemenize olanak sağlar. Bu, özellikle pencere başlatma iletilerini yakalamaya yarar.

 Aşağıdaki tipik bir Iletiler görünümü penceresi görüntülenir. İlk sütunun pencere tanıtıcısını içerdiğini ve ikinci sütunun bir ileti kodu ( [Ileti kodlarında](../debugger/message-codes.md)açıklanmıştır) içerdiğini unutmayın. Kodu çözülen ileti parametreleri ve dönüş değerleri doğru.

 ![Spy&#43;&#43; Iletileri görünümü](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView") Spy + + Iletiler görünümü

## <a name="procedures"></a>Yordamlar

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Bir pencere, işlem veya iş parçacığı için bir Ileti görünümü açmak için

1. Odağı bir [Windows görünümü](../debugger/windows-view.md), [süreçler görünümü](../debugger/processes-view.md)veya [iş parçacığı görünümü](../debugger/threads-view.md) penceresine taşıyın.

2. İletilerini incelemek istediğiniz öğenin düğümünü bulun ve seçin.

3. **Spy** menüsünde **günlük iletileri**' ni seçin.

     [Ileti seçenekleri Iletişim kutusu](../debugger/message-options-dialog-box.md) açılır.

4. Göstermek istediğiniz ileti için seçenekleri belirleyin.

5. İletileri kaydetmeye başlamak için **Tamam** 'a basın.

     Bir Iletiler görünümü penceresi açılır ve Spy + + araç çubuğuna bir **iletiler** menüsü eklenir. Seçilen seçeneklere bağlı olarak, iletiler etkin Iletiler görünümü penceresinde akışa başlar.

6. Yeterli iletiniz olduğunda **iletiler** menüsünden **günlüğü durdur** ' u seçin.

## <a name="in-this-section"></a>Bu Bölümde
 [Iletileri denetleme görünümü](../debugger/how-to-control-messages-view.md) Ileti görünümünün nasıl yönetileceğini açıklar.

 [Bul penceresinden Iletiler görünümünü açma](../debugger/how-to-open-messages-view-from-find-window.md) Pencereyi bul iletişim kutusundan Iletiler görünümünü açmayı açıklar.

 [Iletiler görünümünde Ileti arama](../debugger/how-to-search-for-a-message-in-messages-view.md) Iletiler görünümünde belirli bir iletinin nasıl bulunacağını açıklar.

 [Ileti günlüğü görüntüsünü başlatma ve durdurma](../debugger/how-to-start-and-stop-the-message-log-display.md) İleti günlüğe kaydetmenin nasıl başlatılacağını ve durdurulacağını açıklar.

 [Ileti kodları](../debugger/message-codes.md) Iletiler görünümünde listelenen iletiler için kodları tanımlar.

 [Ileti özelliklerini görüntüleme](../debugger/how-to-display-message-properties.md) İleti hakkında daha fazla bilgi gösterme.

## <a name="related-sections"></a>İlgili Bölümler
 [Spy + + görünümleri](../debugger/spy-increment-views.md) Windows, ileti, işlem ve iş parçacıklarının Spy + + ağaç görünümlerini açıklar.

 [Spy + + kullanma](../debugger/using-spy-increment.md) Spy + + aracını tanıtır ve nasıl kullanılabileceğini açıklar.

 [Ileti seçenekleri Iletişim kutusu](../debugger/message-options-dialog-box.md) Etkin Iletiler görünümünde hangi iletilerin listelendiğini seçmek için kullanılır.

 [Ileti arama Iletişim kutusu](../debugger/message-search-dialog-box.md) Iletiler görünümünde belirli bir iletinin düğümünü bulmak için kullanılır.

 [Ileti özellikleri Iletişim kutusu](../debugger/message-properties-dialog-box.md) Ileti görünümünde seçilen bir iletinin özelliklerini görüntülemek için kullanılır.

 [Spy + + başvurusu](../debugger/spy-increment-reference.md) Her bir Spy + + menü ve iletişim kutusunu açıklayan bölümler içerir.