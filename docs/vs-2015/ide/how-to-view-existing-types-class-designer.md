---
title: 'Nasıl yapılır: varolan türleri görüntüleme (Sınıf Tasarımcısı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 925220d583695e0116fb5901d92626bfcfa7450f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670539"
---
# <a name="how-to-view-existing-types-class-designer"></a>Nasıl Yapılır: Varolan Türleri Görüntüleme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Var olan bir türü ve üyelerini görmek için, şeklini bir sınıf diyagramına ekleyin.

 Yerel ve başvurulan türleri görebilirsiniz. Yerel bir tür o anda açık olan projede mevcuttur ve okunur/yazılır. Başvurulan tür başka bir projede ya da başvurulan bir derlemede bulunur ve salt okunur özelliktedir.

 Sınıf diyagramlarında yeni türler tasarlamak için bkz. [nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](../ide/how-to-create-types-by-using-class-designer.md).

### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Projedeki türleri bir sınıf diyagramı üzerinde görmek için

1. Çözüm Gezgini'ndeki bir projeden varolan bir sınıf diyagramı (.cd) dosyası açın. Ya da hiçbir sınıf diyagramı yoksa, projeye yeni bir sınıf diyagramı ekleyin. Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. Çözüm Gezgini'ndeki projeden bir kaynak kodu dosyasını sınıf diyagramına sürükleyin.

   > [!WARNING]
   > Çözümünüz birden çok uygulama arasında kod paylaşan bir proje içeriyorsa, dosyaları veya kodu yalnızca şu kaynaklardan bir sınıf diyagramına sürükleyebilirsiniz:
   >
   > - Diyagramı içeren uygulama projesi
   >   - Uygulama Projesi tarafından içeri aktarılan paylaşılan bir proje
   >   - Başvurulan bir proje
   >   - Bir derleme

    Kaynak kodu dosyasında tanımlı türleri temsil eden şekiller, diyagram üzerinde dosyayı sürüklediğiniz konumda görünür.

   Sınıf Görünümü'ndeki proje düğümünden bir veya daha fazla türü sınıf diyagramına sürükleyerek projedeki türleri de görüntüleyebilirsiniz.

> [!TIP]
> Sınıf Görünümü açık değilse, **Görünüm** menüsünden sınıf görünümü açın. Sınıf Görünümü hakkında daha fazla bilgi için bkz. [sınıfları ve üyelerini görüntüleme](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

 Diyagramdaki varsayılan konumlarda türleri görüntülemek için Sınıf Görünümü bir veya daha fazla tür seçin, seçili türlere sağ tıklayın ve **sınıf diyagramını görüntüle**' yi seçin.

> [!NOTE]
> Türü içeren bir kapalı sınıf diyagramı projede zaten varsa, sınıf diyagramı açılarak tür şeklini görüntüler. Ancak, proje içinde bu türü içeren hiçbir sınıf diyagramı yoksa, Sınıf Tasarımcısı proje içinde yeni bir sınıf diyagramı oluşturur ve bu diyagramı açarak türü görüntüler.

 Bir türü diyagram üzerinde ilk kez görüntülediğinizde, bu türe ait şekil varsayılan olarak daraltılmış görünür. Şekli genişleterek içeriğini görüntüleyebilirsiniz.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Bir proje içeriğini bir sınıf diyagramında göstermek için

1. Çözüm Gezgini veya Sınıf Görünümü ' de projeye sağ tıklayın ve **görüntüle**' yi seçin ve ardından **sınıf diyagramını görüntüle**' yi seçin.

     Otomatik olarak doldurulan bir Sınıf Diyagramı oluşturulur.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: türler arasında devralmayı görüntüleme (sınıf Tasarımcısı)](../ide/how-to-view-inheritance-between-types-class-designer.md) [nasıl yapılır: sınıf diyagramlarını özelleştirme (sınıf Tasarımcısı)](../ide/how-to-customize-class-diagrams-class-designer.md) [türleri ve ilişkileri görüntüleme (sınıf Tasarımcısı)](../ide/viewing-types-and-relationships-class-designer.md)
