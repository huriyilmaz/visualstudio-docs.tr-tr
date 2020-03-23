---
title: Örnekleme Veri Değerlerini Anlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 289f92deaceca32a44249ed77c17187743a34fa4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778056"
---
# <a name="understand-sampling-data-values"></a>Örnekleme veri değerlerini anlama

Visual Studio Profil Oluşturma Araçları'nın *örnekleme* profil oluşturma yöntemi, bilgisayar işlemcisini belirli aralıklarla keser ve işlev çağrı yığınını toplar. *Çağrı yığını,* işlemcide çalıştırılabilen işlevler hakkında bilgi depolayan dinamik bir yapıdır.

Profil oluşturucu çözümlemesi, işlemcinin hedef işlemde kod yürütüp yürütmediğini belirler. İşlemci hedef işlemde kodu yürütmiyorsa, örnek atılır.

İşlemci hedef kodu çalıştırıyorsa, profiloluşturucu çağrı yığınındaki her işlev için örnek sayar. Örnek alındığı sırada, arama yığınındaki yalnızca bir işlev şu anda kodu yürütmüş durumdadır. Yığındaki diğer işlevler, çocuklarının geri dönmesini bekleyen işlev çağrıları hiyerarşisindeki ebeveynlerdir.

Örnek olay için profiloluşturucu, yönergelerini yürüten işlevin *özel* örnek sayısını artar. Özel bir örnek de işlevin toplam *(kapsayıcı)* örneklerinin bir parçası olduğundan, şu anda etkin olan işlevin kapsayıcı örnek sayısı da artar.

 Profil oluşturucu, çağrı yığınındaki diğer tüm işlevlerin dahil örnek sayısını artımlar.

## <a name="inclusive-samples"></a>Dahil numuneler

Hedef işlevin yürütülmesi sırasında toplanan toplam örnek sayısı.

Bu, işlev kodunun doğrudan yürütülmesi sırasında toplanan örnekleri ve hedef işlev tarafından çağrılan alt işlevlerin yürütülmesi sırasında toplanan örnekleri içerir.

## <a name="exclusive-samples"></a>Özel numuneler

Hedef işlevin yönergelerinin doğrudan yürütülmesi sırasında toplanan örnek sayısı.

Özel örnekler, hedef işlev tarafından çağrılan işlevlerin yürütülmesi sırasında toplanan örnekleri içermez.

## <a name="inclusive-percent"></a>Dahil yüzdesi

Profil oluşturma çalışmasındaki toplam dahil örnek sayısının yüzdesi, işlev in veya veri aralığının kapsayıcı örnekleridir.

## <a name="exclusive-percent"></a>Özel yüzde

Profil oluşturma çalışmasındaki toplam özel örnek sayısının yüzdesi, işlevin veya veri aralığının özel örnekleridir.

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: Toplama yöntemlerini](../profiling/how-to-choose-collection-methods.md)
seçin[Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
