---
title: 'Nasıl yapılır: etkinlik Tasarımcısı kitaplığı oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662866"
---
# <a name="how-to-create-an-activity-designer-library"></a>Nasıl Yapılır: Etkinlik Tasarımcısı Kitaplığı Oluşturma
Özel etkinlik tasarımcıları, standart veya özel bir etkinlik için Kullanıcı arabirimi oluşturmanıza olanak sağlar. Kullanıcı arabiriminin karmaşıklığını kontrol edersiniz ve bir etkinlik için birden fazla etkinlik Tasarımcısı oluşturma olanağına sahip olursunuz. Bu senaryo, birden çok izleyici için uyarlanmış tasarımcılar oluşturmanıza olanak sağlar.

### <a name="to-create-an-activity-designer-library"></a>Bir etkinlik Tasarımcısı kitaplığı oluşturmak için

1. Başlatın [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **proje...** öğesini seçin. **Yeni proje** iletişim kutusunu açmak için.

3. **Proje türleri** bölmesinde, tercih ettiğiniz dile bağlı olarak, **Visual C#** veya **Visual Basic** gruplamalarından **iş akışı** ' nı seçin.

4. **Şablonlar** bölmesinde, **etkinlik Tasarımcısı kitaplığı**' nı seçin.

5. **Ad** kutusuna projeniz için açıklayıcı bir ad girin ve kolayca tanımlanmasını sağlayın.

6. **Konum** kutusunda, projenizi kaydetmek istediğiniz dizini girin veya git ' e tıklayarak bu dosyayı **gösterin** .

7. **Çözüm** kutusuna çözümünüz için açıklayıcı bir ad yazın ve ardından **Tamam**' a tıklayın.

    > [!NOTE]
    > Mevcut bir çözüme bir iş akışı konsol uygulaması eklemek istiyorsanız, bu çözümü içinde açın [!INCLUDE[vs2010](../includes/vs2010-md.md)] , **Çözüm Gezgini**' de çözüme sağ tıklayın ve **Ekle**, **Yeni proje..** . öğesini seçin. **Yeni proje** iletişim kutusunu açmak için. Bu yordamda yukarıda açıklanan şekilde ilerleyin.

8. Proje şablonu, XAML 'de bir etkinlik Tasarımcısı tanımı ve kaynak kodunda arka plan kod uygulama dosyası oluşturur. [!INCLUDE[wfd1](../includes/wfd1-md.md)]Açılır ve etkinlik tasarlayana ilişkin tuvali görüntüler.

9. [!INCLUDE[avalon1](../includes/avalon1-md.md)] **Araç kutusundan** denetimleri özel etkinlik tasarımcısında kullanmak için tasarım yüzeyine sürükleyin.  Özel bir etkinlik tasarımcısının nasıl uygulanacağı hakkında bir örnek için bkz. [nasıl yapılır: özel etkinlik Tasarımcısı oluşturma](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Özel etkinlik tasarımcıları, özel etkinlikler ve varsayılan etkinlikler için kullanılabilir [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

## <a name="see-also"></a>Ayrıca Bkz.
 [İş Akışı Projesi Oluşturma](../workflow-designer/creating-a-workflow-project.md)