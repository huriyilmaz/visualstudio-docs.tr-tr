---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: bağımsız değişken tasarımcısını kullanma'
description: Bağımsız değişken Tasarımcısı ve verilerin bir etkinliğin içine ve dışına akmasını sağlamak için bağımsız değişken tasarımcısının nasıl kullanılacağını öğrenin.
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
ms.openlocfilehash: 52f7d9bb06d60782e67664cf648ce03a2f7437fa
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963750"
---
# <a name="how-to-use-the-argument-designer"></a>Nasıl Yapılır: Bağımsız Değişken Tasarımcısını Kullanma

Bağımsız değişken Tasarımcısı, verilerin bir etkinliğin içine ve dışına akmasını kolaylaştırır. Tasarım tuvalinin sol alt köşesindeki **bağımsız değişkenler** düğmesine tıklayarak tasarımcıya erişin. Tasarımcı, tablo biçiminde görüntülenen bağımsız değişkenlerin bir listesini içerir ve **varsayılan değer** sütunu dışında her bir sütun üst bilgisi tarafından sıralanabilir. Her bağımsız değişken bir ad, ın/out/out/Property Direction, Type ve varsayılan ifade değeri (varsa) içerir. Ad ve varsayılan ifade değeri, düzenlenebilir metin alanlarıdır ve tür ve yönün açılan listeleri vardır. Daha fazla bilgi için bkz. [değişkenler ve bağımsız değişkenler (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Yeni bir bağımsız değişken oluşturmak için

1. Visual Studio bir iş akışı veya etkinlik çözümü açın.

2. Tasarım tuvalinin sol alt köşesindeki **bağımsız değişkenler** düğmesine tıklayarak bağımsız değişkenler tasarımcısını açın. Bağımsız değişkenler Tasarımcısı görüntülenir.

3. **Oluşturma bağımsız değişkeni** etiketli boş satıra tıklayın. Bu, aşağıdaki varsayılan değerleri kullanarak yeni bir bağımsız değişken içeren yeni bir satır ekler: x değeri için bağımsız  değişken **x,** **yönü** Için ve **bağımsız değişken türü** için **dize** olarak benzersiz bağımsız değişken adları oluşturmak üzere otomatik olarak artan 1. **Varsayılan değer** için hiçbir değer eklenmez. Bu değerleri, iş akışı tasarım sürecinde istediğiniz zaman değiştirebilirsiniz.

    > [!NOTE]
    > Bir bağımsız değişkeni silmek için, ve ardından **Delete** tuşuna basarak bağımsız değişkeni seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](developing-applications-with-the-workflow-designer.md)
- [Değişkenler ve Bağımsız Değişkenler](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
