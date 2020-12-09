---
title: Genel sekmesi, Işlem özellikleri Iletişim kutusu | Microsoft Docs
description: Modül adı, işlem KIMLIĞI, temel öncelik, iş parçacığı sayısı, CPU süresi, Kullanıcı saati ve geçen süre dahil olmak üzere bir işlemle ilgili bilgiler için Genel sekmesini görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4980437c63348050db1a007e8f541e9af9e186cc
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862743"
---
# <a name="general-tab-process-properties-dialog-box"></a>Genel Sekmesi, İşlem Özellikleri İletişim Kutusu
Belirli bir işlem hakkında daha fazla bilgi edinmek için **genel** sekmesini kullanın. [Işlem özellikleri Iletişim kutusunu](../debugger/process-properties-dialog-box.md)görüntülemek için odağı bir [işlem görünümü](../debugger/processes-view.md) penceresine taşıyın. Ağaçta herhangi bir işlem düğümünü seçin, sonra **Görünüm** menüsünden **Özellikler** ' i seçin.

 **Genel** sekmesinde aşağıdaki ayarlar kullanılabilir:

|Giriş|Description|
|-----------|-----------------|
|**Modül Adı**|Modülün adı.|
|**İşlem Kimliği**|Bu işlemin benzersiz KIMLIĞI. İşlem KIMLIĞI numaraları yeniden kullanılır, bu nedenle bir işlemi yalnızca bu işlemin kullanım ömrü için tanımlarlar. Işlem nesnesi türü, bir program çalıştırıldığında oluşturulur. Bir işlemdeki tüm iş parçacıkları aynı adres alanını paylaşır ve aynı verilere erişebilir.|
|**Öncelik tabanı**|Bu işlemin geçerli temel önceliği. Bir işlem içindeki iş parçacıkları, işlemin temel önceliğine göre kendi temel önceliklerini artırıp düşürebilirler.|
|**İş Parçacıkları**|Bu işlemde etkin olan iş parçacıklarının sayısı.|
|**CPU süresi**|Bu işlem ve iş parçacıkları üzerinde harcanan toplam CPU süresi. Kullanıcı zamanına ve ayrıcalıklı zamana eşit.|
|**Kullanıcı saati**|Bu işlemin iş parçacıklarının, boşta olmayan iş parçacıklarında Kullanıcı modunda kod çalıştırırken harcadığı toplam geçen süre. Uygulamalar, pencere yöneticisi ve grafik altyapısı gibi alt sistemler gibi kullanıcı modunda yürütülür.|
|**Ayrıcalıklı zaman**|Bu işlemin boşta olmayan iş parçacıklarında ayrıcalıklı modda çalıştığı toplam geçen süre. Hizmet katmanı, yönetici yordamları ve çekirdek ayrıcalıklı modda yürütülür. Grafik bağdaştırıcıları ve yazıcılar dışındaki çoğu cihaz için cihaz sürücüleri de ayrıcalıklı modda yürütülür. Uygulamanız için Windows tarafından yapılan bazı işler, ayrıcalıklı zamana ek olarak diğer alt sistem işlemlerinde görünebilir.|
|**Geçen süre**|Bu işlemin çalıştığı geçen toplam süre.|