---
title: İşlevler Görünümü - Örnekleme Veri | Microsoft Docs
description: Profil oluşturma çalıştırması sırasında örnek alınan işlevleri listeleyerek örnekleme profili yönteminin İşlevler rapor görünümü hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 624b8e3b1c0f20b8be177b89954ea1c3dbc7bb6c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033752"
---
# <a name="functions-view---sampling-data"></a>İşlevler Görünümü - örnekleme verileri
Örnekleme profili yönteminin İşlevler rapor görünümü, profil oluşturma çalıştırması sırasında örnek alınan işlevleri listeler.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

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
|**Kapsayıcı Örnekler**|Bu işlev yürütücü olduğunda toplanan toplam örnek sayısı; diğer bir ifadeyle, bu işlev çağrı yığınındayken toplanan örnek sayısıdır. Bu sayı, bu işlev tarafından çağrılan işlevler yürütücü olduğunda toplanan örnekleri içerir.|
|**Kapsayıcı Örnekler %**|Profil oluşturma çalıştırması içinde yer alan ve bu işlevin kapsayıcı örnekleri olan tüm örneklerin yüzdesi.|
|**Özel Örnekler**|Bu işlevin gövdesinde kod yürütücü olduğunda toplanan toplam örnek sayısı; diğer bir ifadeyle, bu işlev çağrı yığınının en üstündeyken. Bu işlev tarafından çağrılan işlevlerde toplanan örnekler dahil değildir.|
|**Özel Örnekler %**|Profil oluşturma çalıştırması içinde yer alan ve bu işlevin özel örnekleri olan tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor Görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlevler Görünümü - ölçüm](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [İşlevler Görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
