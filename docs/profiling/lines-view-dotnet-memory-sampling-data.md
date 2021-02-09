---
title: Satırlar görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
description: .NET bellek ayırma profil oluşturma verileri için satırlar görünümünün profil oluşturma çalışması sırasında belleği ayrılan deyimleri nasıl listeleyeceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1922851b96ddec47c298b3e7d1e94a7de129505a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917843"
---
# <a name="lines-view---net-memory-sampling-data"></a>Satırlar görünümü-.NET Bellek Örnekleme verileri
Örnekleme yöntemini kullanan .NET bellek ayırma profil oluşturma verileri için Satırlar Görünümü profil oluşturma çalışması sırasında belleği ayrılan deyimleri listeler. Sütunlar ayrıca, ayırma boyutunu ve sayısını da içerir.

 Bir kaynak dosyasında, bir ifade kaynak dosyada birden fazla satıra yayılabilir ve tek bir satır birden fazla ifade içerebilir.

 Bir ifade aşağıdaki şekilde tanımlanır:

- Function ifadesini içeren kaynak dosya.

- İfadesini içeren işlev.

- Deyimin başladığı kaynak satır.

- Deyimin başladığı kaynak satırdaki karakter.

- Deyimin bittiği kaynak satır.

- Deyimin bittiği kaynak satırdaki karakter.

  Satır adı sütunu, tanımlayıcı verilerinin sıralanabilir bir birleştirmesini sağlar.

  Tanım olarak, bir ifade diğer işlevleri çağırmaz. Bu nedenle, yalnızca dışlamalı değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Modül adı**|Deyimin bulunduğu modülün adı.|
|**Modül yolu**|Deyimin bulunduğu modülün yolu.|
|**Kaynak Dosya**|İfadesini içeren kaynak dosya.|
|**İşlev adı**|Deyimin bulunduğu işlevin adı.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**İşlev adresi**|İşlevin başlangıç adresi.|
|**Kaynak satırı başlangıç**|Ayırma gerçekleştiği kaynak dosyadaki başlangıç satırı numarası.|
|**Kaynak satır sonu**|Ayırma gerçekleştiği kaynak dosyadaki bitiş satırı numarası.|
|**Kaynak karakter başlangıcı**|Ayırmanın gerçekleştiği kaynak dosya satırındaki başlangıç karakterinin boşluğu.|
|**Kaynak karakter sonu**|Ayırma gerçekleştiği kaynak dosya satırındaki bitiş karakterinin boşluğu.|
|**Satır adı**|Aşağıdaki sözdizimine sahip satır için profil oluşturucu tarafından oluşturulan bir tanımlayıcı: `Source File` **; [** `Line Number Start` **,**`Character Start` **]->; [**`Line Number Start,Character Start`**]**|
|**Dışlamalı ayırmalar**|Bu satırda oluşturulan toplam nesne sayısı.|
|**Dışlamalı ayırmalar%**|Bu satırda ayrılan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Dışlamalı baytlar**|Bu satırda ayrılan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Dışlamalı bayt yüzdesi**|Bu satırda ayrılan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
