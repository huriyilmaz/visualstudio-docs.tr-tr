---
title: .NET Bellek Ayırmaları Görünümü | Microsoft Docs
description: Profil oluşturma çalıştırması sırasında oluşturulan türleri listeleen .NET bellek ayırmaları görünümü hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f5c456a90ed949063386593734fa21a7b497e361
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131722"
---
# <a name="net-memory-allocations-view"></a>.NET Bellek Ayırma Görünümü
Ayırmalar görünümü, profil oluşturma çalıştırması sırasında oluşturulan türleri listeler. Her tür, türün ayırmaları ile sonuçlandıran işlev yürütme yollarını görüntüleyen bir çağrı ağacının kök düğümüdir.

 Tür satırdaki veriler, profil oluşturma çalıştırması içinde oluşturulan türdeki nesnelerin toplam sayısını ve bu türdeki nesneler için ayrılan toplam bayt sayısını görüntüler. Bir tür için kapsayıcı ve dış değerler her zaman aynıdır.

- Kapsayıcı değerler, işlevin örneklerde ve çağrı ağacında üst işlev tarafından çağrılmış alt işlevlerinde oluşturulan nesnelere göredir.

- Özel değerler, üst işlev tarafından çağrıldıları zaman doğrudan işlev tarafından oluşturulan nesnelere aittir. Alt işlevlerde oluşturulan nesneler dahil değildir.

  Bir işlevin verileri, oluşturulan nesne sayısını ve üst türün nesneleri için ayrılan bayt sayısını görüntüler.

## <a name="highlight-the-execution-hot-path"></a>Yürütmeye açık yolu vurgulama
 Üst türün en çok nesnelerini oluşturan çağrı ağacının yürütme yolunu bulabilirsiniz.

- En etkin yolu görüntülemek için türe veya işleve sağ tıklayın ve ardından Etkin Yolu **Genişlet'e tıklayın.**

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Ayrılan türün veya işlevin adı.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|Türü veya işlevi içeren modülün adı.|
|**Modül Yolu**|Türü veya işlevi içeren modülün yolu.|
|**Kaynak Dosya**|Türün veya işlevin tanımını içeren kaynak dosya.|
|**İşlev Satır Numarası**|Kaynak dosyada bu tür tanımının veya işlevinin başlangıcının satır numarası.|
|**Düzey**|Verilerin bir tür veya işlev için olup olmadığını gösterir.|
|**Kapsayıcı Ayırmalar**|- Bir işlev için, işlev tarafından oluşturulan üst türdeki nesnelerin toplam sayısı. Bu sayı, alt işlevlerde oluşturulan nesneleri içerir.<br />- Bir tür için, oluşturulan bu türe sahip olan toplam örnek sayısıdır.|
|**Kapsayıcı Ayırma %**|- Bir işlev için profil oluşturma çalıştırması içinde oluşturulan ve işlev tarafından üst türün kapsayıcı ayırmaları olan tüm nesnelerin yüzdesi.<br />- Bir tür için, profil oluşturma çalıştırması içinde oluşturulan ve türün örnekleri olan toplam nesne sayısının yüzdesi.|
|**Özel Ayırmalar**|- Bir işlev için, işlev çağrı yığınının en üstünde doğrudan yürütücürken oluşturulan nesne sayısıdır. Bu sayı, alt işlevlerde oluşturulan nesneleri dahil değildir.<br />- Bir tür için, oluşturulan bu türe sahip olan toplam örnek sayısıdır.|
|**Özel Ayırma %**|- Bir işlev için profil oluşturma çalıştırması içinde oluşturulan ve işlev tarafından üst türün özel ayırmaları olan tüm nesnelerin yüzdesi.<br />- Bir tür için, profil oluşturma çalıştırması içinde oluşturulan ve türün örnekleri olan toplam nesne sayısının yüzdesi.|
|**Kapsayıcı Bayt Sayısı**|- Bir işlev için, üst türün nesneleri için işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, alt işlevleri tarafından ayrılan belleği içerir.<br />- Bir tür için, profil oluşturmada ayrılan toplam bayt sayısı, türün örnekleri için çalıştır.|
|**Kapsayıcı Bayt %**|- Bir işlev için, profil oluşturma çalıştırması içinde ayrılan ve işlev tarafından üst türün kapsayıcı ayırmaları olan tüm belleğin yüzdesi.<br />- Bir tür için, tür örnekleri için ayrılmış profil oluşturma çalıştırması içinde ayrılan tüm belleğin yüzdesi.|
|**Özel Bayt Sayısı**|- Bir işlev için, üst türün nesneleri için işlev tarafından ayrılan bellek bayt sayısı. Bu sayı, alt işlevleri tarafından ayrılan belleği dahil değildir.<br />- Bir tür için, profil oluşturmada ayrılan toplam bayt sayısı, türün örnekleri için çalıştır.|
|**Özel Bayt %**|- Bir işlev için profil oluşturma çalıştırması içinde ayrılan ve işlev tarafından üst türün özel ayırmaları olan tüm belleğin yüzdesi.<br />- Bir tür için, tür örnekleri için ayrılmış profil oluşturma çalıştırması içinde ayrılan tüm belleğin yüzdesi.|
