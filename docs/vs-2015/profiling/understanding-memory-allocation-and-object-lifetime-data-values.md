---
title: Bellek ayırmayı ve nesne ömrü veri değerlerini anlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 816f750148cc30de86fc116f80f64b218b4699d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145452"
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Bellek Ayırma ve Nesne Yaşam Verisi Değerlerini Anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları *.net bellek ayırma* profili oluşturma yöntemi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir ayırma içinde oluşturulan veya atık toplamada yok edilen nesnelerin boyutu ve sayısı hakkında bilgi ve olay oluştuğunda işlev *çağrı yığını* hakkında ek bilgiler toplar. *Çağrı yığını* , işlemcide yürütülen işlevlerle ilgili bilgileri depolayan dinamik bir yapıdır.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Bellek profili Oluşturucu, profili oluşturulmuş bir uygulamadaki .NET Framework nesnesinin her ayırmada bilgisayar işlemcisini keser. Nesne ömür verileri de toplandığında, Profil Oluşturucu .NET Framework her bir çöp toplama işleminden sonra işlemciyi keser. Veriler, her bir profili oluşturulan işlev ve her nesne türü için toplanır.  
  
## <a name="allocation-data"></a>Ayırma verileri  
 Bir. Memory olayı gerçekleştiğinde, ayrılan veya yok edilen bellek nesnelerinin toplam sayısı ve boyutları artırılır.  
  
 Bir. bellek ayırma olayı gerçekleştiğinde, profil oluşturucu çağrı yığınında her bir işlevin örnek sayılarını arttırır. Veriler toplandığında, çağrı yığınında yalnızca bir işlev şu anda kendi işlev gövdesinde yürütülen kodu yürütüyor. Yığındaki diğer işlevler, döndürmek için çağırdıkları işlevleri bekleyen işlev çağrılarının hiyerarşisinde üstlerdir.  
  
- Ayırma olayı için, profil oluşturucu Şu anda yönergelerini yürüten işlevin *dışlamalı* örnek sayısını artırır. Dışlamalı bir örnek aynı zamanda işlevin toplam (*kapsamlı*) örneklerinin bir parçası olduğundan, şu anda etkin olan işlevin kapsamlı örnek sayısı da artırılır.  
  
- Profiler, Çağrı yığınındaki diğer tüm işlevlerin dahil edilen örnek sayısını artırır.  
  
## <a name="lifetime-data"></a>Ömür verileri  
 .NET Framework atık toplayıcısı, uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir. Atık toplayıcının performansını optimize etmek için, yönetilen yığın üç nesle ayrılır: 0, 1 ve 2. Çalışma zamanı atık toplayıcısı yeni nesneleri nesil 0 ' da depolar. Tutulan koleksiyonlar, 1. ve 2. nesil içinde yükseltilerek saklanır.  
  
 Tüm nesnelerin neslini ayırmayı kaldırarak çöp toplayıcı geri kazanır belleği. Profili oluşturulan uygulamanın oluşturduğu nesneler için, nesne ömrü görünümü, nesnelerin sayısını ve boyutunu, geri kazanıladıklarında oluşturmayı görüntüler.
