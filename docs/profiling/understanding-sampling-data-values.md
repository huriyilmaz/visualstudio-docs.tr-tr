---
title: Örnekleme veri değerlerini anlama | Microsoft Docs
description: Visual Profil Oluşturma Araçları Studio 'nun örnekleme profili oluşturma yönteminin, küme aralıklarında bilgisayar işlemcisini nasıl kestireceğinizi ve işlev çağrı yığınını topladığını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 40902746e1dd1a4c68c9e1aa54ed4e72030a8fff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886034"
---
# <a name="understand-sampling-data-values"></a>Örnekleme veri değerlerini anlama

Visual Profil Oluşturma Araçları Studio 'nun *örnekleme* profili oluşturma yöntemi, bilgisayar işlemcisini ayarlanan aralıklarla keser ve işlev çağrı yığınını toplar. *Çağrı yığını* , işlemcide yürütülen işlevlerle ilgili bilgileri depolayan dinamik bir yapıdır.

Profil Oluşturucu analizi, işlemcinin hedef işlemde kod yürütmediğini belirler. İşlemci hedef işlemde kod yürütülemiyor, örnek atılır.

İşlemci hedef kodu yürütüp, profil oluşturucu çağrı yığınında her bir işlevin örnek sayılarını arttırır. Örneğin alındığı sırada, çağrı yığınında yalnızca bir işlev şu anda kodu yürütüyor. Yığındaki diğer işlevler, alt öğelerinin dönebilmeleri için bekleyen işlev çağrılarının hiyerarşisinde üstlerdir.

Örnek olay için, profil oluşturucu Şu anda yönergelerini yürüten işlevin *dışlamalı* örnek sayısını artırır. Dışlamalı bir örnek aynı zamanda işlevin toplam (*kapsamlı*) örneklerinin bir parçası olduğundan, şu anda etkin olan işlevin kapsamlı örnek sayısı da artırılır.

 Profiler, Çağrı yığınındaki diğer tüm işlevlerin dahil edilen örnek sayısını artırır.

## <a name="inclusive-samples"></a>Kapsamlı örnekler

Hedef işlevin yürütülmesi sırasında toplanan örneklerin toplam sayısı.

Bu, işlev kodunun doğrudan yürütülmesi sırasında toplanan örnekleri ve hedef işlev tarafından çağrılan alt işlevlerin yürütülmesi sırasında toplanan örnekleri içerir.

## <a name="exclusive-samples"></a>Dışlamalı örnekler

Hedef işlevin yönergelerinin doğrudan yürütülmesi sırasında toplanan örneklerin sayısı.

Dışlamalı örnekler, hedef işlev tarafından çağrılan işlevlerin yürütülmesi sırasında toplanan örnekleri içermez.

## <a name="inclusive-percent"></a>Kapsamlı yüzde

Profil oluşturma çalıştırmasında, işlevin veya veri aralığının kapsamlı örnekleri olan toplam kapsamlı örnek sayısının yüzdesi.

## <a name="exclusive-percent"></a>Dışlamalı yüzde

Profil oluşturma çalıştırmasında, işlevin veya veri aralığının özel örnekleri olan toplam dışlamalı örnek sayısının yüzdesi.

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: koleksiyon Yöntemleri Seçme](../profiling/how-to-choose-collection-methods.md) 
 [Performans araçları verilerini çözümleme](../profiling/analyzing-performance-tools-data.md)
