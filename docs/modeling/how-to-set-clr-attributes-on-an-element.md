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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9f8b16edcbe575ebac67f4acde9111a9511b85
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363854"
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

6. **Tamam** düğmesine tıklayın.

     **Özel öznitelikler** özelliği artık özniteliği aşağıdaki biçimde görüntüler:

     `[`*AttributeName* `(` *ParameterName* `=` *Tür*`)]`

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))