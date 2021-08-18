---
title: Bellek Sekmesi, İşlem Özellikleri İletişim Kutusu | Microsoft Docs
description: İşlem Özellikleri'nin Bellek sekmesini kullanarak bir sürecin belleği nasıl kullandığını görüntüleyin. Kullanılan alan, paylaşılan alan ve kullanılan sanal alan hakkında bilgi vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 65171b796f440bc612bb7e0802bacd2373b23eb6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120939"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Bellek Sekmesi, İşlem Özellikleri İletişim Kutusu
Bir sürecin **belleği** nasıl kullandığını göstermek için Bellek sekmesini kullanın. İşlem Özellikleri [İletişim Kutusunu görüntülemek için,](../debugger/process-properties-dialog-box.md)odağı bir İşlemler Görünümü [penceresine](../debugger/processes-view.md) sürükleyin. Ağaçtan herhangi bir işlem düğümünü seçin ve ardından **Görünüm menüsünden** **Özellikler'i** seçin.

 Bellek sekmesinde aşağıdaki ayarlar **kullanılabilir:**

|Giriş|Açıklama|
|-----------|-----------------|
|**Sanal Bayt Sayısı**|sürecin kullanmakta olduğu sanal adres alanı için geçerli boyut (bayt cinsinden). Sanal adres alanı kullanımı, disk veya ana bellek sayfalarının kullanımına karşılık gelen bir durum değildir. Ancak, sanal alan sınırlıdır ve çok fazla kullanmak, sürecin kitaplıkları yükleme becerisini sınırlayıcı olabilir.|
|**En Yüksek Sanal Bayt Sayısı**|İşlemde tek bir anda kullanılan en fazla sanal adres alanı bayt sayısı.|
|**Çalışma Kümesi**|Bellek sayfaları kümesi, işlemde yer alan iş parçacıkları tarafından yakın zamanda dokunduğunda. Bilgisayarda boş bellek bir eşiğin üzerinde ise, kullanımda olsalar bile sayfalar bir sürecin Çalışma Kümesinde bırakılamaz. Boş bellek eşiğin altına düştüğünde sayfalar Çalışma Kümesinden kırpıldı. Gerekirse, ana bellek bırakmadan önce çalışma kümesine yeniden yazılım hatasıyla geri dönerler.|
|**En Yoğun Çalışma Kümesi**|Bu sürecin çalışma kümesinde herhangi bir zamanda en fazla sayfa sayısı.|
|**Diske Alınan Havuz Bayt sayısı**|İşlem tarafından ayrılan geçerli sayfalı havuz miktarı. Disk belleği havuzu, işletim sistemi bileşenlerinin görevleri yerine getirildiklerinde alan edinen bir sistem bellek alanıdır. Disk belleğine alınan havuz sayfaları, sistem tarafından sürekli süreler boyunca erişilmeme durumuyla disk belleği dosyasına çağrılabiliyor.|
|**Disk Belleği Olmayan Havuz Baytları**|İşlem tarafından ayrılan sayfasız havuz içinde geçerli bayt sayısı. Disk belleği olmayan havuz, işletim sistemi bileşenleri tarafından atanan görevleri yerine getirildiklerinde alan elde edilen bir sistem bellek alanıdır. Disk belleğine alınmayan havuz sayfaları disk belleği dosyasına sayfalandırılamaz; ayrılmış olduğu sürece ana bellekte kalırlar.|
|**Özel Bayt sayısı**|Bu işlem tarafından ayrılan ve diğer işlemlerle paylaşılamaz olan geçerli bayt sayısı.|
|**Boş Bayt Sayısı**|Bu sürecin kullanılmayan toplam sanal adres alanı.|
|**Ayrılmış Bayt sayısı**|Bu işlem tarafından gelecekte kullanılmak üzere ayrılmış toplam sanal bellek miktarı.|
|**Boş Görüntü Bayt sayısı**|Bu işlem içindeki görüntüler tarafından kullanımda veya ayrılmış olan sanal adres alanı miktarı.|
|**Ayrılmış Görüntü Bayt sayısı**|Görüntüler tarafından ayrılan tüm sanal belleğin toplamı bu işlem içinde çalıştır.|