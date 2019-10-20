---
title: XSLT Varsayılan Şablonları
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81a764aa45eb74ba110d8b3b5965ede1e62bdadd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607775"
---
# <a name="xslt-default-templates"></a>XSLT varsayılan şablonları

Stil sayfasında eşleşen açık şablon kuralı olmadığında XSLT işleme sırasında varsayılan bir şablon kullanılır. Ayrıca, yerleşik şablon kuralı olarak da adlandırılan varsayılan şablon, W3C XSLT 1,0 önerisi 5,8 bölümünde tanımlanmıştır. Varsayılan şablon, XSLT işlemcisinin bir düğümü işlemesini sağlar, bununla eşleşen açık bir şablon kuralı olmasa da. Ancak, yerleşik şablon kuralı stil sayfasında açıkça tanımlanmadığı için, bu durum beklenmedik veya kafa karıştırıcı XSLT dönüştürme sonuçlarına yol açabilir.

XSLT hata ayıklayıcısı şimdi XSLT varsayılan şablonlarının kodunu görüntüler. Bir XSLT dönüşümünde, varsayılan bir şablon kullanılıyorsa, hata ayıklayıcı varsayılan şablonu bir pencerede görüntüler. Bu, varsayılan şablonun kodunda ilerlemenize ve yönergeleri üzerinde kesme noktaları ayarlamanıza olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)