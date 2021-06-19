---
title: 'Nasıl yapılır: Bir Öğede CLR Özniteliklerini Ayarlama'
description: System.Attribute sınıfından devralınan herhangi bir özniteliği nasıl ekley oIyrın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b11a6bd4a04bdb469cdf5c2fe2d7b78e0c0fe29a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387339"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Nasıl yapılır: Bir Öğede CLR Özniteliklerini Ayarlama
Özel öznitelikler etki alanı öğelerine, şekillerine, bağlayıcılarına ve diyagramlarına eklenilen özel özniteliklerdir. sınıfından devralınan herhangi bir özniteliği `System.Attribute` ekleme.

### <a name="to-add-a-custom-attribute"></a>Özel öznitelik eklemek için

1. DSL **Gezgini'nde,** özel öznitelik eklemek istediğiniz öğeyi seçin.

2. Özellikler **penceresinde,** Özel Öznitelikler **özelliğinin yanındaki** Gözat (**... ) simgesine** tıklayın.

     Öznitelikleri **Düzenle iletişim** kutusu açılır.

3. Ad **sütununa** tıklayın **\<add attribute>** ve özniteliğinizin adını yazın. ENTER tuşuna basın.

4. Öznitelik adının altındaki satır parantezleri gösterir. Bu satırda özniteliği için bir parametre türü yazın (örneğin, `string` ) ve enter tuşuna basın.

5. Ad **Özelliği sütununa** uygun bir ad yazın; örneğin, `MyString` .

6. **Tamam**'a tıklayın.

     Özel **Öznitelikler** özelliği artık özniteliği şu biçimde görüntüler:

     `[`*AttributeName* `(` *ParameterName* `=` *Tür*`)]`

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))