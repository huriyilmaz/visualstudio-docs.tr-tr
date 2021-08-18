---
title: Çağrı Ağacı Görünümü - .NET Bellek Örnekleme Verileri | Microsoft Docs
description: Çağrı Ağacı görünümünün profili profili yapılan uygulamada çapraz geçiş yapılan işlev yürütme yolları için .NET bellek örnekleme verilerini nasıl görüntüley olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9b2473a38961a6ff94a25d08867541b4dd2a8baf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093339"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Çağrı Ağacı görünümü - .NET bellek örnekleme verileri
Çağrı Ağacı görünümü, profili yapılan uygulamada çapraz geçiş yapılan işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamaya veya bileşene giriş noktasıdır. Her işlev düğümü, çağıran tüm işlevleri ve bu işlev çağrılarına ilişkin .NET bellek ayırma verilerini listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacında üst işlev tarafından çağrılmış işlev örneklerine göredir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırması içinde toplam ayırma sayısı veya boyutuyla karşılaştırarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütmeye açık yolu vurgulama
 Çağrı Ağacı görünümü, en büyük veya en büyük bellek nesnelerini oluşturan işlem veya işlevin yürütme yolunu genişletecek ve vurgular. En etkin yolu görüntülemek için işleme veya işleve sağ tıklayın ve ardından Etkin Yolu **Genişlet'e tıklayın.**

## <a name="set-the-call-tree-root-node"></a>Çağrı Ağacı kök düğümünü ayarlama
 Profil oluşturma çalıştırması içinde her işlem bir kök düğüm olarak görüntülenir. Çağrı Ağacı görünümünün başlangıç düğümünü farklı bir düğüme ayarlamak için başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayın ve Kök **Ayarla'yı seçin.**

 Kök düğümü ayarda, seçili düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırmış oluruz. Kök düğümü, görüntülemekte olduğu düğüme geri sıfırlayabilirsiniz; Çağrı Ağacı Görünümü penceresine sağ tıklayın ve Kökünü **Sıfırla'yı seçin.**

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
|**Düzey**|Çağrı ağacında işlevin derinliği.|
|**Kapsayıcı Ayırmalar**|Bu işlevin örnekleri tarafından çağrı ağacında üst işlev tarafından çağrılmış nesnelerinin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve bu işlevin kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Ayırmalar**|Bu işlevin örnekleri tarafından çağrı ağacında üst işlev tarafından çağrılmış nesnelerinin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları dahil değildir.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve çağrı ağacında üst işlev tarafından çağrılmış işlev örneklerinin özel ayırmaları olan tüm nesnelerin yüzdesi.|
|**Kapsayıcı Bayt Sayısı**|Çağrı ağacında üst işlev tarafından çağrılmış bu işlevin örnekleri tarafından ayrılan bellekte bayt sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin kapsayıcı ayırmaları olan tüm bellek baytlarının yüzdesi.|
|**Özel Bayt Sayısı**|Çağrı ağacında üst işlev tarafından çağrılmış bu işlevin örnekleri tarafından ayrılan bellekte bayt sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları dahil değildir.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde ayrılan ve bu işlevin özel ayırmaları olan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çağrı Ağacı görünümü - ölçüm](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
