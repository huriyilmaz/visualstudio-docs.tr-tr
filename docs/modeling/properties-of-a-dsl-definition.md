---
title: DSL Tanımının Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 650e4db75b3896a04b2dd4ef9056191d4a83d46a
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810099"
---
# <a name="properties-of-a-dsl-definition"></a>DSL Tanımının Özellikleri
DslDefinition özellikleri, sürüm numaralandırması gibi, *etki alanına özgü dil* tanımı özelliklerini tanımlar. *Alana özgü dil Tasarımcısı*diyagramın açık bir alanına tıkladığınızda DslDefinition özellikleri **Özellikler** penceresinde görünür.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition aşağıdaki tabloda bulunan özelliklere sahiptir:

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim değiştiricisi|Etki alanı sınıfına ait erişim değiştiricisinin public veya internal olduğunu belirler.|public|
|Özel Öznitelikler|Alan sınıfı için özel tanımlanmış öznitelikler.<br /><br /> **Göz önünde** Bir öznitelik eklemek için tarayıcı düğmesini kullanın.|\<none>|
|Şirket Adı|Sistem kayıt defterindeki geçerli şirket adının adı.|Geçerli şirket adı|
|Name|Bu alan sınıfının adı.|Geçerli ad|
|Ad Alanı|Bu alan sınıfıyla ilişkili ad alanı.|Geçerli ad alanı|
|Paket GUID 'Si|Bu DSL için oluşturulan Visual Studio paketinin Guid 'i.|\<none>|
|Paket ad alanı|Bu DSL için oluşturulan Visual Studio paketinin ad alanı.|\<none>|
|Ürün Adı|Bu DSL için oluşturulan Visual Studio paketi için kaydedilecek ürünün adı.|\<none>|
|Notlar|Bu alan sınıfıyla ilişkili notlar.|\<none>|
|Açıklama|Bu alan sınıfı için açıklama.|\<none>|
|Görünen Ad|Bu alan sınıfı için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Help anahtar sözcüğü|Bu alan sınıfıyla ilişkili Yardım anahtar sözcüğü.|\<none>|
|Yapı|Bu etki alanına özgü dil tanımı için Artımlı derleme numarası.|0|
|Ana Sürüm|Bu etki alanına özgü dil tanımı için artımlı ana derleme numarası.|1|
|Alt Sürüm|Bu etki alanına özgü dil tanımı için artımlı küçük derleme numarası.|0|
|Revizyon|Bu etki alanına özgü dil tanımı için artımlı düzeltme derleme numarası.|0|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))