---
title: Çağrı Ağacı Görünümü - .NET Bellek Araçları Veri | Microsoft Docs
description: Veri kaynağında .NET bellek ayırma ölçümleme verileri çağrı ağacı görünümü hakkında Performans Gezgini.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1c5c1bc3b54aa7f79d92660ee21bc10cc4f7bfea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076951"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Çağrı Ağacı görünümü - .NET bellek ölçüm verileri
Ölçüm aracı yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin Çağrı Ağacı görünümü, profili yapılan uygulamada çapraz geçiş yapılan işlev yürütme yollarını görüntüler. Ağacın kökü, uygulama veya bileşene giriş noktasıdır. Her işlev düğümü, çağıran tüm işlevleri ve işlevin .NET bellek ve zamanlama verilerini listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacında üst işlev tarafından çağrılmış işlev örneklerine göredir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırması içinde toplam ayırma sayısı veya boyutuyla karşılaştırarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütmeye açık yolu vurgulama
 Çağrı Ağacı görünümü, en büyük veya en büyük bellek nesnelerini oluşturan işlem veya işlevin yürütme yolunu genişletecek ve vurgular. En etkin yolu görüntülemek için işleme veya işleve sağ tıklayın ve ardından Etkin Yolu **Genişlet'e tıklayın.**

## <a name="set-the-call-tree-root-node"></a>Çağrı Ağacı kök düğümünü ayarlama
 Profil oluşturma çalıştırması içinde her işlem bir kök düğüm olarak görüntülenir. Başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayarak ve ardından Kök Ayarla'yi seçerek Çağrı Ağacı görünümünün başlangıç **düğümünü ayarlayın.**

 Kök düğümü ayarda, seçili düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırmış oluruz. Kök düğümü görüntülemekte olduğu düğüme geri sıfırlayabilirsiniz; Çağrı Ağacı Görünümü penceresine sağ tıklayın ve Kökünü **Sıfırla'yı seçin.**

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**İşlev Adı**|İşlevin adı.|
|**İşlev Adresi**|İşlevin adresi.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|İşleme atanan ad.|
|**Zaman Özel Yoklama Ek Yükü**|Bu işlevin, ölçümlemeden kaynaklanan zaman yükü. Yoklama ek yükü tüm dışlama zamanlarından çıkarıldı.|
|**Zaman Dahil Yoklama Ek Yükü**|Bu işlev ve alt işlevleri için, ölçümlemeden kaynaklanan zaman yükü. Yoklama ek yükü tüm kapsayıcı zamanlardan çıkarıldı.|
|**Tür**|İşlevin bağlamı:<br /><br /> -   **0** - geçerli işlev<br />-   **1** - geçerli işlevi çağıran bir işlev<br />-   **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök İşlev Adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin kapsayıcı .NET bellek değerleri, işlev ve işlev tarafından çağrılan işlevler tarafından oluşturulan nesnelerin sayısını (ayırmaları) ve boyutunu (bayt) belirtir.

 Özel bellek değerleri, işlev tarafından çağrılan işlevler tarafından değil, işlev gövdesinde kod tarafından oluşturulan nesnelerin sayısını ve boyutunu gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsayıcı Ayırmalar**|Bu işlevin örnekleri tarafından çağrı ağacında üst işlev tarafından çağrılmış nesnelerinin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve çağrı ağacında üst işlev tarafından çağrılmış işlev örneklerinin kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.|
|**Özel Ayırmalar**|Bu işlevin örnekleri tarafından çağrı ağacında üst işlev tarafından çağrılmış nesnelerinin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları dahil değildir.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve çağrı ağacında üst işlev tarafından çağrılmış işlev örneklerinin özel ayırmaları olan tüm nesnelerin yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsayıcı değerler
 Geçen kapsayıcı değerler, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, işlev tarafından çağrılan işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Kapsayıcı Süre**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan tüm çağrıların toplam kapsayıcı süresi.|
|**Geçen Kapsayıcı Saat %**|Çağrı ağacında üst işlev tarafından çağrıldığnda bu işlevin geçen toplam kapsayıcı süresinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Geçen Kapsayıcı Süre**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan çağrının ortalama kapsayıcı süresi.|
|**En Fazla Geçen Kapsayıcı Süre**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan bir çağrının en uzun geçen kapsayıcı süresi.|
|**En Az Geçen Kapsayıcı Süre**|Bu işleve yapılan çağrının, çağrı ağacında üst işlev tarafından çağrıldıklarında geçen en düşük kapsayıcı süresi.|

## <a name="elapsed-exclusive-values"></a>Geçen özel değerler
 Geçen özel değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütülmektedir zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda zaman içerir. Ancak zaman, işlev tarafından çağrılan işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen Özel Süre**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan tüm çağrıların toplam özel süresi.|
|**Geçen Özel Saat %**|Çağrı ağacında üst işlev tarafından çağrıldığnda bu işlevin geçen toplam özel süresinde harcanan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Geçen Özel Süre**|Bu işleve yapılan çağrının çağrı ağacında üst işlev tarafından çağrıldığ ortalama özel süresi.|
|**En Fazla Geçen Özel Süre**|Bu işleve yapılan bir çağrının, çağrı ağacında üst işlev tarafından çağrıldıklarında geçen en uzun özel süresi.|
|**En Az Geçen Özel Süre**|Bu işleve yapılan bir çağrının, çağrı ağacında üst işlev tarafından çağrıldıklarında geçen en düşük özel süresi.|

## <a name="application-inclusive-values"></a>Uygulama dahil değerleri
 Uygulama dahil değerleri, bir işlevin çağrı yığınında olduğu zamanı gösterir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dahil değildir. Bu süre, işlev tarafından çağrılan alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan tüm çağrıların toplam uygulama dahil süresi.|
|**Uygulama Dahil Saati %**|Çağrı ağacında üst işlev tarafından çağrıldıken bu işlevin toplam uygulama dahil süresi içinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan çağrının ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|Çağrı ağacında üst işlev tarafından çağrıldıken bu işleve yapılan çağrının dahil olduğu maksimum uygulama süresi.|
|**En Az Uygulama Dahil Süresi**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan çağrının en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, işlev tarafından çağrılan alt işlevlerde harcanan süre hariç olmak üzere işlevde harcanan zamanı gösterir. Zaman ayrıca bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan tüm çağrıların uygulamaya özel toplam süresi.|
|**Uygulamaya Özel Saat %**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işlevin toplam uygulama için özel zaman harcaması yapılan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|Bu işleve yapılan çağrının çağrı ağacında üst işlev tarafından çağrılmış olduğu ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|Bu işleve yapılan çağrının çağrı ağacında üst işlev tarafından çağrılmış olduğu en uzun uygulama özel süresi.|
|**En Az Uygulama Için Özel Süre**|Bu işleve yapılan çağrının çağrı ağacında üst işlev tarafından çağrılmış olduğu en düşük uygulama özel süresi.|
