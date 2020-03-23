---
title: Çağrı Ağacı Görünümü - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e91e231f72b006d2020c8b4d5d96c7e24fa1dd9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779785"
---
# <a name="call-tree-view---contention-data"></a>Çağrı Ağacı görünümü - çekişme verileri
Çağrı Ağacı görünümü, profilli uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamaya veya bileşene giriş noktasıdır. Her işlev düğümü, aradığı tüm işlevleri, işlevin engellenme sayısını ve diğer iş parçacıkları veya işlemlerle bir kaynak için uğraşmak tanındığı için işlevin engellenme süresini listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örnekleri içindir. Yüzde değerleri, işlev örneği değeri profil oluşturma çalışmasındaki toplam çekişme sayısıyla karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme sıcak yolunu vurgulayın
 Çağrı Ağacı görünümü genişletebilir ve en çok çekişmeoluşturan işlemin veya işlevin yürütme yolunu niçin önplana atabilir.

- En etkin yolu görüntülemek için, işlemi veya işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın.

## <a name="set-the-call-tree-root-node"></a>Çağrı Ağacı kök düğümünü ayarlama
 Profil oluşturma çalışmasındaki her işlem kök düğümü olarak görünür. Çağrı Ağacı görünümünün başlangıç düğümünü ayarlamak için, başlangıç düğümü olarak ayarlamak istediğiniz düğümü sağ tıklatın ve ardından **Root'u ayarla'yı**tıklatın.

 Kök düğümünü ayarladığınızda, seçtiğiniz düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırırsınız. Kök düğümünü özgün düğüme geri sıfırlamak için Çağrı Ağacı görünümünde sağ tıklatın ve ardından **Root'u Sıfırla'yı**tıklatın.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bu yürütme yolundaki bu işlev örneklerinin profil oluşturma çalışmasında yürütülmesi engellendi. Zaman, işlev tarafından çağrılan alt işlevlerin engellenen zamanını içermez.|
|**Özel Engellenen Süre %**|Bu yürütme yolundaki bu işlev için özel olarak engellenen süre olan profil oluşturma çalışmasındaki tüm engellenen zamanın yüzdesi.|
|**Özel Çekişmeler**|Bu yürütme yolunda bu işlevin örneklerinde oluşan çekişmelerin sayısı. Sayı, işlev tarafından çağrılan alt işlevlerin çekişmelerini içermez.|
|**Özel Çekişmeler %**|Profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, çağrı ağacındaki üst işlev tarafından çağrılan bu işlevörneklerinin özel çekişmeleriydi.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Fonksiyon Adı**|İşlevin tam nitelikli adı.|
|**Kapsayıcı Engellenen Süre**|Bu yürütme yolundaki bu işlevin örneklerinin profil oluşturma çalışmasında yürütülmesi engellendi toplam zamanı. Zaman, işlev tarafından çağrılan alt işlevlerin engellenen zamanını içerir.|
|**Kapsayıcı Engellenen Süre %**|Bu yürütme yolundaki bu işlevörnekleri için kapsayıcı engellenen süre olan profil oluşturma çalışmasındaki tüm engellenen zamanın yüzdesi.|
|**Kapsayıcı Çekişmeler**|Bu yürütme yolunda bu işlevin örneklerini engelleyen çekişmelerin toplam sayısı. Sayı, işlev tarafından çağrılan alt işlevlerin çekişmelerini içerir.|
|**Kapsayıcı Çekişmeler %**|Profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, bu yürütme yolundaki bu işlevin örneklerinin kapsayıcı çekişmeleriydi.|
|**Düzey**|Çağrı ağacındaki işlev düzeyi. Yalnızca VSReport komut satırı raporlarında. Daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view.md)
- [Çağrı Ağacı görünümü - enstrümantasyon](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı Ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
