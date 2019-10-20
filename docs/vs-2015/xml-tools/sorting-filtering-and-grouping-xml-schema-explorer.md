---
title: Sıralama, filtreleme ve gruplandırma (XML şema Gezgini) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c28842a92ab598ff196e80fc96678c256e4db8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656142"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sıralama, filtreleme ve gruplandırma (XML şema Gezgini)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, XML şema Gezgini araç çubuğundaki **sıralama, filtreleme ve gruplandırma seçenekleri** menüsünde bulunan seçenekler açıklanmaktadır.

## <a name="filter-options"></a>Filtre seçenekleri
 Aşağıdaki filtre seçenekleri kullanılabilir. Varsayılan olarak, **ad alanlarını göster** ve **şema dosyalarını göster** seçenekleri seçilidir.

- **Ad alanlarını göster**.

- **Şema dosyalarını göster**.

- Oluşturucuları **göster (Sequence/Choice/All)** .

## <a name="sorting-options"></a>Sıralama seçenekleri
 Aşağıdaki sıralama seçenekleri kullanılabilir. Varsayılan değer **türe göre sıralanır**. Seçeneklere göre sırala, dosyalar ve ad alanları için geçerlidir.

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
