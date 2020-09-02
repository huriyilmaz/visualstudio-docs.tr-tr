---
title: Sınıf sekmesi, pencere özellikleri Iletişim kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62565019"
---
# <a name="class-tab-window-properties-dialog-box"></a>Sınıf Sekmesi, Pencere Özellikleri İletişim Kutusu
Seçili pencerenin sınıfındaki bilgileri göstermek için **sınıf** sekmesini kullanın. [Pencere özellikleri Iletişim kutusunu](../debugger/window-properties-dialog-box.md)görüntülemek Için odağı [Windows görünümü](../debugger/windows-view.md) penceresine taşıyın. Ağaçta herhangi bir pencere düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

 Aşağıdaki ayarlar **sınıf** sekmesinde mevcuttur:

|Giriş|Açıklama|
|-----------|-----------------|
|**Sınıf adı**|Bu pencere sınıfının adı (veya sıra numarası).|
|**Sınıf stilleri**|Sınıf stili kodlarının birleşimi.|
|**Sınıf baytları**|Bu pencere sınıfıyla ilişkili uygulamaya özel veriler.|
|**Sınıf atom 'u**|**RegisterClass** çağrısı tarafından döndürülen sınıf için atom.|
|**Örnek tanıtıcısı**|Sınıfı kaydettiğiniz modülün örnek tanıtıcısı. Örnek tutamaçları benzersiz değil.|
|**Pencere baytları**|Bu sınıfın her bir penceresiyle ilişkili ek baytların sayısı. Bu baytların anlamı uygulama tarafından belirlenir. Bayt değerlerini DWORD biçiminde görmek için liste kutusunu genişletin.|
|**Pencere proc**|Bu sınıfın Windows için **WndProc** işlevinin geçerli adresi. Bu, pencere alt sınıflandır, **genel** sekmesindeki **pencere proc** ' dan farklıdır.|
|**Menü adı**|Bu sınıfın Windows ile ilişkili ana menünün adı (menü yoksa "none").|
|**Simge tutamacı**|Bu sınıfın (simge yoksa "none") Windows ile ilişkili simgenin tutamacı.|
|**İmleç tutamacı**|Bu sınıfın (imleç yoksa "none") Windows ile ilişkili imleç için tanıtıcı.|
|**Arka plan Fırçası**|Bu sınıfın Windows ile ilişkili arka plan fırçasının tanıtıcısı veya pencere arka planını boyamak için önceden tanımlanmış COLOR_ * renklerinden biri (fırça yoksa "yok").|