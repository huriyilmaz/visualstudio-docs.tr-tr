---
title: Satır Görünümü - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1dfcdf67c897c0c1565e536a69cc940b9df83390
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778602"
---
# <a name="lines-view---contention-data"></a>Satırlar Görünümü - çekişme verileri
Çekişme verilerinin Satırlar görünümü, örnekler profil oluşturma çalışmasında toplandığında çalıştırılan ifadelere ait performans verilerini listeler. Kaynak dosyada, bir deyim kaynak dosyada birden fazla satıra yayılabilir ve tek bir satır birden fazla deyim içerebilir.

 Bir deyim aşağıdaki verilerle tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- İfadeyi içeren işlev.

- İfadenin başladığı kaynak satırı.

- İfadenin başladığı kaynak satırdaki karakter.

- İfadenin sona erdiği kaynak satırı.

- İfadenin sona erdiği kaynak satırdaki karakter.

  Satır Adı sütunu tanımlayıcı verilerinin tasnif edilebilir bir bir bir araya aksamasağlar.

  Aşağıdaki tabloda Satır Görünümü raporunun sütunları açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bu bildirimin bir çekişme olayı nedeniyle bildirimde kod yürütmesinin engellendiği süre. Çağrılan deyimin dahil olmadığı işlevlerde engellenen süre.|
|**Özel Engellenen Süre %**|İfadenin münhasıran engellenen zamanı olan işlemdeki tüm engellenen zamanın yüzdesi.|
|**Özel Çekişmeler**|Bu bildirimin bir çekişme olayı nedeniyle bildirimde kod yürütmesinin engellenme sayısı. İfade olarak adlandırılan işlevlerde çekişme olayları dahil edilmez.|
|**Özel Çekişmeler %**|Bu bildirimin münhasır çekişmeleri olan süreçteki tüm çekişme olaylarının yüzdesi.|
|**Fonksiyon Adresi**|Bu ifadeyi içeren işlevin adresi.|
|**Fonksiyon Adı**|Bu ifadeyi içeren işlevin tam nitelikli adı.|
|**Kapsayıcı Engellenen Süre**|Bu ifadede engellenen süre ve işlevler deyiminde çağrılır.|
|**Kapsayıcı Engellenen Süre %**|İfadenin kapsayıcı olarak engellenen zamanı olan işlemdeki tüm engellenen zamanın yüzdesi.|
|**Kapsayıcı Çekişmeler**|Bu deyimin ve deyimde çağrılan işlevlerin kaç kez yürütülmesi engellendi.|
|**Kapsayıcı Çekişmeler %**|Bu bildirimin kapsayıcı çekişmeleri olan süreçteki tüm çekişme olaylarının yüzdesi.|
|**Satır Adı**|Çizginin profil oluşturucu tarafından oluşturulan tanımlayıcısı. Tanımlayıcı aşağıdaki sözdizimini kullanır:`SourceFile`**;[** `LineNumberStart` **,**,`CharacterStart`**]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İfadeyi içeren modülün adı.|
|**Modül Yolu**|İfadeyi içeren modülün yolu.|
|**İşlem Kimliği**|Profilli işlemin işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Karakter Başlangıç**|Bu bildirimin başladığı kaynak dosya satırındaki başlangıç karakterinin mahsup noktası.|
|**Kaynak Karakter Sonu**|Bu bildirimin sona erdiği kaynak dosya satırındaki başlangıç karakterinin mahsup uyrucu.|
|**Kaynak Dosya**|İşlev deyimini içeren kaynak dosyanın adı.|
|**Kaynak Satırı Başlangıç**|İfadenin başladığı kaynak dosyadaki satır numarası.|
|**Kaynak Satır Sonu**|İfadenin sona erdiği kaynak dosyadaki satır numarası.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [Satırlar Görünümü](../profiling/lines-view.md)
- [Satır Görünümü - örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
