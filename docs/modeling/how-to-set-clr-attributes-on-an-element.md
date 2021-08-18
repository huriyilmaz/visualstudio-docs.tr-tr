---
title: 'Nasıl yapılır: Bir Öğede CLR Özniteliklerini Ayarlama'
description: System. Attribute sınıfından devralan herhangi bir özniteliği nasıl ekleyebileceğiniz hakkında bilgi edinin.
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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b6b11d186ea6c4831679c111a632ffe710a6b886
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143371"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Nasıl yapılır: Bir Öğede CLR Özniteliklerini Ayarlama
Özel öznitelikler, etki alanı öğelerine, şekillere, bağlayıcılara ve diyagramlarına eklenebilen özel özniteliklerdir. Sınıfından devralan herhangi bir özniteliği ekleyebilirsiniz `System.Attribute` .

### <a name="to-add-a-custom-attribute"></a>Özel bir öznitelik eklemek için

1. **DSL Gezgini**' nde, özel öznitelik eklemek istediğiniz öğeyi seçin.

2. **Özellikler** penceresinde, **özel öznitelikler** özelliğinin yanındaki gezinme (**...**) simgesine tıklayın.

     **Öznitelikleri Düzenle** iletişim kutusu açılır.

3. **Ad** sütununda, **\<add attribute>** özniteliðin adını tıklayın ve yazın. ENTER tuşuna basın.

4. Öznitelik adının altındaki satır parantez ' nu gösterir. Bu satırda, öznitelik için bir parametre türü yazın (örneğin, `string` ) ve ardından ENTER tuşuna basın.

5. **Ad özelliği** sütununda, örneğin, uygun bir ad yazın `MyString` .

6. **Tamam**'a tıklayın.

     **Özel öznitelikler** özelliği artık özniteliği aşağıdaki biçimde görüntüler:

     `[`*AttributeName* `(` *ParameterName* `=` *Tür*`)]`

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))