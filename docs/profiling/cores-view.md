---
title: Çekirdekler görünümü | Microsoft Docs
description: Çekirdek görünümü tarafından sunulan bilgiler hakkında bilgi edinin. Önbellek performansını iyileştirmek için iş parçacığı benzeşimini veya iş parçacığı havuzu yönetimini kullanmanıza yardımcı olabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3caa4401e706aa72e99a82fcb244538f51d5d7b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039325"
---
# <a name="cores-view"></a>Çekirdekler Görünümü
**Çekirdekler görünümü** iş parçacığı yürütmenin mantıksal işlemci çekirdekleri ile nasıl eşlenildiğini gösterir (   >  eşzamanlılık Görselleştiriciyi başlatmak için **eşzamanlılık görselleştirmesini** Çözümle ' yi seçin). Sunucu uygulamaları yazıyorsanız, bu görünüm iş parçacığı benzeşimini veya iş parçacığı havuzu yönetimini kullanarak önbellek performansını iyileştirmenize yardımcı olabilir. Ayrıca, iş parçacığı benzeşimi kullanımı, platformlar arası geçiş sorununu etkileyebilecek durumları incelemenize yardımcı olabilir. Çekirdekler görünümü iki bölümden oluşur, bir grafik ve bir gösterge.

 Grafik, x eksenindeki y ekseni ve saat üzerindeki mantıksal çekirdekleri gösterir. Grafikteki her iş parçacığının, kendi hareketini zaman içindeki çekirdekler arasında izleyebilmeniz için benzersiz bir rengi vardır. Bu grafikteki iş parçacıklarını gösterge alanında seçerek filtreleyebilirsiniz.

 Gösterge alanının grafikteki her renk için bir girişi vardır. Her giriş iş parçacığı rengini ve adını, platformlar arası bağlam anahtarlarını, toplam bağlam anahtarı sayısını ve çekirdekler arası bağlam anahtarlarının yüzdesini gösterir. Gösterge, azalan sırada çapraz çekirdek bağlam anahtarları sayısına göre sıralanır. Yalnızca görüntülenen zaman aralığı boyunca yürütülen iş parçacıklarını listeler.  Yakınlaştırma veya kaydırma yaparsanız liste güncellenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)
- [Kullanım Görünümü](../profiling/utilization-view.md)
- [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)