---
title: Bellek sekmesi, Işlem özellikleri Iletişim kutusu | Microsoft Docs
description: İşlemin nasıl bellek kullandığını görüntülemek için Işlem özelliklerinin bellek sekmesini kullanın. Kullanılan boşlukla, paylaşılan alana ve kullanılan sanal alana ilişkin bilgiler vardır.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725408"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Bellek Sekmesi, İşlem Özellikleri İletişim Kutusu
Bir işlemin belleği nasıl kullandığını göstermek için **bellek** sekmesini kullanın. [Işlem özellikleri Iletişim kutusunu](../debugger/process-properties-dialog-box.md)görüntülemek için odağı bir [işlem görünümü](../debugger/processes-view.md) penceresine taşıyın. Ağaçta herhangi bir işlem düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

 **Bellek** sekmesinde aşağıdaki ayarlar kullanılabilir:

|Giriş|Description|
|-----------|-----------------|
|**Sanal Bayt Sayısı**|İşlemin kullandığı sanal adres alanının geçerli boyutu (bayt cinsinden). Sanal adres alanının kullanımı, disk veya ana bellek sayfalarının karşılık gelen kullanımını göstermez. Ancak, sanal alan sınırlı olur ve çok fazla kullanımı, işlemin kitaplıklarını yükleme yeteneğini sınırlayabilir.|
|**En yüksek sanal bayt sayısı**|İşlemin herhangi bir anda kullandığı en fazla sanal adres alanı bayt sayısı.|
|**Çalışma Kümesi**|Bellek sayfaları kümesi, son zamanlarda işlemdeki iş parçacıkları tarafından aynıdır. Bilgisayardaki boş bellek eşiğin üstünde ise, sayfalar kullanımda olmasalar bile bir işlemin çalışma kümesinde bırakılır. Boş bellek eşiğin altına düştüğünde, sayfalar çalışma kümesinden kırpılır. Bunlar gerekliyse, Ana bellekten ayrılmadan önce çalışma kümesine geçici olarak geri dönecek.|
|**Yoğun çalışma kümesi**|Bu işlemin çalışma kümesindeki her zaman bir noktada en fazla sayfa sayısı.|
|**Disk belleğine alınan havuz baytları**|İşlemin ayırdığı, disk belleğine alınan havuzun geçerli miktarı. Disk belleğine alınan havuz, işletim sistemi bileşenlerinin, kendilerine ait görevleri gerçekleştirirken alan edindikleri bir sistem bellek alanıdır. Disk belleğine alınan havuz sayfaları, sistem tarafından sürdürülen süreler boyunca erişilmediği zaman disk belleği dosyasına eklenebilir.|
|**Disk belleğine alınmayan havuz baytları**|İşlem tarafından ayrılan, disk belleksiz havuzdaki geçerli bayt sayısı. Disk belleksiz havuz, ayrılan görevlerini gerçekleştirirken, işletim sistemi bileşenleri tarafından alanın alındığı bir sistem bellek alanıdır. Disk belleğine alınamayan havuz sayfaları disk belleği dosyası için disk belleğine alınamıyor; Bunlar ayrıldığı sürece ana bellekte kalır.|
|**Özel baytlar**|Bu işlemin ayırdığı, diğer işlemlerle paylaşılamayan geçerli bayt sayısı.|
|**Boş baytlar**|Bu işlemin kullanılmayan toplam sanal adres alanı.|
|**Ayrılan bayt sayısı**|Bu işlem tarafından gelecekte kullanılmak üzere ayrılan toplam sanal bellek miktarı.|
|**Serbest görüntü baytları**|Bu işlem içindeki görüntüler tarafından kullanımda veya ayrılmış sanal adres alanı miktarı.|
|**Ayrılmış görüntü baytları**|Bu işlemde çalıştırılan görüntülerde ayrılan tüm sanal bellek toplamı.|