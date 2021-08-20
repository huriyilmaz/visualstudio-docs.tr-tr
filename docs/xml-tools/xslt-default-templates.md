---
title: XSLT Varsayılan Şablonları
description: Stil sayfalarında eşleşen bir belirtik şablon kuralı yokturken XSLT işleme sırasında kullanılan XSLT varsayılan şablonları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: b4c6fa558a11966045865bd4da079d3266ed61a5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135019"
---
# <a name="xslt-default-templates"></a>XSLT varsayılan şablonları

Stil sayfalarında eşleşen bir açık şablon kuralı olmayan XSLT işleme sırasında varsayılan şablon kullanılır. Yerleşik şablon kuralı olarak da adlandırılan varsayılan şablon, W3C XSLT 1.0 Önerisi'nin 5.8. bölümünde tanımlanır. Varsayılan şablon, bir düğümle eşleşen açık bir şablon kuralı olsa bile XSLT işlemcisinin bir düğümü işlemesini sağlar. Ancak, yerleşik şablon kuralı stil sayfalarında açıkça tanımlanmamış olduğundan, bu beklenmeyen veya kafa karıştırıcı XSLT dönüştürme sonuçlarına yol açabilir.

XSLT hata ayıklayıcısı artık XSLT varsayılan şablonlarının kodunu görüntüler. XSLT dönüşümünde adım adım ilerlerken, varsayılan bir şablon kullanılırsa hata ayıklayıcı varsayılan şablonu bir pencerede görüntüler. Bu, varsayılan şablonun kodunda adım adım ilerler ve yönergelerine kesme noktaları ayarlamaya olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
