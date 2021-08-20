---
title: Örnekleme Veri Değerlerini Anlama | Microsoft Docs
description: Kümenin örnekleme profil oluşturma yönteminin, Visual Studio Profil Oluşturma Araçları aralıklarla bilgisayar işlemcisini kesintiye uğratmasını ve işlev çağrı yığınını toplamasını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 04ff212cce0de1faa07cd31e115346de98e44f0e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140992"
---
# <a name="understand-sampling-data-values"></a>Örnekleme veri değerlerini anlama

*Uygulamanın* örnekleme profil oluşturma Visual Studio Profil Oluşturma Araçları, bilgisayar işlemcisini belirli aralıklarla kesintiye uğratması ve işlev çağrı yığınını toplaması. Çağrı *yığını,* işlemcide yürütülen işlevlerle ilgili bilgileri depolar dinamik bir yapıdır.

Profil oluşturma analizi, işlemcinin hedef işlemde kod yürüterek yürütmesinin gerekip gerek olmadığını belirler. İşlemci hedef işlemde kod çalıştırmıyorsa örnek atılır.

İşlemci hedef kodu yürütüyorsa, profilleyici çağrı yığınındaki her işlev için örnek sayıları artırır. Örnek alınırken, çağrı yığınında şu anda yalnızca bir işlev kod yürütür. Yığında yer alan diğer işlevler, işlev çağrılarının hiyerarşisinde yer alan ve çocukların geri dönmesini bekleyen üst işlevlerdir.

Örnek olay için, profilleyici şu anda *yönergelerini* yürüten işlevin özel örnek sayısını artırır. Özel bir örnek de işlevin toplam *(* dahil ) örneklerinin bir parçası olduğundan, o anda etkin olan işlevin kapsayıcı örnek sayısı da artırılır.

 Profilleyici, çağrı yığınında yer alan diğer tüm işlevlerin kapsayıcı örnek sayısını artırır.

## <a name="inclusive-samples"></a>Kapsayıcı örnekler

Hedef işlevin yürütülmesi sırasında toplanan toplam örnek sayısı.

Bu, işlev kodunun doğrudan yürütülmesi sırasında toplanan örnekleri ve hedef işlev tarafından çağrılan alt işlevlerin yürütülmesi sırasında toplanan örnekleri içerir.

## <a name="exclusive-samples"></a>Özel örnekler

Hedef işlevin yönergelerinin doğrudan yürütülmesi sırasında toplanan örnek sayısı.

Özel örnekler, hedef işlev tarafından çağrılan işlevlerin yürütülmesi sırasında toplanan örnekleri dahil değildir.

## <a name="inclusive-percent"></a>Kapsayıcı yüzde

Profil oluşturma çalıştırması içinde işlev veya veri aralığının kapsayıcı örnekleri olan toplam kapsayıcı örnek sayısının yüzdesi.

## <a name="exclusive-percent"></a>Özel yüzde

Profil oluşturma çalıştırması içinde işlev veya veri aralığının özel örnekleri olan toplam özel örnek sayısının yüzdesi.

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md) 
 [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
