---
title: Kanallar (İş Parçacığı Görünümü) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94ac6e9e85a2d7dd504b2d2bd83bd1bbdb265ea0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62776783"
---
# <a name="channels-threads-view"></a>Kanallar (iş parçacığı görünümü)
Eşzamanlılık Görselleştiricisi dört tür kanal gösterir: iş parçacığı kanalları, disk kanalları, işaretkanalları ve GPU kanalları.

## <a name="thread-channels"></a>İş parçacığı kanalları
 İş parçacığı kanalı, yalnızca bir iş parçacığı için iş parçacığı durumunu renk olarak gösterir. Kanal adını duraklattığınızda, verilen iş parçacığının başlangıç işlevi görüntülenir. Eşzamanlılık Görselleştiricisi çeşitli iş parçacığı türleri algılar. En yaygın türler aşağıdaki tabloda gösterilmiştir.

|||
|-|-|
|Ana iş parçacığı|Uygulamayı başlatan iş parçacığı.|
|İşçi iş parçacığı|Uygulama ana iş parçacığı tarafından oluşturulan bir iş parçacığı.|
|CLR İşçi İş Parçacığı|Ortak dil çalışma zamanı (CLR) tarafından oluşturulan bir alt iş parçacığı.|
|Hata Ayıklayıcı Yardımcısı|Visual Studio hata ayıklama tarafından oluşturulan bir işçi iş parçacığı.|
|ConcRT İplik|Microsoft Concurrency Runtime tarafından oluşturulan bir iş parçacığı.|
|GDI Konu|GDIPlus tarafından oluşturulan bir iş parçacığı.|
|OLE/RPC İş Parçacığı|RPC İşçi İş parçacığı olarak oluşturulan bir iş parçacığı.|
|RPC İş Parçacığı|RPC İş parçacığı olarak oluşturulan bir iş parçacığı.|
|Winsock Konu|Winsock Thread olarak oluşturulan bir iş parçacığı.|
|Konu Havuzu|CLR İş Parçacığı Havuzu tarafından oluşturulan bir iş parçacığı.|

## <a name="disk-channels"></a>Disk kanalları
 Disk kanalları bilgisayardaki fiziksel sürücülere karşılık gelir. Sistemdeki her fiziksel sürücü için Okuma ve Yazma işlemleri için ayrı kanallar bulunduğundan, her sürücünün iki kanalı vardır. Disk numaraları çekirdek aygıt adlarına karşılık gelir. Bir disk kanalı yalnızca diskte etkinlik varsa gösterilir.

## <a name="marker-channels"></a>İşaretleyici kanalları
 İşaretleyici kanalları, uygulama tarafından oluşturulan olaylara ve kullandığı kitaplıklara karşılık gelir. Örneğin, Görev Paralel Kitaplığı, Paralel Desenler Kitaplığı ve C++ AMP işaretçiolarak görüntülenen olaylar oluşturur. Her işaretçi kanalı, kanalın açıklamasının yanında görüntülenen bir iş parçacığı kimliğiyle ilişkilidir. Kimlik, olayı oluşturan iş parçacığı tanımlar. Kanalın açıklaması, olayları oluşturan Windows için Olay İzleme (ETW) sağlayıcısının adını içerir. Kanal [Eşzamanlı Görselleştirici SDK'daki](../profiling/concurrency-visualizer-sdk.md)olayları görüntülerse, dizi adı da görüntülenir.

## <a name="gpu-channels"></a>GPU kanalları
 GPU kanalları sistemde DirectX 11 etkinliği hakkında bilgi görüntüler.  Grafik kartıyla ilişkili her DirectX motorunun ayrı bir kanalı vardır.  Tek tek segmentler, Bir DMA paketini işlemek için harcanan zamanı temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)