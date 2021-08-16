---
title: Satırlar Görünümü - İçerik Veri | Microsoft Docs
description: Sorgu verilerinin Satırlar görünümünün, profil oluşturma çalıştırması içinde örnekler toplanmış olduğunda yürütülen deyimlerin performans verilerini nasıl listele olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 34e1280b9f44bef7017afed0cc6af60852d6c1bd82f7c9667313bdee6602edb0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426709"
---
# <a name="lines-view---contention-data"></a>Satırlar Görünümü - karşıtlık verileri
Sorgu verilerinin Satırlar görünümü, profil oluşturma çalıştırması içinde örnekler toplanmışken yürütülen deyimlerin performans verilerini listeler. Kaynak dosyada bir deyim, bir kaynak dosyada birden fazla satıra yayma ve tek bir satır birden fazla deyim içerebilir.

 Deyimi aşağıdaki veriler tarafından tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- deyimini içeren işlev.

- Deyimin başlat olduğu kaynak satır.

- Deyimin başlat olduğu kaynak satırda yer alan karakter.

- Deyimin bitiş yaptığı kaynak satır.

- Deyimin sona erdiğinde kaynak satırda yer alan karakter.

  Satır Adı sütunu, tanımlayıcı verileri için sıralanabilir bir concatenation sağlar.

  Aşağıdaki tabloda Satır Görünümü raporunun sütunları açık almaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bir tartışma olayı nedeniyle bu deyimin deyiminde kod yürütmesi engellenmiş olan süre. deyiminin çağırmış olduğu işlevlerde engellenen süre dahil değildir.|
|**Özel Engellenen Saat %**|İşlemde, deyiminin yalnızca engellenen süresi olan tüm engellenen sürelerin yüzdesi.|
|**Özel İçerikler**|Bu deyimin, bir olay nedeniyle deyiminde kod yürütmesi engellenmiş sayısı. deyiminin çağır olduğu işlevlerde yer alan contention olayları dahil değildir.|
|**Özel İçerik %**|İşlemde yer alan ve bu deyimin özel olarak ele alan tüm olaylarının yüzdesi.|
|**İşlev Adresi**|Bu deyimi içeren işlevin adresi.|
|**İşlev Adı**|Bu deyimi içeren işlevin tam adı.|
|**Kapsayıcı Engellenen Süre**|Bu deyimde engellenen süre ve deyiminde çağrılır işlevler.|
|**Kapsayıcı Engellenen Saat %**|İşlemde engellenen tüm zamanların yüzdesi, deyiminin kapsayıcı engellenen zamanıdır.|
|**Kapsayıcı İçerikler**|Bu deyimin ve deyiminde çağrılmış işlevlerin yürütülmesinin kaç kez engellenmiş olduğu.|
|**Kapsayıcı İçerik %**|Süreç içinde yer alan ve bu deyimin kapsayıcı olarak ele alan tüm olaylarının yüzdesi.|
|**Satır Adı**|Çizginin profil oluşturma tanımlayıcısı. Tanımlayıcı şu söz dizimi kullanır: `SourceFile` **;[** `LineNumberStart` **,**`CharacterStart` **]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|deyimini içeren modülün adı.|
|**Modül Yolu**|deyimini içeren modülün yolu.|
|**İşlem Kimliği**|Profili yapılan sürecin işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Karakter Başlangıç**|Bu deyimin başladığı kaynak dosya satırda başlangıç karakterinin uzaklığı.|
|**Kaynak Karakter Sonu**|Bu deyimin sona erdiğinde kaynak dosya satırda başlangıç karakterinin uzaklığı.|
|**Kaynak Dosya**|İşlev deyimini içeren kaynak dosyanın adı.|
|**Kaynak Satırı Başlangıç**|Deyimin başlat olduğu kaynak dosyanın satır numarası.|
|**Kaynak Satır Sonu**|Deyimin sona erdiğinde kaynak dosyada yer alan satır numarası.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor Görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Satırlar Görünümü](../profiling/lines-view.md)
- [Çizgi Görünümü - örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
