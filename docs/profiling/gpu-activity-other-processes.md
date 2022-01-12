---
title: GPU Etkinliği (Diğer İşlemler) | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi'nin İş Parçacıkları görünümünde GPU Etkinliği (Diğer İşlemler) segmentleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c050e190a1b98ef1cc143c8181e4e9ce9a6bd12b
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806007"
---
# <a name="gpu-activity-other-processes"></a>GPU Etkinliği (Diğer İşlemler)
Eşzamanlılık Görselleştiricisi'nin İş Parçacıkları görünümündeki GPU Etkinliği **(Diğer İşlemler)** segmentleri, GPU'nun sistem üzerinde diğer işlemler adına istekleri işleme zamanlarını temsil eder. Bu istekler GPU'ya doğrudan bellek erişimi (DMA) paketleri olarak gönderilir.  Bir kesimin uzunluğu, paketin GPU tarafından işlenme süresini temsil eder.

 Bu tür bir segmenti seçerek Geçerli **sekmesindeki rapor,** işlenen paketle ilgili bilgileri görüntüler.  Bilgiler, paketin DirectX altyapısıyla ilişkili donanım kuyruğunda beklediği süre, paketin gönderilen işlemi ve paketin iş için gerekli olduğu zamanı içerir.