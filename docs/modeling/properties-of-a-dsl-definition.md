---
title: DSL Tanımının Özellikleri
description: DslDefinition özelliklerinin sürüm numarası gibi etki alanına özgü dil tanımı özelliklerini tanımlay olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: cd32788e6b423b5ceb1ceafa54ad72cd3a885b15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034259"
---
# <a name="properties-of-a-dsl-definition"></a>DSL Tanımının Özellikleri
DslDefinition özellikleri, *sürüm numarası gibi etki* alanına özgü dil tanımı özelliklerini tanımlar. DslDefinition özellikleri, **diyagramda** diyagramın açık bir alanına tıklarsanız Özellikler penceresinde *Alana Özgü Dil Tasarımcısı.*

 Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, bkz. Domain-Specific Dili [Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 DslDefinition aşağıdaki tabloda yer alan özelliklere sahiptir:

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim Değiştiricisi|Etki alanı sınıfı için erişim değiştiricinin genel mi yoksa iç mi olduğunu belirler.|public|
|Özel Öznitelikler|Etki alanı sınıfı için özel tanımlı öznitelikler.<br /><br /> **Not** Öznitelik eklemek için gözat düğmesini kullanın.|\<none>|
|Şirket Adı|Sistem kayıt defterindeki geçerli şirket adının adı.|Geçerli şirket adı|
|Name|Bu etki alanı sınıfının adı.|Geçerli ad|
|Ad Alanı|Bu etki alanı sınıfına bağlı ad alanı.|Geçerli ad alanı|
|Paket Guid'i|Bu DSL için Visual Studio paketi için guid.|\<none>|
|Paket Ad Alanı|Bu DSL için Visual Studio paketi için ad alanı.|\<none>|
|Ürün Adı|Bu DSL için oluşturulan paket için Visual Studio ürünün adı.|\<none>|
|Notlar|Bu etki alanı sınıfıyla ilişkili notlar.|\<none>|
|Açıklama|Bu etki alanı sınıfının açıklaması.|\<none>|
|Görünen Ad|Bu etki alanı sınıfı için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Help Anahtar Sözcüğü|Bu etki alanı sınıfıyla ilişkili help anahtar sözcüğü.|\<none>|
|Oluşturma|Bu etki alanına özgü dil tanımı için artımlı derleme numarası.|0|
|Ana Sürüm|Bu etki alanına özgü dil tanımı için artımlı ana derleme numarası.|1|
|Alt Sürüm|Bu etki alanına özgü dil tanımı için artımlı küçük derleme numarası.|0|
|Revizyon|Bu etki alanına özgü dil tanımı için artımlı düzeltme derleme numarası.|0|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))