---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: değişken tasarımcısını kullanma'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f02aab6c5ecf545e0f754f1a88fa7e26a88f206d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817417"
---
# <a name="how-to-use-the-variable-designer"></a>Nasıl Yapılır: Değişken Tasarımcısını Kullanma

Değişken tasarımcı, veri bağlama senaryolarında ve Koşullu deyimlerde kullanılmak üzere değişkenler oluşturmak için kullanılır. Tasarımcı, tasarım tuvalinin sol alt köşesindeki **değişkenler** düğmesine tıklanarak erişilir. Tasarımcı, tablo biçiminde görüntülenen ve **varsayılan** sütun hariç her bir sütun üst bilgisi tarafından sıralanan değişkenlerin bir listesini içerir. Her değişken bir ad, değişken türü, kapsam ve varsayılan değer (varsa) içerir. Ad ve varsayılan değer düzenlenebilir metin alanlarıdır ve tür ve kapsam açılır. Kapsam, değişken tasarımcı çağrıldığında seçilmiş olan etkinliktir. Seçim kapsamında bir değişken oluşturuoluşturuoluşturulamadığı takdirde kapsam, varsayılan olarak, değişkenlerin kapsamında oluşturulmasına izin veren seçimin en yakın üst etkinliği olur. Daha fazla bilgi için bkz. [değişkenler ve bağımsız değişkenler (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Sıralama düzeni, kullanıcı açıkça sıralama denetimlerinden birini kullanmadığı sürece uygulanmaz, değişken tasarımcısını kapatır ve yeniden açar ya da başka bir değişken oluşturur.

## <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için

1. Visual Studio 'da bir iş akışı veya etkinlik çözümü açın.

2. Tasarım tuvalinde iş akışınızda bir etkinlik seçin.

3. Tasarım tuvalinin sol alt köşesindeki **değişkenler** düğmesine tıklayarak değişken tasarımcısını açın. Değişken tasarımcı belirir.

4. **Oluşturma değişkeni**etiketli boş satıra tıklayın. Bu, aşağıdaki varsayılan değerleri kullanarak yeni bir değişken içeren yeni bir satır ekler: x, benzersiz değişken adları, **değişken türü**için **dize** ve **kapsam** **sırası** için otomatik olarak arttırılan 1 başlangıç değeri olan bir tamsayı olan **addır** . **Varsayılan**için değer eklenmez. Bu değerleri, iş akışı tasarım sürecinde istediğiniz zaman değiştirebilirsiniz.

    > [!NOTE]
    > Bir değişkeni silmek için, ve ardından **Delete** tuşuna basarak değişkeni seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [Değişkenler ve Bağımsız Değişkenler](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Nasıl Yapılır: Bağımsız Değişken Tasarımcısını Kullanma](../workflow-designer/how-to-use-the-argument-designer.md)
