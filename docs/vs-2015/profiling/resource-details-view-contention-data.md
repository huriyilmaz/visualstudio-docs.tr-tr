---
title: Kaynak Ayrıntıları görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 922edcd45dd42c8da5a9ec4dc8d3e8f450ceea09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823607"
---
# <a name="resource-details-view---contention-data"></a>Kaynak Ayrıntıları Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak Ayrıntıları görünümü, seçili bir kaynak üzerinde çekişmeler nedeniyle oluşan engelleme olaylarının bir zaman çizelgesi grafiğini sunar. Başka bir iş parçacığının kaynağa erişimi kilitlendiğinden, bir iş parçacığı yürütmeyi askıya almaya zorlandığında engelleyici bir olay oluşur.  
  
 Bu görünüm her bir iş parçacığının yürütme zaman çizelgesini yatay bir çubuk olarak temsil eder ve her engelleme olayını iş parçacığı zaman çizelgesinde dikey bir çubuk olarak temsil eder. Gerektiğinde, bağımsız olayları görüntülemek için zaman çizelgesinin bir bölümünü büyütebilirsiniz. Olaya yol eden işlevlerin yürütme yolunu (çağrı yığını) görüntülemek için olay çubuğuna tıklayın. İşlevler **çağrı yığını** penceresinde görünür. Bir işlevin kaynak kodu kullanılabilir olduğunda, için arabirimindeki kaynak dosyayı düzenlemek için işlev adına tıklayabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
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
  
     Kaynak için çekişmeler görünümü görüntülenir. Daha fazla bilgi için bkz. [kaynak çekişmeleri görünümü](../profiling/resource-contentions-view-contention-data.md)  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Bir iş parçacığının tüm çekişme olaylarını görüntülemek için  
  
- Zaman çizelgesi grafiğinde, iş parçacığının adına veya KIMLIğINE tıklayın.  
  
     Seçili iş parçacığı için Iş parçacığı Ayrıntıları görünümü görüntülenir. Daha fazla bilgi için bkz. [Iş parçacığı Ayrıntıları görünümü](../profiling/thread-details-view-contention-data.md).
