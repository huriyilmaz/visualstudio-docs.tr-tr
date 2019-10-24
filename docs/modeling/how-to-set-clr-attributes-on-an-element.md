---
title: 'Nasıl yapılır: Bir Öğede CLR Özniteliklerini Ayarlama'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f943f9713e4432f0b06242a2f66acae6b390e5cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748365"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Nasıl yapılır: Bir Öğede CLR Özniteliklerini Ayarlama
Özel öznitelikler, etki alanı öğelerine, şekillere, bağlayıcılara ve diyagramlarına eklenebilen özel özniteliklerdir. @No__t_0 sınıfından devralan herhangi bir özniteliği ekleyebilirsiniz.

### <a name="to-add-a-custom-attribute"></a>Özel bir öznitelik eklemek için

1. **DSL Gezgini**' nde, özel öznitelik eklemek istediğiniz öğeyi seçin.

2. **Özellikler** penceresinde, **özel öznitelikler** özelliğinin yanındaki gezinme ( **...** ) simgesine tıklayın.

     **Öznitelikleri Düzenle** iletişim kutusu açılır.

3. **Ad** sütununda **\<add özniteliği >** ' ne tıklayın ve öznitebir adının adını yazın. ENTER tuşuna basın.

4. Öznitelik adının altındaki satır parantez ' nu gösterir. Bu satırda, öznitelik için bir parametre türü yazın (örneğin, `string`) ve ardından ENTER tuşuna basın.

5. **Ad özelliği** sütununda, uygun bir ad yazın, örneğin `MyString`.

6. **Tamam**'a tıklayın.

     **Özel öznitelikler** özelliği artık özniteliği aşağıdaki biçimde görüntüler:

     `[` *AttributeName* `(` *ParameterName* `=` *türü* `)]`

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)