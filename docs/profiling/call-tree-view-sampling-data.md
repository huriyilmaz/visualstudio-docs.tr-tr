---
title: Çağrı Ağacı Görünümü - Örnekleme Veri | Microsoft Docs
description: Çağrı Ağacı görünümünün, Performans Gezgini'de profili profili yapılan uygulamada çapraz geçiş yapılan işlev yürütme yolları için örnekleme verilerini Performans Gezgini.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44aaa125b464b90a101693f7dd6357123e6f7afa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084772"
---
# <a name="call-tree-view---sampling-data"></a>Çağrı Ağacı görünümü - örnekleme verileri
Çağrı Ağacı görünümü, profili yapılan uygulamada çapraz geçiş yapılan işlev yürütme yollarını görüntüler.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

 Ağacın kökü, uygulamaya veya bileşene giriş noktasıdır. Her işlev düğümü, çağıran tüm işlevleri ve bu işlev çağrılarını performans verilerini listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacında üst işlev tarafından çağrılmış işlev örneklerine göredir. Yüzde değerleri, işlev örneği değeri profil oluşturma çalıştırmadaki toplam örnek sayısıyla karşılaştırarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütmeye açık yolu vurgulama
 Çağrı Ağacı görünümü, en sık örnek alınan işlem veya işlevin yürütme yolunu genişletecek ve vurgular. En etkin yolu görüntülemek için işleme veya işleve sağ tıklayın ve ardından Etkin Yolu **Genişlet'e tıklayın.**

## <a name="set-the-call-tree-root-node"></a>Çağrı ağacı kök düğümünü ayarlama
 Profil oluşturma çalıştırması içinde her işlem bir kök düğüm olarak görüntülenir. Çağrı Ağacı görünümünün başlangıç düğümünü ayarlamak için başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayın ve Kök **Ayarla'yı seçin.**

 Kök düğümü ayarda, seçili düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırmış oluruz. Kök düğümü özgün düğüme geri sıfırlamak için Çağrı Ağacı Görünümü penceresine sağ tıklayın ve Kökünü Sıfırla'yı **seçin.**

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**İşlev Adı**|İşlevin tam adı.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**İşlev Adresi**|İşlevin adresi.|
|**Düzey**|Bu işlevin çağrı ağacında derinliği. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Özel Örnekler**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işlevde toplanan örneklerin sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde toplanan örnekleri içermemektedir.|
|**Özel Örnekler %**|Profil oluşturma çalıştırması içindeki tüm örneklerin yüzdesi, çağrı ağacında üst işlev tarafından çağrıldıklarında bu işlevin özel örnekleridir.|
|**Kapsayıcı Örnekler**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işlevde toplanan örneklerin sayısı. Bu sayı, işlev tarafından çağrılan işlevlerde toplanan örnekleri içerir.|
|**Kapsayıcı Örnekler %**|Profil oluşturma çalıştırması içindeki tüm örneklerin yüzdesi, çağrı ağacında üst işlev tarafından çağrıldıklarında bu işlevin kapsayıcı örnekleridir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Çağrı Ağacı görünümü - profil oluşturma örnekleme verileri](../profiling/call-Tree-view-sampling-data.md)
- [Çağrı Ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Çağrı Ağacı görünümü - ölçüm](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
