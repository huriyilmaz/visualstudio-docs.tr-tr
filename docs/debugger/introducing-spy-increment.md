---
title: Spy + + tanıtımı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d04b2e9e04e1f2b952baadbdf0cca32cc3b301b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731815"
---
# <a name="introducing-spy"></a>Spy++'a Giriş
Spy + + aşağıdaki görevleri gerçekleştirmenize olanak tanır:

- Sistem nesneleri arasındaki ilişkilerin grafik ağacını görüntüler. Bunlar, [süreçler](../debugger/processes-view.md), [iş parçacıkları](../debugger/threads-view.md)ve [pencereleri](../debugger/windows-view.md)içerir.

- Belirtilen [Windows](../debugger/how-to-search-for-a-window-in-windows-view.md), [iş parçacıkları](../debugger/how-to-search-for-a-thread-in-threads-view.md), [süreçler](../debugger/how-to-search-for-a-process-in-processes-view.md)veya [iletiler](../debugger/how-to-search-for-a-message-in-messages-view.md)için arama yapın.

- Seçili [pencerelerin](../debugger/how-to-display-window-properties.md), [iş parçacıklarının](../debugger/how-to-display-thread-properties.md), [işlemlerin](../debugger/how-to-display-process-properties.md)veya [iletilerin](../debugger/how-to-display-message-properties.md)özelliklerini görüntüleyin.

- Doğrudan görünümde bir pencere, iş parçacığı, işlem veya ileti seçin.

- Fare işaretçisi konumlandırmayı seçerek bir pencere seçmek için [Bulucu aracını](../debugger/how-to-use-the-finder-tool.md) kullanın.

- Karmaşık ileti günlüğü seçim parametrelerini kullanarak [ileti seçeneğini](../debugger/how-to-open-messages-view-from-find-window.md) ayarlayın.

  Spy + + ' da daha hızlı çalışmanıza yardımcı olacak bir araç çubuğu ve köprüler vardır. Ayrıca, etkin görünümü güncelleştirmek için bir **yenileme** komutu, bir **pencere Bulucu aracı** ve görünüm pencerelerini özelleştirmek için bir **yazı tipi** iletişim kutusu sağlar. Ayrıca, Spy + + Kullanıcı tercihlerini kaydetmenizi ve geri yüklemenize imkan tanır.

  Çeşitli Spy + + Windows 'da, sık kullanılan komutların kısayol menüsünü göstermek için sağ tıklayabilirsiniz. Hangi komutların görüntüleneceği, işaretçinin bulunduğu yere bağlıdır. Örneğin, pencere görünümünde bir girdiye sağ tıklarsanız ve seçilen pencere görünür durumdaysa, kısayol menüsünde **Vurgula** ' ya tıklamak, Seçili pencerenin kenarlığının daha kolay konumlandırılabilir olması için Flash olarak yanıp sönebilmesini sağlar.

> [!NOTE]
> Spy + +: PView gibi, süreçler ve iş parçacıklarının ayrıntılarını gösteren ve DDESPY.EXE dinamik veri değişimi (DDE) iletilerini izlemenize olanak tanıyan iki diğer yardımcı program vardır.

## <a name="64-bit-operating-systems"></a>64 bit Işletim sistemleri
 Spy + + uygulamasının iki sürümü vardır. Spy + + (spyxx.exe) adlı ilk sürüm, 32 bitlik bir işlemde çalışan bir pencereye gönderilen iletileri görüntüleyecek şekilde tasarlanmıştır. Örneğin, Visual Studio 32 bitlik bir işlemde çalışır. Bu nedenle, **Çözüm Gezgini**gönderilen iletileri göstermek için Spy + + kullanabilirsiniz. Visual Studio 'da çoğu derleme için varsayılan yapılandırma, 32 bitlik bir işlemde çalıştırmak olduğundan, Spy + + ' un bu ilk sürümü, [gerekli bileşenler yüklenmişse](../debugger/how-to-start-spy-increment.md)Visual Studio 'daki **Araçlar** menüsünde kullanılabilir olan bir sürümdür.

 Spy + + (64-bit) (spyxx_amd64.exe) adlı ikinci sürüm, 64 bit işlemde çalışan bir pencereye gönderilen iletileri görüntüleyecek şekilde tasarlanmıştır. Örneğin, 64 bitlik bir işletim sisteminde Not defteri, 64 bit süreçte çalışır. Bu nedenle, Notepad 'e gönderilen iletileri göstermek için Spy + + (64-bit) kullanabilirsiniz. Spy + + (64-bit) genellikle içinde bulunur

 ..\\ *Visual Studio yükleme klasörü*\Common7\Tools\spyxx_amd64.exe.

 Doğrudan komut satırından Spy + + ' ın her iki sürümünü de çalıştırabilirsiniz.

> [!NOTE]
> Spy + + (64-bit) dosya adı "AMD" içerse de, tüm x64 Windows işletim sistemlerinde çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Spy++ Hizmetini Başlatma](../debugger/how-to-start-spy-increment.md)
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)