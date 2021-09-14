---
title: Spy++ Araç Çubuğu | Microsoft Docs
description: Menü çubuğunun altında görünen Spy++ araç çubuğundaki kullanıcı arabirimi öğelerini anlayabilirsiniz. Araç çubuğunu görüntülemek veya gizlemek için Görünüm menüsünde Araç Çubuğu'nu tıklatın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 97c03fe68b810cbd7e907b4020b8487ae5c547f2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636585"
---
# <a name="spy-toolbar"></a>Spy++ Araç Çubuğu
Araç çubuğu Spy++ menü çubuğunun altında görünür. Araç çubuğunu görüntülemek veya gizlemek için Görünüm menüsünde **Araç Çubuğu'nu** **tıklatın.**

 Araç çubuğunda aşağıdaki denetimler kullanılabilir.

## <a name="uielement-list"></a>UIElement Listesi

|Düğme|Etki|
|------------|------------|
|![Spy&#43;&#43; Windows Düğmesi](../debugger/media/icon_spy--_windows.gif "Icon_Spy++_Windows")|Sistemde pencerelerin ve denetimlerin ağaç görünümünü görüntüler. Daha fazla bilgi için [bkz. Windows.](../debugger/windows-view.md)|
|![Spy&#43;&#43; İşlemleri Düğmesi](../debugger/media/icon_spy--_processes.gif "Icon_Spy++_Processes")|Sistemde işlemlerin ağaç görünümünü görüntüler. Daha fazla bilgi için bkz. [İşlemler Görünümü.](../debugger/processes-view.md)|
|![Spy&#43;&#43; İş Parçacıkları Düğmesi](../debugger/media/icon_spy--_threads.gif "Icon_Spy++_Threads")|Sistemde iş parçacıklarının ağaç görünümünü görüntüler. Daha fazla bilgi için bkz. [İş Parçacıkları Görünümü.](../debugger/threads-view.md)|
|![Spy&#43;&#43; İletileri Düğmesi](../debugger/media/icon_spy--_messages.gif "Icon_Spy++_Messages")|Pencere iletilerini görüntülemek için bir  pencere oluşturur ve iletileri görüntülenecek olan pencereyi seçerek diğer seçenekleri de seçerek İleti Seçenekleri iletişim kutusunu açar. Daha fazla bilgi için bkz. [İletiler Görünümü.](../debugger/messages-view.md)|
|![Spy&#43;&#43; Günlüğü Başlat Düğmesi](../debugger/media/icon_spy--_startlog.gif "Icon_Spy++_StartLog")|İleti günlüğünü başlatır ve ileti akışını görüntüler. Bu denetim yalnızca bir İletiler **penceresi** etkin pencere olduğunda kullanılabilir. Daha fazla bilgi için, [bkz. How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43; Günlüğü Durdur Düğmesi](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy++_StopLog")|İleti günlüğünü ve ileti akışının iletiyi görüntülemeyi durdurur. Bu denetim yalnızca bir İletiler **penceresi** etkin pencere olduğunda kullanılabilir. Daha fazla bilgi için, [bkz. How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43; Günlük Seçenekleri Düğmesi](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy++_LogOptions")|İleti Seçenekleri [iletişim](../debugger/message-options-dialog-box.md) kutusunu görüntüler. Görüntülemek üzere windows ve ileti türlerini seçmek için bu iletişim kutusunu kullanın. Bu denetim yalnızca bir İletiler **penceresi** etkin pencere olduğunda kullanılabilir.|
|![Spy&#43;&#43; Günlüğü Temizle Düğmesi](../debugger/media/spy--_clearlog.gif "Spy++_ClearLog")|Etkin İletiler penceresinin içeriğini **temizler.** Bu denetim yalnızca bir İletiler **penceresi** etkin pencere olduğunda kullanılabilir.|
|![Spy&#43;&#43; Pencere Bul Düğmesi](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy++_FindWindow")|Pencere arama [ölçütlerini](../debugger/find-window-dialog-box.md) ayarlamanızı ve özellikleri veya iletileri görüntülemenizi sağlayan Pencere Bul iletişim kutusunu açar. Daha fazla bilgi için, [bkz. How to: Use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|
|![Spy&#43;&#43; bul İlk Pencere Düğmesi](../debugger/media/icon_spy--_window.gif "Icon_Spy++_Window")|Geçerli görünümde eşleşen bir pencere, işlem, iş parçacığı veya ileti arar.|
|![Spy&#43;&#43; Sonraki PencereYi Bul Düğmesi](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy++_NextWindow")|Geçerli görünümde sonraki eşleşen pencereyi, işlemi, iş parçacığını veya iletiyi arar. Bu denetim (ve ilgili menü komutu), yalnızca benzersiz olmayan geçerli bir arama sonucu olduğunda kullanılabilir. Örneğin, pencere ağacında arama ölçütü olarak bir pencere tanıtıcısı kullanırsınız, pencere ağacında bu tanıtıcıya sahip yalnızca bir pencere olduğundan benzersiz sonuçlar üretir; Bu örnekte, **Sonrakini Bul** kullanılamaz.|
|![Spy&#43;&#43; Önceki Pencereyi Bul Düğmesi](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy++_PrevWindow")|Önceki eşleşen pencere, işlem, iş parçacığı veya ileti için geçerli görünümü arar. Bu denetim (ve ilgili menü komutu), yalnızca benzersiz olmayan geçerli bir arama sonucu olduğunda kullanılabilir. Örneğin, pencere ağacında arama ölçütü olarak bir pencere tanıtıcısı kullanırsınız, pencere ağacında bu tanıtıcıya sahip yalnızca bir pencere olduğundan benzersiz sonuçlar üretir; Bu örnekte **Öncekini Bul** kullanılamıyor.|
|![Spy&#43;&#43; Özellik Gezgini Düğmesi](../debugger/media/icon_spy--_propexp.gif "Icon_Spy++_PropExp")|Windows görünümünde seçilen pencerenin Windows görüntüler.|
|![Spy&#43;&#43; Yenile Düğmesi](../debugger/media/icon_spy--_refresh.gif "Icon_Spy++_Refresh")|Sistem görünümlerini yeniler.|

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)