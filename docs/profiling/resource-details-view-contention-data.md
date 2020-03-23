---
title: Kaynak Ayrıntıları Görünümü - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e66432fd2f5d8b1532bece9d76e7dfc2a261e4b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771614"
---
# <a name="resource-details-view---contention-data"></a>Kaynak Ayrıntıları Görünümü - Çakışma Verileri
Kaynak Ayrıntıları görünümü, seçili bir kaynak üzerindeki çekişmelerin neden olduğu engelleme olaylarının bir zaman çizelgesi grafiğisunar. Başka bir iş parçacığı kaynağa erişimi kilitlediği için iş parçacığı yürütmeyi askıya almak zorunda kaldığında engelleme olayı oluşur.

 Bu görünüm, her iş parçacığının yürütme zaman çizelgesini yatay çubuk olarak temsil eder ve her engelleme olayını iş parçacığı zaman çizelgesinde dikey bir çubuk olarak temsil eder. Gerektiğinde, tek tek olayları görüntülemek için zaman çizelgesinin bir bölümünü büyütebilirsiniz. Olaya yol açan işlevlerin yürütme yolunu (çağrı yığını) görüntülemek için olay çubuğunu tıklatın. İşlevler **Çağrı Yığını** penceresinde görünür. Bir işlevin kaynak kodu kullanılabilir olduğunda, '' için arabirimdeki kaynak dosyayı yeniden yapmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]işlev adını tıklatabilirsiniz.

## <a name="procedures"></a>Yordamlar

#### <a name="to-magnify-a-timeline-segment"></a>Zaman çizelgesi segmentini büyütmek için

- Fare işaretçisini zaman çizelgesinin bir alanının üzerine sürükleyin.

     Fare düğmesini serbest bıraktığınızda, görünüm seçili zaman segmentine yakınlaştırır. Segmenti daha da büyütmek için işlemi yineleyebilirsiniz. Zaman kaydırma çubuğundaki kaydırma kutusu, görünümde görünen zaman kesiminin göreli boyutunu temsil eder.

#### <a name="to-zoom-out-on-a-timeline"></a>Zaman çizelgesini uzaklaştırmak için

- Aşağıdaki adımlardan birini uygulayın:

  - Önceki yakınlaştırma düzeyine dönmek için **Uzaklaştır'ı** tıklatın.

  - Görünümdeki tüm zaman çizelgesini göstermek için **Yakınlaştır'ı Sıfırla'yı** tıklatın.

#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için

- Zaman çizelgesi grafiğinde olay çubuğunu tıklatın.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Arama yığınındaki bir işlevin kaynak kodunu görüntülemek veya görüntülemek için

- Arama **Yığını** penceresinde işlev adını tıklatın.

  İşlev kaynak kodu geçerli projenin bir parçası olmalıdır.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Kaynak için çekişme olayları çağrı ağacıgörüntülemek için

- Zaman çizelgesi grafiğinde **Toplam'ı**tıklatın.

     Kaynak için Çekişmeler görünümü görüntülenir. Daha fazla bilgi için [Kaynak Çekişmeleri Görünümü'ne](../profiling/resource-contentions-view-contention-data.md)bakın.

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Bir iş parçacığının tüm çekişme olaylarını görüntülemek için

- Zaman çizelgesi grafiğinde, iş parçacığının adını veya kimliğini tıklatın.

     Seçili iş parçacığı için İş Parçacığı Ayrıntıları Görünümü görüntülenir. Daha fazla bilgi için [İş Parçacığı Ayrıntıları Görünümü'ne](../profiling/thread-details-view-contention-data.md)bakın.
