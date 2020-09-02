---
title: Kaynak çakışması veri değerlerini anlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5983396924f38c31b6dafcd42b762042e1880e8d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145430"
---
# <a name="understanding-resource-contention-data-values"></a>Kaynak Çakışması Veri Değerlerini Anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak Çekişmesi profili oluşturma, bir uygulamadaki rekabet iş parçacıklarının paylaşılan bir kaynağa erişim için beklemeye zorlanması durumunda ayrıntılı çağrı yığını bilgilerini toplar.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Kaynak çekişmeleri, modüller, işlevler, kaynak kodu satırları ve bekleme gerçekleştiği yönergelerin bir kaynağı beklerken harcanan toplam çekişme sayısını ve toplam süreyi görüntüler.  
  
- Kapsamlı değerler, bir işlevi kaynak çekişmeleri ve işlevin bekleme toplam süresi tarafından beklemeye zorlayan toplam çekişmelerin sayısını görüntüler.  İşlev tarafından çağrılan alt işlevlerin neden olduğu çekişmeler, kapsamlı değerlere dahildir.  
  
- Dışlamalı değerler yalnızca bir işlevin beklemesini ve işlevin gövdesinde kodun neden olduğunu zorlayan çekişmelerin sayısını görüntüler. Alt işlevlerin neden olduğu çekişmeler dahil değildir. İşlevin dışlamalı zamanı, yalnızca işlev gövdesinde deyimlerin neden olduğu bekleme sürelerini de içerir.  
  
  Kaynak çekişme raporu görünümleri Ayrıca zaman içinde bireysel çekişme olaylarını gösteren zaman çizelgesi grafiklerini içerir ve belirli bir olayı oluşturan çağrı yığınlarını gösterir. Daha fazla bilgi için aşağıdaki konulardan birine bakın:  
  
- [İş Parçacığı Ayrıntıları Görünümü](../profiling/thread-details-view-contention-data.md)  
  
- [Kaynak Ayrıntıları Görünümü](../profiling/resource-details-view-contention-data.md)  
  
  Eşzamanlılık profili oluşturma işleminin ikinci modu hakkında daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md).
