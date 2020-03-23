---
title: Modüller Görünümü - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2de844867e9c0a8d95abdaa13f860a6487254bfe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780019"
---
# <a name="modules-view---contention-data"></a>Modüller Görünümü - çekişme verileri
Çekişme verilerinin Modülgörünümü, profil oluşturma verilerinde örneklenen modüller tarafından gruplanan eşzamanlılık verilerini görüntüler. Her modül hiyerarşik bir ağacın köküdür. Çekişme olaylarının meydana geldiği modülün işlevleri modül düğümü altında listelenir.

 Bir çekişme olayı oluştuğunda işlev kendi kodunu yürütüyorsa, yani işlev çağrı yığınının en üstündeydi, yürütülen kaynak satırları ve yönerge adresleri işlev düğümünün altında listelenir. Satır veya yönerge yürütüldüğünde bir kaynak satırı veya yönerge işaretçisi için veri toplandığından, kapsayıcı ve özel değerler hem satır verileri hem de yönerge verileri için her zaman aynıdır.

 Aşağıdaki tabloda, çekişme verilerinin Modüller görünümündeki sütunların değerleri açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|- Bir işlev için, bu işlevin işlevin gövdesinde kod yürütmesinin engellediği süre. İşlev tarafından çağrılan işlevlerde engellenen süre dahil edilmez.<br />- Bir modül için, modüldeki fonksiyonların münhasır bloke süresi toplamı.<br />- Bir satır veya talimat için, bu satırın veya talimatın yürütülmesinin engellediği süre.|
|**Özel Engellenen Süre %**|- Bir işlev veya modül için, profil oluşturma çalışmasındaki tüm engellenen sürenin yüzdesi, bu işlevin veya modülün münhasır engellenen zamanıdır.<br />- Bir satır veya yönerge için, bu satırın veya talimatın yürütülmesinin engellendiği profil oluşturma çalışmasındaki tüm engellenen sürenin yüzdesi.|
|**Özel Çekişmeler**|- Bir işlev için, bu işlevin işlevin gövdesinde kod yürütmesinin engellenme sayısı. İşlev tarafından çağrılan işlevlerde çekişmeler dahil edilmez.<br />- Bir modül için, modüldeki fonksiyonların münhasır çekişmelerinin toplamı.<br />- Bir satır veya talimat için, bu satır ın veya talimatın yürütülmesinin engellenme sayısı.|
|**Özel Çekişmeler %**|- Bir işlev veya modül için, profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi bu işlevin veya modülün özel çekişmeleridir.<br />- Bir satır veya talimat için, profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, bu satırı veya talimatın yürütülmesini engelleyen çekişmelerdir.|
|**Kapsayıcı Engellenen Süre**|- Bir işlev için, bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütülmesinin engellediği süre.<br />- Bir modül için, bu modülden en az bir fonksiyonun yığında olduğu engellenen sürenin toplamı.<br />- Bir satır veya talimat için, bu satırın veya talimatın yürütülmesinin engellediği süre.|
|**Kapsayıcı Engellenen Süre %**|- Bir işlev veya modül için, profil oluşturma çalışmasındaki tüm engellenen sürenin yüzdesi, bu işlevin veya modülün bloke edilmiş süresini kapsa.<br />- Bir satır veya yönerge için, bu satırın veya talimatın yürütüldettiği profil oluşturma çalışmasında engellenen tüm zamanın yüzdesi.|
|**Kapsayıcı Çekişmeler**|- Bir işlev için, bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütülmesinin engellenme sayısı.<br />- Bir modül için, bu modülden en az bir fonksiyonun yığında olduğu çekişmelerin sayısı.<br />- Bir satır veya talimat için, bu satır ın veya talimatın yürütülmesinin engellenme sayısı.|
|**Kapsayıcı Çekişmeler %**|- Bir işlev veya modül için, profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, bu işlevin veya modülün kapsayıcı çekişmeleridir.<br />- Bir satır veya yönerge için, bu satırın veya talimatın yürütüldettiği profil oluşturma çalışmasında engellenen tüm zamanın yüzdesi.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşlev, çizgi veya yönerge işaretçisini içeren modülün adı.|
|**Modül Yolu**|Modülü, işlevi, satırı veya talimat işaretçisini içeren modülün yolu.|
|**Adı**|Modülün veya fonksiyonun adı.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [Modüller Görünümü](../profiling/modules-view.md)
- [Modülgörünümü - enstrümantasyon](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modülgörünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
