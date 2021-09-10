---
title: 'İş Akışı Tasarımcısı - Nasıl kullanılır: Değişken Tasarımcısını Kullanma'
description: Veri bağlama senaryolarında ve koşullu deyimlerde kullanmak üzere değişkenler oluşturmak için değişken tasarımcısını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 2391694c44c5494fb9410acd7247c59e95a1b9bf
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963752"
---
# <a name="how-to-use-the-variable-designer"></a>Nasıl Yapılır: Değişken Tasarımcısını Kullanma

Değişken tasarımcısı, veri bağlama senaryolarında ve koşullu deyimlerde kullanılacak değişkenleri oluşturmak için kullanılır. Tasarımcıya, tasarım **tuvalin** sol alt köşesindeki Değişkenler düğmesine tıklayarak erişilir. Tasarımcı, tablosal bir formda görünen değişkenlerin listesini içerir ve Varsayılan sütun dışında her sütun başlığına göre **sıralanır.** Her değişken bir ad, değişken türü, kapsam ve varsayılan değer (varsa) içerir. Ad ve varsayılan değer düzenlenebilir metin alanlarıdır ve tür ve kapsam açılır listedir. Kapsam, değişken tasarımcısı çağrıldığında seçilen etkinliktir. Bir değişken seçim kapsamında oluşturulamazsa, kapsam varsayılan olarak seçimin en yakın üst etkinliğidir ve bu da kendi kapsamında değişkenlerin oluşturularak izin verir. Daha fazla bilgi için [bkz. Değişkenler ve bağımsız değişkenler (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Sıralama düzeni, kullanıcı sıralama denetimlerinden birini açıkça kullanana, değişken tasarımcısını kapatıp yeniden açıncaya veya başka bir değişken oluşturana kadar uygulanmaz.

## <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için

1. Bir iş akışı veya etkinlik çözümünü Visual Studio.

2. Tasarım tuvali üzerinde iş akışınıza bir etkinlik seçin.

3. Tasarım tuvalin sol alt **köşesindeki** Değişkenler düğmesine tıklayarak değişken tasarımcısını açın. Değişken tasarımcısı görüntülenir.

4. Değişken Oluştur etiketli boş **satıra tıklayın.** Bu, şu varsayılan değerleri kullanarak yeni bir değişken içeren yeni  bir satır ekler: x, Name için variablex, benzersiz değişken adları oluşturmak için otomatik  olarak artırılır 1 ilk değerine sahip bir **tamsayı,** Değişken türü için Dize **ve** Kapsam için **Sıra.** Varsayılan için değer **eklenmez.** bu değerleri iş akışı tasarım işlemi sırasında herhangi bir zamanda değiştirebilirsiniz.

    > [!NOTE]
    > Bir değişkeni silmek için değişkene tıklayarak değişkeni seçin ve Sil **tuşuna** basın.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [Değişkenler ve Bağımsız Değişkenler](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Nasıl Yapılır: Bağımsız Değişken Tasarımcısını Kullanma](../workflow-designer/how-to-use-the-argument-designer.md)
