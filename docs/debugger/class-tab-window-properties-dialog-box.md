---
title: Sınıf Sekmesi, Pencere Özellikleri İletişim Kutusu | Microsoft Docs
description: Visual Studio'de Sınıf sekmesini seçin, odağı Windows Görünümü penceresine taşı, bir pencere düğümü seçin ve Pencere Özellikleri iletişim kutusunu görmek için Görünüm > Özellikleri'ne tıklayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4179680ae5f5c55c322de8fbfc9552923ba3962a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630915"
---
# <a name="class-tab-window-properties-dialog-box"></a>Sınıf Sekmesi, Pencere Özellikleri İletişim Kutusu
Seçilen **pencerenin** sınıfındaki bilgileri göstermek için Sınıf sekmesini kullanın. Pencere Özellikleri [İletişim Kutusunu görüntülemek için](../debugger/window-properties-dialog-box.md)odağı Görünüm [penceresine Windows](../debugger/windows-view.md) hareket ettirin. Ağaçta herhangi bir pencere düğümünü seçin ve ardından Görünüm **menüsünden** **Özellikler'i** seçin.

 Sınıf sekmesinde aşağıdaki ayarlar **kullanılabilir:**

|Giriş|Description|
|-----------|-----------------|
|**Sınıf Adı**|Bu pencere sınıfının adı (veya dizi numarası).|
|**Sınıf Stilleri**|Sınıf stili kodlarının birleşimi.|
|**Sınıf Bayt sayısı**|Bu pencere sınıfıyla ilişkili uygulamaya özgü veriler.|
|**Sınıf Atomu**|**RegisterClass** çağrısı tarafından döndürülen sınıfın atomu.|
|**Örnek Tanıtıcısı**|sınıfını kaydeden modülün örnek tanıtıcısı. Örnek tanıtıcıları benzersiz değildir.|
|**Pencere Bayt sayısı**|Bu sınıfın her penceresiyle ilişkili ek bayt sayısı. Bu baytların anlamı uygulama tarafından belirlenir. DWORD biçimindeki bayt değerlerini görmek için liste kutusunu genişletin.|
|**Window Proc**|Bu sınıfın pencereleri için **WndProc** işlevinin geçerli adresi. Bu durum, pencere **alt sınıfına** alındı **ise** Genel sekmesindeki Window Proc'dan farklıdır.|
|**Menü Adı**|Bu sınıfın pencereleri ile ilişkili ana menenin adı ("menü yoksa hiçbiri").|
|**Simge Tanıtıcısı**|Bu sınıfın pencereleri ile ilişkili simgenin tanıtıcısı ("simge yoksa hiçbiri").|
|**İmleç Tanıtıcısı**|Bu sınıfın pencereleri ile ilişkili imlecin tanıtıcısı ("imleç yoksa hiçbiri").|
|**Bkgnd Fırça**|Bu sınıfın pencereleriyle ilişkili arka plan fırçasının tanıtıcısı veya pencere arka planını boyamak için önceden tanımlanmış COLOR_* renklerinden biri ("fırça yoksa hiçbiri").|