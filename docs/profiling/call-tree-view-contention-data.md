---
title: Çağrı Ağacı Görünümü - İçerik Veri | Microsoft Docs
description: Profili profili yapılan uygulamada çapraz geçiş yapılan işlev yürütme yollarında ilgili verileri gösteren Çağrı Ağacı görünümünü gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 28cd7b22e64afbfb4c7c4100bd44c28e6dec6bb6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625437"
---
# <a name="call-tree-view---contention-data"></a>Çağrı Ağacı görünümü - karşıtlık verileri
Çağrı Ağacı görünümü, profili yapılan uygulamada çapraz geçiş yapılan işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamaya veya bileşene giriş noktasıdır. Her işlev düğümü, çağırmış olduğu tüm işlevleri, işlevin engellenmiş olduğu zamanı ve diğer iş parçacıkları veya işlemlerle bir kaynak için yarışıyor olduğu için işlevin engellenmiş olduğu zamanı listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacında üst işlev tarafından çağrılmış işlev örneklerine göredir. Yüzde değerleri, işlev örneği değeri profil oluşturma çalıştırması içinde yer alan toplam karşılaştırma sayısıyla karşılaştırarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütmeye açık yolu vurgulama
 Çağrı Ağacı görünümü, en fazla tartışmayı oluşturan işlem veya işlevin yürütme yolunu genişletecek ve vurgular.

- En etkin yolu görüntülemek için işleme veya işleve sağ tıklayın ve ardından Etkin Yolu **Genişlet'e tıklayın.**

## <a name="set-the-call-tree-root-node"></a>Çağrı Ağacı kök düğümünü ayarlama
 Profil oluşturma çalıştırması içinde her işlem bir kök düğüm olarak görünür. Çağrı Ağacı görünümünün başlangıç düğümünü ayarlamak için başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayın ve ardından Kök **Ayarla'ya tıklayın.**

 Kök düğümü ayarda, seçtiğiniz düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırmış oluruz. Kök düğümü özgün düğüme geri sıfırlamak için Çağrı Ağacı görünümünde sağ tıklayın ve ardından Kökünü Sıfırla'ya **tıklayın.**

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bu işlev örneklerinin bu yürütme yolundaki yürütülmesinin profil oluşturma çalıştırması sırasında engellenmiş olduğu zaman. Zaman, işlev tarafından çağrılmış alt işlevlerin engellenen zamanı içermez.|
|**Özel Engellenen Saat %**|Profil oluşturma çalıştırması içinde bu işlev için özel olarak engellenen sürenin bu yürütme yolundaki tüm engellenen sürenin yüzdesi.|
|**Özel İçerikler**|Bu yürütme yolunda bu işlevin örneklerde meydana gelen içerik sayısı. Sayı, işlev tarafından çağrılan alt işlevlerin içeriklerini içermez.|
|**Özel İçerik %**|Profil oluşturma çalıştırması içindeki tüm irdelemelerin yüzdesi, çağrı ağacında üst işlev tarafından çağrılmış bu işlevin örneklerinin özel itirazlarıdır.|
|**İşlev Adresi**|İşlevin adresi.|
|**İşlev Adı**|İşlevin tam adı.|
|**Kapsayıcı Engellenen Süre**|Bu yürütme yolundaki bu işlevin örneklerinin profil oluşturma çalıştırması içinde yürütülmesinin engellenmiş olduğu toplam süre. Zaman, işlev tarafından çağrılmış alt işlevlerin engellenen saati içerir.|
|**Kapsayıcı Engellenen Saat %**|Profil oluşturma çalıştırması sırasında bu işlevin bu yürütme yolundaki örnekleri için engellenen tüm zamanların yüzdesi.|
|**Kapsayıcı İçerikler**|Bu yürütme yolunda bu işlevin örneklerini engellenmiş olan toplam içerik sayısı. Sayı, işlev tarafından çağrılan alt işlevlerin içeriklerini içerir.|
|**Kapsayıcı İçerik %**|Profil oluşturma çalıştırması içinde yer alan ve bu işlevin bu yürütme yolundaki örneklerinin kapsayıcı itirazları olan tüm itirazların yüzdesi.|
|**Düzey**|Çağrı ağacında işlevin düzeyi. Yalnızca VSReport komut satırı raporlarında. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view.md)
- [Çağrı Ağacı görünümü - ölçüm](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı Ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
