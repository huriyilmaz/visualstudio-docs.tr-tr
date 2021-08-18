---
title: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme
description: Varsayılan olarak, ek yükü azaltmak için diğer işlevleri çağırmadan kısa işlevler ölçüme dahil değildir. Bunları dahil etmeyi veya dışlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd541574efa9be7b58774d77aead729ceab92231
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141863"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Nasıl yapılır: Kısa işlevleri izlemeden hariç tutma veya izlemeye dahil etme
Varsayılan olarak, Profil oluşturma araçları küçük *işlevleri ölçümden* dışlar. Küçük işlevler, işlev çağrısı yapmayan kısa işlevlerdir. Bu küçük işlevleri dışlama, daha az ölçüm ek yükü ve dolayısıyla gelişmiş ölçüm hızı sağlar. Küçük işlevlerin dışlanması, performans profili oluşturma veri dosyasını da azaltır (.*vsp*) boyutu ve analiz için gereken süre. Küçük işlevler dışlanmışsa, küçük işlevlerde harcanan süre, üst işlevlerin özel ve kapsayıcı zamanlarına göre sayılır. Aşağıdaki yordamda açıklandığı gibi küçük işlevler hariç tutularak veya ölçümlere dahil olabilir.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Kısa işlevleri ölçümden dışlamak veya dahil etmek için

1. Bu **Performans Gezgini** Performans **Oturumu'u seçin** ve ardından özellikler'e sağ tıklayın ve öğesini **seçin.**

     **Özellik Sayfaları** iletişim kutusu görüntülenir.

2. Özellik **Sayfaları'nın** altında, Ölçüm **özellikleri'ne** tıklayın.

3. Kısa işlevleri ölçümden dışlamak için Kısa işlevleri **Ölçümler'den hariç tut'ı seçin.** Bu varsayılan ayardır.

     -veya-

     Ölçümlere kısa işlevleri dahil etmek için Kısa işlevleri **Ölçümler'den hariç tut'a net bir şekilde bakabilirsiniz.**

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
