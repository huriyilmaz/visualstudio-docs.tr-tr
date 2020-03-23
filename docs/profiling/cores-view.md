---
title: Çekirdek Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b26b913a42a563e0226ff2697b947684dfec53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553064"
---
# <a name="cores-view"></a>Çekirdekler Görünümü
**Çekirdek Görünümü,** iş parçacığı yürütmenin mantıksal işlemci çekirdeklerine nasıl eşlandığını gösterir (eşzamanlılık görselleştiricisini başlatmak için**Eşzamanlılık Görselleştiricisini** **Çözümle'yi** > seçin). Sunucu uygulamaları yazıyorsanız, bu görünüm iş parçacığı afiyeti veya iş parçacığı havuzu yönetimini kullanarak önbellek performansını en iyi duruma getirmenize yardımcı olabilir. Ayrıca, iş parçacığı yakınlığı nın kullanımının çekirdekler arası geçiş sorununu daha da kötüleştirdiği durumları incelemenize de yardımcı olabilir. Cores View iki bölümden, bir grafik ve bir göstergeden oluşur.

 Grafik, y ekseninde mantıksal çekirdekleri ve x ekseninde zamanı gösterir. Grafikteki her iş parçacığı, zaman içinde çekirdekler üzerindeki hareketini izleyebilmeniz için benzersiz bir renge sahiptir. Bu grafikteki iş parçacıklarını gösterge alanında seçerek filtreleyebilirsiniz.

 Gösterge alanı, grafikteki her renk için bir girişe sahiptir. Her giriş iş parçacığı rengini ve adını, çekirdekler arası bağlam anahtarlarının sayısını, toplam bağlam anahtarlarını ve çekirdekleri geçen bağlam anahtarlarının yüzdesini gösterir. Gösterge, azalan sırada, çapraz çekirdek bağlam anahtarlarının sayısına göre sıralanır. Yalnızca görüntülenen zaman aralığında çalıştırılan iş parçacıklarını listeler.  Yakınlaştırırsanız veya kaydırdığınızda liste güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)
- [Kullanım Görünümü](../profiling/utilization-view.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)