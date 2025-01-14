---
title: Sıralama, filtreleme ve gruplama
description: XML Şema Gezgini araç çubuğundaki Sıralama, Filtreleme ve Gruplama Seçenekleri menüsünden kullanılabilen seçenekler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: f317ea59fd7f3318669a71d4480c5b53a182b327
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726037"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sıralama, filtreleme ve gruplama (XML Şema Gezgini)

Bu konuda, XML Şema Gezgini araç çubuğundaki **Sıralama,** Filtreleme ve Gruplama Seçenekleri menüsü aracılığıyla kullanılabilen **seçenekler açıklanmıştır.**

## <a name="filter-options"></a>Filtre seçenekleri

Aşağıdaki filtre seçenekleri kullanılabilir. Varsayılan olarak, **Ad Alanlarını Göster ve** Şema Dosyalarını **Göster** seçenekleri seçilir.

- **Ad Alanlarını Göster.**

- **Şema Dosyalarını Göster.**

- **Compositors 'i (sequence/choice/all) göster.**

## <a name="sorting-options"></a>Sıralama seçenekleri

Aşağıdaki sıralama seçenekleri mevcuttur. Varsayılan değer Türüne **Göre Sırala'dır.** **SıralamaYa** göre seçenekleri dosyalar ve ad alanları için geçerli değildir.

- **Türüne Göre Sırala.**

- **Adına göre sırala.**

- **Belge Sırası.**

### <a name="sort-by-type"></a>Türe Göre Sırala

Türe **Göre Sırala** seçeneği seçildiğinde, genel düğümler aşağıdaki sırayla sıralanmış olur. Düğümler daha sonra her grup içinde alfabetik olarak sıralanır.

1. `import` Düğüm.

2. `include` Düğüm.

3. `redefine` Düğüm.

4. `attribute` Düğüm.

5. `attributeGroup` Düğüm.

6. `complexType` Düğüm.

7. `simpleType` Düğüm.

8. `element` Düğüm.

9. `group` Düğüm.

### <a name="sort-by-name"></a>Ad ile Sırala

Adla **Sırala** seçeneği seçildiğinde, genel düğümler aşağıdaki sırayla sıralanmış olur:

1. `import` düğümler (ad alanlarının alfabetik sırasına göre).

2. `include` düğümleri (özniteliklerin alfabetik `schemaLocation` sırasına göre).

3. `redefine` düğümleri (özniteliklerin alfabetik `schemaLocation` sırasına göre).

4. Alfabetik sırada diğer genel düğümler.

### <a name="document-order"></a>Belge Sırası

Şema **Dosyalarını Göster** seçeneği seçildiğinde Belge **Sırası** seçeneği kullanılabilir. Belge **Sırası** seçildiğinde, genel düğümler şema dosyasında görünme sırasına göre görüntülenir.

## <a name="persisting-sortfilter-options"></a>Kalıcı sıralama/filtreleme seçenekleri

Sıralama, filtreleme ve gruplama seçenekleri, ayarlar değiştiriken hangi çözümün veya dosyaların açık olduğu fark etmez her kullanıcı için kayıt defterine kaydedilir.
