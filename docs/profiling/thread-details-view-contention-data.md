---
title: İş Parçacığı Ayrıntıları Görünümü - İçerik Veri | Microsoft Docs
description: İş Parçacığı Ayrıntıları görünümünün profil oluşturma çalıştırması için seçilen iş parçacığında engelleme olaylarının zaman çizelgesi grafiğini nasıl görüntüley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 18e227775be9885595855ec6230b6cf8521df675
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157039"
---
# <a name="thread-details-view---contention-data"></a>İş Parçacığı Ayrıntıları görünümü - karşıtlık verileri
İş Parçacığı Ayrıntıları görünümü, kaynaklar üzerinden yapılan sorunlardan kaynaklanan profil oluşturma çalıştırmalarının seçili iş parçacığında engelleme olaylarının zaman çizelgesi grafiğini sunar. Başka bir iş parçacığı bir kaynağa erişimi kilitledi diye iş parçacığı yürütmeyi askıya almak zorunda olduğunda engelleme olayı oluşur.

 Bu görünüm, iş parçacığının yürütme zaman çizelgesini yatay çubuk olarak, engelleme olayları ise iş parçacığı için yatay bir zaman çizelgesinde dikey çubuk olarak temsil eder. Gerektiğinde, tek tek olayları görüntülemek için zaman çizelgesinin bir bölümünü yakınlaştırabilirsiniz. Olayı yönlendiren işlevlerin yürütme yolunu görüntülemek için olay çubuğuna tıklayın. İşlevler Çağrı Yığını **penceresinde** görüntülenir. Bir işlevin kaynak kodu kullanılabilir olduğunda, IDE'nin kaynak dosyasını düzenlemek için işlev adına Visual Studio.

## <a name="navigate-the-timeline"></a>Zaman çizelgesinde gezinme

#### <a name="to-zoom-in-on-a-timeline-segment"></a>Zaman çizelgesi segmentini yakınlaştırmak için

- Zaman çizelgesinin bir alanı seçmek için fare işaretçisine tıklayın ve sürükleyin.

     Fareyi serbest bırakarak görünüm seçilen zaman segmentini yakınlaştırabilir. Daha fazla ayrıntıyı yakınlaştırmak için işlemi tekrarlayın. Saat kaydırma çubuğundaki kaydırma kutusu, görünümde görüntülenen zaman kesiminin göreli boyutunu temsil eder.

#### <a name="to-zoom-out-on-a-timeline"></a>Zaman çizelgesini yakınlaştırmak için

- Önceki **yakınlaştırma düzeyine** dönmek için Uzaklaştır'a tıklayın.

- Görünümde **zaman çizelgesinin** tamamını göstermek için Sıfırla'yı Yakınlaştır'a tıklayın.

#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için

- Zaman çizelgesi grafiğinde, olayı temsil eden dikey çıtaya tıklayın.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Çağrı yığınındaki bir işlevin kaynak kodunu görüntülemek veya düzenlemek için

- Çağrı **Yığını penceresinde** işlev adına tıklayın.

  İşlev kaynak kodu geçerli projenin parçası olması gerekir.

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Profil oluşturma çalıştırması içinde tüm iş parçacıklarında bir kaynağın içerik olaylarını görüntülemek için

- Zaman çizelgesi grafiğinde kaynağın adına veya kimliğine tıklayın.

     Seçilen [kaynak için](../profiling/resource-details-view-contention-data.md) Kaynak Ayrıntıları Görünümü görüntülenir.

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>İşlemler penceresinde iş parçacığı musiki verilerini görüntülemek için

- Zaman çizelgesi grafiğinde Toplam'a **tıklayın.**

     İşlem [Görünümü,](../profiling/process-view-contention-data.md) iş parçacığı seçili olarak görünür.
