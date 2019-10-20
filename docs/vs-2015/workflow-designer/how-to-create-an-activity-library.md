---
title: 'Nasıl yapılır: etkinlik kitaplığı oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662752"
---
# <a name="how-to-create-an-activity-library"></a>Nasıl yapılır: etkinlik kitaplığı oluşturma
Özel Etkinlikler, iş akışındaki belirli iş işlemlerinizi modellemek için kullanılır. @No__t_1 kullanarak bu tür özel etkinlikleri görsel olarak oluşturmanızı sağlamak için [!INCLUDE[vs2010](../includes/vs2010-md.md)] etkinlik kitaplığı şablonu verilmiştir.

### <a name="to-create-a-workflow-activity-library"></a>Bir Iş akışı etkinlik kitaplığı oluşturmak için

1. @No__t_0 başlatın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **proje...** öğesini seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Proje türleri** bölmesinde, dil tercihlerinize göre **görsel C#**  projelerden veya **Visual Basic** gruplarından **iş akışı** ' nı seçin.

4. **Şablonlar** bölmesinde **etkinlik kitaplığı**' nı seçin.

5. **Ad** kutusuna projeniz için açıklayıcı bir ad yazın ve kolayca tanımlanmasını sağlayın.

6. **Konum** kutusunda, projenizi kaydetmek istediğiniz dizini yazın veya gitmek için git ' **e tıklayın.**

7. **Çözüm** kutusuna çözümünüz için açıklayıcı bir ad yazın ve ardından **Tamam**' a tıklayın.

    > [!NOTE]
    > Mevcut bir çözüme bir iş akışı konsol uygulaması eklemek istiyorsanız, bu çözümü [!INCLUDE[vs2010](../includes/vs2010-md.md)] açın, **Çözüm Gezgini**çözüme sağ tıklayın ve **Ekle**, **Yeni proje..** . öğesini seçin. **Yeni proje** iletişim kutusunu açmak için. Bu yordamda yukarıda açıklanan şekilde ilerleyin.

8. Proje şablonu XAML 'de bir etkinlik tanımı oluşturur. [!INCLUDE[wfd1](../includes/wfd1-md.md)] açılır ve özel etkinliğinizin tuvali görüntülenir.

9. **Araç kutusundan** bir etkinliği özel etkinliğinizden dahil etmek için tasarım yüzeyine sürükleyin.

    > [!CAUTION]
    > Özel etkinliğinizin gövdesinde yalnızca bir alt etkinliğe izin verilir; Ancak, bu alt etkinlik <xref:System.Activities.Statements.Sequence> etkinliği veya <xref:System.Activities.Statements.Flowchart> etkinliği gibi bir bileşik etkinlik olabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır:](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [iş akışı projesi oluşturma](../workflow-designer/creating-a-workflow-project.md) etkinliği oluşturma