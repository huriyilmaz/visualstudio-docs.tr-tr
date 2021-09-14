---
title: Yönerge İşaretçileri (PS) Görünümü - Örnekleme Veri | Microsoft Docs
description: Örnekleme verilerine ilişkinPS görünümünün, örnekler toplanmış olduğunda doğrudan yürütülen derleme yönergeleri için performans verilerini nasıl listelemektedir?
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 10eb11ccd2263ab0d66040137067ef2baad56f87
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637086"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Yönerge İşaretçileri (PS) Görünümü - örnekleme verileri
Örnekleme verilerinde IP'ler görünümü, profil oluşturma çalıştırması içinde örnekler toplanmışken doğrudan yürütülen derleme yönergelerine ilişkin performans verilerini listeler.

> [!NOTE]
> Bu platformlarda Windows 8 Windows Server 2012 profil oluşturma Visual Studio önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|Yönergeyi içeren modülün adı.|
|**Modül Yolu**|Yönergeyi içeren modülün yolu.|
|**Kaynak Dosya**|Yönergeyi içeren kaynak dosya.|
|**İşlev Adı**|Yönergeyi içeren işlevin adı.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**İşlev Adresi**|Yüklenen ikili dosyada işlevin başlangıç bellek adresi.|
|**Kaynak Satırı Başlangıç**|Bu örneğin toplanmış olduğu kaynak dosyada başlangıç satırı numarası.|
|**Kaynak Satır Sonu**|Bu örneğin toplanmış olduğu kaynak dosyanın bitiş satırı numarası.|
|**Kaynak Karakter Başlangıç**|Bu örneğin toplanmış olduğu kaynak dosya satırına başlangıç karakterinin uzaklığı.|
|**Kaynak Karakter Sonu**|Bu örneğin toplanmış olduğu kaynak dosya satırına bitiş karakterinin uzaklığı.|
|**Yönerge Adresi**|Yüklenen ikili dosyada yönergenin adresi.|
|**Özel Örnekler**|Yönerge yürütücüyken toplanan toplam örnek sayısı.|
|**Özel Örnekler %**|Profil oluşturma çalıştırması içinde yönerge yürüt edilirken toplanan tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönerge İşaretçileri (PS) Görünümü - örnekleme](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
