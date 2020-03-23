---
title: Çağrı Ağacı Görünümü - Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 558cef408ceca48a55563ae31f2399da0e951b8e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779759"
---
# <a name="call-tree-view---sampling-data"></a>Çağrı Ağacı görünümü - örnekleme verileri
Çağrı Ağacı görünümü, profilli uygulamada geçen işlev yürütme yollarını görüntüler.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

 Ağacın kökü, uygulamaya veya bileşene giriş noktasıdır. Her işlev düğümü, aradığı tüm işlevleri ve bu işlev çağrılarıyla ilgili performans verilerini listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örnekleri içindir. Yüzde değerleri, işlev örneği değeri profil oluşturma çalışmasındaki toplam örnek sayısıyla karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme sıcak yolunu vurgulayın
 Çağrı Ağacı görünümü genişletebilir ve en sık örneklendi işlemin veya işlevin yürütme yolunu vurgulayabilir. En etkin yolu görüntülemek için, işlemi veya işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın.

## <a name="set-the-call-tree-root-node"></a>Çağrı ağacı kök düğümünü ayarlama
 Profil oluşturma çalışmasındaki her işlem kök düğüm olarak görüntülenir. Çağrı Ağacı görünümünün başlangıç düğümünü ayarlamak için, başlangıç düğümü olarak ayarlamak istediğiniz düğümü sağ tıklatın ve **Root'u ayarla'yı**seçin.

 Kök düğümünü ayarladığınızda, seçili düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırırsınız. Kök düğümünü özgün düğüme geri sıfırlamak için, Çağrı Ağacı Görünümü penceresinde sağ tıklatın ve **Root'u Sıfırla'yı**seçin.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Fonksiyon Adı**|İşlevin tam nitelikli adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Düzey**|Arama ağacındaki bu işlevin derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Özel Örnekler**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işlevde toplanan örnek sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde toplanan örnekleri içermez.|
|**Özel Örnekler %**|Çağrı ağacındaki üst işlev tarafından çağrıldığında profil oluşturma çalışmasındaki tüm örneklerin yüzdesi bu işlevin özel örnekleriydi.|
|**Dahil Örnekler**|Çağrı ağacındaki üst işlev tarafından çağrıldığında bu işlevde toplanan örnek sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde toplanan örnekleri içerir.|
|**Kapsayıcı Örnekler %**|Çağrı ağacındaki üst işlev tarafından çağrıldığında profil oluşturma çalışmasındaki tüm örneklerin yüzdesi bu işlevin kapsayıcı örnekleriydi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı Ağacı görünümü - profilci örnekleme verileri](../profiling/call-Tree-view-sampling-data.md)
- [Çağrı Ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Çağrı Ağacı görünümü - enstrümantasyon](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
