---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: Içeri aktarmalar tasarımcısını kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df019157b6a8bd6199b01a093efb422792804b3e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650258"
---
# <a name="how-to-use-the-imports-designer"></a>Nasıl yapılır: Içeri aktarmalar tasarımcısını kullanma

İçeri aktarmalar Tasarımcısı, ifadeleriniz içinde kullanacağınız türler için ad alanları girmenize olanak sağlar. **Içeri aktarmalar** **veya Visual Basic** anahtar kelimeleriyle çok benzer ve C#içeri aktarmalar tasarımcısında ad alanlarını belirtmek, yalnızca ifadenizde tam bir sürüm türü adı yerine bir tür adı girmenizi sağlar.

İçeri aktarmalar Tasarımcısı, Kullanıcı arabirimindeki her iki değişikliğe ve iş akışı kaydedildiğinde yapılan değişikliklere tepki verir. İş akışı kaydedildiğinde, ad alanları içeri aktarmalar tasarımcısına otomatik olarak eklenebilir. Bunlar aşağıdakileri içerir:

- Değişken ve bağımsız değişken bildirimlerinde kullanılan her türlü tür için ad alanları.

- İfadelerde kullanılan herhangi bir tür için ad alanları.

- İş akışını serileştirmek için gereken diğer ad alanları (örneğin, iş akışında bırakılan özel etkinlikler tarafından kullanılan ad alanları).

  İş akışı kaydedildiğinde, önceki listede açıklanan mantık nedeniyle el ile sildiğiniz bazı ad alanlarının içeri aktarma tasarımcısına otomatik olarak yeniden eklendiğini fark edebilirsiniz.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>İçeri aktarılan ad alanları listesine bir ad alanı eklemek için

1. Visual Studio 'da veya bir yeniden barındırılan iş akışı uygulamasında bir WCF Iş akışı hizmeti uygulaması, iş akışı konsol uygulaması veya etkinlik kitaplığı projesi açın.

2. Ana tuvalin alt kısmındaki **Içeri aktarmalar** ' a tıklayın. Içeri aktarmalar Tasarımcısı görüntülenir.

3. Içeri aktarmalar tasarımcısının en üstündeki aşağı açılan liste denetiminden bir ad alanı girin veya seçin.

     Siz yazarken, yazılan karakterlerle eşleşen geçerli ad alanlarının listesi görüntülenir.

4. Ad alanını listeye eklemek için **ENTER** tuşuna basın.

5. Listeden bir ad alanı kaldırmak istiyorsanız, ad alanını seçin ve klavyenizdeki **Delete** tuşuna basın. Bir ad alanı yalnızca herhangi bir nedenle ad alanı geçersizse silinebileceğini unutmayın. Örneğin, ad alanını içeren derlemeye artık proje tarafından başvurulmuyorsa.