---
title: Çağrı ağacı görünümü-.NET bellek Izleme verileri | Microsoft Docs
description: Performans Gezgini .NET bellek ayırma izleme verilerinin çağrı ağacı görünümü hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f417c5601e812ee9001db9ed0ae4bb4bcb1d0f0e53a02e30d6e57f2abb7eb4a3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427216"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Çağrı ağacı görünümü-.NET bellek izleme verileri
İzleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri ve işlevin .NET belleğini ve zamanlama verilerini listeler.

 Çağrı ağacı görünümündeki değerler, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerine yöneliktir. Yüzde değerleri, işlev örneği değeri, profil oluşturma çalıştırmasında toplam sayı veya ayırma boyutuyla karşılaştırılarak hesaplanır.

## <a name="highlight-the-execution-hot-path"></a>Yürütme etkin yolunu Vurgula
 Çağrı ağacı görünümü, en büyük veya en fazla bellek nesnelerini oluşturan işlemin veya işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu göstermek için, işlem veya işleve sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın.

## <a name="set-the-call-tree-root-node"></a>Çağrı ağacı kök düğümünü ayarla
 Profil oluşturma çalıştırmasında her işlem kök düğüm olarak görüntülenir. Başlangıç düğümü olarak ayarlamak istediğiniz düğüme sağ tıklayıp ardından **kökü ayarla**' yı seçerek çağrı ağacı görünümünün başlangıç düğümünü ayarlayabilirsiniz.

 Kök düğümü ayarladığınızda, seçili düğümün alt ağacı hariç diğer tüm girişleri görünümden ortadan kaldırabilirsiniz. Kök düğümü, görüntülemekte olduğunuz düğüme geri sıfırlayabilirsiniz; Çağrı Ağacı Görünümü penceresine sağ tıklayın ve **kökü Sıfırla**' yı seçin.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**İşlev adı**|İşlevin adı.|
|**İşlev adresi**|İşlevin adresi.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Çağrı Sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|İşleme atanan ad.|
|**Zaman Dışlamalı Araştırma ek yükü**|Bu işlev için, izleme nedeniyle oluşan zaman ek yükü. Araştırma ek yükü tüm özel zamanlarda çıkarıldı.|
|**Zaman kapsamlı araştırma ek yükü**|Bu işlev için zaman yükü ve alt işlevleri, izleme nedeniyle oluşur. Araştırma ek yükü tüm kapsamlı bir şekilde çıkarıldı.|
|**Tür**|İşlevin bağlamı:<br /><br /> -   **0** -geçerli işlev<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kök Işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|

## <a name="net-memory-values"></a>.NET bellek değerleri
 Bir işlevin dahil .NET bellek değerleri, işlev tarafından çağrılan işlevlerin ve işlevin tarafından oluşturulan nesnelerin sayısını (ayırmalar) ve boyutunu (bayt) belirtir.

 Dışlamalı bellek değerleri işlev gövdesinde oluşturulan ve işlev tarafından çağrılan işlevlere göre değil, nesne sayısını ve boyutunu belirtir.

|Sütun|Açıklama|
|------------|-----------------|
|**Kapsamlı ayırmalar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı, alt işlevler tarafından yapılan ayırmaları içerir.|
|**Kapsamlı ayırmalar%**|Profil oluşturma çalıştırmasında oluşturulan, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin dahil tahsisatlarından oluşan tüm nesnelerin yüzdesi.|
|**Dışlamalı ayırmalar**|Çağrı ağacındaki üst işlev tarafından çağrılan bu işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı alt işlevler tarafından yapılan ayırmaları içermez.|
|**Dışlamalı ayırmalar%**|Profil oluşturma çalıştırmasında oluşturulan, çağrı ağacındaki üst işlev tarafından çağrılan işlev örneklerinin özel ayırmaları olan tüm nesnelerin yüzdesi.|

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler
 Geçen kapsamlı değerler, bir işlevin çağrı yığınında olduğu süreyi belirtir. Süre, işlev tarafından çağrılan işlevlerde ve bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılar için harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen kapsamlı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrıların toplam geçen kapsamlı süresi.|
|**Geçen kapsamlı süre yüzdesi**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işlevin toplam geçen iç zaman içinde harcanan toplam geçen kapsamlı süre yüzdesi.|
|**Ortalama geçen kapsamlı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının ortalama geçen kapsamlı süresi.|
|**Geçen maksimum kapsamlı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının geçen en uzun kapsamlı süresi.|
|**Geçen minimum kapsamlı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının geçen en az kapsamlı süre.|

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler
 Geçen dışlamalı değerler, bir işlevin çağrı yığınının en üstünde doğrudan yürütüldüğü süreyi belirtir. Bu süre, işletim sistemine çağrı sırasında bağlam anahtarları ve giriş/çıkış işlemleri gibi zaman alır. Ancak, zaman, işlev tarafından çağrılan işlevlerde harcanan zamanı içermez.

|Sütun|Açıklama|
|------------|-----------------|
|**Geçen dışlamalı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrıların toplam dışlamalı süresi geçti.|
|**Geçen dışlamalı süre yüzdesi**|Bu işlevin çağrı ağacındaki üst işlev tarafından çağrıldığında geçen toplam dışlamalı süre içinde harcanan toplam çalışma süresi geçen özel süre yüzdesi.|
|**Geçen ortalama dışlamalı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının geçen ortalama dışlamalı süresi.|
|**Geçen maksimum dışlamalı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının geçen maksimum dışlamalı süresi.|
|**Geçen en düşük dışlamalı süre**|Çağrı ağacındaki üst işlev tarafından çağrıldığında, bu işleve yapılan çağrının en az geçen dışlamalı süresi.|

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler
 Uygulama kapsamlı değerleri bir işlevin çağrı yığınında olduğu süreyi belirtir. Bu süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı dahil değildir. Bu süre, işlev tarafından çağrılan alt işlevlerde harcanan zamanı içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulama Dahil Saati**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan tüm çağrıların toplam uygulama dahil süresi.|
|**Uygulama Dahil Saati %**|Çağrı ağacında üst işlev tarafından çağrıldıken bu işlevin toplam uygulama dahil süresi içinde harcanan profil oluşturma çalıştırması için geçen toplam kapsayıcı sürenin yüzdesi.|
|**Ortalama Uygulama Dahil Süresi**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan çağrının ortalama uygulama dahil süresi.|
|**En Fazla Uygulama Dahil Süresi**|Çağrı ağacında üst işlev tarafından çağrıldıken bu işleve yapılan çağrının dahil olduğu maksimum uygulama süresi.|
|**En Az Uygulama Dahil Süresi**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan çağrının en düşük uygulama dahil süresi.|

## <a name="application-exclusive-values"></a>Uygulamaya özel değerler
 Uygulamaya özel değerler, işlev tarafından çağrılan alt işlevlerde harcanan süre hariç olmak üzere işlevde harcanan zamanı gösterir. Zaman ayrıca bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrıları da dışlar.

|Sütun|Açıklama|
|------------|-----------------|
|**Uygulamaya Özel Zaman**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işleve yapılan tüm çağrıların uygulamaya özel toplam süresi.|
|**Uygulamaya Özel Saat %**|Çağrı ağacında üst işlev tarafından çağrıldıklarında bu işlevin toplam uygulama için özel zaman harcaması yapılan profil oluşturma çalıştırması için geçen toplam özel sürenin yüzdesi.|
|**Ortalama Uygulama Özel Süresi**|Bu işleve yapılan çağrının çağrı ağacında üst işlev tarafından çağrılmış olduğu ortalama uygulama özel süresi.|
|**En Fazla Uygulama Özel Süresi**|Bu işleve yapılan çağrının çağrı ağacında üst işlev tarafından çağrılmış olduğu en uzun uygulama özel süresi.|
|**En Az Uygulama Için Özel Süre**|Bu işleve yapılan çağrının çağrı ağacında üst işlev tarafından çağrılmış olduğu en düşük uygulama özel süresi.|
