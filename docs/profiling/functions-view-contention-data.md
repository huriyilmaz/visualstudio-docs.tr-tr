---
title: İşlevler Görünümü - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5874ffc7b4d304d1eaacd78032d657fe6ff31d94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780058"
---
# <a name="functions-view---contention-data"></a>İşlevler Görünümü - çekişme verileri
Çekişme verilerinin İşlevler rapor görünümü, profil oluşturma çalışması sırasında yürütülmesi engellenen profil oluşturma çalışmasındaki işlevleri listeler.

 Aşağıdaki tabloda eşzamanlılık yöntemi kullanılarak toplanan profil oluşturma veri dosyasının İşlevler görünümünde görüntülenen değerler açıklanır.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bu işlevin işlevin gövdesinde kod yürütmesinin engellendiği süre. İşlev tarafından çağrılan işlevlerde engellenen süre dahil edilmez.|
|**Özel Engellenen Süre %**|Profil oluşturma çalışmasındaki tüm engellenen sürenin yüzdesi, bu işlevin münhasır engellenen zamanıydı.|
|**Özel Çekişmeler**|Bu işlevin işlevin gövdesinde kod yürütmesi kaç kez engellendi. İşlev tarafından çağrılan işlevlerde çekişmeler dahil edilmez.|
|**Özel Çekişmeler %**|Profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi bu işlevin özel çekişmeleriydi.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Fonksiyon Adı**|İşlevin tam nitelikli adı.|
|**Kapsayıcı Engellenen Süre**|Bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütülmesi engellenen süre.|
|**Kapsayıcı Engellenen Süre %**|Profil oluşturma çalışmasındaki tüm engellenen sürenin yüzdesi, bu işlevin veya modülün engellenen süresini kapsayıcıdır.|
|**Kapsayıcı Çekişmeler**|Bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütülmesinin engellenme sayısı.|
|**Kapsayıcı Çekişmeler %**|Profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, bu işlevin veya modülün kapsayıcı çekişmeleriydi.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|İşlevin yürütüldettiği işlemin işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view.md)
- [Fonksiyonlar Görünümü - enstrümantasyon](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Fonksiyonlar Görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-instrumentation-data.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-sampling-data.md)
