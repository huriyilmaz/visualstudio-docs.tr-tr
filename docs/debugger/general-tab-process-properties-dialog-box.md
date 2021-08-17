---
title: Genel Sekmesi, İşlem Özellikleri İletişim Kutusu | Microsoft Docs
description: Modül adı, işlem kimliği, temel öncelik, iş parçacığı sayısı, CPU süresi, kullanıcı saati ve geçen süre gibi bir işlem hakkında bilgi için Genel sekmesini görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e50cffecb1ef12373e8a6774efebf832aebaa9b61fdc362657474028acdb7cc9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391401"
---
# <a name="general-tab-process-properties-dialog-box"></a>Genel Sekmesi, İşlem Özellikleri İletişim Kutusu
Belirli bir **işlem hakkında** daha fazla bilgi için Genel sekmesini kullanın. İşlem Özellikleri [İletişim Kutusunu görüntülemek için,](../debugger/process-properties-dialog-box.md)odağı bir İşlemler Görünümü [penceresine](../debugger/processes-view.md) sürükleyin. Ağaçtan herhangi bir işlem düğümünü seçin ve ardından **Görünüm menüsünden** **Özellikler'i** seçin.

 Genel sekmesinde aşağıdaki ayarlar **kullanılabilir:**

|Giriş|Açıklama|
|-----------|-----------------|
|**Modül Adı**|Modülün adı.|
|**İşlem Kimliği**|Bu sürecin benzersiz kimliği. İşlem kimliği numaraları yeniden kullanılır, bu nedenle bir işlemi yalnızca o sürecin ömrü boyunca tanımlamaları gerekir. Bir program çalıştırılan İşlem nesne türü oluşturulur. Bir işlemde yer alan tüm iş parçacıkları aynı adres alanı paylaşır ve aynı verilere erişime sahiptir.|
|**Öncelik Tabanı**|Bu sürecin geçerli temel önceliği. Bir işlem içindeki iş parçacıkları, sürecin temel önceliğe göre kendi temel önceliklerini yükseltecek ve düşürecek.|
|**İş Parçacıkları**|Bu işlemde etkin olan iş parçacığı sayısı.|
|**CPU Süresi**|Bu işlem ve iş parçacıkları için harcanan toplam CPU süresi. Kullanıcı Saati ve Ayrıcalıklı Saat'e eşittir.|
|**Kullanıcı Saati**|Bu işlem iş parçacıklarının boşta olmayan iş parçacıklarında Kullanıcı Modu'nun kodu yürütmeye harcadığı toplu geçen süre. Uygulamalar, pencere yöneticisi ve grafik altyapısı gibi alt sistemlerde olduğu gibi Kullanıcı Modu'da yürütülür.|
|**Ayrıcalıklı Saat**|Bu işlem boşta olmayan iş parçacıklarında Ayrıcalıklı Modda çalıştırılma süresi boyunca geçen toplam süre. Hizmet katmanı, Yönetici yordamları ve Çekirdek Ayrıcalıklı Mod'da yürütülür. Grafik bağdaştırıcıları ve yazıcılar dışında çoğu cihaz için cihaz sürücüleri ayrıcalıklı modda da yürütülür. Uygulamanıza Windows bazı işler, Ayrıcalıklı Zaman'a ek olarak diğer alt sistem işlemlerde görünebilir.|
|**Geçen Süre**|Bu işlem çalıştırıldı geçen toplam süre.|