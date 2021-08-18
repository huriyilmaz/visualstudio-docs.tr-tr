---
title: Kaynak Ayrıntıları Görünümü - İçerik Verileri | Microsoft Docs
description: Kaynak Ayrıntıları görünümünün, seçili bir kaynakla ilgili olarak oluşan ve engelleme olaylarının zaman çizelgesi grafiğini nasıl görüntüley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3e07b658d28cfbc91e8c9ea3d3613f201be1146e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054528"
---
# <a name="resource-details-view---contention-data"></a>Kaynak Ayrıntıları Görünümü - Çakışma Verileri
Kaynak Ayrıntıları görünümü, seçilen bir kaynakla ilgili içeriklerden kaynaklanan engelleme olaylarının zaman çizelgesi grafiğini gösterir. Başka bir iş parçacığı kaynağa erişimi kilitledi diye bir iş parçacığı yürütmeyi askıya almak zorunda olduğunda engelleme olayı oluşur.

 Bu görünüm, her iş parçacığının yürütme zaman çizelgesini yatay çubuk olarak temsil eder ve engelleme olaylarını iş parçacığı zaman çizelgesinde dikey çubuk olarak temsil eder. Gerektiğinde, tek tek olayları görüntülemek için zaman çizelgesinin bir bölümünü büyütebilirsiniz. Olayı yönlendiren işlevlerin yürütme yolunu (çağrı yığını) görüntülemek için olay çubuğuna tıklayın. İşlevler Çağrı Yığını **penceresinde** görüntülenir. Bir işlevin kaynak kodu kullanılabilir olduğunda işlevin adına tıklar ve arabiriminde kaynak dosyasını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] düzenleyebilirsiniz.

## <a name="procedures"></a>Yordamlar

#### <a name="to-magnify-a-timeline-segment"></a>Zaman çizelgesi kesimini büyütme

- Fare işaretçisini zaman çizelgesinin bir alanına sürükleyin.

     Fare düğmesini serbest bıraktığınızda görünüm seçilen zaman segmentini yakınlaştırıyor. Segmenti daha da büyütmek için işlemi tekrarlayın. Saat kaydırma çubuğundaki kaydırma kutusu, görünümde görüntülenen zaman kesiminin göreli boyutunu temsil eder.

#### <a name="to-zoom-out-on-a-timeline"></a>Zaman çizelgesini yakınlaştırmak için

- Aşağıdaki adımlardan birini uygulayın:

  - Önceki **yakınlaştırma düzeyine** dönmek için Uzaklaştır'a tıklayın.

  - Görünümde **zaman çizelgesinin** hepsini görüntülemek için Sıfırla'yı Yakınlaştır'a tıklayın.

#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için

- Zaman çizelgesi grafiğinde olay çubuğuna tıklayın.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Çağrı yığınındaki bir işlevin kaynak kodunu görüntülemek veya düzenlemek için

- Çağrı **Yığını penceresinde** işlev adına tıklayın.

  İşlev kaynak kodu geçerli projenin parçası olması gerekir.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Kaynağın içerik olaylarının çağrı ağacını görüntülemek için

- Zaman çizelgesi grafiğinde Toplam'a **tıklayın.**

     Kaynak için İçerikler görünümü görüntülenir. Daha fazla bilgi için [bkz. Kaynak İçerikleri Görünümü.](../profiling/resource-contentions-view-contention-data.md)

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Bir iş parçacığının tüm etkinlik olaylarını görüntülemek için

- Zaman çizelgesi grafiğinde iş parçacığının adına veya kimliğine tıklayın.

     Seçilen iş parçacığı için İş Parçacığı Ayrıntıları Görünümü görüntülenir. Daha fazla bilgi için bkz. [İş Parçacığı Ayrıntıları Görünümü.](../profiling/thread-details-view-contention-data.md)
