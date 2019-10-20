---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: değişken tasarımcısını kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59a0da5ad0345ba0733f52d087b262bdc706cd21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650245"
---
# <a name="how-to-use-the-variable-designer"></a>Nasıl yapılır: değişken tasarımcısını kullanma

Değişken tasarımcı, veri bağlama senaryolarında ve Koşullu deyimlerde kullanılmak üzere değişkenler oluşturmak için kullanılır. Tasarımcı, tasarım tuvalinin sol alt köşesindeki **değişkenler** düğmesine tıklanarak erişilir. Tasarımcı, tablo biçiminde görüntülenen ve **varsayılan** sütun hariç her bir sütun üst bilgisi tarafından sıralanan değişkenlerin bir listesini içerir. Her değişken bir ad, değişken türü, kapsam ve varsayılan değer (varsa) içerir. Ad ve varsayılan değer düzenlenebilir metin alanlarıdır ve tür ve kapsam açılır. Kapsam, değişken tasarımcı çağrıldığında seçilmiş olan etkinliktir. Seçim kapsamında bir değişken oluşturuoluşturuoluşturulamadığı takdirde kapsam, varsayılan olarak, değişkenlerin kapsamında oluşturulmasına izin veren seçimin en yakın üst etkinliği olur. Daha fazla bilgi için bkz. [değişkenler ve bağımsız değişkenler (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Sıralama düzeni, kullanıcı açıkça sıralama denetimlerinden birini kullanmadığı sürece uygulanmaz, değişken tasarımcısını kapatır ve yeniden açar ya da başka bir değişken oluşturur.

## <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için

1. Visual Studio 'da bir iş akışı veya etkinlik çözümü açın.

2. Tasarım tuvalinde iş akışınızda bir etkinlik seçin.

3. Tasarım tuvalinin sol alt köşesindeki **değişkenler** düğmesine tıklayarak değişken tasarımcısını açın. Değişken tasarımcı belirir.

4. **Oluşturma değişkeni**etiketli boş satıra tıklayın. Bu işlem, şu varsayılan değerleri kullanarak yeni bir değişken içeren yeni bir satır ekler: **x, benzersiz** değişken adları oluşturmak için otomatik olarak artan 1 başlangıç değeri olan bir tamsayı, değişken için **dize** **kapsam**Için tür ve **sıra** . **Varsayılan**için değer eklenmez. Bu değerleri, iş akışı tasarım sürecinde istediğiniz zaman değiştirebilirsiniz.

    > [!NOTE]
    > Bir değişkeni silmek için, ve ardından **Delete** tuşuna basarak değişkeni seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [Değişkenler ve Bağımsız Değişkenler](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Nasıl Yapılır: Bağımsız Değişken Tasarımcısını Kullanma](../workflow-designer/how-to-use-the-argument-designer.md)