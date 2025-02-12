---
title: Satırlar Görünümü - Örnekleme Veri | Microsoft Docs
description: Örnekleme verilerinin Satırlar görünümünün, profil oluşturma çalıştırması içinde örnekler toplanmış olduğunda yürütülen deyimlerin performans verilerini nasıl listele olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 91f6037dfec4d9bee620c0377445550b3b8d562345017592daad018e09ec5b19
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426670"
---
# <a name="lines-view---sampling-data"></a>Satırlar Görünümü - örnekleme verileri
Örnekleme verilerinin Satırlar görünümü, profil oluşturma çalıştırması içinde örnekler toplanmışken yürütülen deyimlerin performans verilerini listeler.

> [!NOTE]
> Windows 8 ve Windows Server 2012 profil oluşturma Visual Studio bu platformlarda veri toplama şeklinde önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

 Kaynak dosyada bir deyim, bir kaynak dosyada birden fazla satıra yayma ve tek bir satır birden fazla deyim içerebilir. Deyimi aşağıdakiler tarafından tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- deyimini içeren işlev.

- Deyimin başladığı kaynak satır.

- Deyimin başlat olduğu kaynak satırda yer alan karakter.

- Deyimin bitiş yaptığı kaynak satır.

- Deyimin bitiş yaptığı kaynak satırda yer alan karakter.

  Satır Adı sütunu, tanımlayıcı verileri için sıralanabilir bir concatenation sağlar.

  Tanımı gereği, bir deyimi diğer işlevleri çağırmaz. Bu nedenle yalnızca özel değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşlev çizgilerini içeren modülün adı.|
|**Modül Yolu**|İşlev çizgilerini içeren modülün yolu.|
|**Kaynak Dosya**|İşlev çizgilerini içeren kaynak dosya.|
|**İşlev Adı**|İşlevin adı.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**İşlev Adresi**|İşlevin başlangıç adresi.|
|**Kaynak Satırı Başlangıç**|Bu örneğin toplanmış olduğu kaynak dosyada başlangıç satırı numarası.|
|**Kaynak Satır Sonu**|Bu örneğin toplanmış olduğu kaynak dosyanın bitiş satırı numarası.|
|**Kaynak Karakter Başlangıç**|Bu örneğin toplanmış olduğu kaynak dosya satırına başlangıç karakterinin uzaklığı.|
|**Kaynak Karakter Sonu**|Bu örneğin toplanmış olduğu kaynak dosya satırına bitiş karakterinin uzaklığı.|
|**Satır Adı**|Şu söz dizimleriyle satırın profil oluşturma tanımlayıcısı: `Source File` **;[** `Line Number Start` **,**`Character Start` **]->; [**`Line Number End`**,**`Character End`**]**|
|**Özel Örnekler**|İşlev satırı yürütücüyken toplanan toplam örnek sayısı.|
|**Özel Örnekler %**|profil oluşturma çalıştırması içinde işlev satırı yürüt edilirken toplanan tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çizgi Görünümü - örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
