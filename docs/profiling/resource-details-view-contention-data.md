---
title: Kaynak Ayrıntıları görünümü-çekişme verileri | Microsoft Docs
description: Kaynak ayrıntıları görünümünün, seçili bir kaynak üzerinde çekişmeler nedeniyle oluşan engelleme olaylarının zaman çizelgesi grafiğini nasıl sunabileceğini öğrenin.
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
ms.openlocfilehash: 45babe50e794e0831fd0e93048b32feaf18be87a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720364"
---
# <a name="resource-details-view---contention-data"></a>Kaynak Ayrıntıları Görünümü - Çakışma Verileri
Kaynak Ayrıntıları görünümü, seçili bir kaynak üzerinde çekişmeler nedeniyle oluşan engelleme olaylarının bir zaman çizelgesi grafiğini sunar. Başka bir iş parçacığının kaynağa erişimi kilitlendiğinden, bir iş parçacığı yürütmeyi askıya almaya zorlandığında engelleyici bir olay oluşur.

 Bu görünüm her bir iş parçacığının yürütme zaman çizelgesini yatay bir çubuk olarak temsil eder ve her engelleme olayını iş parçacığı zaman çizelgesinde dikey bir çubuk olarak temsil eder. Gerektiğinde, bağımsız olayları görüntülemek için zaman çizelgesinin bir bölümünü büyütebilirsiniz. Olaya yol eden işlevlerin yürütme yolunu (çağrı yığını) görüntülemek için olay çubuğuna tıklayın. İşlevler **çağrı yığını** penceresinde görünür. Bir işlevin kaynak kodu kullanılabilir olduğunda, için arabirimindeki kaynak dosyayı düzenlemek için işlev adına tıklayabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="procedures"></a>Yordamlar

#### <a name="to-magnify-a-timeline-segment"></a>Bir zaman çizelgesi segmentini büyütmek için

- Fare işaretçisini zaman çizelgesinin bir alanının üzerine sürükleyin.

     Fare düğmesini serbest bırakırsanız, görünüm seçilen zaman segmentine yakınlaştırır. Segmenti daha fazla büyütmek için işlemi yineleyebilirsiniz. Zaman kaydırma çubuğundaki kaydırma kutusu, görünümde görüntülenen zaman diliminin göreli boyutunu temsil eder.

#### <a name="to-zoom-out-on-a-timeline"></a>Bir zaman çizelgesinde uzaklaştırmak için

- Aşağıdaki adımlardan birini uygulayın:

  - Önceki yakınlaştırma düzeyine dönmek için **uzaklaştır** ' ı tıklatın.

  - Görünümdeki tüm zaman çizelgesini göstermek için **Yakınlaştırma sıfırlaması** ' na tıklayın.

#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için

- Zaman çizelgesi grafiğinde olay çubuğuna tıklayın.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Çağrı yığınında bir işlevin kaynak kodunu görüntülemek veya düzenlemek için

- **Çağrı yığını** penceresinde, işlev adına tıklayın.

  İşlev kaynak kodu, geçerli projenin bir parçası olmalıdır.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Kaynak için çekişme olaylarının çağrı ağacını görüntülemek için

- Zaman çizelgesi grafiğinde **Toplam**' a tıklayın.

     Kaynak için çekişmeler görünümü görüntülenir. Daha fazla bilgi için bkz. [kaynak çekişmeleri görünümü](../profiling/resource-contentions-view-contention-data.md).

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Bir iş parçacığının tüm çekişme olaylarını görüntülemek için

- Zaman çizelgesi grafiğinde, iş parçacığının adına veya KIMLIğINE tıklayın.

     Seçili iş parçacığı için Iş parçacığı Ayrıntıları görünümü görüntülenir. Daha fazla bilgi için bkz. [Iş parçacığı Ayrıntıları görünümü](../profiling/thread-details-view-contention-data.md).
