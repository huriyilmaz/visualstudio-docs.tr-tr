---
title: 'İş Akışı Tasarımcısı - Nasıl kullanılır: Bağımsız Değişken Tasarımcısını Kullanma'
description: Bağımsız değişken tasarımcısını ve bir etkinliğin içine ve dışında veri akışına izin vermek için bağımsız değişken tasarımcısını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 9fcad04eb19c7ba42a0148078af6685b7dc69406ecb46e802f4e3206235fb317
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383774"
---
# <a name="how-to-use-the-argument-designer"></a>Nasıl Yapılır: Bağımsız Değişken Tasarımcısını Kullanma

Bağımsız değişken tasarımcısı, bir etkinliğin içine ve dışarı veri akışına izin vermeyi kolaylaştırır. Tasarım tuvalin sol **alt köşesindeki** Bağımsız Değişkenler düğmesine tıklayarak tasarımcıya erişin. Tasarımcı, tablosal bir formda görünen bağımsız değişkenlerin listesini içerir ve Varsayılan değer sütunu dışında her sütun başlığına **göre sıralanır.** Her bağımsız değişken bir ad, in/out/in-out/property yönü, tür ve varsayılan ifade değeri (varsa) içerir. Ad ve varsayılan ifade değeri düzenlenebilir metin alanlarıdır ve tür ve yön açılır listedir. Daha fazla bilgi için [bkz. Değişkenler ve bağımsız değişkenler (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Yeni bir bağımsız değişken oluşturmak için

1. bir iş akışı veya etkinlik çözümünü Visual Studio.

2. Tasarım tuvalin sol alt **köşesindeki Bağımsız** Değişkenler düğmesine tıklayarak bağımsız değişkenler tasarımcısını açın. Bağımsız değişkenler tasarımcısı görüntülenir.

3. Bağımsız Değişken Oluştur etiketli boş **satıra tıklayın.** Bu, aşağıdaki varsayılan değerleri kullanarak yeni bir bağımsız değişken içeren  yeni bir satır ekler: x, Name için argumentx değeri ilk değeri 1 olan ve benzersiz bağımsız değişken adları oluşturmak için otomatik olarak artırılır,  Yön için Içinde **ve** Bağımsız Değişken türü için **Dize.** Varsayılan değeri için değer **eklenmez.** bu değerleri iş akışı tasarım işlemi sırasında herhangi bir zamanda değiştirebilirsiniz.

    > [!NOTE]
    > Bir bağımsız değişkeni silmek için, bağımsız değişkene tıklayarak bağımsız değişkeni seçin ve ardından Sil **tuşuna** basın.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [Değişkenler ve Bağımsız Değişkenler](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
