---
title: 'Nasıl yapılır: Iş akışı konsol uygulaması oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604927"
---
# <a name="how-to-create-a-workflow-console-application"></a>Nasıl yapılır: Iş akışı konsol uygulaması oluşturma
[!INCLUDE[wf](../includes/wf-md.md)], sistem veya insan süreçlerini yürütmek için iş akışları oluşturmanıza olanak tanır. @No__t_0, bu iş akışlarını oluşturmaya yönelik tasarım yüzeyi sağlar. @No__t_0, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içinden iş akışları oluşturmak için kullanılabilir veya tasarımcıyı yeniden barındıran diğer uygulamalarla tümleştirilebilir.

 Bu konuda, bir konsol uygulamasında iş akışı oluşturmak için [!INCLUDE[vs2010](../includes/vs2010-md.md)] [!INCLUDE[wfd2](../includes/wfd2-md.md)] nasıl kullanılacağı açıklanmaktadır.

### <a name="to-create-a-workflow-console-application"></a>Bir iş akışı konsol uygulaması oluşturmak için

1. @No__t_0 başlatın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **proje...** öğesini seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, tercih diliniz ' ne bağlı olarak, **görsel C#**  veya **Visual Basic** gruplandırmalarından **iş akışı** ' nı seçin.

4. Orta bölmede **Iş akışı konsol uygulaması**' nı seçin.

5. **Ad** kutusuna projeniz için açıklayıcı bir ad girin ve kolayca tanımlanmasını sağlayın.

6. **Konum** kutusunda, projenizi kaydetmek istediğiniz dizini girin veya git ' e tıklayarak bu dosyayı **gösterin** .

7. **Çözüm** kutusuna yeni çözüm için bir ad girin. Uygulamayı oluşturmak için **Tamam** ' ı tıklatın.

    > [!NOTE]
    > Mevcut bir çözüme bir iş akışı konsol uygulaması eklemek istiyorsanız, bu çözümü [!INCLUDE[vs2010](../includes/vs2010-md.md)] açın, **Çözüm Gezgini**çözüme sağ tıklayın ve **Ekle**, **Yeni proje..** . öğesini seçin. **Yeni proje** iletişim kutusunu açmak için. Bu yordamda yukarıda açıklanan şekilde ilerleyin.

8. Proje şablonu XAML 'de bir iş akışı tanımı oluşturur ve konsol uygulama tanımı kaynak kodunda bulunur. @No__t_0 açılır ve oluşturduğunuz iş akışının tuvali görüntülenir.

9. Bir iş akışı oluşturmak için, etkinlik veya diğer iş akışı öğelerini **araç kutusundan** , iş akışınızın tasarım yüzeyine sürükleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [İş Akışı Projesi Oluşturma](../workflow-designer/creating-a-workflow-project.md)