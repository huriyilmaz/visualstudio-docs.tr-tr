---
title: XML şema Gezgininde sıralama, filtreleme ve gruplandırma
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd288171cd8713e6b403f71a4eee6ba09d3f6ea9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592522"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sıralama, filtreleme ve gruplandırma (XML şema Gezgini)

Bu konu başlığı altında, **XML şema Gezgini** araç çubuğundaki **sıralama, filtreleme ve gruplandırma seçenekleri** menüsünde bulunan seçenekler açıklanmaktadır.

## <a name="filter-options"></a>Filtre seçenekleri

Aşağıdaki filtre seçenekleri kullanılabilir. Varsayılan olarak, **ad alanlarını göster** ve **şema dosyalarını göster** seçenekleri seçilidir.

- **Ad alanlarını göster**.

- **Şema dosyalarını göster**.

- Oluşturucuları **göster (Sequence/Choice/All)** .

## <a name="sorting-options"></a>Sıralama seçenekleri

Aşağıdaki sıralama seçenekleri kullanılabilir. Varsayılan değer **türe göre sıralanır**. Seçeneklere **göre sırala** , dosyalar ve ad alanları için geçerlidir.

- **Türe göre sırala**.

- **Ada göre sıralayın**.

- **Belge sırası**.

### <a name="sort-by-type"></a>Türe göre sırala

**Türe göre sırala** seçeneği belirlendiğinde, genel düğümler aşağıdaki sırada sıralanır. Daha sonra düğümler her grup içinde alfabetik olarak sıralanır.

1. düğümleri `import`.

2. düğümleri `include`.

3. düğümleri `redefine`.

4. düğümleri `attribute`.

5. düğümleri `attributeGroup`.

6. düğümleri `complexType`.

7. düğümleri `simpleType`.

8. düğümleri `element`.

9. düğümleri `group`.

### <a name="sort-by-name"></a>Ada göre sırala

**Ada göre sırala** seçeneği belirlendiğinde, genel düğümler aşağıdaki sıraya göre sıralanır:

1. düğümleri `import` (ad alanlarının alfabetik sırasıyla).

2. düğümler `include` (`schemaLocation` özniteliklerinin alfabetik sırasıyla).

3. düğümler `redefine` (`schemaLocation` özniteliklerinin alfabetik sırasıyla).

4. Alfabetik sırada diğer genel düğümler.

### <a name="document-order"></a>Belge sırası

**Belge sırası** seçeneği, **şema dosyalarını göster** seçeneği belirlendiğinde kullanılabilir. **Belge sırası** seçildiğinde, genel düğümler, şema dosyasında göründükleri sırada görüntülenir.

## <a name="persisting-sortfilter-options"></a>Kalıcı sıralama/filtre seçenekleri

Sıralama, filtreleme ve gruplandırma seçenekleri, her kullanıcı için kayıt defterine kaydedilir, bu da ayarlar değiştirildiğinde hangi çözüm veya dosyaların açık olduğuna bakılmaksızın.
