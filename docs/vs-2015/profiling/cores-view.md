---
title: Çekirdekler görünümü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 869980fe7bbb773d566dffd38088b003e3a97a3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145648"
---
# <a name="cores-view"></a>Çekirdekler Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekirdekler görünümü iş parçacığı yürütmenin mantıksal işlemci çekirdekleri ile nasıl eşleştirildiğini gösterir. Sunucu uygulamaları yazıyorsanız, bu görünüm iş parçacığı benzeşimini veya iş parçacığı havuzu yönetimini kullanarak önbellek performansını iyileştirmenize yardımcı olabilir. Ayrıca, iş parçacığı benzeşimi kullanımı, platformlar arası geçiş sorununu etkileyebilecek durumları incelemenize yardımcı olabilir. Çekirdekler görünümü iki bölümden oluşur, bir grafik ve bir gösterge.  
  
 Grafik, x eksenindeki y ekseni ve saat üzerindeki mantıksal çekirdekleri gösterir. Grafikteki her iş parçacığının, kendi hareketini zaman içindeki çekirdekler arasında izleyebilmeniz için benzersiz bir rengi vardır. Bu grafikteki iş parçacıklarını gösterge alanında seçerek filtreleyebilirsiniz.  
  
 Gösterge alanının grafikteki her renk için bir girişi vardır. Her giriş iş parçacığı rengini ve adını, platformlar arası bağlam anahtarlarını, toplam bağlam anahtarı sayısını ve çekirdekler arası bağlam anahtarlarının yüzdesini gösterir. Gösterge, azalan sırada çapraz çekirdek bağlam anahtarları sayısına göre sıralanır. Yalnızca görüntülenen zaman aralığı boyunca yürütülen iş parçacıklarını listeler.  Yakınlaştırma veya kaydırma yaparsanız liste güncellenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)   
 [Kullanım görünümü](../profiling/utilization-view.md)   
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
