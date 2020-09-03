---
title: 'Test alanı 6: silme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3ffe786b5bc5f6d0bb0233fbb431988e0145611d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155929"
---
# <a name="test-area-6-delete"></a>Test Alanı 6: Sil
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu kaynak denetimi eklentisi test alanı silme eylemlerini içerir.  
  
 Kaynak denetimi **Çözüm Gezgini**eylemleri silme işlemlerine yanıt verir.  
  
 Silinebilecek öğelerin listesi aşağıda verilmiştir:  
  
- Dosyalar  
  
- Klasörler  
  
- Project  
  
  Proje türüne bağlı olarak, projeyi kaldırma (dosyaları diskte bırakır) veya projeyi **silme** (diskteki dosyaları **kaldırma** ) seçeneğiniz olabilir. Her iki eylem de **Çözüm Gezgini**proje veya öğeyi kaldırır.  
  
## <a name="expected-behavior"></a>Beklenen davranış  
 Silme testi alanındaki test çalışmaları için beklenen davranış:  
  
- Silinen öğe artık **Çözüm Gezgini**içinde görünür değil.  
  
- Silinen projenin veya öğenin üst öğesi gerektiğinde kullanıma alındı (muhtemelen bir istem ile.)  
  
- Kullanıma alınmış veya eklenen bir öğeyi sildikten sonra, **bekleyen checkins** penceresinde görüntülenmez.  
  
- Öğe, silme işleminden sonra bile kaynak denetim deposu içinde hala var ve el ile temizlenmelidir.  
  
|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|  
|------------|----------------|--------------------------------|  
|İstemci projesini silme|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. tüm projeyi çözümden kaldır|Ortak beklenen davranış.|  
|Boş bir dosyayı Sil|1. bir istemci projesi oluşturun.<br />2. projeye sıfır baytlık bir dosya ekleyin.<br />3. çözümü kaynak denetimine ekleyin.<br />4. dosyayı seçin, silin.|Ortak beklenen davranış.|  
|Tek dosya içeren bir klasörü silme|1. tek proje çözümü oluşturun.<br />2. bir klasör ekleyin.<br />3. klasöre bir dosya ekleyin.<br />4. çözümü kaynak denetimine ekleyin.<br />5. istemden kaçınmak için projeye göz atın.<br />6. klasörü silin.|Ortak beklenen davranış.|  
|Dosya sistemi Web projesini silme|1. bir dosya sistemi Web projesi oluşturun (bir UNC yolu belirtmek için Gözatılacak düğmeyi kullanın).<br />2. çözümü kaynak denetimine ekleyin.<br />3. tüm projeyi çözümden kaldırın.<br />4. yerel Web projesi için 1 ile 3 arasındaki adımları yineleyin (kod üzerinden farklı yollar alıştırmaları, ancak aynı dış arabirime ve davranışa sahiptir).|Ortak beklenen davranış.|  
|Dosya sistemi Web projesinden dosya silme|1. bir dosya sistemi Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. bir dosyayı projeden silin.<br />4. yerel Web projesi için 1 ile 3 arasındaki adımları yineleyin (kod üzerinden farklı yollar alıştırmaları, ancak aynı dış arabirime ve davranışa sahiptir).|Ortak beklenen davranış.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
