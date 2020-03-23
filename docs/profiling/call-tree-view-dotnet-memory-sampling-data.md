---
title: Çağrı Ağacı Görünümü - .NET Bellek Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 76ea78f37cbc8c5e2b6df900aa0e3f320346300a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779772"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Çağrı Ağacı görünümü - .NET bellek örnekleme verileri
Çağrı Ağacı görünümü, profilli uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamaya veya bileşene giriş noktasıdır. Her işlev düğümü, adlandırdığı tüm işlevleri ve bu işlev çağrıları yla ilgili .NET bellek ayırma verilerini listeler.

 Çağrı Ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örnekleri içindir. Yüzde değerleri, işlev örneği değeri profil oluşturma çalışmasındaki ayırmaların toplam sayısı veya boyutuyla karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme sıcak yolunu vurgulayın
 Çağrı Ağacı görünümü, en büyük veya en çok bellek nesnesini oluşturan işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu görüntülemek için, işlemi veya işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın.

## <a name="set-the-call-tree-root-node"></a>Çağrı Ağacı kök düğümünü ayarlama
 Profil oluşturma çalışmasındaki her işlem kök düğüm olarak görüntülenir. Çağrı Ağacı görünümünün başlangıç düğümünü farklı bir düğüme ayarlamak için, başlangıç düğümü olarak ayarlamak istediğiniz düğümü sağ tıklatın ve **Root'u ayarla'yı**seçin.

 Kök düğümünü ayarladığınızda, seçili düğümün alt ağacı dışında görünümdeki diğer tüm girişleri ortadan kaldırırsınız. Kök düğümünü görüntülediğiniz düğüme geri sıfırlayabilirsiniz; Çağrı Ağacı Görünümü penceresinde sağ tıklatın ve **Root'u Sıfırla'yı**seçin.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Fonksiyon Adı**|İşlevin tam nitelikli adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Düzey**|Çağrı ağacındaki işlevin derinliği.|
|**Kapsayıcı Tahsisatlar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsayıcı Tahsisler %**|Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi, bu işlevin kapsayıcı ayırmalarıydı.|
|**Özel Tahsisler**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesnelerin sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içermez.|
|**Özel Tahsisatlar %**|Çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin özel ayırmaları olan profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Dahil Baytlar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan bellekteki bayt sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Dahil Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin kapsayıcı ayırmaları olan tüm bellek baytlarının yüzdesi.|
|**Özel Baytlar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan bellekteki bayt sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içermez.|
|**Özel Bayt %**|Profil oluşturma çalışmasında ayrılan ve bu işlevin özel ayırmaları olan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çağrı Ağacı görünümü - enstrümantasyon](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-sampling-data.md)
- [Çağrı Ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)
