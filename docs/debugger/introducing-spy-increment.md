---
title: Spy++ | Microsoft Docs
description: Spy++ hata ayıklama aracı hakkında bilgi edinebilirsiniz. Sistem nesnesi ilişkilerinin grafik ağacını görüntüleme. Seçili pencereler, iş parçacıkları, işlemler veya iletiler için özellikleri al.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6ab19d666bf02d1c9c9d764ed1c18d097a3f8935
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138919"
---
# <a name="introducing-spy"></a>Spy++'a Giriş
Spy++ aşağıdaki görevleri gerçekleştirmenizi sağlar:

- Sistem nesneleri arasındaki ilişkilerin grafik ağacını görüntüleme. Bunlar [işlemleri, iş](../debugger/processes-view.md) [parçacıklarını ve](../debugger/threads-view.md) [windows'u içerir.](../debugger/windows-view.md)

- Belirtilen pencereler, [iş parçacıkları,](../debugger/how-to-search-for-a-window-in-windows-view.md) [işlemler](../debugger/how-to-search-for-a-thread-in-threads-view.md) [veya](../debugger/how-to-search-for-a-process-in-processes-view.md)iletiler [için arama.](../debugger/how-to-search-for-a-message-in-messages-view.md)

- Seçilen pencerelerin, iş [](../debugger/how-to-display-thread-properties.md) [parçacıklarının,](../debugger/how-to-display-window-properties.md) [işlemlerin veya iletilerin](../debugger/how-to-display-process-properties.md)özelliklerini [görüntüleyin.](../debugger/how-to-display-message-properties.md)

- Doğrudan görünümde bir pencere, iş parçacığı, işlem veya ileti seçin.

- Fare [işaretçisi konumlandırma ile](../debugger/how-to-use-the-finder-tool.md) bir pencere seçmek için Bulıcı Aracı'nı kullanın.

- Karmaşık [ileti günlüğü](../debugger/how-to-open-messages-view-from-find-window.md) seçim parametrelerini kullanarak ileti seçeneğini ayarlayın.

  Spy++ daha hızlı çalışmanıza yardımcı olacak bir araç çubuğuna ve köprülere sahip. Ayrıca etkin görünümü güncelleştirmek **için Yenile** komutu, gözetlenmeyi kolaylaştırmak için Bir  **Pencere** Bulıcı Aracı ve görünüm pencerelerini özelleştirmek için Yazı Tipi iletişim kutusu sağlar. Ayrıca Spy++ kullanıcı tercihlerini kaydetmenizi ve geri yüklemenizi sağlar.

  Çeşitli Spy++ pencerelerinde, sık kullanılan komutların kısayol menüsünü görüntülemek için sağ tıklarsınız. Hangi komutların görüntüleniyor olduğu işaretçinin bulunduğu yere bağlıdır. Örneğin, Pencere görünümünde bir girişe sağ tıklarsanız ve seçili pencere  görünürse, kısayol menüsünde Vurgula'ya tıklarsanız, seçili pencerenin kenarlığı daha kolay bir şekilde yer alasınız.

> [!NOTE]
> Spy++'a benzeyen iki yardımcı program daha vardır: süreçler ve iş parçacıklarıyla ilgili ayrıntıları gösteren PView ve Dinamik Veri Exchange (DDE) iletilerini izlemenizi sağlayan DDESPY.EXE.

## <a name="64-bit-operating-systems"></a>64 Bit İşletim Sistemleri
 Spy++ iki sürümü vardır. Spy++ (spyxx.exe) adlı ilk sürüm, 32 bit işlemde çalışan bir pencereye gönderilen iletileri görüntülemek için tasarlanmıştır. Örneğin, Visual Studio 32 bit işlemde çalışır. Bu nedenle, spy++'a gönderilen iletileri görüntülemek için **Çözüm Gezgini.** Visual Studio'daki derlemelerin çoğu için varsayılan yapılandırma 32 bit işlemde çalıştırıla olduğundan, gerekli bileşenler yüklenirse Spy++'ın bu ilk sürümü Visual Studio'daki Araçlar menüsünde bulunan [sürümdür.](../debugger/how-to-start-spy-increment.md) 

 Spy++ (64 bit) (spyxx_amd64.exe) adlı ikinci sürüm, 64 bit işlemde çalışan bir pencereye gönderilen iletileri görüntülemek için tasarlanmıştır. Örneğin, 64 bit işletim sisteminde, Not Defteri 64 bit işlemde çalışır. Bu nedenle, spy++ (64 bit) kullanarak bir Not Defteri. Spy++ (64 bit) genellikle

 ..\\ *Visual Studio klasörü\Common7\Tools\spyxx_amd64.exe.*

 Spy++ 'ın herhangi bir sürümünü doğrudan komut satırı üzerinden çalıştırabilirsiniz.

> [!NOTE]
> Spy++ (64 bit) dosya adı "amd" içeriyor olsa da, tüm x64 Windows çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Spy++ Hizmetini Başlatma](../debugger/how-to-start-spy-increment.md)
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)