---
title: 'Nasıl Yapılır: Bir öğe üzerinde CLR özniteliklerini ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662550"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Nasıl Yapılır: Bir Öğede CLR Özniteliklerini Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel öznitelikler, etki alanı öğelerine, şekillere, bağlayıcılara ve diyagramlarına eklenebilen özel özniteliklerdir. @No__t_0 sınıfından devralan herhangi bir özniteliği ekleyebilirsiniz.

### <a name="to-add-a-custom-attribute"></a>Özel bir öznitelik eklemek için

1. **DSL Gezgini**' nde, özel öznitelik eklemek istediğiniz öğeyi seçin.

2. **Özellikler** penceresinde, **özel öznitelikler** özelliğinin yanındaki gezinme ( **...** ) simgesine tıklayın.

     **Öznitelikleri Düzenle** iletişim kutusu açılır.

3. **Ad** sütununda **\<add özniteliği >** ' ne tıklayın ve öznitebir adının adını yazın. ENTER tuşuna basın.

4. Öznitelik adının altındaki satır parantez ' nu gösterir. Bu satırda, öznitelik için bir parametre türü yazın (örneğin, `string`) ve ardından ENTER tuşuna basın.

5. **Ad özelliği** sütununda, uygun bir ad yazın, örneğin `MyString`.

6. **Tamam**'ı tıklatın.

     **Özel öznitelikler** özelliği artık özniteliği aşağıdaki biçimde görüntüler:

     `[` *AttributeName* `(` *ParameterName* `=` *türü* `)]`

## <a name="see-also"></a>Ayrıca Bkz.
 [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
