---
title: Satır Görünümü - Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff4d851937111400002de531696b9b69aec20ba9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778589"
---
# <a name="lines-view---sampling-data"></a>Satır Görünümü - örnekleme verileri
Örnekleme verilerinin Satırlar görünümü, örnekler profil oluşturma çalışmasında toplandığında çalıştırılan ifadelere ait performans verilerini listeler.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

 Kaynak dosyada, bir deyim kaynak dosyada birden fazla satıra yayılabilir ve tek bir satır birden fazla deyim içerebilir. Bir deyim aşağıdaki ler tarafından tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- İfadeyi içeren işlev.

- İfadenin başladığı kaynak satırı.

- İfadenin başladığı kaynak satırdaki karakter.

- İfadenin sona erdiği kaynak satırı.

- İfadenin sona erdiği kaynak satırdaki karakter.

  Satır Adı sütunu tanımlayıcı verilerinin tasnif edilebilir bir bir bir araya aksamasağlar.

  Tanım olarak, bir deyim diğer işlevleri çağırmaz. Bu nedenle, yalnızca özel değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşlev çizgisini içeren modülün adı.|
|**Modül Yolu**|İşlev çizgisini içeren modülün yolu.|
|**Kaynak Dosya**|İşlev satırını içeren kaynak dosya.|
|**Fonksiyon Adı**|İşlevin adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|İşlevin başlangıç adresi.|
|**Kaynak Satırı Başlangıç**|Bu örneğin toplandığı kaynak dosyadaki başlangıç satır numarası.|
|**Kaynak Satır Sonu**|Bu örneğin toplandığı kaynak dosyadaki bitiş satır numarası.|
|**Kaynak Karakter Başlangıç**|Bu örneğin toplandığı kaynak dosya satırındaki başlangıç karakterinin mahsup edilmesi.|
|**Kaynak Karakter Sonu**|Bu örneğin toplandığı kaynak dosya satırındaki bitiş karakterinin mahsup edilmesi.|
|**Satır Adı**|Aşağıdaki sözdizimi ile çizginin profil oluşturucu tarafından oluşturulan`Source File`tanımlayıcısı:**;[** `Line Number Start` **,**,`Character Start`**]->; [**`Line Number End`**,**`Character End`**]**|
|**Özel Örnekler**|İşlev çizgisi yürütüldüğünde toplanan toplam örnek sayısı.|
|**Özel Örnekler %**|İşlev çizgisi yürütüldüğünde toplanan profil oluşturma çalışmasındaki tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Satır Görünümü - örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
