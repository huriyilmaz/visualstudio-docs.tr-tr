---
title: İş Parçacığı Ayrıntıları Görünümü - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 679fd9fd039fa903f5df5a479fa4f0e119bb7a9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778173"
---
# <a name="thread-details-view---contention-data"></a>İş Parçacığı Ayrıntıları görünümü - çekişme verileri
İş Parçacığı Ayrıntıları görünümü, kaynaklar üzerindeki çekişmelerden kaynaklanan bir profil oluşturma çalışmasının seçili iş parçacığındaki engelleme olaylarının bir zaman çizelgesi grafiğini sunar. Başka bir iş parçacığı kaynağa erişimi kilitlediği için iş parçacığı yürütmeyi askıya almak zorunda kaldığında engelleme olayı oluşur.

 Bu görünüm, iş parçacığının yürütme zaman çizelgesini yatay çubuk olarak ve engelleme olaylarını iş parçacığı için yatay bir zaman çizelgesi üzerinde dikey çubuk olarak temsil eder. Gerektiğinde, tek tek olayları görüntülemek için zaman çizelgesinin bir bölümünü yakınlaştırabilirsiniz. Olaya yol açan işlevlerin yürütme yolunu görüntülemek için olay çubuğunu tıklatın. İşlevler **Çağrı Yığını** penceresinde görünür. Bir işlevin kaynak kodu kullanılabilir olduğunda, Visual Studio IDE'deki kaynak dosyayı yeniden oluşturmak için işlev adını tıklatabilirsiniz.

## <a name="navigate-the-timeline"></a>Zaman çizelgesinde gezinme

#### <a name="to-zoom-in-on-a-timeline-segment"></a>Zaman çizelgesi segmentini yakınlaştırmak için

- Zaman çizelgesinin bir alanını seçmek için fare işaretçisini tıklatın ve sürükleyin.

     Fareyi serbest bıraktığınızda, görünüm seçili zaman kesimine yakınlaştırır. Daha ayrıntılı olarak yakınlaştırmak için işlemi yineleyebilirsiniz. Zaman kaydırma çubuğundaki kaydırma kutusu, görünümde görüntülenen zaman kesiminin göreli boyutunu temsil eder.

#### <a name="to-zoom-out-on-a-timeline"></a>Zaman çizelgesini uzaklaştırmak için

- Önceki yakınlaştırma düzeyine dönmek için **Uzaklaştır'ı** tıklatın.

- Görünümdeki tüm zaman çizelgesini göstermek için **Yakınlaştır'ı Sıfırla'yı** tıklatın.

#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için

- Zaman çizelgesi grafiğinde, olayı temsil eden dikey çubuğu tıklatın.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Arama yığınındaki bir işlevin kaynak kodunu görüntülemek veya görüntülemek için

- Arama **Yığını** penceresinde işlev adını tıklatın.

  İşlev kaynak kodu geçerli projenin bir parçası olmalıdır.

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Profil oluşturma çalışmasındaki tüm iş parçacıklarında bir kaynağın çekişme olaylarını görüntülemek için

- Zaman çizelgesi grafiğinde, kaynağın adını veya kimliğini tıklatın.

     [Seçili](../profiling/resource-details-view-contention-data.md) kaynak için Kaynak Ayrıntıları Görünümü görüntülenir.

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>İşlemler penceresinde iş parçacığı çekişme verilerini görüntülemek için

- Zaman çizelgesi grafiğinde **Toplam'ı**tıklatın.

     [İşlem Görünümü](../profiling/process-view-contention-data.md) seçili iş parçacığıyla görünür.
