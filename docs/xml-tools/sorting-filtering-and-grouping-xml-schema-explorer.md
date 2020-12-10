---
title: Sıralama, filtreleme ve gruplandırma
description: XML şeması Gezgini araç çubuğunda sıralama, filtreleme ve gruplandırma seçenekleri menüsünde bulunan seçenekler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41f0aff39350b0307db6b02a148fb70022fb51ca
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996259"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sıralama, filtreleme ve gruplandırma (XML şema Gezgini)

Bu konu başlığı altında, **XML şema Gezgini** araç çubuğundaki **sıralama, filtreleme ve gruplandırma seçenekleri** menüsünde bulunan seçenekler açıklanmaktadır.

## <a name="filter-options"></a>Filtre seçenekleri

Aşağıdaki filtre seçenekleri kullanılabilir. Varsayılan olarak, **ad alanlarını göster** ve **şema dosyalarını göster** seçenekleri seçilidir.

- **Ad alanlarını göster**.

- **Şema dosyalarını göster**.

- Oluşturucuları **göster (Sequence/Choice/All)**.

## <a name="sorting-options"></a>Sıralama seçenekleri

Aşağıdaki sıralama seçenekleri kullanılabilir. Varsayılan değer **türe göre sıralanır**. Seçeneklere **göre sırala** , dosyalar ve ad alanları için geçerlidir.

- **Türe göre sırala**.

- **Ada göre sıralayın**.

- **Belge sırası**.

### <a name="sort-by-type"></a>Türe göre sırala

**Türe göre sırala** seçeneği belirlendiğinde, genel düğümler aşağıdaki sırada sıralanır. Daha sonra düğümler her grup içinde alfabetik olarak sıralanır.

1. `import` düğümlerini.

2. `include` düğümlerini.

3. `redefine` düğümlerini.

4. `attribute` düğümlerini.

5. `attributeGroup` düğümlerini.

6. `complexType` düğümlerini.

7. `simpleType` düğümlerini.

8. `element` düğümlerini.

9. `group` düğümlerini.

### <a name="sort-by-name"></a>Ada göre sırala

**Ada göre sırala** seçeneği belirlendiğinde, genel düğümler aşağıdaki sıraya göre sıralanır:

1. `import` düğümler (ad alanlarının alfabetik sırasıyla).

2. `include` düğümler (özniteliklerin alfabetik sırasına göre `schemaLocation` ).

3. `redefine` düğümler (özniteliklerin alfabetik sırasına göre `schemaLocation` ).

4. Alfabetik sırada diğer genel düğümler.

### <a name="document-order"></a>Belge sırası

**Belge sırası** seçeneği, **şema dosyalarını göster** seçeneği belirlendiğinde kullanılabilir. **Belge sırası** seçildiğinde, genel düğümler, şema dosyasında göründükleri sırada görüntülenir.

## <a name="persisting-sortfilter-options"></a>Kalıcı sıralama/filtre seçenekleri

Sıralama, filtreleme ve gruplandırma seçenekleri, her kullanıcı için kayıt defterine kaydedilir, bu da ayarlar değiştirildiğinde hangi çözüm veya dosyaların açık olduğuna bakılmaksızın.
