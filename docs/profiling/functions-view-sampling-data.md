---
title: İşlevler Görünümü-Örnekleme verileri | Microsoft Docs
description: Profil oluşturma çalışması sırasında örneklendiği işlevleri listeleyen örnekleme profili yöntemi için Işlevler rapor görünümü hakkında bilgi edinin.
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 82b48689b6348c7d003f5418224260b7939e907a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907354"
---
# <a name="functions-view---sampling-data"></a>İşlevler Görünümü-Örnekleme verileri
Örnekleme profili yöntemi için Işlevler rapor görünümü profil oluşturma çalıştırması sırasında örneklendiği işlevleri listeler.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**İşlev adı**|İşlevin tam adı.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**İşlev adresi**|İşlevin adresi.|
|**Kapsamlı örnekler**|Bu işlev yürütüldüğü zaman toplanan örneklerin toplam sayısı; diğer bir deyişle, bu işlev çağrı yığınında olduğunda toplanan örneklerin sayısı. Bu sayı, bu işlev tarafından çağrılan işlevler yürütüldüğü zaman toplanan örnekleri içerir.|
|**Kapsamlı örnekler%**|Profil oluşturma çalıştırmasında, bu işlevin kapsamlı örnekleri olan tüm örneklerin yüzdesi.|
|**Dışlamalı örnekler**|Bu işlevin gövdesinde kod yürütürken toplanan örneklerin toplam sayısı; diğer bir deyişle, bu işlev çağrı yığınının en üstünde olduğunda. Bu işlev tarafından çağrılan işlevlerde toplanan örnekler dahil değildir.|
|**Dışlamalı örnekler%**|Bu işlevin özel örnekleri olan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlevler görünümü-izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [İşlevler Görünümü-Örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
