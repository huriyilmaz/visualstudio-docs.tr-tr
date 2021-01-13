---
title: Spy + + araç çubuğu | Microsoft Docs
description: Menü çubuğunun altında görüntülenen Spy + + araç çubuğunda Kullanıcı arabirimi öğelerini anlayın. Araç çubuğunu görüntülemek veya gizlemek için, Görünüm menüsünde Araç Çubuğu ' na tıklayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dc2564a69c291055d53e358c084e7dd9c4d0506
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148201"
---
# <a name="spy-toolbar"></a>Spy++ Araç Çubuğu
Araç çubuğu Spy + + ' daki menü çubuğunun altında görüntülenir. Araç çubuğunu görüntülemek veya gizlemek için, **Görünüm** menüsünde **araç çubuğu**' na tıklayın.

 Araç çubuğunda aşağıdaki denetimler bulunur.

## <a name="uielement-list"></a>UIElement Listesi

|Düğme|Etki|
|------------|------------|
|![Spy&#43;&#43; Windows düğmesi](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Sistemdeki pencerelerin ve denetimlerin ağaç görünümünü görüntüler. Daha fazla bilgi için bkz. [Windows görünümü](../debugger/windows-view.md).|
|![Spy&#43;&#43; süreçler düğmesi](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Sistemdeki işlemlerin ağaç görünümünü görüntüler. Daha fazla bilgi için bkz. [süreçler görünümü](../debugger/processes-view.md).|
|![Spy&#43;&#43; Iş parçacıkları düğmesi](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Sistemdeki iş parçacıklarının ağaç görünümünü görüntüler. Daha fazla bilgi için bkz. [Iş parçacıkları görünümü](../debugger/threads-view.md).|
|![Spy&#43;&#43; Iletileri düğmesi](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Pencere iletilerini görüntülemek için bir pencere oluşturur ve **Ileti seçenekleri** iletişim kutusunu açar, böylece iletileri görüntülenecek pencereyi seçebilir ve diğer seçenekleri de belirleyebilirsiniz. Daha fazla bilgi için bkz. [Iletiler görünümü](../debugger/messages-view.md).|
|![Spy&#43;&#43; başlangıç günlüğü düğmesi](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|İleti günlüğünü başlatır ve ileti akışını görüntüler. Bu denetim yalnızca bir **iletiler** penceresi etkin pencere olduğunda kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: Ileti günlüğü görüntülemeyi başlatma ve durdurma](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43; günlüğü durdur düğmesi](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|İleti günlüğünü ve ileti akışının görüntülenmesini engeller. Bu denetim yalnızca bir **iletiler** penceresi etkin pencere olduğunda kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: Ileti günlüğü görüntülemeyi başlatma ve durdurma](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43; günlük seçenekleri düğmesi](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|[Ileti seçenekleri](../debugger/message-options-dialog-box.md) iletişim kutusunu görüntüler. Görüntülenecek Windows ve ileti türlerini seçmek için bu iletişim kutusunu kullanın. Bu denetim yalnızca bir **iletiler** penceresi etkin pencere olduğunda kullanılabilir.|
|![Spy&#43;&#43; Günlüğü Temizle düğmesi](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|Etkin **iletiler** penceresinin içeriğini temizler. Bu denetim yalnızca bir **iletiler** penceresi etkin pencere olduğunda kullanılabilir.|
|![Spy&#43;&#43; pencere bul düğmesi](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Pencere arama ölçütlerini ayarlamanıza ve özellikleri ya da iletileri görüntülemenize olanak tanıyan [pencere bul](../debugger/find-window-dialog-box.md) iletişim kutusunu açar. Daha fazla bilgi için bkz. [nasıl yapılır: Bulucu aracını kullanma](../debugger/how-to-use-the-finder-tool.md).|
|![Spy&#43;&#43; Ilk pencereyi bul düğmesi](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Geçerli görünümde eşleşen bir pencere, işlem, iş parçacığı veya ileti arar.|
|![Spy&#43;&#43; sonraki pencereyi bul düğmesi](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Sonraki eşleşen pencere, süreç, iş parçacığı veya ileti için geçerli görünümü arar. Bu denetim (ve ilgili menü komutu) yalnızca benzersiz olmayan geçerli bir arama sonucu olduğunda kullanılabilir. Örneğin, pencere ağacında arama ölçütü olarak bir pencere tutamacı kullandığınızda, bu tutamaya sahip pencere ağacında yalnızca bir pencere olduğundan, benzersiz sonuçlar üretir; Bu örnekte, **Sonrakini Bul** kullanılamıyor.|
|![Spy&#43;&#43; önceki pencereyi bul düğmesi](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Önceki eşleşen pencere, süreç, iş parçacığı veya ileti için geçerli görünümü arar. Bu denetim (ve ilgili menü komutu) yalnızca benzersiz olmayan geçerli bir arama sonucu olduğunda kullanılabilir. Örneğin, pencere ağacında arama ölçütü olarak bir pencere tutamacı kullandığınızda, bu tutamaya sahip pencere ağacında yalnızca bir pencere olduğundan, benzersiz sonuçlar üretir; Bu örnekte, **Öncekini Bul** kullanılamıyor.|
|![Spy&#43;&#43; Özellik Gezgini düğmesi](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Windows görünümünde seçilen pencerenin özelliklerini görüntüler.|
|![Spy&#43;&#43; yenileme düğmesi](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Sistem görünümlerini yeniler.|

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)