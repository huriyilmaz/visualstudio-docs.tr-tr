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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604927"
---
# <a name="how-to-create-a-workflow-console-application"></a>Nasıl Yapılır: İş Akışı Konsol Uygulaması Oluşturma
[!INCLUDE[wf](../includes/wf-md.md)] Sistem veya insan süreçlerini yürütmek için iş akışları oluşturmanıza olanak tanır. , [!INCLUDE[wfd1](../includes/wfd1-md.md)] Bu iş akışlarını oluşturmaya yönelik tasarım yüzeyi sağlar. , [!INCLUDE[wfd2](../includes/wfd2-md.md)] İçinden iş akışı oluşturmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya tasarımcıyı yeniden barındıran diğer uygulamalarla tümleştirilebilecek şekilde kullanılabilir.

 Bu konu, [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[vs2010](../includes/vs2010-md.md)] bir konsol uygulamasında iş akışı oluşturmak için ' ın nasıl kullanılacağını açıklar.

### <a name="to-create-a-workflow-console-application"></a>Bir iş akışı konsol uygulaması oluşturmak için

1. Başlatın [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **proje...** öğesini seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, tercih diliniz ' ne bağlı olarak, **Visual C#** veya **Visual Basic** gruplamalarından **iş akışı** ' nı seçin.

4. Orta bölmede **Iş akışı konsol uygulaması**' nı seçin.

5. **Ad** kutusuna projeniz için açıklayıcı bir ad girin ve kolayca tanımlanmasını sağlayın.

6. **Konum** kutusunda, projenizi kaydetmek istediğiniz dizini girin veya git ' e tıklayarak bu dosyayı **gösterin** .

7. **Çözüm** kutusuna yeni çözüm için bir ad girin. Uygulamayı oluşturmak için **Tamam** ' ı tıklatın.

    > [!NOTE]
    > Mevcut bir çözüme bir iş akışı konsol uygulaması eklemek istiyorsanız, bu çözümü içinde açın [!INCLUDE[vs2010](../includes/vs2010-md.md)] , **Çözüm Gezgini**' de çözüme sağ tıklayın ve **Ekle**, **Yeni proje..** . öğesini seçin. **Yeni proje** iletişim kutusunu açmak için. Bu yordamda yukarıda açıklanan şekilde ilerleyin.

8. Proje şablonu XAML 'de bir iş akışı tanımı oluşturur ve konsol uygulama tanımı kaynak kodunda bulunur. [!INCLUDE[wfd2](../includes/wfd2-md.md)]Açılır ve oluşturduğunuz iş akışı için tuvali görüntüler.

9. Bir iş akışı oluşturmak için, etkinlik veya diğer iş akışı öğelerini **araç kutusundan** , iş akışınızın tasarım yüzeyine sürükleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [İş Akışı Projesi Oluşturma](../workflow-designer/creating-a-workflow-project.md)