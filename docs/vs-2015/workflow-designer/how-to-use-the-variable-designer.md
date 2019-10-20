---
title: 'Nasıl yapılır: değişken tasarımcısını kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4744864824da5efb238e9af1a5a12fcef79ea4ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659069"
---
# <a name="how-to-use-the-variable-designer"></a>Nasıl yapılır: değişken tasarımcısını kullanma
Değişken tasarımcı, veri bağlama senaryolarında ve Koşullu deyimlerde kullanılmak üzere değişkenler oluşturmak için kullanılır. Tasarımcı, tasarım tuvalinin sol alt köşesindeki **değişkenler** düğmesine tıklanarak erişilir. Tasarımcı, tablo biçiminde görüntülenen ve **varsayılan** sütun hariç her bir sütun üst bilgisi tarafından sıralanan değişkenlerin bir listesini içerir. Her değişken bir ad, değişken türü, kapsam ve varsayılan değer (varsa) içerir. Ad ve varsayılan değer düzenlenebilir metin alanlarıdır ve tür ve kapsam açılır. Kapsam, değişken tasarımcı çağrıldığında seçilmiş olan etkinliktir. Seçim kapsamında bir değişken oluşturuoluşturuoluşturulamadığı takdirde kapsam, varsayılan olarak, değişkenlerin kapsamında oluşturulmasına izin veren seçimin en yakın üst etkinliği olur. değişkenleri [!INCLUDE[crabout](../includes/crabout-md.md)], bkz. [değişkenler ve bağımsız değişkenler](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

 Sıralama düzeni, kullanıcı açıkça sıralama denetimlerinden birini kullanmadığı sürece uygulanmaz, değişken tasarımcısını kapatır ve yeniden açar ya da başka bir değişken oluşturur.

### <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için

1. @No__t_0 bir iş akışı veya etkinlik çözümü açın.

2. Tasarım tuvalinde iş akışınızda bir etkinlik seçin.

3. Tasarım tuvalinin sol alt köşesindeki **değişkenler** düğmesine tıklayarak değişken tasarımcısını açın. Değişken tasarımcı belirir.

4. **Oluşturma değişkeni**etiketli boş satıra tıklayın. Bu işlem, şu varsayılan değerleri kullanarak yeni bir değişken içeren yeni bir satır ekler: **x, benzersiz** değişken adları oluşturmak için otomatik olarak artan 1 başlangıç değeri olan bir tamsayı, değişken için **dize** **kapsam**Için tür ve **sıra** . **Varsayılan**için değer eklenmez. Bu değerleri, iş akışı tasarım sürecinde istediğiniz zaman değiştirebilirsiniz.

    > [!NOTE]
    > Bir değişkeni silmek için, ve ardından **Delete** tuşuna basarak değişkeni seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [İş akışı Tasarımcısı](../workflow-designer/using-the-workflow-designer.md) [değişkenlerini ve bağımsız değişkenleri](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) kullanma [nasıl yapılır: bağımsız değişken tasarımcısını kullanma](../workflow-designer/how-to-use-the-argument-designer.md)